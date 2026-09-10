# User Story: US22b 扩展埋点（后续迭代）

**Source**: 产品运营需求

**As a** 产品运营，
**I want to** 采集卡车助手的扩展使用行为数据，
**So that** 我可以深入分析用户行为并持续优化产品。

## Acceptance Criteria

**Scenario: 扩展事件**
- Given 用户在使用卡车助手
- When 发生以下事件，触发埋点上报：
  - 退出卡车助手
  - 停止生成
  - 点击复制答案
  - 点击语音播报
  - 点击车书链接
  - 上拉加载历史会话
  - 搜索历史会话
  - 删除会话 / 清空全部记录
  - 会话时长
- Then 事件数据上报到埋点平台

**Scenario: 埋点数据字段**
- Given 每个埋点事件
- Then 包含：事件名称、时间戳、会话 ID、用户 ID（脱敏）、VIN（脱敏）、事件属性

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 事件列表可增减 |
| Valuable | pass | 深入优化数据支撑 |
| Estimable | pass | 范围清晰 |
| Small | pass | 9 个扩展事件 |
| Testable | pass | 可验证埋点数据 |

## Sizing Hint

S

## Status

Confirmed

---

*Created: 2026-09-02*