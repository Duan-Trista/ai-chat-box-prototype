# User Story: US10 会话删除与清空分离

**Source**: F10 会话删除与清空分离 → J2 Phase 4 Pain Point #13

**As a** 卡车司机，
**I want to** 区分删除当前会话和清空全部记录，
**So that** 我不会误删所有历史记录。

## Acceptance Criteria

**Scenario: 删除单条会话**
- Given 用户在历史会话列表
- When 用户左滑某条会话，点击"删除"
- Then 该会话从列表中移除，不可恢复
- And toast "已删除"

**Scenario: 清空全部记录**
- Given 用户在历史会话列表顶部
- When 用户点击"清空全部记录"
- Then 弹出确认弹窗："确认清空全部聊天记录？此操作不可恢复。"
- When 用户点击"确认"
- Then 所有历史会话被清空，列表展示空态
- And toast "已清空全部记录"

**Scenario: 取消清空**
- Given 确认弹窗已弹出
- When 用户点击"取消"
- Then 弹窗关闭，历史会话列表不变

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 交互方式可调整 |
| Valuable | pass | 避免误操作 |
| Estimable | pass | 范围极小 |
| Small | pass | 左滑删除 + 弹窗确认 |
| Testable | pass | 所有场景可测 |

## Sizing Hint

XS — 列表操作 + 确认弹窗

## Status

Confirmed

---

*Created: 2026-09-02*