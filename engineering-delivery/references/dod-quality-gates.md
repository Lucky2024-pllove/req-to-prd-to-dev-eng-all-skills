# Definition Of Done And Quality Gates

Adapted from `ENGINEERING.md`.

## Minimum DoD

Before marking a task done:

1. Functional behavior in the accepted scope works or is demonstrable.
2. Tests are complete for the relevant level; bug fixes include regression proof.
3. Static checks such as lint/typecheck pass according to project configuration.
4. Documentation is updated when external behavior, API, config, or operation changes.
5. No known high-risk secret/token/permission issue is introduced.

## Test Layers

| Layer | Purpose |
|-------|---------|
| Unit | Pure logic, branches, boundaries |
| Integration | DB, queue, external service contracts |
| API/contract | Request/response stability |
| E2E/smoke | Critical user journey |

## Quality Gates

| Gate | Required Evidence |
|------|-------------------|
| Development ready | Approved scope, task owner, environment ready |
| Code review ready | Diff summary, linked task, test evidence |
| Test ready | Build passes, test data ready, QA scope clear |
| Release ready | CI passes, rollback plan, deployment notes |
| Done | Acceptance evidence, known issues logged, handoff complete |

## Artifact Review Gates

| Artifact | Required Review |
|----------|-----------------|
| Agent workflow/design | Product, tech, and QA confirm responsibilities, tool/data permissions, sequence flow, human review, fallback, and monitoring |
| Pseudocode | Tech lead confirms branch logic, edge cases, permissions, and data consistency |
| AI Prompt Package | Product, tech, and QA confirm prompt goal, schema, safety, fallback, and evaluation samples |
| Mermaid diagrams | Product/tech/QA confirm diagrams match PRD/dev spec and task split |
| API/data contract | Frontend/backend/data/QA confirm fields, errors, permissions, and compatibility |
| SQL drafts | DBA/data engineer confirms backup, impact, rollback, and verification before execution |

## Code Review Checklist

- [ ] Scope matches PRD/dev spec.
- [ ] Code is readable and follows project conventions.
- [ ] Edge cases and permission checks are covered.
- [ ] Data changes are backward compatible or have migration plan.
- [ ] Tests or manual verification steps are attached.
- [ ] Logs avoid sensitive data.

## CI Guidance

Use the repository's existing CI as source of truth. Typical gates include lint, typecheck, unit tests, integration tests, and build. Do not lower thresholds silently; record technical debt if a gate cannot pass.
