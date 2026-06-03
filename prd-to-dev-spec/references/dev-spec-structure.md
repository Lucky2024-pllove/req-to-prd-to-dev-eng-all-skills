# Development Specification Structure

Use this reference to transform PRD scope into implementable technical documentation.

## Source Priority

Use sources in this order:

1. Baselined PRD
2. Requirement analysis document
3. Reviewer comments or change notes
4. Existing system constraints provided by the user
5. Explicit assumptions, marked as assumptions

Do not invent implementation details that change product scope. If a technical choice affects scope, list it under open questions.

## Recommended Decomposition

```text
Product scope
-> modules
-> menus/pages/functions
-> APIs/events/jobs
-> data objects
-> database script drafts when storage changes
-> permissions
-> tests
-> tasks
```

## Module Table

```markdown
| 模块 | 职责 | 输入 | 处理 | 输出 | 关联菜单/功能 | 关联FR/AC |
|------|------|------|------|------|--------------|-----------|
```

## Diagram Guidance

Include diagrams when they clarify implementation:

| Need | Mermaid |
|------|---------|
| Module boundaries | `flowchart` |
| User/business workflow | `flowchart` |
| Frontend/backend/external calls | `sequenceDiagram` |
| Object lifecycle | `stateDiagram` |
| Data model | `erDiagram` |

Keep diagrams lightweight. The goal is shared understanding, not formal architecture ceremony. All diagrams must follow [mermaid-compatibility.md](mermaid-compatibility.md) before delivery.

## Mermaid Compatibility

Use cross-platform compatible Mermaid syntax:

- Use English/digit/underscore IDs for nodes, participants, entities, and classes.
- Put Chinese in node labels, aliases, notes, or nearby Markdown tables.
- Do not use high-risk edge-label syntax such as `-.label.->`.
- Keep `/`, brackets, colons, version numbers, decimals, and long business text out of edge labels when possible.
- In `sequenceDiagram`, use `participant Agent as 建模 Agent`.
- In `erDiagram`, entity names must be English IDs; explain Chinese names in tables.

## Technical Decision Record

When the PRD leaves room for implementation choice, add:

```markdown
| Decision | Options | Recommendation | Reason | Risk |
|----------|---------|----------------|--------|------|
```

## Traceability

Every implementation unit should connect back to PRD:

```text
FA -> FR -> AC -> Module -> Function/API/Data -> TC -> Task
```

## Database Script Handoff

When storage changes are required, the development specification should not only describe the data model. It should also list script drafts by type and table/object:

```markdown
| Script | Type | Object/Table | Purpose | Status | Reviewer |
|--------|------|--------------|---------|--------|----------|
```

All database scripts are drafts, not executed, and require DBA/data engineer review.
