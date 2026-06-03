# DailyBill 开发任务确认单

> **PRD 版本**：v0.1（草案）  **日期**：2026-06-03  
> **追溯**：[input-prd.md](input-prd.md) · [expected-dev-spec.md](expected-dev-spec.md)

## 1. 输入与状态

| 文档 | 版本/状态 |
|------|-----------|
| PRD | v0.1 草案 — 回归用例，正式开发前须基线 |
| 开发说明 | [expected-dev-spec.md](expected-dev-spec.md) v0.1 |
| 测试用例 | [expected-test-cases.md](expected-test-cases.md) |
| 追溯矩阵 | [expected-traceability.md](../../requirements-to-prd/demo/expected-traceability.md) |

## 2. 开放问题（阻塞项）

| ID | 问题 | Owner | 影响 | 状态 |
|----|------|-------|------|------|
| OQ-01 | 端形态（Web/App） | 产品 | 技术选型、AIC 环境 | 未关闭 · 可书面默认 Web MVP |
| OQ-02 | 分类学习是否 V1 | 产品+架构 | FR-003 | 未关闭 |

## 3. 开发前确认清单

| 检查项 | 产品 | 研发 | QA | 备注 |
|--------|:----:|:----:|:--:|------|
| FR/AC 与开发说明一致 | ☐ | ☐ | ☐ | |
| 测试用例覆盖 AC-01～05 | ☐ | ☐ | ☐ | 见 TC-001/002/003/004/005 |
| Out of Scope 未误入开发说明 | ☐ | ☐ | ☐ | |
| 关键功能含伪代码/接口/数据逻辑 | ☐ | ☐ | — | 记一笔 §4.2 |
| 数据库变更仅草案、未执行 | ☐ | ☐ | — | 本用例 N/A |

## 4. 工程交付与 AI 编码（下游 skills 3）

| 检查项 | 状态 | Owner | 说明 |
|--------|------|-------|------|
| 是否由编码 Agent 实现 | 是（回归假设） | 技术负责人 | 须走 `engineering-delivery` **四件套** |
| 须产出 AI-Agent 任务卡 | ☐ 已计划 | 技术负责人 | `{project}-AI-Agent任务卡.md` |
| todolist 实现项链接 AIC | ☐ 已计划 | 技术负责人 | 一次一卡 |
| 分工计划含完成标准/估时 | ☐ 已计划 | 技术负责人 | |

## 5. 开工条件

- [ ] PRD 基线或书面接受「草案开发」风险
- [ ] OQ-01 有结论或 **书面默认 Web MVP**（阻塞 AIC 实现类任务直至满足）
- [ ] 确认单三方签字（或回归标注「拟批准」）
