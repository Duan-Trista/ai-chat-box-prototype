# User Story: US21 停止生成

**Source**: 竞品参考 — Journey-discovered

**As a** 卡车司机，
**I want to** 在流式答案生成中点击停止按钮中断生成，
**So that** 答案方向不对或等待太久时我可以及时止损，不必干等或退出。

## Acceptance Criteria

**Scenario: 流式输出中停止**
- Given 答案正在流式上屏中
- When 用户点击答案气泡下方的"停止生成"按钮
- Then 生成立即中断
- And 已生成的部分内容保留在对话区
- And 输入框恢复可用，用户可重新提问

**Scenario: 停止后重新提问**
- Given 用户已停止生成
- When 用户输入新问题并发送
- Then 正常进入问答流程

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 按钮位置可调整 |
| Valuable | pass | 减少无效等待 |
| Estimable | pass | 范围极小 |
| Small | pass | 单次交互 |
| Testable | pass | 可模拟流式输出场景 |

## Sizing Hint

XS — 中断按钮 + 状态重置

## Status

Confirmed

---

*Created: 2026-09-02*