# engineering-delivery · Demo 与回归

本目录仅用于维护者回归验证，不作为日常生成上下文。正常使用 [../SKILL.md](../SKILL.md) 时，不应读取本目录，除非用户明确要求检查 demo 或做回归。

固定输入用于验证技能能否产出：

- **人排期三件套**：开发分工计划、todolist、工程交付检查清单  
- **AI 编码四件套**：上述三件套 + **AI-Agent 任务卡**（本 demo 默认按 AI 编码场景回归）

## 文件

| 文件 | 说明 |
|------|------|
| [input-materials.md](input-materials.md) | 已对齐材料摘要（DailyBill；含 AI 编码标记） |
| [expected-assignment-plan.md](expected-assignment-plan.md) | 开发分工计划轻量金样（含优先级/估时/完成标准/AIC 列） |
| [expected-todolist.md](expected-todolist.md) | todolist 轻量金样（实现项链接 AIC） |
| [expected-delivery-checklist.md](expected-delivery-checklist.md) | 工程交付检查清单（含 AIC 门禁） |
| [expected-ai-agent-task-cards.md](expected-ai-agent-task-cards.md) | **AI-Agent 任务卡金样**（AIC-001/002） |
| [TEST-RUN.md](TEST-RUN.md) | 回归记录 |

上游开发三件套金样见 [`prd-to-dev-spec/demo/`](../prd-to-dev-spec/demo/)。

## 如何通过自检

对照 [../SKILL.md](../SKILL.md) **Self-Check**：

- [ ] 源文档版本与批准状态明确
- [ ] 任务可追溯至 FR/AC/TC
- [ ] RACI 与 owner 清晰；分工计划含优先级、估时、完成标准
- [ ] DoD/门禁含可执行标准或标为人工门禁
- [ ] **AI 编码时**：存在任务卡文件；实现类 todolist 项链接 `AIC-xxx`
- [ ] 数据库工作仅为脚本草案且标注人工执行

## 与仓库关系

- 本技能根目录为 `engineering-delivery/`。
- 上游：`prd-to-dev-spec`；更上游：`requirements-to-prd`。
- 见 [../SECURITY.md](../SECURITY.md) 勿提交连接串与密钥。
