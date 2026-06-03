# Contributing

本仓库为 **monorepo**，包含三条可独立挂载的 Agent Skill 流水线。欢迎 Issue / PR。

贡献者名单见 [CONTRIBUTORS.md](CONTRIBUTORS.md)（含维护者与 Codex / OpenAI AI 辅助说明）。

## 仓库结构

| 子目录 | 技能 | 何时改这里 |
|--------|------|------------|
| [requirements-to-prd/](requirements-to-prd/) | 用户需求 → 需求分析 + PRD | 需求拆解、PRD 模板、方法论 references |
| [prd-to-dev-spec/](prd-to-dev-spec/) | PRD → 开发说明 + 测试用例 + 确认单 | 研发交接、追溯链、伪代码/AI 实施 |
| [engineering-delivery/](engineering-delivery/) | 定稿材料 → 分工 / todolist / 交付清单 | RACI、DoD、ADR、DB 脚本草案边界 |

各子目录另有专属贡献说明：**[requirements-to-prd/CONTRIBUTING.md](requirements-to-prd/CONTRIBUTING.md)** · **[prd-to-dev-spec/CONTRIBUTING.md](prd-to-dev-spec/CONTRIBUTING.md)** · **[engineering-delivery/CONTRIBUTING.md](engineering-delivery/CONTRIBUTING.md)**。技能专属规则以子目录为准。

## 提交流程

1. 先确认改动属于哪个子目录；跨技能模板联动（如 FR/AC 命名、demo 金样）请在 PR 中一并说明。
2. Fork → 基于 `main` 开分支，单次 PR 聚焦一个主题。
3. PR 说明包含：**改了什么**、**为什么**、**如何验证**（可引用对应 `demo/TEST-RUN.md` 或 `SKILL.md` Self-Check）。
4. 勿提交密钥、token、未脱敏业务机密；见 [SECURITY.md](SECURITY.md)。

## Demo 回归（可选）

三技能共用 **DailyBill** 轻量用例，可按流水线顺序回归：

```
requirements-to-prd/demo → prd-to-dev-spec/demo → engineering-delivery/demo
```

不必逐字与金样相同，但 **FR/AC/TC 追溯关系** 应一致；全链路 **AC 编号统一为 `AC-{nn}`**（勿混用 `AC-001`）；`requirements-to-prd/demo/expected-traceability.md` 可作追溯参照。`engineering-delivery` 若按 AI 编码场景回归，还应具备 **AIC 任务卡** 且实现类 todolist 项链接 `AIC-xxx`。

## 许可证

本仓库原创部分以根目录 [LICENSE](LICENSE)（MIT）为准。
