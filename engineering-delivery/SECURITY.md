# Security Policy

## 范围

`engineering-delivery` 是 **文档型 Agent Skill**，组织工程分工与交付检查清单。本技能**禁止** Agent 直连或修改目标数据库；风险来自误提交连接串、密钥或在任务卡中扩大 AI 自主执行范围。

## 请勿提交或公开分享

| 类别 | 示例 |
|------|------|
| 连接串与密钥 | 数据库 URL、密码、云访问密钥 |
| 生产标识 | 真实库名、内网主机、租户 ID |
| CI/CD 机密 | 部署 token、kubeconfig、webhook secret |
| 脚本中的凭据 | 迁移 SQL 硬编码 password |

`.gitignore` 已忽略 `*.local.md` 与 `.env*`。

## AI 执行边界

AI Agent 任务卡应保留：一次一任务、涉及生产/凭据/架构/依赖变更须人工确认。若 PR 削弱此类约束，请在 Review 中重点讨论。

## 报告安全问题

发现有效密钥入库或 unsafe 指引时，请通过私密渠道联系维护者，勿在公开 Issue 粘贴机密。
