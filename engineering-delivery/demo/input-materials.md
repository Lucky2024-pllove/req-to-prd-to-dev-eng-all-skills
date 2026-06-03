# 回归 / Demo 输入：已对齐材料摘要

> 场景：DailyBill · 用例 UC-DEMO-ENG-01。材料为**拟批准基线**（回归用）。  
> **AI 编码**：是（示范 Agent 可执行任务卡）。

## 元数据

| 项 | 值 |
|----|-----|
| 项目名 | DailyBill |
| 批准状态 | 拟批准（回归标注；正式项目须书面批准） |
| AI 编码 | 是 · 须产出 AI-Agent 任务卡 |
| 完整上游 | [prd-to-dev-spec/demo/](../../prd-to-dev-spec/demo/) |

## 范围与 FR/AC（摘要）

| FR | 简述 | AC |
|----|------|-----|
| FR-001 | 单条收支 CRUD | AC-01 |
| FR-006 | 缺金额不可保存 | AC-03 |
| FR-004 | 周期分析汇总 | AC-04 |

## 模块（来自开发说明摘要）

- M-01 记账：记一笔、流水列表
- M-02 分析：汇总与建议

## 测试用例（摘要）

TC-001（AC-01）、TC-002（AC-02）、TC-003（AC-03）、TC-004（AC-04）、TC-005（AC-05）

## 开放问题（来自确认单）

- OQ-01 端形态未定 → **阻塞 AIC 实现类任务直至关闭或书面默认 Web MVP**
- OQ-02 分类学习是否 V1 纳入

## 预期输出文件名

```text
DailyBill-开发分工计划.md
DailyBill-todolist.md
DailyBill-工程交付检查清单.md
DailyBill-AI-Agent任务卡.md
```

**说明**：本 demo 不含数据库变更；若扩展 DB 场景，另建用例并附 `{project-name}-db-scripts/` 草案。
