# User Story: US1 消息撤回后编辑重发

**Source**: F1 消息撤回后编辑重发 → J1 Phase 2 Pain Point #1, J2 Phase 3 Pain Point #12

**As a** 卡车司机，
**I want to** 撤回已发送的消息并使原文本自动回填到输入框，
**So that** 打错字后可以快速修改重发，无需重新手打全部内容。

## Acceptance Criteria

**Scenario: 发送后撤回并编辑重发**
- Given 用户刚发送了一条消息
- And 答案尚未开始生成
- When 用户长按消息并选择"撤回"
- Then 消息从对话区消失
- And 原消息文本自动回填到输入框，光标定位到末尾
- And 用户修改后可直接点击发送

**Scenario: 答案已开始生成时撤回**
- Given 用户发送了消息
- And 答案已开始流式上屏
- When 用户长按消息并选择"撤回"
- Then 整个对话轮次（问题+已生成答案）从对话区移除
- And 原问题文本回填到输入框

**Scenario: 撤回后不修改直接发送**
- Given 用户撤回了消息，文本已回填到输入框
- When 用户不修改直接点击发送
- Then 消息正常发送，与原消息内容一致

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 撤回时机可讨论 |
| Valuable | pass | 减少重新手打成本 |
| Estimable | pass | 范围清晰 |
| Small | pass | 单次交互 |
| Testable | pass | 所有场景可测 |

## Sizing Hint

XS — 单次交互，范围明确

## Status

Confirmed

---

*Created: 2026-09-02*