# User Story: US9 历史会话内容预览

**Source**: F9 历史会话内容预览 → J2 Phase 2 Pain Point #11

**As a** 卡车司机，
**I want to** 历史会话列表展示每条会话的问题摘要，
**So that** 我可以一眼看出每条会话问了什么，快速定位目标。

## Acceptance Criteria

**Scenario: 历史会话列表展示**
- Given 用户有历史会话记录
- When 用户上拉加载历史会话
- Then 每条会话展示：会话首个问题（截断到 30 字）+ 时间戳
- And 按时间倒序排列

**Scenario: 无历史会话**
- Given 用户没有历史会话记录
- When 用户上拉加载
- Then 展示空态："暂无历史会话"

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 截断字数可调整 |
| Valuable | pass | 快速定位会话 |
| Estimable | pass | 范围清晰 |
| Small | pass | 列表 UI 改动 |
| Testable | pass | 有/无数据场景可测 |

## Sizing Hint

S — 列表 UI 展示逻辑

## Status

Confirmed

---

*Created: 2026-09-02*