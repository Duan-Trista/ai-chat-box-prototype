# User Story: US6 语音播报播放控制

**Source**: F6 语音播报播放控制 → J1 Phase 4 Pain Point #7

**As a** 卡车司机，
**I want to** 语音播报时能暂停/继续/停止，
**So that** 我可以自由控制播报进度，不必干等完整听完。

## Acceptance Criteria

**Scenario: 播报中暂停与继续**
- Given 答案已生成，用户点击了语音播报
- When 播报进行中，用户点击暂停按钮
- Then 播报暂停，按钮变为继续图标
- When 用户点击继续按钮
- Then 播报从暂停位置继续

**Scenario: 播报中停止**
- Given 答案正在语音播报中
- When 用户点击停止按钮
- Then 播报立即停止，播放控制栏收起
- And 用户可再次点击语音播报从头播放

**Scenario: 播报完成**
- Given 答案正在语音播报中
- When 播报到达末尾
- Then 播放控制栏自动收起
- And 按钮恢复为初始状态

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 控制按钮样式可调整 |
| Valuable | pass | 卡车场景刚需 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有控制状态可测 |

## Sizing Hint

S — TTS 播放器控制

## Status

Confirmed

---

*Created: 2026-09-02*