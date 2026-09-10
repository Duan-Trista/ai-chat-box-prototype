# User Story: US15a 悬浮入口（含拖拽吸附）

**Source**: 设计范畴

**As a** 卡车司机，
**I want to** 在 APP 首页看到悬浮小机器人入口，并在车书页看到内嵌"问AI"按钮，
**So that** 我可以随时唤起卡车助手，看车书时也能直接跳转提问。

## Acceptance Criteria

**Scenario: 悬浮入口展示**
- Given 用户已登录，在 APP 首页
- When 页面加载
- Then 右下角展示悬浮小机器人图标
- And 图标不遮挡底部 Tab 栏

**Scenario: 拖拽移动**
- Given 悬浮按钮在首页展示
- When 用户按住按钮并拖拽
- Then 按钮跟随手指在屏幕范围内自由移动
- And 拖拽过程中按钮半透明，展示拖拽态
- And 按钮不会超出屏幕边界

**Scenario: 边框吸附**
- Given 用户拖拽按钮后松手
- When 按钮中心点在屏幕左半区
- Then 按钮吸附到左侧边缘（距离边缘 16px）
- When 按钮中心点在屏幕右半区
- Then 按钮吸附到右侧边缘（距离边缘 16px）
- And 吸附过程带 0.3s 过渡动画

**Scenario: 点击进入（不误触）**
- Given 悬浮按钮在首页展示
- When 用户点击按钮（移动距离 < 3px，视为点击）
- Then 触发进入卡车助手流程
- When 用户拖拽按钮（移动距离 >= 3px，视为拖拽）
- Then 不触发点击进入

**Scenario: 位置记忆**
- Given 用户拖拽按钮到某个位置后松手
- When 用户下次进入 APP 首页
- Then 按钮保持在用户上次设置的位置

**Scenario: 车书页内嵌入口**
- Given 用户在车书模块浏览某个章节
- When 页面加载
- Then 页面底部或右下角展示"问AI"按钮
- When 用户点击"问AI"按钮
- Then 跳转到卡车助手页，进入正常对话流程

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 吸附距离、动画时长可调整 |
| Valuable | pass | 产品入口 + 避免遮挡 |
| Estimable | pass | 范围清晰 |
| Small | pass | 拖拽 + 吸附 + 点击 |
| Testable | pass | 拖拽/点击/吸附可测 |

## Sizing Hint

S — 拖拽手势 + 吸附逻辑 + 位置记忆 + 车书页内嵌入口

## Status

Confirmed

## W52 变更说明

- 新增拖拽移动功能
- 新增边框吸附（左/右 16px，0.3s 动画）
- 新增点击/拖拽误触区分（< 3px 为点击）
- 新增位置记忆
- 新增车书页内嵌"问AI"入口，点击跳转助手页

---

*Created: 2026-09-02*
*Updated: 2026-09-03 (W52)*