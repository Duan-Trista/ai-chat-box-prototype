# User Story: US19 车辆上下文标识

**Source**: 产品设计确认 — 设计范畴

**As a** 卡车司机，
**I want to** 在对话页顶部看到当前咨询的车辆信息并可切换，
**So that** 我知道 AI 回答是基于哪辆车的知识库。

## Acceptance Criteria

**Scenario: 展示当前车辆**
- Given 用户已绑定车辆
- When 用户进入对话页
- Then 顶部导航栏展示当前车辆标识（车牌号 + 车型简称）
- And 默认选中最近一次咨询的车辆

**Scenario: 切换车辆**
- Given 用户有多辆绑定车辆
- When 用户点击顶部车辆标识
- Then 弹出车辆选择列表，每辆展示车牌号 + 车型
- When 用户选择另一辆车
- Then 车辆标识更新
- And 对话区插入系统提示："已切换到「沪B·67890 G Series ICE」"
- And 后续问题基于新车辆的知识库

**Scenario: 仅有一辆车**
- Given 用户仅绑定一辆车
- Then 顶部展示车辆标识但不展示切换箭头
- And 用户无法切换

**Scenario: 未绑定车辆**
- Given 用户未绑定任何车辆
- Then 顶部展示"未选择车辆"
- When 用户点击
- Then 引导去车辆管理页绑定

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 展示样式可调整 |
| Valuable | pass | 避免张冠李戴 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 多车/单车/无车可测 |

## Sizing Hint

S — 顶部 UI + 车辆选择面板

## Status

Confirmed

---

*Created: 2026-09-02*