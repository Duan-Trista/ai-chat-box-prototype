# User Story: US25 流式输出中操作按钮可用

**Source**: 竞品参考 — Journey-discovered

**As a** 卡车司机，
**I want to** 在答案流式输出中就能复制和点赞，
**So that** 我不用等答案全部出完才能操作。

## Acceptance Criteria

**Scenario: 流式输出中复制**
- Given 答案正在流式上屏中
- When 用户点击答案气泡下方的"复制"按钮
- Then 复制当前已展示的文本内容
- And toast "已复制"

**Scenario: 流式输出中反馈**
- Given 答案正在流式上屏中
- When 用户点击答案气泡下方的"点赞"或"不点赞"
- Then 记录反馈，按钮高亮
- And toast "感谢反馈"

**Scenario: 流式输出中语音播报**
- Given 答案正在流式上屏中
- When 用户点击"语音播报"按钮
- Then 播报当前已生成的内容

**Scenario: 操作按钮展示时机**
- Given 答案流式输出
- When 首个字符上屏
- Then 操作按钮区域（复制、点赞、不点赞、语音播报）立即展示
- And 答案生成完毕后按钮不消失

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 按钮展示时机可调整 |
| Valuable | pass | 减少等待时间 |
| Estimable | pass | 范围极小 |
| Small | pass | 按钮展示时机调整 |
| Testable | pass | 可模拟流式输出场景 |

## Sizing Hint

XS — 按钮展示时机调整

## Status

Confirmed

---

*Created: 2026-09-02*