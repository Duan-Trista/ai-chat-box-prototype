# User Story: US11 历史会话搜索

**Source**: F11 历史会话搜索 → J2 Phase 2 Pain Point #15

**As a** 卡车司机，
**I want to** 通过关键词搜索历史会话，
**So that** 历史会话多了之后能快速找到目标会话。

## Acceptance Criteria

**Scenario: 搜索匹配**
- Given 用户在历史会话列表
- When 用户点击搜索框，输入"方向盘"
- Then 实时展示问题或答案中包含"方向盘"的会话列表
- And 每条会话展示问题摘要 + 时间，按相关度排序

**Scenario: 搜索无结果**
- Given 用户输入了搜索关键词
- When 没有匹配的会话
- Then 展示空态："未找到相关会话"

**Scenario: 清空搜索**
- Given 用户正在进行搜索
- When 用户清空搜索框内容
- Then 恢复完整历史会话列表

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | flag | 依赖 F9 的会话摘要数据 |
| Negotiable | pass | 搜索算法可调整 |
| Valuable | pass | 快速定位历史 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 匹配/无结果场景可测 |

## Sizing Hint

S — 搜索框 + 本地关键词匹配

## Status

Confirmed

---

*Created: 2026-09-02*