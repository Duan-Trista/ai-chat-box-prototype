# User Story: US27 上拉加载历史消息

**Source**: W52 新增

**As a** 卡车司机，
**I want to** 在对话页上拉加载更早的历史消息，
**So that** 我可以回顾之前的对话内容，无需跳转到独立的"历史会话"页面。

## Acceptance Criteria

**Scenario: 上拉加载**
- Given 用户在对话页，且有历史消息
- When 用户向上滑动到对话区顶部
- Then 展示"下拉加载更多..."提示
- And 加载完成后，更早的历史消息追加到对话区顶部
- And 滚动位置保持在当前可视区域

**Scenario: 加载中状态**
- Given 用户触发上拉加载
- When 数据正在请求中
- Then 展示加载动画 + "加载中..." 文案
- And 加载完成后动画消失

**Scenario: 没有更多历史**
- Given 所有历史消息已加载完毕
- When 用户再次上拉
- Then 展示"没有更多了"提示
- And 不再触发加载请求

**Scenario: 无历史消息**
- Given 用户没有历史消息
- When 用户进入对话页
- Then 展示欢迎语 + FAQ（首次进入状态）
- And 上拉不触发加载

**Scenario: 加载失败**
- Given 用户触发上拉加载
- When 网络请求失败
- Then 展示"加载失败，点击重试"
- And 用户点击可重新加载

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 分页大小、加载文案可调整 |
| Valuable | pass | 替代历史会话页面，减少页面跳转 |
| Estimable | pass | 范围清晰 |
| Small | pass | 分页加载 + 状态提示 |
| Testable | pass | 有/无数据、加载失败场景可测 |

## Sizing Hint

S — 分页加载逻辑 + 状态提示

## Status

Confirmed

---

*Created: 2026-09-03 (W52)*