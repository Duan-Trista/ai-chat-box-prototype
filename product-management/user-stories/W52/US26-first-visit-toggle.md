# User Story: US26 首次/非首次进入差异化展示

**Source**: W52 新增

**As a** 卡车司机，
**I want to** 首次进入时看到欢迎语和 FAQ 引导，再次进入时看到上次的聊天记录，
**So that** 首次能快速上手，后续能直接继续上次的对话。

## Acceptance Criteria

**Scenario: 首次进入展示欢迎引导**
- Given 用户从未使用过卡车助手
- When 用户点击悬浮入口进入
- Then 展示欢迎语 + 分类 FAQ
- And 关键词条在输入框上方展示

**Scenario: 非首次进入展示聊天记录**
- Given 用户之前使用过卡车助手且有聊天记录
- When 用户再次点击悬浮入口进入
- Then 展示上次的聊天记录（对话区已有历史消息）
- And 输入框可用，用户可继续发送新问题
- And 不展示欢迎语和 FAQ

**Scenario: 非首次进入但无聊天记录**
- Given 用户之前使用过但已清空记录
- When 用户再次进入
- Then 展示欢迎语 + FAQ（同首次进入）

**Scenario: 点击"新对话"后**
- Given 用户点击了"新对话"
- When 确认后进入新对话
- Then 展示欢迎语 + FAQ（等同于首次进入状态）

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 展示逻辑可调整 |
| Valuable | pass | 降低首次门槛 + 减少重复操作 |
| Estimable | pass | 范围清晰 |
| Small | pass | 状态判断 + 条件渲染 |
| Testable | pass | 首次/非首次/清空后场景可测 |

## Sizing Hint

S — 状态判断 + 条件渲染

## Status

Confirmed

---

*Created: 2026-09-03 (W52)*