# prd-to-dev-spec · Demo 与回归

本目录仅用于维护者回归验证，不作为日常生成上下文。正常使用 [../SKILL.md](../SKILL.md) 时，不应读取本目录，除非用户明确要求检查 demo 或做回归。

固定输入用于验证技能是否能输出三份协调文档：**开发说明**、**测试用例**、**开发任务确认单**。

## 文件

| 文件 | 说明 |
|------|------|
| [input-prd.md](input-prd.md) | 已评审 PRD 摘录（DailyBill 场景；测试时勿改**核心 FR/AC 编号**） |
| [expected-dev-spec.md](expected-dev-spec.md) | 开发说明轻量金样 |
| [expected-test-cases.md](expected-test-cases.md) | 测试用例轻量金样 |
| [expected-task-confirmation.md](expected-task-confirmation.md) | 开发任务确认单轻量金样 |
| [TEST-RUN.md](TEST-RUN.md) | 每次回归的简要记录（可追加） |

完整 PRD 金样见同级流水线技能 [`requirements-to-prd`](../../requirements-to-prd/demo/expected-prd.md)（可选对照）。

## 如何通过自检

对照 [../SKILL.md](../SKILL.md) **Self-Check**：

- [ ] 输入 tied 到 PRD 版本/状态
- [ ] 未静默扩 scope
- [ ] 核心功能含菜单/控件/业务逻辑/数据逻辑/异常/追溯
- [ ] 测试用例回溯 FR/AC，覆盖权限/边界/异常
- [ ] 确认单列出阻塞项、owner、完成标准  
- [ ] 开发说明含菜单/控件、API、数据逻辑、关键伪代码（或说明省略原因）  
- [ ] 确认单标明是否 AI 编码及 engineering-delivery 四件套/AIC  

**与金样比较**：不必逐字相同，但三文档的 FR/AC/TC 追溯关系应一致。追溯矩阵可对照 [requirements-to-prd/demo/expected-traceability.md](../../requirements-to-prd/demo/expected-traceability.md)。

## 与仓库关系

- 本技能根目录为 `prd-to-dev-spec/`。
- 上游：`requirements-to-prd`；下游：`engineering-delivery`。
- 密钥与内网标识勿入公开库：见 [../README.md](../README.md) 与 [../SECURITY.md](../SECURITY.md)。
