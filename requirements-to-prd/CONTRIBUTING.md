# Contributing to requirements-to-prd

感谢关注本技能。本仓库为 **Agent Skill**（`SKILL.md` + 参考资料 + demo），不含可执行应用代码。

## 适合贡献的内容

- `SKILL.md` 模板、自检清单、工作流说明的改进
- `references/` 中自撰方法论文档的修订（勿随意改动上游 lark 快照的正文，除非同步更新出处说明）
- `demo/` 金样与回归记录的更新
- `README.md` / `README.en.md` 的安装、示例提示、安全说明
- 与新版 `@larksuite/cli` 行为一致的命令示例（须注明 CLI 版本或验证日期）

## 暂不适合通过 PR 提交的内容

- 飞书 **App Secret**、OAuth token、私钥、真实 `space_id` / `parent_node_token` 等（见 [SECURITY.md](SECURITY.md)）
- 未经说明的大段上游文档复制（应保留许可证与出处）

## 提交方式

1. 先开 **Issue** 描述问题或改进方向（小修可直接 PR）。
2. Fork 后基于 `main` 开分支，保持改动聚焦单一主题。
3. PR 说明请包含：**改了什么**、**为什么**、**如何验证**（例如对照 `demo/TEST-RUN.md` 或 SKILL Self-Check）。
4. 若改动影响输出结构，请同步更新 `demo/` 金样或注明「金样待后续迭代」。

## 风格约定

- 主技能元数据（`SKILL.md` frontmatter 的 `name` / `description`）保持英文，便于跨 Agent 发现。
- 正文与用户可见交付物默认支持中文；用户明确要求英文时以英文为准。
- Mermaid 遵循 [references/mermaid-compatibility.md](references/mermaid-compatibility.md)。

## 许可证

对本仓库 **原创部分** 的贡献以 [LICENSE](LICENSE)（MIT）为准。`references/` 内上游快照遵循各自原许可证，见 [references/README.md](references/README.md)。
