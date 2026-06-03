# Security Policy

## 范围

本 monorepo 为 **文档型 Agent Skill 集合**，不含服务端运行时。主要风险是 **误提交机密** 或在 Issue/PR 中粘贴真实令牌。

## 请勿提交或公开分享

| 类别 | 说明 |
|------|------|
| 飞书应用密钥与令牌 | App Secret、OAuth token、真实 `space_id` / `node_token` 等 — 详见 [requirements-to-prd/SECURITY.md](requirements-to-prd/SECURITY.md) |
| API / 模型 / 数据库密钥 | 见 [prd-to-dev-spec/SECURITY.md](prd-to-dev-spec/SECURITY.md)、[engineering-delivery/SECURITY.md](engineering-delivery/SECURITY.md) |
| 本地覆盖 | `*.local.md`、`.env*` — 已在 [.gitignore](.gitignore) 忽略 |

## 各技能细则

- [requirements-to-prd/SECURITY.md](requirements-to-prd/SECURITY.md) — 飞书 / `lark-cli`
- [prd-to-dev-spec/SECURITY.md](prd-to-dev-spec/SECURITY.md) — 开发说明与脚本草案
- [engineering-delivery/SECURITY.md](engineering-delivery/SECURITY.md) — 分工、DB 脚本、AI 任务卡边界

## 报告安全问题

若仓库历史中含有效密钥，或技能说明鼓励不安全做法，请 **不要** 在公开 Issue 粘贴完整机密。通过 GitHub 私密报告（若已启用）或私信维护者，说明路径、影响与建议修复。
