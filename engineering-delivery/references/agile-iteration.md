# Agile Version Iteration And Sprint Delivery

Use this reference when approved product and technical materials must become an agile or phased engineering execution plan.

## Goals

- Convert PRD/dev-spec versions into executable releases and Sprints.
- Ensure all PRD FR/AC/TC are planned, deferred, blocked, or explicitly out of scope.
- Keep every Sprint independently reviewable with clear Definition of Done.
- Preserve AI coding agent boundaries and human review gates.

## Required Tables

### Release And Sprint Plan

| Release | Sprint | Goal | Included FR/AC/TC | Key Tasks | Owner | Exit Criteria |
|---------|--------|------|-------------------|-----------|-------|---------------|

### Full Coverage Matrix

| FR | AC | TC | Version/Release | Sprint/Backlog | Task ID | Owner | Status |
|----|----|----|-----------------|----------------|---------|-------|--------|

### Backlog And Deferral Register

| Item | Related FR/AC | Reason Deferred | Dependency/Trigger | Owner | Review Timing |
|------|---------------|-----------------|--------------------|-------|---------------|

## Sprint Planning Rules

1. A Sprint should have a coherent goal, not just a pile of unrelated tasks.
2. Split tasks so each can be validated by tests, review evidence, or stakeholder review.
3. Include setup work only when it is tied to a release goal or explicit prerequisite.
4. Keep cross-functional dependencies visible: frontend/backend/data/QA/DevOps/AI owner.
5. Put risky integration, data, security, AI evaluation, and deployment work early enough to avoid late discovery.
6. Do not add product scope inside engineering tasks. Route scope changes back to PRD/dev spec review.

## Sprint Definition Of Done

Each Sprint should define evidence for:

- Implemented FR/AC/TC scope.
- Unit/integration/UI/manual test result, as applicable.
- Code review and quality gate result.
- Updated docs, API contracts, diagrams, or task cards when changed.
- Release/rollback readiness for releasable increments.
- Open defects, blockers, and backlog changes.

## AI Coding Agent Task Cards

For AI-executable tasks, include the version/release/Sprint label in every task card and report. The task card must preserve allowed files/modules, forbidden actions, validation commands, failure handling, and final report format.

## Self-Check

- No FR/AC/TC is missing from the coverage matrix.
- Every planned task has owner, dependency, estimate, acceptance link, and completion standard.
- Deferred items have reasons and review triggers.
- Sprint and release gates include evidence, not just status words.
