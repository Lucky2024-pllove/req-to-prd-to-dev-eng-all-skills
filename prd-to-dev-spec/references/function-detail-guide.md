# Function Detail Guide

Use this reference when writing the technical module and detailed function sections.

## Function Detail Minimum

For each menu/page/function, include:

| Field | Description |
|-------|-------------|
| Menu/function name | User-facing name plus internal module/function name |
| Entry | Navigation path, route, API endpoint, scheduled trigger, or event |
| Role/permission | Visible, editable, approvable, exportable roles |
| Inputs | User inputs, query params, uploaded files, external payloads |
| Buttons/controls | Button name, state, action, validation, confirmation |
| Business logic | Rules, calculations, workflow, state transition |
| Data logic | Create/read/update/delete fields, defaults, derived fields |
| Output | UI result, persisted data, event, file, notification |
| Exceptions | Empty, invalid, duplicate, conflict, timeout, permission denied |
| Logs/audit | Operation log, audit log, sensitive data exclusions |
| Related PRD | FR/AC/BR/NFR |

## Button Detail Table

```markdown
| 按钮/控件 | 位置 | 默认状态 | 启用条件 | 点击/变更行为 | 二次确认 | 成功反馈 | 失败反馈 | 关联逻辑 |
|-----------|------|----------|----------|----------------|----------|----------|----------|----------|
```

## Low-Fidelity Prototype Sketches

Use one of these formats:

### Page Layout Table

```markdown
| 区域 | 内容 | 交互 |
|------|------|------|
| 顶部筛选区 | 日期、状态、关键字 | 查询、重置 |
| 列表区 | 表格字段... | 分页、排序 |
| 操作区 | 新增、编辑、删除 | 按权限展示 |
```

### ASCII Sketch

```text
+------------------------------------------------+
| Page Title                         [Primary]   |
+------------------------------------------------+
| Filter A [____]  Filter B [v]      [Search]    |
+------------------------------------------------+
| Table: col1 | col2 | status | actions          |
+------------------------------------------------+
```

### State Table

```markdown
| 状态 | 可见按钮 | 禁用按钮 | 允许操作 | 下一状态 |
|------|----------|----------|----------|----------|
```

## Data Logic Detail

Separate business meaning from storage:

| Field | Business Meaning | Source | Storage/Type | Validation | Default/Derived | Write Timing |
|-------|------------------|--------|--------------|------------|-----------------|--------------|

## Common Missing Details

- Button disabled conditions
- Duplicate submission handling
- Empty-state display
- Permission-denied behavior
- Batch operation partial success
- Data refresh timing
- Audit log content
- Export scope and sensitive field masking
