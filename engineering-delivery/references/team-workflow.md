# Team Workflow

This reference is adapted from `E:\AI\MySkills\ENGINEERING.md` for skill use.

## Core Workflow

```text
Receive confirmed docs
-> clarify priority and DoD
-> classify task level
-> assign roles
-> create/update todolist
-> create AI Agent task cards when AI coding is used
-> implement by sequence
-> test and CI
-> review
-> release/handoff
```

## Task Levels

| Level | Typical Work | Required Planning |
|-------|--------------|-------------------|
| S | Small single-file fix, copy, config typo | Minimal plan and risk note |
| M | Single module/function, local refactor, one bug root cause | Normal plan, tradeoffs, tests |
| L | New subsystem, cross-service migration, security/data/deployment change | Full plan, RACI, ADR, rollback, quality gates |

## Role Lenses

Use these as thinking lenses, not fixed org roles:

| Lens | Focus |
|------|-------|
| Architect | Boundaries, interfaces, NFR, ADR |
| Clean code engineer | Readability, naming, maintainability, error handling |
| Debug/security engineer | Failure modes, edge cases, performance, security |
| QA engineer | Test layers, regression, CI gates |
| Data engineer/DBA | Schema, migration, SQL, rollback, data quality |

## RACI

Use RACI when multiple people collaborate:

| Letter | Meaning |
|--------|---------|
| R | Responsible: does the work |
| A | Accountable: approves result |
| C | Consulted: provides input |
| I | Informed: kept aware |

## Todolist Rules

- Use checkboxes.
- Use action verbs.
- One item should be independently verifiable.
- Include dependency and FR/AC/TC references when possible.
- Include artifact review tasks for pseudocode, Prompt Packages, diagrams, API/data contracts, and SQL drafts when present.
- For AI coding, link todolist items to AI Agent task cards and include allowed/forbidden execution boundaries.
- If plan changes materially, add a revision note with reason and date.
- Focus on one coherent feature/PR at a time.

## Scope Change Rule

If implementation discovers a product scope issue, do not hide it in code. Route it back to PRD/dev spec review and document impact on schedule, risk, and tests.
