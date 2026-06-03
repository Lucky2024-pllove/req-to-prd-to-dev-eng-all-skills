# Security Policy

## 范围

`requirements-to-prd` 是 **文档型 Agent Skill**，不包含服务端运行时、不托管用户数据。主要风险来自**误提交机密**或**在 Issue/PR 中粘贴真实令牌**。

## 请勿提交或公开分享

| 类别 | 示例 |
|------|------|
| 飞书应用密钥 | App Secret、`client_secret` |
| 令牌 | `user_access_token`、`tenant_access_token`、`refresh_token` |
| 私钥与证书 | RSA/EC 私钥、`.pem`、JWT 签名密钥 |
| 租户资源标识 | 真实 `space_id`、`parent_node_token`、`file_token`（公开库请用占位符，见 `references/wiki-archive-defaults*.md`） |

本地覆盖文件（如 `*.local.md`、`.env`）已在 [.gitignore](.gitignore) 中忽略；提交前请 `git status` 自检。

## 报告安全问题

若发现：

- 仓库历史中意外包含有效密钥或令牌
- 技能说明鼓励不安全做法（例如要求 Agent 明文输出 token）

请 **不要** 在公开 Issue 中粘贴完整机密。优先：

1. 通过 GitHub **Private vulnerability reporting**（若仓库已启用），或
2. 向维护者私信，说明**文件路径、 commit（如有）、影响面与复现步骤**。

维护者确认后会协调**轮换密钥、历史清理（如需要）、文档修订**。

## 飞书集成

使用 `lark-cli` 时，认证与 scope 管理遵循 [references/lark-shared-SKILL.md](references/lark-shared-SKILL.md)。本技能默认**不假设**已配置飞书；未配置时只交付 Markdown。
