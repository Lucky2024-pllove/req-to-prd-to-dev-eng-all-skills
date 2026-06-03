# Database Script Specification

Use this reference when the development specification involves database, schema, table, index, seed data, data correction, migration, rollback, or verification work.

## Hard Boundary

Generate script drafts only. Do not execute scripts against target business databases.

Every script must be marked:

```text
Status: DRAFT, NOT EXECUTED
Reviewer: DBA/Data Engineer required
```

Human DBA/data engineer must review, back up, assess impact, and execute in the target environment.

## Split Rules

Split scripts by **change type** and by **database/table/object**.

Do not put unrelated tables or unrelated change types in one large script unless the change is a single atomic migration and the reason is documented.

## Script File Naming

Use sortable numeric prefixes:

```text
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

If multiple tables are involved:

```text
010_create_table_order.sql
011_create_table_order_item.sql
020_alter_table_order.sql
021_alter_table_order_item.sql
090_rollback_order_tables.sql
100_verify_order_tables.sql
```

## Script Types

| Type | File Pattern | Purpose |
|------|--------------|---------|
| Database creation | `001_create_database_{database}.sql` | Create database/schema/namespace |
| Table creation | `010_create_table_{table}.sql` | Create table and base constraints |
| Table alteration | `020_alter_table_{table}.sql` | Add/modify/drop columns or constraints |
| Index/constraint | `025_create_index_{table}_{index}.sql` | Add index/unique/check constraints |
| Seed/reference data | `030_seed_data_{table}.sql` | Insert dictionary/config/reference rows |
| Data correction | `040_update_data_{table}.sql` | Update existing rows with bounded condition |
| Migration/backfill | `050_migrate_data_{table}.sql` | Backfill derived fields or migrate structure |
| Rollback | `090_rollback_{change}.sql` | Reverse or compensate the change |
| Verification | `100_verify_{change}.sql` | Counts, constraints, samples, data quality |

## Script Header

```sql
-- Project: {project-name}
-- Script: {file-name}
-- Type: {database-create/table-create/table-alter/index/data-seed/data-update/data-migration/rollback/verification}
-- Object: {database/table/index/change}
-- Source: PRD/DevSpec version
-- Status: DRAFT, NOT EXECUTED
-- Reviewer: DBA/Data Engineer required
-- Preconditions:
-- Expected impact:
-- Rollback script:
-- Verification script:
```

## DML Safety Rules

For data creation/modification scripts:

- Use explicit columns in `INSERT`.
- Use bounded `WHERE` clauses for `UPDATE`/`DELETE`.
- Include preview/select queries before destructive or broad updates.
- Prefer idempotent patterns where possible.
- Include affected row expectations when known.
- Avoid production data literals unless provided and approved.

## Review Checklist

- [ ] Backup/restore point confirmed.
- [ ] Execution order documented.
- [ ] Rollback script exists or compensating action documented.
- [ ] Verification script exists.
- [ ] Locking/runtime impact considered.
- [ ] Index impact and execution plan considered when needed.
- [ ] Sensitive data is masked in examples/logs.
- [ ] Script is marked draft/not executed.
