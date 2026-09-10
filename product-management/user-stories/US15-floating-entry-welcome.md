# User Story: US15 悬浮入口与欢迎引导

**Source**: C1 ~F1, ~F11, ~F12 — 设计范畴

**As a** 卡车司机，
**I want to** 在 APP 首页看到悬浮小机器人入口并点击进入后看到清晰的欢迎引导，
**So that** 我知道这个功能是什么、能问什么、怎么开始。

## Acceptance Criteria

**Scenario: 悬浮入口展示**
- Given 用户已登录，在 APP 首页
- When 页面加载
- Then 右下角展示悬浮小机器人图标
- And 图标不遮挡主要功能区域

**Scenario: 点击入口进入**
- Given 用户点击悬浮小机器人
- When 首次进入
- Then 展示隐私协议弹窗（见 US12）
- When 用户同意后
- Then 进入对话页，展示欢迎语："你好，我是卡车助手，有什么可以帮你的？"
- And 欢迎语下方展示 3-4 个初始问题卡片（横向滑动）
- And 初始问题卡片下方展示分类标签栏（至少包含"车书"标签，后续可扩展）
- And 选中标签后展示对应的常用问题 FAQ 列表

**Scenario: 关键词条入口**
- Given 运营配置了关键词条（如"体验数字钥匙"）
- When 用户进入对话页
- Then 关键词条在欢迎语下方固定位置展示，可点击
- When 用户点击关键词条
- Then 以用户消息形式发送对应问题

**Scenario: 非首次进入**
- Given 用户非首次进入
- When 用户点击悬浮入口
- Then 直接进入对话页，展示空态欢迎语 + 引导

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 布局和文案可调整 |
| Valuable | pass | 产品第一印象 |
| Estimable | pass | 范围清晰 |
| Small | flag | 内容较多，可拆分为入口、欢迎引导、FAQ 三条 |
| Testable | pass | 所有场景可测 |

## Sizing Hint

M — 建议拆分为 US15a 悬浮入口、US15b 欢迎引导+FAQ、US15c 关键词条

## Status

Confirmed

---

*Created: 2026-09-02*