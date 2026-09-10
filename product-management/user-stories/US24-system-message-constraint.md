# User Story: US24 系统消息操作约束

**Source**: 竞品参考 — Journey-discovered

**As a** 卡车司机，
**I want to** 系统消息（如车辆切换提示）不支持撤回/引用/删除，
**So that** 操作菜单只出现在用户可操作的消息上，不混淆。

## Acceptance Criteria

**Scenario: 用户消息长按**
- Given 对话区有用户发送的消息
- When 用户长按该消息
- Then 弹出操作菜单：撤回、引用、复制、删除

**Scenario: 系统消息长按**
- Given 对话区有系统消息（如"已切换到沪B·67890"）
- When 用户长按该系统消息
- Then 不弹出操作菜单，无反应

**Scenario: AI 答案长按**
- Given 对话区有 AI 生成的答案
- When 用户长按该答案
- Then 不弹出用户消息的操作菜单
- And 答案自身的操作按钮（点赞/不点赞/复制/语音播报）已在答案底部展示

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 菜单项可调整 |
| Valuable | pass | 避免用户困惑 |
| Estimable | pass | 范围极小 |
| Small | pass | 消息类型判断 |
| Testable | pass | 三种消息类型可测 |

## Sizing Hint

XS — 消息类型判断 + 菜单显示控制

## Status

Confirmed

---

*Created: 2026-09-02*