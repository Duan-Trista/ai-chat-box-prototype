# User Story: US15a 悬浮入口

**Source**: 设计范畴

**As a** 卡车司机，
**I want to** 在 APP 首页看到悬浮小机器人入口并点击进入，
**So that** 我可以随时唤起卡车助手。

## Acceptance Criteria

**Scenario: 悬浮入口展示**
- Given 用户已登录，在 APP 首页
- When 页面加载
- Then 右下角展示悬浮小机器人图标
- And 图标不遮挡主要功能区域
- And 图标可拖动，吸附到屏幕边缘

**Scenario: 点击入口进入**
- Given 用户点击悬浮小机器人
- When 首次进入
- Then 触发隐私协议流程（见 US12）
- When 隐私协议通过后
- Then 进入对话页

**Scenario: 非首次进入**
- Given 用户非首次使用
- When 用户点击悬浮入口
- Then 直接进入对话页

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 图标位置、样式可调整 |
| Valuable | pass | 产品入口 |
| Estimable | pass | 范围极小 |
| Small | pass | 悬浮按钮 + 跳转 |
| Testable | pass | 首次/非首次可测 |

## Sizing Hint

XS

## Status

Confirmed

---

*Created: 2026-09-02*