# User Story: US17 复制答案

**Source**: C3 ~F8 复制答案 — 设计范畴

**As a** 卡车司机，
**I want to** 一键复制 AI 答案的完整文本，
**So that** 我可以粘贴到微信或备忘录里分享给其他人。

## Acceptance Criteria

**Scenario: 复制完整答案**
- Given 答案已生成完毕，底部展示操作按钮
- When 用户点击"复制"按钮
- Then 完整答案文本复制到系统剪贴板
- And toast "已复制"

**Scenario: 流式输出中复制**
- Given 答案正在流式上屏中
- When 用户点击"复制"按钮
- Then 复制当前已展示的文本内容
- And toast "已复制"

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | toast 文案可调整 |
| Valuable | pass | 高频使用场景 |
| Estimable | pass | 范围极小 |
| Small | pass | 单次交互 |
| Testable | pass | 可验证剪贴板内容 |

## Sizing Hint

XS — 系统剪贴板调用

## Status

Confirmed

---

*Created: 2026-09-02*