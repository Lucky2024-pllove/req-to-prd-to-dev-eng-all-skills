# Pseudocode Guide

Use this reference when key functionality needs clearer developer handoff.

## When To Add Pseudocode

Add pseudocode for a function or process when it is:

- Core to the MVP or release risk
- Algorithmic or calculation-heavy
- Permission-sensitive
- Data-sensitive or transaction-like
- Stateful or workflow-driven
- Integration-heavy
- Batch/job/scheduled
- AI-related or prompt orchestration
- Error-prone, concurrent, idempotent, or rollback-sensitive

Do not add pseudocode for every simple UI action. A button that only opens a modal usually needs a button behavior table, not pseudocode.

## Style

- Keep it language-neutral unless the user specifies a stack.
- Use clear control flow: validate, authorize, load data, process, persist, emit event, log, handle errors.
- Include failure and fallback branches.
- Reference FR/AC/BR/NFR IDs.
- Avoid implementation-specific library calls unless already chosen.

## Function Pseudocode Template

```text
function {function_name}(input, actor):
  # Related: FR-..., AC-..., BR-...
  validate input
  if input invalid:
    return validation_error

  check actor permission
  if permission denied:
    audit denied action
    return forbidden

  load required data
  if required data missing:
    return not_found_or_empty_state

  apply business rules
  if business rule fails:
    return business_error

  persist changes or calculate result
  emit event or update downstream state if needed
  write audit log without sensitive data
  return success result
```

## AI Orchestration Pseudocode

```text
function run_ai_capability(input, actor):
  validate input and redact sensitive fields
  build prompt variables
  call model with timeout
  if model timeout or unavailable:
    return fallback_result

  parse structured output
  if output invalid:
    repair_or_reject output

  evaluate confidence
  if confidence below threshold:
    mark result as needs_human_confirmation

  persist result, prompt version, model version, and audit summary
  return result
```

## Data/Transaction Pseudocode

```text
function update_business_object(input, actor):
  begin transaction
  lock or reload current object state
  verify state transition is allowed
  apply changes
  write audit log
  commit transaction
  on failure:
    rollback transaction
    return error with trace id
```

## Pseudocode Trace Table

```markdown
| 功能 | 伪代码名称 | 触发原因 | 关联FR/AC/BR | 测试关注点 |
|------|------------|----------|--------------|------------|
```
