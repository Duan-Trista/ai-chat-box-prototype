# User Story: US22a 核心埋点（MVP）

**Source**: 产品运营需求

**As a** 产品运营，
**I want to** 采集卡车助手的核心使用行为数据，
**So that** 我可以衡量产品表现（渗透率、完成率、拒识率、点踩率）。

## Acceptance Criteria

**Scenario: MVP 核心事件**
- Given 用户在使用卡车助手
- When 发生以下事件，触发埋点上报：
  - 进入卡车助手
  - 发送问题
  - 收到答案（标记是否拒识）
  - 点赞 / 不点赞
  - 点击 FAQ
  - 点击关键词条
- Then 事件数据上报到埋点平台

**Scenario: 埋点数据字段**
- Given 每个埋点事件
- Then 包含：事件名称、时间戳、会话 ID、用户 ID（脱敏）、VIN（脱敏）、事件属性

**Scenario: 埋点不影响用户体验**
- Given 埋点上报
- When 上报失败
- Then 不阻塞用户操作，静默丢弃

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 事件列表可增减 |
| Valuable | pass | 支撑 Success Metrics |
| Estimable | pass | 范围清晰 |
| Small | pass | 7 个核心事件 |
| Testable | pass | 可验证埋点数据 |

## Sizing Hint

S

## Status

Confirmed

---

*Created: 2026-09-02*