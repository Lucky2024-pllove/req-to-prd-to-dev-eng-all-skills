# Database Change Control

This reference encodes the database safety rule: **generate scripts only; human DBA/data engineer reviews and executes**.

## Hard Boundary

When database work is involved, the AI should:

1. Generate SQL/migration script drafts.
2. Generate rollback script drafts.
3. Generate verification/check script drafts.
4. Split scripts by change type and by database/table/object.
5. Explain execution order, prerequisites, and risk.
6. Mark all scripts as **DRAFT / NOT EXECUTED**.
7. Require human DBA/data engineer approval, backup, execution, and verification.

The AI should not directly operate production, staging, or target business databases unless the user explicitly requests and approves a safe local/dev action. Production-like operations remain human-owned.

## Script Package

Prefer a project-level script folder:

```text
{project-name}-db-scripts/
  001_create_database_{database}.sql
  010_create_table_{table}.sql
  020_alter_table_{table}.sql
  025_create_index_{table}_{index}.sql
  030_seed_data_{table}.sql
  040_update_data_{table}.sql
  050_migrate_data_{table}.sql
  090_rollback_{table_or_change}.sql
  100_verify_{table_or_change}.sql
```

Use one file per change type and target. For example, create separate scripts for `order_header` table creation, `order_line` table creation, `order_header` data backfill, and `order_header` verification.

## Migration Script Header

```sql
-- Project: {project-name}
-- Script: {file-name}
-- Type: DDL | DML | Migration | Rollback | Verification
-- Target: {database}.{schema}.{table_or_object}
-- Purpose: {change purpose}
-- Source: PRD/DevSpec version
-- Status: DRAFT, NOT EXECUTED
-- Reviewer: DBA/Data Engineer required
-- Preconditions:
-- Execution order:
-- Rollback script:
-- Verification script:
```

## Split Rules

| Change | File pattern | Rule |
|--------|--------------|------|
| Database/schema creation | `001_create_database_{database}.sql` | One database/schema per script. Include charset/collation/owner notes when known. |
| Table creation | `010_create_table_{table}.sql` | One table per script. Include primary key, constraints, comments, and nullable defaults. |
| Table alteration | `020_alter_table_{table}.sql` | One table per script. Split high-risk column rename/drop from additive changes. |
| Index/constraint creation | `025_create_index_{table}_{index}.sql` | One index/constraint per script when lock/performance risk exists. |
| Seed/reference data | `030_seed_data_{table}.sql` | One table per script. Make inserts idempotent where the SQL dialect supports it. |
| Data creation/update/correction | `040_update_data_{table}.sql` | One table or business change per script. Require WHERE conditions, impact estimate, and before/after verification. |
| Data migration/backfill | `050_migrate_data_{table}.sql` | One table or bounded migration per script. Include batching/locking notes for large data. |
| Rollback/compensation | `090_rollback_{table_or_change}.sql` | Pair with the relevant forward script. State when rollback is impossible and provide compensation. |
| Verification | `100_verify_{table_or_change}.sql` | Pair with forward/rollback scripts. Include counts, constraints, samples, and anomaly checks. |

## Review Checklist

- [ ] Backup or restore point confirmed.
- [ ] DDL/DML impact understood.
- [ ] Backward compatibility checked.
- [ ] Index and execution plan reviewed when needed.
- [ ] Locking and runtime impact considered.
- [ ] Rollback path tested or manually verified.
- [ ] Verification query confirms expected result.
- [ ] Sensitive data is masked in logs/examples.

## Common Script Types

| Type | Notes |
|------|-------|
| DDL | Tables, columns, indexes, constraints |
| DML | Backfill, correction, reference data |
| Migration | Ordered change with compatibility notes |
| Rollback | Reverse or compensating operation |
| Verification | Counts, constraints, sample checks |

## DML Safety Rules

- Require an explicit `WHERE` condition for update/delete scripts unless the task is intentionally full-table and DBA-approved.
- Include an impact estimate query before destructive or bulk DML.
- Prefer idempotent seed scripts.
- Keep sensitive values out of script bodies and examples.
- For large tables, include batching, lock, timeout, and off-peak execution notes.

## Output Wording

Always include:

```text
以下 SQL 为草案，尚未执行。需由 DBA/数据工程师在目标环境审核、备份、评估影响后执行。
```
