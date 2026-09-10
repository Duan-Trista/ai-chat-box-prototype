# User Story: US15c 关键词条推荐

**Source**: 设计范畴

**As a** 卡车司机，
**I want to** 在输入框上方看到运营配置的关键词条推荐，
**So that** 我可以快速了解新功能或重要消息，点击即可发送。

## Acceptance Criteria

**Scenario: 关键词条展示**
- Given 运营在后台配置了关键词条（如"体验数字钥匙"、"新车交付指南"）
- When 用户进入对话页
- Then 关键词条在输入框上方固定位置展示，横向排列，支持横向滚动
- And 每个关键词条可点击

**Scenario: 点击关键词条**
- When 用户点击某个关键词条
- Then 以用户消息形式发送对应的问题/内容
- And 进入正常问答流程

**Scenario: 无关键词条配置**
- Given 运营未配置任何关键词条
- Then 关键词条区域不展示

**Scenario: 关键词条点击数据收集**
- Given 用户点击了关键词条
- When 消息发送
- Then 记录该关键词条的点击事件（见 US22a）

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 展示位置、样式可调整 |
| Valuable | pass | 运营推广入口 |
| Estimable | pass | 范围极小 |
| Small | pass | 横向列表 + 点击 |
| Testable | pass | 有/无配置可测 |

## Sizing Hint

XS

## Status

Confirmed

## W52 变更说明

- 关键词条位置从欢迎语下方移至输入框上方悬浮
- 支持横向滚动，适配更多关键词条

---

*Created: 2026-09-02*
*Updated: 2026-09-03 (W52)*