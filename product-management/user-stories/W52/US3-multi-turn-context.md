# User Story: US3 多轮对话上下文保持

**Source**: F3 多轮对话上下文保持 → J1 Phase 2 Pain Point #3

**As a** 卡车司机，
**I want to** 在同一会话中自然追问且 AI 能理解上下文，
**So that** 我不需要每次重新解释问题背景。

## Acceptance Criteria

**Scenario: 会话内追问**
- Given 用户问"方向盘怎么调"
- And 系统返回了答案
- When 用户追问"那调多高合适"
- Then 系统理解"那"指代方向盘，基于上下文生成答案
- And 答案展示在对话区

**Scenario: 上下文超时**
- Given 用户有一个活跃会话
- When 用户切后台超过 5 分钟后返回
- Then 系统自动开始新会话
- And 展示空态欢迎语

**Scenario: 新对话**
- Given 用户点击"新对话"
- When 确认开启
- Then 清空当前对话区，展示空态欢迎语
- And 之前的上下文不再保留

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 依赖 Session 管理机制 |
| Negotiable | pass | 超时时间可调整 |
| Valuable | pass | 减少重复解释 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有场景可测 |

## Sizing Hint

M — 涉及 Session 管理 + 上下文维护，跨端协同

## Status

Confirmed

## W52 变更说明

- 移除"历史会话继续追问"场景（历史会话页面已移除）
- 简化为新对话 + 会话内追问 + 超时重置

---

*Created: 2026-09-02*
*Updated: 2026-09-03 (W52)*