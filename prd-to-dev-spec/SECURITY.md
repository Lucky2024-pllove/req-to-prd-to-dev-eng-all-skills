# Security Policy

## 范围

`prd-to-dev-spec` 是 **文档型 Agent Skill**，不连接数据库、不执行迁移脚本。风险主要来自交付物或 Issue/PR 中**泄露密钥/内网信息**。

## 请勿提交或公开分享

| 类别 | 示例 |
|------|------|
| API 与模型密钥 | 网关 API Key、LLM provider key |
| 数据库与中间件 | 连接串、密码、生产 schema 快照含真实 PII |
| 内网拓扑 | 未公开 URL、真实服务名、VPN 内网段 |
| 样例数据 | 未脱敏手机号、身份证、银行卡号 |

`.gitignore` 已忽略 `*.local.md` 与 `.env*`；提交前请自检。

## 数据库脚本边界

本技能生成的 SQL/迁移/回滚/校验内容均为 **draft / not executed / requires DBA or data engineer review**。若在 PR 或 demo 中包含 SQL，不得含硬编码凭据；不得暗示 Agent 已连接目标库。

## 报告安全问题

若发现仓库含有效密钥，或技能说明弱化人工审阅边界，请通过 GitHub 私密报告渠道或私信维护者，附**路径、影响、建议修复**，勿在公开 Issue 粘贴机密全文。
