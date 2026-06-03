# Test Case Design

Use this reference to derive test cases from PRD acceptance criteria and development logic.

## Derivation Chain

```text
FR -> AC -> business rule -> data logic -> permission -> exception -> TC
```

Do not create test cases from assumptions unless marked.

## Test Types

| Type | Coverage |
|------|----------|
| Functional | Main user/system paths |
| Validation | Required fields, format, range, duplicates |
| Permission | Visible/use/edit/export/approve denial and allow cases |
| State | State transition and forbidden transition |
| Data consistency | Totals, derived fields, persistence, rollback |
| Integration | API success/failure, timeout, retry, idempotency |
| UI behavior | Button state, confirmation, loading, empty state |
| NFR | Performance, security, compatibility, audit |
| Regression | High-risk changed behavior |
| AI | Low confidence, fallback, correction, unsafe/invalid output |

## Test Case Table

```markdown
| TC | 关联FR/AC | 模块/功能 | 优先级 | 类型 | 前置条件 | 测试数据 | 步骤 | 预期结果 |
|----|-----------|-----------|--------|------|----------|----------|------|----------|
```

## Priority

| Priority | Meaning |
|----------|---------|
| P0 | Blocks release or core MVP |
| P1 | Important path or high-risk exception |
| P2 | Secondary path, compatibility, polish |

## Coverage Checklist

- [ ] Every AC has at least one P0/P1 TC.
- [ ] Every business rule has positive and negative cases when applicable.
- [ ] Every required field has missing/invalid tests.
- [ ] Every role has allow/deny tests.
- [ ] Every state transition has allowed/forbidden tests.
- [ ] Every external dependency has success/failure tests.
- [ ] Every AI capability has quality and fallback tests.
- [ ] Every high-risk NFR has a verification method.
