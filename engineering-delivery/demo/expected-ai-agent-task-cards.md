# DailyBill AI-Agent任务卡

> **用途**：回归金样 · 供编码 Agent 与人类开发共同执行（DailyBill / UC-DEMO-ENG-01）  
> **执行原则**：一次只执行一张任务卡；不得扩大 PRD/开发说明范围；**OQ-01（端形态）未关闭时不得开始实现类任务**。  
> **输入**：[input-materials.md](input-materials.md) · 上游 [prd-to-dev-spec/demo/](../../prd-to-dev-spec/demo/)

---

## AIC-001 流水 CRUD API（POST/GET）

| 项 | 内容 |
|----|------|
| 任务目标 | 实现 `POST/GET /api/transactions`，支持单条收支流水创建与列表查询 |
| 人工负责人 | 后端 Owner |
| AI 执行方 | Cursor / Codex / Claude Code |
| 关联任务 | T-01 |
| 关联需求 | FR-001 / AC-01 / TC-001 |
| 输入文档 | [input-prd.md](../../prd-to-dev-spec/demo/input-prd.md) v0.1；[expected-dev-spec.md](../../prd-to-dev-spec/demo/expected-dev-spec.md) §3–§4 |
| 先读再改 | `backend/src/api/`（若不存在则按开发说明创建）；`backend/tests/` 中既有 API 测试模式 |
| 允许修改 | `backend/src/api/transactions/**`、`backend/src/routes/**`、`backend/tests/api/test_transactions*` |
| 禁止修改 | `frontend/**`；数据库迁移执行；`.env*`；CI/CD；无关模块 |
| 数据库/脚本范围 | 无（本用例无库表变更；若需持久化层仅 mock/内存实现并注明） |
| 执行步骤 | 1. 阅读开发说明 API 表与 FR-001 2. 实现 POST 创建与 GET 列表 3. 金额必填校验对齐 FR-006 共用校验层（可同 PR 但勿扩 scope 到前端） 4. 补充/更新 API 测试 |
| 验证命令 | `cd backend && npm test -- --grep transactions`（或项目等价命令；无则见手工验证） |
| 手工验证 | 按 TC-001：有效支出保存后列表可见 |
| 完成标准 | TC-001 通过；响应字段含 type/amount/occurred_at；与开发说明 API 一致 |
| 失败处理 | 测试失败则修复后重跑；需求与 PRD 冲突或 OQ-01 阻塞 → **停止**并列出问题 |
| 回报格式 | 使用下方「AIC-001 执行报告」 |

### AIC-001 执行报告（Agent 完成后填写）

| 项 | 内容 |
|----|------|
| 状态 | Done / Blocked / Partial |
| 变更文件 | （待填） |
| 已完成需求 | FR-001 / TC-001 |
| 验证执行 | （命令 + 结果） |
| 已知风险 | （待填） |
| 需人工确认 | （待填） |
| 未触碰范围 | frontend、DB 执行 |

---

## AIC-002 记一笔页与缺金额校验

| 项 | 内容 |
|----|------|
| 任务目标 | 记一笔表单：类型、金额、日期、备注；缺金额时阻断保存并提示 |
| 人工负责人 | 前端 Owner |
| AI 执行方 | Cursor / Codex / Claude Code |
| 关联任务 | T-02 |
| 关联需求 | FR-006 / AC-03 / TC-003 |
| 输入文档 | 同上 PRD/开发说明；依赖 **AIC-001 已完成** 或 API mock |
| 先读再改 | `frontend/src/pages/AddTransaction*`、`frontend/src/api/client*` |
| 允许修改 | `frontend/src/pages/**`、`frontend/src/components/**`、`frontend/src/api/**`、`frontend/tests/**` |
| 禁止修改 | `backend/**`（除非与 Owner 约定由本卡修复 API 契约 bug）；DB 执行；生产配置 |
| 数据库/脚本范围 | 无 |
| 执行步骤 | 1. 确认 API 基址与 OQ-01 默认（Web MVP） 2. 实现表单与保存 3. 空金额提交 → 提示、不调用保存 4. 联调或 mock TC-003 |
| 验证命令 | `cd frontend && npm test`；`npm run lint` |
| 手工验证 | TC-003：不填金额点保存 → 提示、无新记录 |
| 完成标准 | TC-003 通过；不破坏 TC-001 主路径 |
| 失败处理 | API 未就绪 → 标记 Blocked，请求先完成 AIC-001 |
| 回报格式 | 使用下方「AIC-002 执行报告」 |

### AIC-002 执行报告（Agent 完成后填写）

| 项 | 内容 |
|----|------|
| 状态 | Done / Blocked / Partial |
| 变更文件 | （待填） |
| 已完成需求 | FR-006 / TC-003 |
| 验证执行 | （待填） |
| 已知风险 | （待填） |
| 需人工确认 | （待填） |
| 未触碰范围 | backend（默认）、DB |

---

## 索引（与 todolist 对齐）

| AIC | 关联 todolist | FR/TC |
|-----|---------------|-------|
| AIC-001 | T-01 | FR-001, TC-001 |
| AIC-002 | T-02 | FR-006, TC-003 |

> T-03/T-04 等可在正式项目中按同模板追加 AIC-003、AIC-004；本 demo 仅示范 M1 两条实现任务。
