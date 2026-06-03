# DailyBill todolist

> **修订说明**：v0.2 · 含 AI 任务卡链接（回归金样）  
> **追溯**：[input-materials.md](input-materials.md) · 任务卡 [expected-ai-agent-task-cards.md](expected-ai-agent-task-cards.md)

## M0 开发准备

- [ ] 确认 PRD/开发说明/测试用例版本与范围（文首版本号一致）
- [ ] 关闭或书面默认 OQ-01（端形态）— 产品 · **阻塞一切 AIC 实现类任务**

## M1 记账闭环

- [ ] T-01 实现 POST/GET `/api/transactions`（FR-001, TC-001；**AIC-001**） — 后端
- [ ] T-02 记一笔表单与缺金额提示（FR-006, TC-003；**AIC-002**；依赖 T-01） — 前端
- [ ] T-02a 分类建议展示接口对接（FR-002, TC-002） — 前后端 · *暂无 AIC（人工拆分或后续补 AIC-003）*
- [ ] QA-01 执行 TC-001、TC-002、TC-003 — QA

## M2 分析

- [ ] T-03 分析汇总 API（FR-004, TC-004） — 后端
- [ ] T-04 分析页 UI + 建议区（FR-005, TC-005） — 前端
- [ ] QA-02 执行 TC-004、TC-005 — QA

## 阻塞

- [ ] 关闭 OQ-01（端形态）— 产品 · 阻塞 M1 联调环境决策
