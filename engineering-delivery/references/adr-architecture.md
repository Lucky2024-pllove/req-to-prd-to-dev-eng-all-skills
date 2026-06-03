# ADR, Architecture, Security, And NFR

Adapted from `ENGINEERING.md`.

## ADR Triggers

Suggest an ADR when work involves:

- Cross-module or cross-service boundary changes
- Persistence/schema strategy changes
- Major dependency replacement
- Security model changes
- Deployment/runtime topology changes
- Data migration or rollback assumptions
- High-cost irreversible technical choices

## ADR Template

```markdown
# ADR-{number}: {decision title}

## Status
Proposed | Accepted | Superseded

## Context

## Decision

## Alternatives Considered

## Consequences

## Rollback Or Revisit Trigger
```

## NFR Topics

For L-level work, at least consider relevant items:

| Topic | Questions |
|-------|-----------|
| Performance | Latency, throughput, data volume |
| Availability | SLO, failure handling, fallback |
| Consistency | Transaction, eventual consistency, compensation |
| Security | Secrets, permissions, tenant/data boundaries |
| Observability | Logs, metrics, trace IDs, audit |
| Compatibility | Existing API/data/client compatibility |
| Operations | Deploy, rollback, config, migration |

## Security Baseline

- Use environment variables or secret management for secrets.
- Do not commit real secrets or tokens.
- Prefer least privilege.
- Document permission changes and sensitive data handling.
- For multi-tenant or sensitive data, describe access boundaries explicitly.
