# Contributing to prd-to-dev-spec

感谢关注本技能。本仓库为 **Agent Skill**（`SKILL.md` + `references/` + `demo/`），产出为 Markdown 开发说明、测试用例与确认单，不含可执行应用代码。

## 适合贡献的内容

- `SKILL.md` 章节结构、Operating Rules、Self-Check 的改进
- `references/` 专题指南（开发说明结构、功能细节、伪代码、用例设计、确认单、AI 实施、数据库脚本规范等）
- `demo/` 输入与轻量金样的更新
- `README.md` / `README.en.md` 的使用示例与兼容说明
- `agents/openai.yaml` 的宿主适配示例（注明目标平台）

## 暂不适合通过 PR 提交的内容

- API Key、数据库连接串、生产 JWT、未脱敏个人数据样例（见 [SECURITY.md](SECURITY.md)）
- 与 PRD 范围无关的大段臆造需求（技能应强调 FR/AC 可追溯）

## 提交方式

1. 大改前先开 **Issue**；文档小修可直接 PR。
2. Fork 后基于 `main` 开分支，单次 PR 聚焦一个主题。
3. PR 说明包含：**改动摘要**、**验证方式**（对照 `SKILL.md` Self-Check 或 `demo/TEST-RUN.md`）。
4. 若调整默认交付物结构，请同步更新 `demo/` 金样或在 PR 中说明后续跟进。

## 风格约定

- `SKILL.md` frontmatter 保持英文；正文与交付物语言跟随用户请求。
- 保持 `FA → FR → AC → 模块/API/TC/任务` 追溯链表述一致。
- Mermaid 遵循 [references/mermaid-compatibility.md](references/mermaid-compatibility.md)。

## 许可证

贡献以 [LICENSE](LICENSE)（MIT）为准。
