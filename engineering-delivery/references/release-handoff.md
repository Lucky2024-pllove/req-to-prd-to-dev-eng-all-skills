# Release And Handoff

Use this reference for release readiness and final development handoff.

## Release Checklist

| Item | Evidence |
|------|----------|
| Scope confirmed | PRD/dev spec version |
| Tests complete | Test report or manual verification |
| CI passes | Pipeline link or local command output |
| Config ready | Env vars, feature flags, secrets |
| Data scripts reviewed | DBA/data engineer signoff when applicable |
| Rollback plan | Steps and trigger condition |
| Monitoring ready | Logs, metrics, alert, audit |
| Known issues | Owner and mitigation |

## Rollback Plan

```markdown
| Trigger | Action | Owner | Data impact | Verification |
|---------|--------|-------|-------------|--------------|
```

## Handoff Package

At completion, prepare:

1. Implementation summary
2. Linked PR/issues/tasks
3. Test evidence
4. Known issues and risks
5. Deployment notes
6. Rollback notes
7. Database script status, if any
8. Operations/monitoring notes

## Daily/Stage Sync

For team execution, short updates should include:

```text
Done:
Next:
Blocked:
Risk:
Need decision:
```
