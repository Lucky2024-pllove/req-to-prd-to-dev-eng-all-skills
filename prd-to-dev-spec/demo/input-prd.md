# 回归 / Demo 输入：PRD 摘录

> 场景：DailyBill 个人日账（与 `requirements-to-prd/demo` 同用例 UC-DEMO-BILL-01）。**不得修改**下列 FR/AC 编号，作为三件套输出的追溯输入。

## 元数据

| 项 | 值 |
|----|-----|
| 项目名 | DailyBill |
| 用例ID | UC-DEMO-BILL-DEV-01 |
| PRD 状态 | 草案 v0.1（回归用；正式项目应标注 Baselined） |
| 完整 PRD | 见 [`requirements-to-prd/demo/expected-prd.md`](../../requirements-to-prd/demo/expected-prd.md) |

## 范围摘要

- **V1**：单用户、手工录入收支、规则分类/标签、周期汇总、规则建议、用户可修正。
- **Out of Scope**：投资建议、支付直连、多人账本。

## 功能需求（EARS 摘录）

1. **FR-001** 系统应支持用户创建、查看、编辑与删除单条收支流水（类型、金额、日期、可选备注）。
2. **FR-002** 当用户保存新流水时，系统应展示建议类目与建议标签。
3. **FR-004** 系统应提供分析视图，按时间范围汇总收入、支出及类目构成。
4. **FR-005** 系统应基于汇总生成至少一条可读建议。
5. **FR-006** 若金额缺失或不可解析，系统不得保存并应提示补全。

## 验收标准（GWT 摘录）

| ID | 场景 | Given-When-Then | FR |
|----|------|-----------------|-----|
| AC-01 | 主成功-记账 | Given 有效支出金额与日期，When 保存，Then 流水持久化并出现在列表 | FR-001 |
| AC-02 | 自动分类展示 | Given 备注含可识别关键词，When 保存，Then 展示与规则一致的建议类目/标签 | FR-002 |
| AC-03 | 失败-缺金额 | Given 未填金额，When 保存，Then 拒绝并提示 | FR-006 |
| AC-04 | 分析可出数 | Given 周期内有已确认支出，When 打开分析，Then 展示支出合计与类目汇总 | FR-004 |
| AC-05 | 建议可读 | Given 分析结果可计算，When 查看建议区，Then 至少一条非空白建议文案 | FR-005 |

## 预期输出文件名

```text
DailyBill-开发说明文档.md
DailyBill-测试用例.md
DailyBill-开发任务确认单.md
```
