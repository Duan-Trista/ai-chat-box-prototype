# User Story: US18 车书章节跳转

**Source**: C3 ~F10 车书章节跳转 — 设计范畴

**As a** 卡车司机，
**I want to** 点击答案中附带的车书章节链接跳转到 APP 内车书模块对应章节，
**So that** 我可以查看完整的功能说明和操作图示。

## Acceptance Criteria

**Scenario: 答案包含车书章节链接**
- Given 答案中包含车书章节 URL
- When 答案渲染完成
- Then URL 以蓝色可点击链接形式展示
- When 用户点击链接
- Then 跳转到 APP 内车书模块对应章节

**Scenario: 从车书返回**
- Given 用户已跳转到车书模块
- When 用户返回
- Then 对话页恢复，所有消息气泡完整展示（见 US5）
- And 上下文保持，用户可继续追问

**Scenario: 答案不包含链接**
- Given 答案中不包含车书章节 URL
- Then 不展示链接入口

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | flag | 依赖 US5 的对话状态恢复 |
| Negotiable | pass | 链接样式可调整 |
| Valuable | pass | 连通车书模块 |
| Estimable | pass | 范围极小 |
| Small | pass | 路由跳转 |
| Testable | pass | 有/无链接场景可测 |

## Sizing Hint

XS — APP 内路由跳转

## Status

Confirmed

---

*Created: 2026-09-02*