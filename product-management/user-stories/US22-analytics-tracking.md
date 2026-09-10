# User Story: US22 埋点与数据采集

**Source**: 产品运营需求 — Journey-discovered

**As a** 产品运营，
**I want to** 采集用户使用卡车助手的关键行为数据，
**So that** 我可以衡量产品表现并优化答案质量。

## Acceptance Criteria

**Scenario: 关键事件埋点**
- Given 用户在使用卡车助手
- When 发生以下事件，触发埋点上报：
  - 进入卡车助手 / 退出
  - 发送问题 / 收到答案（含是否拒识）
  - 点击 FAQ / 点击关键词条
  - 点赞 / 不点赞
  - 点击复制 / 点击语音播报 / 点击车书链接
  - 停止生成
  - 上拉加载历史 / 搜索历史
  - 删除会话 / 清空全部记录
- Then 事件数据上报到埋点平台

**Scenario: 埋点数据字段**
- Given 每个埋点事件
- Then 包含以下字段：事件名称、时间戳、会话 ID、用户 ID（脱敏）、VIN（脱敏）、事件属性

**Scenario: 埋点不影响用户体验**
- Given 埋点上报
- When 上报失败
- Then 不阻塞用户操作，静默丢弃

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 事件列表可增减 |
| Valuable | pass | 数据驱动优化 |
| Estimable | pass | 范围清晰 |
| Small | flag | 事件较多，可分阶段 |
| Testable | pass | 可验证埋点数据 |

## Sizing Hint

M — 建议分阶段：MVP 先上核心事件（发送/收到/点赞/拒识），后续补充

## Status

Confirmed

---

*Created: 2026-09-02*