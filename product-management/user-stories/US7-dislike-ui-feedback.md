# User Story: US7 点踩 UI 反馈

**Source**: F7 点踩 UI 反馈 → J1 Phase 4 Pain Point #9

**As a** 卡车司机，
**I want to** 点踩后看到明确反馈，
**So that** 我知道我的反馈被系统记录了。

## Acceptance Criteria

**Scenario: 点赞**
- Given 答案生成完毕，底部展示点赞/不点赞按钮
- When 用户点击点赞按钮
- Then toast "感谢反馈"
- And 点赞按钮高亮，不点赞按钮置灰

**Scenario: 不点赞**
- Given 答案生成完毕，底部展示点赞/不点赞按钮
- When 用户点击不点赞按钮
- Then toast "感谢反馈"
- And 不点赞按钮高亮，点赞按钮置灰

**Scenario: 重复点击**
- Given 用户已点赞
- When 用户再次点击点赞按钮
- Then 不触发任何操作（已反馈状态不可撤销）

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | toast 文案可调整 |
| Valuable | pass | 提升反馈意愿 |
| Estimable | pass | 范围极小 |
| Small | pass | 单次交互 |
| Testable | pass | 所有状态可测 |

## Sizing Hint

XS — 极简交互

## Status

Confirmed

---

*Created: 2026-09-02*