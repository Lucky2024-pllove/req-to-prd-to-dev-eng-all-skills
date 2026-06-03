# Agile Iteration Mapping For Development Specifications

Use this reference when converting a PRD with MVP/V1, roadmap, backlog, Sprint, or agile planning into developer-facing documents.

## Goals

- Preserve the PRD's version boundaries while adding technical detail.
- Make sure every FR/AC has a delivery home: version, iteration, backlog, or out of scope.
- Connect version planning to modules, APIs, data work, tests, and task confirmation.
- Prepare clean handoff to `engineering-delivery`.

## Required Mapping

| FA | FR | AC | Version/Iteration | Module/Menu | API/Data/Event | Test Case | Dev Task | Status |
|----|----|----|-------------------|-------------|----------------|-----------|----------|--------|

## Mapping Rules

1. Start with PRD version assignments. If missing, infer cautiously from priority, dependencies, and MVP scenario, and mark the inference.
2. Keep MVP/V1 as a complete closed-loop delivery. Do not split it into only foundations unless the PRD explicitly defines a foundation-only release.
3. Put cross-cutting work such as auth, data model, CI, observability, migration, or AI evaluation into the earliest version that depends on it.
4. Attach test cases to the same version as the FR/AC they validate.
5. Attach open questions, blockers, and owner confirmation to the affected version.
6. Do not move backlog or out-of-scope items into implementation tasks unless a PRD change review approves it.

## Dev Spec Additions

Add these sections when applicable:

- Version/Iteration Scope Matrix
- Technical Prerequisites By Version
- Version-Based Test Scope
- Deferred Backlog And Out-of-Scope Register
- Handoff Notes For Engineering Delivery

## Self-Check

- Every FR/AC has a version/backlog/out-of-scope status.
- Every MVP/V1 item has enough module/API/data/test detail to be implemented.
- Later-version items are not over-specified beyond what is useful for sequencing.
- Deferred items are visible in the handoff checklist.
