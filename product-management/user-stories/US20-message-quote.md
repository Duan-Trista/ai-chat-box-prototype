# User Story: US20 消息引用回复

**Source**: C2 ~F5 消息操作 — 设计范畴

**As a** 卡车司机，
**I want to** 长按某条消息后选择"引用"，
**So that** 我可以在追问时引用之前的对话内容，让 AI 更准确理解我在问什么。

## Acceptance Criteria

**Scenario: 引用消息并回复**
- Given 对话区有历史消息
- When 用户长按某条消息，选择"引用"
- Then 输入框上方展示被引用的消息摘要（截断到一行）
- And 输入框获得焦点，键盘弹起
- When 用户输入文字并发送
- Then 新消息气泡展示引用内容 + 用户输入的文字

**Scenario: 取消引用**
- Given 输入框上方已展示引用消息
- When 用户点击引用消息上的"×"按钮
- Then 引用消息消失，恢复普通输入状态

**Scenario: 引用自己的消息**
- Given 用户长按自己发送的消息
- When 选择"引用"
- Then 引用行为同上

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 引用样式可调整 |
| Valuable | pass | 追问更精准 |
| Estimable | pass | 范围极小 |
| Small | pass | 单次交互 |
| Testable | pass | 引用/取消可测 |

## Sizing Hint

XS — 长按菜单 + 引用展示

## Status

Confirmed

---

*Created: 2026-09-02*