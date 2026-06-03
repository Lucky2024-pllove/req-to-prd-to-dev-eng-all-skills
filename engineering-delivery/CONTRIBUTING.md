# Contributing to engineering-delivery

感谢关注本技能。本仓库为 **Agent Skill**，在 PRD / 开发说明 / 测试用例 / 确认单对齐后，产出分工计划、todolist、工程交付检查清单及（按需）数据库脚本草案与 AI 任务卡。

## 适合贡献的内容

- `SKILL.md` 任务分级（S/M/L）、Hard Rules、Self-Check 的改进
- `references/`（团队工作流、DoD/门禁、ADR、发布交接、数据库变更边界、跨 Agent 兼容等）
- `demo/` 输入与轻量金样
- `README.md` / `README.en.md` 示例提示
- `agents/openai.yaml` 宿主声明示例

## 暂不适合通过 PR 提交的内容

- 数据库 URL、密码、云服务密钥、真实生产库名/主机（见 [SECURITY.md](SECURITY.md)）
- 声称「已在某环境执行」的 SQL（本技能只产出**待人工审阅的脚本草案**）

## 提交方式

1. 结构性改动建议先开 **Issue**。
2. PR 说明包含验证方式：对照 Self-Check、RACI/DoD 是否可追溯至 FR/AC/TC；若改动 AI 编码路径，对照 `demo/expected-ai-agent-task-cards.md` 与 todolist 的 `AIC-` 链接。
3. 涉及数据库脚本模板变更时，在 PR 中强调 **draft / not executed / requires DBA review** 边界未弱化。

## 风格约定

- 任务必须可追溯至已批准材料或显式标注的「未批准草案」。
- AI Agent 任务卡须保留「一次一任务、敏感变更须人工确认」类约束。
- Mermaid 遵循 [references/mermaid-compatibility.md](references/mermaid-compatibility.md)。

## 许可证

贡献以 [LICENSE](LICENSE)（MIT）为准。
