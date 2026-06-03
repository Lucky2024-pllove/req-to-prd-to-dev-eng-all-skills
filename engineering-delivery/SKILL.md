---
name: engineering-delivery
description: >-
  Turn confirmed PRD, development specification, test cases, and task confirmation materials into
  human-and-AI executable engineering artifacts: development assignment plan, RACI, todolist.md,
  AI coding agent task cards, Definition of Done, quality gates, ADR suggestions, review checklist,
  release/rollback checklist, and engineering collaboration rules. Use after PRD, dev spec, and
  test cases are approved to organize team assignments, engineering standards, AI/vibe coding
  execution, DoD, CI gates, code review, ADRs, release and rollback planning, database script
  packages split by change type and database/table/object, Agent workflow reviews, prompt package
  reviews, pseudocode reviews, and Mermaid-based artifacts. Database work must generate
  SQL/migration/rollback/check scripts for human DBA/data engineer review and execution, not
  directly operate target databases. Outputs are portable across Codex, Claude Code, Cursor, and
  other Markdown-capable agents.
---

# Engineering Delivery

Use this skill after product and technical documents are approved:

```text
Requirement analysis + PRD
-> development specification + test cases + development task confirmation
-> engineering-delivery
-> team assignments + todolist + DoD + gates + ADR/release/data checklists
```

Default deliverables:

```text
{project-name}-开发分工计划.md
{project-name}-todolist.md
{project-name}-工程交付检查清单.md
{project-name}-AI-Agent任务卡.md
```

If database changes are involved, also generate a reviewed script package draft. Split scripts by change type and by database/table/object; do not merge unrelated database, table, data update, rollback, or verification work into one large SQL file.

```text
{project-name}-db-scripts/
  001_create_database_{database}.sql
  010_create_table_{table}.sql
  020_alter_table_{table}.sql
  025_create_index_{table}_{index}.sql
  030_seed_data_{table}.sql
  040_update_data_{table}.sql
  050_migrate_data_{table}.sql
  090_rollback_{table_or_change}.sql
  100_verify_{table_or_change}.sql
```

### Deliverable sets (pick by scenario)

| Scenario | Required Markdown outputs | Notes |
|----------|---------------------------|-------|
| **Human-led scheduling** (default) | Assignment plan + todolist + delivery checklist | RACI, milestones, DoD; no AI task cards required |
| **AI coding / vibe coding / handoff to coding agents** | Above **plus** `{project-name}-AI-Agent任务卡.md` | Every **implementation** todolist item must link `AIC-xxx`; agents execute **one card at a time** |
| **Database change** | Above + `{project-name}-db-scripts/` draft package | Scripts are DRAFT / NOT EXECUTED; human DBA/data engineer executes |

If the user does not specify, ask whether coding agents will implement tasks. When yes (or when the user says AI programming / vibe coding), always include AI Agent task cards even if other outputs stay lightweight.

## Hard Rules

1. Treat approved PRD/dev spec/test cases as the source of truth. Do not change scope silently.
2. Produce executable team tasks with owner, dependency, priority, acceptance link, estimate, and completion standard.
3. Use RACI for multi-role collaboration.
4. Every task should trace to FR/AC/TC or a documented engineering prerequisite.
5. Treat dev-spec Agent workflow, Agent responsibilities, AI Prompt Packages, pseudocode, diagrams, API/data contracts, and test cases as reviewable engineering artifacts with owners and quality gates.
6. Use Definition of Done and quality gates before marking work complete.
7. Suggest ADRs for major architecture, data, dependency, security, AI, prompt governance, or deployment decisions.
8. For database work, **generate SQL/migration/rollback/check scripts only**. Do not execute against production or target databases. Split scripts by change type and database/table/object, and require human DBA/data engineer review, approval, backup, and execution.
9. Mermaid diagrams must use cross-platform compatible syntax. Use English/digit/underscore IDs, put Chinese in display labels or aliases, avoid high-risk edge-label syntax such as `-.label.->`, keep version numbers and punctuation-heavy text out of edge labels, and run a Mermaid compatibility self-check before delivery.
10. If a development finding changes product scope, route it back to PRD/dev spec change review instead of burying it inside code tasks.
11. For AI coding/vibe coding, tasks must include machine-readable execution boundaries: allowed files/modules, forbidden actions, input docs, execution steps, validation commands, failure handling, and reporting format.
12. AI coding agents must execute one task card at a time, avoid scope creep, avoid destructive operations, avoid direct database execution, and stop for human confirmation when requirements conflict or permissions are unclear.

## Reference Loading

Load only what is needed:

| Need | Reference |
|------|-----------|
| Team workflow, task levels, roles | [references/team-workflow.md](references/team-workflow.md) |
| DoD, testing, CI, review gates | [references/dod-quality-gates.md](references/dod-quality-gates.md) |
| ADR, architecture, security, NFR | [references/adr-architecture.md](references/adr-architecture.md) |
| Database scripts and data engineer boundary | [references/database-change-control.md](references/database-change-control.md) |
| Release, rollback, delivery package | [references/release-handoff.md](references/release-handoff.md) |
| Cross-agent portability | [references/agent-compatibility.md](references/agent-compatibility.md) |
| Mermaid rendering compatibility | [references/mermaid-compatibility.md](references/mermaid-compatibility.md) |
| AI coding agent execution | [references/ai-agent-execution.md](references/ai-agent-execution.md) |

## Agent Compatibility

Keep outputs portable across Codex, Claude Code, Cursor, and other Markdown-capable agents:

- Use plain Markdown, checklists, tables, Mermaid diagrams, ASCII sketches, and code blocks.
- Keep pseudocode and Prompt Packages in Markdown/code blocks.
- Make tasks readable by both humans and AI coding agents.
- Do not depend on proprietary task/project/design/prompt tools unless the user explicitly asks.
- If an agent cannot load `references/`, inline the relevant reference rules.
- If an agent cannot write files, output intended file names and Markdown bodies in chat.

## Bilingual Usage

Match the user's requested output language. If the user writes in Chinese or does not specify a language, Chinese output is acceptable; if the user asks for English, produce English documents. Keep frontmatter metadata in English for cross-agent compatibility.

Common Chinese requests that should trigger this skill include:

- 团队分工
- 开发规范 / 工程规范
- 研发协作
- AI编程 / vibe coding
- AI任务卡 / Agent执行任务
- todolist / DoD / ADR
- CI门禁 / 代码评审
- 发布回滚
- 数据库变更 / SQL脚本 / 迁移脚本
- Prompt包评审 / 伪代码评审

## Workflow

### 1. Intake

Extract:

| Item | Output |
|------|--------|
| Project name | Use source document title |
| Source documents | PRD, dev spec, test cases, task confirmation |
| Baseline status | Approved / pending / unknown |
| Scope | V1/MVP, out of scope |
| Modules/functions | From dev spec |
| Agent workflow | Agent flow, responsibilities, tool/data permissions, sequence diagrams |
| Pseudocode | Key-function pseudocode from dev spec |
| Prompt packages | AI Prompt Packages from dev spec |
| Diagrams | Mermaid architecture/flow/sequence/state/ER diagrams |
| Test scope | From test cases |
| Technical risks | Architecture, data, security, deployment, external dependencies |
| Team roles | Product, tech lead, frontend, backend, QA, data engineer/DBA, DevOps, reviewer |
| AI coding context | Whether tasks may be executed by AI coding agents, and required boundaries |

If source documents are not approved, mark outputs as **execution draft based on unapproved inputs**.

### 2. Task Level And Execution Strategy

Classify work:

| Level | Use For | Planning Depth |
|-------|---------|----------------|
| S | Single small fix/config/doc update | Short todolist and direct DoD |
| M | One module/function or local refactor | Normal task plan, tests, risks |
| L | New subsystem, cross-service, data/security/deployment change | Full RACI, ADR, rollout, rollback, quality gates |

### 3. Team Assignment Plan

Produce:

1. Role map
2. RACI table
3. Module/function ownership
4. Agent workflow/Pseudocode/Prompt Package/API/data/diagram review ownership
5. Dependency graph or dependency table
6. Task list grouped by milestone
7. Risk/blocker register
8. Communication cadence and escalation rule
9. AI coding agent execution boundaries when applicable

### 4. Todolist

Write a `todolist.md` style plan:

- Use checkboxes.
- Start every item with an action verb.
- Include linked FR/AC/TC where applicable.
- Preserve sequence and dependencies.
- Add a revision note if the plan changes materially.
- For AI-executable tasks, include a linked AI Agent task card ID.

### 5. Quality Gates

Define gates:

1. Development ready
2. Code review ready
3. Test ready
4. Release ready
5. Done

Each gate should list evidence required: tests, screenshots/logs, scripts, review signoff, CI result, or manual verification steps.

Artifact-specific gate examples:

| Artifact | Gate Evidence |
|----------|---------------|
| Agent workflow/design | Reviewed by product/tech/QA; responsibilities, permissions, sequence, fallback are clear |
| Pseudocode | Reviewed by tech lead; maps to FR/AC/TC; edge cases covered |
| AI Prompt Package | Reviewed by product/tech/QA; schema, safety, fallback, evaluation samples present |
| Mermaid diagrams | Reviewed for consistency with dev spec and task split |
| API/data contract | Reviewed by frontend/backend/data owner |
| AI Agent task card | Contains input docs, allowed/forbidden scope, execution steps, validation commands, failure handling, and report format |

### 6. AI Coding Agent Execution

When the team uses AI programming/vibe coding (or the user says coding agents will implement work), generate `{project-name}-AI-Agent任务卡.md` and task cards that an AI coding agent can execute directly:

1. One task card per coherent development task.
2. Include input documents and relevant FR/AC/TC.
3. State allowed and forbidden files/modules/actions.
4. Provide execution steps and validation commands.
5. Define failure/blocked handling.
6. Define final report format.
7. Mark database, production, credential, dependency, and architecture changes that require human approval.

### 7. Database Change Control

When database/schema/data migration is involved:

1. Assign data engineer/DBA review responsibility.
2. Generate a database script package manifest.
3. Split SQL drafts by type and target: database creation, table creation, table alteration, index/constraint changes, seed data, data update/correction, data migration/backfill, rollback, and verification.
4. Use deterministic file names such as `001_create_database_{database}.sql`, `010_create_table_{table}.sql`, `040_update_data_{table}.sql`, `090_rollback_{table_or_change}.sql`, and `100_verify_{table_or_change}.sql`.
5. Mark every script as **DRAFT / NOT EXECUTED** and requiring human approval.
6. Include execution order, dependency, backup, timing, compatibility, rollback, and verification notes.
7. Put each script-producing task under DBA/data engineer review in the RACI and quality gates.

Never claim a database change has been applied unless the user provides execution evidence.

## Output Templates

### Development Assignment Plan

```markdown
# {项目名} 开发分工计划

> **依据文档**：PRD / 开发说明 / 测试用例 / 开发任务确认单
> **状态**：草案 | 已确认

## 1. 输入与范围

## 2. 团队角色与职责
| 角色 | 人员/占位 | 职责 | 备注 |
|------|-----------|------|------|

## 3. RACI
| 工作项 | R 负责 | A 审批 | C 咨询 | I 知会 |
|--------|--------|--------|--------|--------|

## 4. 模块/功能归属
| 模块/功能 | Owner | 协作方 | 关联FR/AC/TC | 备注 |
|-----------|-------|--------|--------------|------|

## 5. 关键工程制品归属
| 制品 | Owner | Reviewer | 关联模块/功能 | 通过标准 |
|------|-------|----------|---------------|----------|
| Agent工作流/职责 | 技术负责人/AI负责人 | 产品+技术+测试 | ... | 职责、权限、时序、兜底清晰 |
| 关键逻辑伪代码 | 技术负责人/开发 | 技术负责人 | ... | 覆盖核心分支与异常 |
| AI Prompt包 | AI/后端 | 产品+测试+技术 | ... | Schema/兜底/样例齐全 |
| Mermaid图 | 技术负责人 | 产品+开发+测试 | ... | 与开发说明一致 |
| API/数据契约 | 后端/数据 | 前端+测试 | ... | 字段、错误码、权限明确 |

## 6. 任务依赖与里程碑
| 任务ID | 任务 | 模块 | FR/AC/TC | 优先级 | 估时 | 依赖 | Owner | 完成标准 | AIC（若 AI 编码） |
|--------|------|------|----------|--------|------|------|-------|----------|-------------------|
| T-01 | ... | ... | FR-001 / AC-01 / TC-001 | P0 | 2d | — | 后端 | TC-001 通过；API 与开发说明一致 | AIC-001 |

## 7. 风险、阻塞与升级
```

### Todolist

```markdown
# {项目名} todolist

> **修订说明**：v0.1 初版；依据已确认开发说明与测试用例生成。

## M1 开发准备
- [ ] 确认 PRD/开发说明/测试用例版本与范围
- [ ] 确认环境、依赖、权限与配置

## M2 功能开发
- [ ] 实现 ...（关联 FR-... / AC-... / TC-...；AI任务卡：AIC-...）

## M3 测试与修复
- [ ] 执行 P0/P1 测试用例并记录结果

## M4 发布准备
- [ ] 完成回滚方案与发布验证清单
```

### AI Agent Task Cards

Use the same field set as [references/ai-agent-execution.md](references/ai-agent-execution.md). One card per coherent dev task; link from todolist and assignment plan (`T-...` / `AIC-...`).

```markdown
# {项目名} AI-Agent任务卡

> **用途**：供 Codex / Claude Code / Cursor 等 AI 编程 Agent 与人类开发共同执行。
> **执行原则**：一次只执行一个任务卡；不得扩大范围；遇到冲突、开放问题未关闭或高风险操作先停止并请求人工确认。

## AIC-001 {任务名称}

| 项 | 内容 |
|----|------|
| 任务目标 | ... |
| 人工负责人 | ... |
| AI 执行方 | Codex / Claude Code / Cursor / 其他 |
| 关联任务 | T-...（分工计划 / todolist） |
| 关联需求 | FR-... / AC-... / TC-... |
| 输入文档 | PRD v...；开发说明 v...；测试用例 v...；（可选）工程交付检查清单 |
| 先读再改 | 须先阅读的文件/文档路径列表 |
| 允许修改 | 目录/文件/模块（尽量具体，如 `backend/src/api/transactions/`） |
| 禁止修改 | 无关模块；目标库执行/迁移；生产配置；密钥；未经批准的大依赖 |
| 数据库/脚本范围 | 无 / 仅生成草案 SQL（列脚本文件名） |
| 执行步骤 | 1. ... 2. ... 3. ... |
| 验证命令 | `npm test` / `pytest ...` / 等可复制命令；无自动化则写「无，见手工验证」 |
| 手工验证 | 与 TC-... 对应的步骤（若自动化不足） |
| 完成标准 | 可判定通过/失败（对齐 TC/AC） |
| 失败处理 | 测试失败、需求冲突、OQ 未关闭 → 停止并提问 |
| 回报格式 | 见下方「AIC-001 执行报告」模板 |

### AIC-001 执行报告（Agent 完成后填写）

| 项 | 内容 |
|----|------|
| 状态 | Done / Blocked / Partial |
| 变更文件 | ... |
| 已完成需求 | FR-... / TC-... |
| 验证执行 | 命令与结果 |
| 已知风险 | ... |
| 需人工确认 | ... |
| 未触碰范围 | ... |
```

### Delivery Checklist

```markdown
# {项目名} 工程交付检查清单

## 1. Definition of Done
| 项 | 要求 | 证据 | 状态 |
|----|------|------|------|

## 2. 质量门禁
| 门禁 | 检查项 | 负责人 | 通过标准 |
|------|--------|--------|----------|

## 3. ADR 建议
| ADR | 触发原因 | 决策范围 | Owner | 状态 |
|-----|----------|----------|-------|------|

## 4. 工程制品评审
| 制品 | 检查项 | 负责人 | 通过标准 | 状态 |
|------|--------|--------|----------|------|
| Agent工作流 | 职责、工具权限、时序、人审、兜底 | 产品/技术/测试 | 与PRD和开发说明一致 | ... |
| 伪代码 | 核心逻辑、异常、权限、数据一致性 | 技术负责人 | 与FR/AC/TC一致 | ... |
| Prompt包 | System/User Prompt、Schema、兜底、评估样例 | 产品/技术/测试 | 可测试、可回滚、可监控 | ... |
| Mermaid图 | 流程/时序/状态/ER/架构 | 技术负责人 | 与开发任务一致 | ... |
| AI任务卡 | 输入、边界、步骤、验证、回报格式 | 技术负责人 | AI可直接执行且不越权 | ... |

## 5. 发布与回滚
| 项 | 内容 | Owner | 状态 |
|----|------|-------|------|

## 6. 数据库/数据变更（如适用）
> 以下 SQL / migration 脚本均为草案，尚未执行。需由 DBA / 数据工程师在目标环境审核、备份、评估影响后执行。AI Agent 不得直接执行目标数据库变更。

### 6.1 脚本包清单
| 脚本文件 | 类型 | 目标数据库/表/对象 | 用途 | 状态 | 人工处理人 | 执行顺序 |
|---------|------|-------------------|------|------|------------|----------|
| 001_create_database_{database}.sql | DDL-数据库创建 | {database} | 创建数据库/Schema | DRAFT / NOT EXECUTED | DBA/数据工程师 | 1 |
| 010_create_table_{table}.sql | DDL-表创建 | {table} | 创建数据表 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 2 |
| 020_alter_table_{table}.sql | DDL-表结构修改 | {table} | 字段/约束变更 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 3 |
| 025_create_index_{table}_{index}.sql | DDL-索引/约束 | {table}.{index} | 新增索引/约束 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 4 |
| 030_seed_data_{table}.sql | DML-初始化数据 | {table} | 基础字典/配置数据 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 5 |
| 040_update_data_{table}.sql | DML-数据创建/修改 | {table} | 数据修正/批量更新 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 6 |
| 050_migrate_data_{table}.sql | Migration-数据迁移 | {table} | 回填/迁移/兼容处理 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 7 |
| 090_rollback_{table_or_change}.sql | Rollback | {table_or_change} | 回滚或补偿 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 应急 |
| 100_verify_{table_or_change}.sql | Verification | {table_or_change} | 校验数量/约束/样例 | DRAFT / NOT EXECUTED | DBA/数据工程师 | 执行后 |

### 6.2 数据库任务门禁
| 检查项 | 通过标准 | 负责人 | 状态 |
|-------|----------|--------|------|
| 脚本拆分 | 已按类型、数据库、表或对象拆分，避免大而全脚本 | 技术负责人/DBA | ... |
| 审核边界 | 所有脚本均标记未执行，并指定 DBA/数据工程师审核执行 | 技术负责人 | ... |
| 回滚校验 | 每个高风险变更有回滚/补偿与校验脚本 | DBA/数据工程师 | ... |
| AI执行边界 | AI任务卡禁止直接连接或修改目标数据库 | 技术负责人 | ... |
```

## Self-Check

- [ ] Source document versions and approval state are explicit.
- [ ] Tasks trace to FR/AC/TC or engineering prerequisites.
- [ ] RACI and owners are clear.
- [ ] DoD and quality gates include evidence.
- [ ] ADR triggers are listed for major decisions.
- [ ] Agent workflow/design, pseudocode, Prompt Packages, diagrams, API/data contracts, and tests have explicit owners and review gates when present.
- [ ] Outputs use Markdown/Mermaid/code blocks so they can be used in Codex, Claude Code, Cursor, and similar agents.
- [ ] Every Mermaid block passes compatibility checks: closed code fence, valid diagram type, English IDs, Chinese only in labels/aliases, no high-risk edge labels such as `-.label.->`, and no punctuation-heavy labels on edges.
- [ ] When AI coding/vibe coding is in scope, `{project-name}-AI-Agent任务卡.md` is included (not only the human scheduling triad).
- [ ] Every **implementation** todolist item links to an `AIC-xxx` that exists in the task-card file.
- [ ] AI Agent task cards include: input docs, read-first paths, allowed/forbidden scope, steps, validation commands, manual verification when needed, failure handling, and report format (aligned with `references/ai-agent-execution.md`).
- [ ] AI Agent task cards enforce one-task-at-a-time execution and human confirmation for scope, database, production, credential, dependency, or architecture changes.
- [ ] Assignment-plan tasks include priority, estimate, and completion standard when the plan is used for execution (not only high-level RACI).
- [ ] Quality gates use measurable pass criteria or are explicitly marked **human gate only** (avoid vague placeholders such as “TBD” without owner).
- [ ] Database work generates scripts only, splits scripts by type and database/table/object, and clearly says human review/execution is required.
- [ ] Scope changes are routed back to PRD/dev spec review.
