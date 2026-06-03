# AI Coding Agent Execution

Use this reference when tasks may be executed by Codex, Claude Code, Cursor, or another AI coding agent.

**Generation template**: When producing deliverables, use the **AI Agent Task Cards** section in `SKILL.md` (field names in Chinese table headers). This file keeps the English field names for the same columns; do not omit fields such as **Read first**, **Manual verification**, or **Database/script scope**.

## Core Principle

Engineering delivery documents should be readable by humans and executable by AI coding agents. A task is AI-executable only when it has:

- Clear input documents
- Explicit allowed and forbidden scope
- Step-by-step execution guidance
- Validation commands or manual verification steps
- Failure/blocked handling
- Required final report format

## Vibe Coding Safety Rules

1. Execute one task card at a time.
2. Do not expand PRD/dev spec scope.
3. Do not modify unrelated files.
4. Do not introduce new frameworks or large dependencies without human approval.
5. Do not execute database changes; generate script drafts only for human DBA/data engineer review and execution.
6. Do not modify production config, credentials, secrets, CI/CD permissions, or deployment targets without explicit approval.
7. Stop and ask when requirements conflict, source documents disagree, or acceptance criteria are unclear.
8. Always report changed files, validation results, risks, and open questions.

## AI Agent Task Card Template

```markdown
## AIC-{number} {task name}

| Field | Content |
|-------|---------|
| Task goal | ... |
| Human owner | ... |
| AI executor | Codex / Claude Code / Cursor / other |
| Source docs | PRD v..., DevSpec v..., TC..., ADR... |
| Related task | T-... (assignment plan / todolist) |
| Related requirement | FR-... / AC-... / TC-... |
| Allowed scope | directories/files/modules |
| Forbidden scope | unrelated modules, DB execution, prod config, secrets, new large deps |
| Database/script scope | none / generate draft SQL only / affected tables and script file names |
| Read first | files/docs to inspect before editing |
| Execution steps | 1. ... 2. ... 3. ... |
| Validation commands | ... |
| Manual verification | ... |
| Completion standard | ... |
| Failure handling | ... |
| Final report format | changed files + summary + tests + risks + questions |
```

## Database Script Task Card Add-on

When an AI task card includes database work, add this block:

```markdown
### Database Script Boundary

| Field | Content |
|-------|---------|
| Execution permission | Generate draft scripts only; do not connect to or modify target databases |
| Script package | {project-name}-db-scripts/ |
| Split rule | Split by type and by database/table/object |
| Required scripts | 001_create_database_... / 010_create_table_... / 040_update_data_... / 090_rollback_... / 100_verify_... |
| Human reviewer | DBA / data engineer |
| Human execution prerequisites | approval, backup/restore point, target environment confirmation, execution window |
| Validation evidence | verification SQL draft, expected counts/constraints/samples |
```

## AI Final Report Format

```markdown
## AIC-{number} Execution Report

- **Status**: Done / Blocked / Partial
- **Changed files**:
- **Completed requirements**:
- **Validation run**:
- **Validation result**:
- **Known risks**:
- **Needs human confirmation**:
- **Scope not touched**:
```

## Human Review Checklist

- [ ] Task stayed within allowed scope.
- [ ] No prohibited database/production/secret/dependency action occurred.
- [ ] Database-related work, if any, produced draft scripts only and did not execute target database changes.
- [ ] Changed files match the task card.
- [ ] Tests or verification steps are reported.
- [ ] Any failed validation has a clear explanation.
- [ ] Open questions are routed to owner.
