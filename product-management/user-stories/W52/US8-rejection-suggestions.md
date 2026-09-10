# User Story: US8 拒识后智能建议追问

**Source**: F8 拒识后智能建议追问 → J1 Phase 4 Pain Point #10

**As a** 卡车司机，
**I want to** 拒识后看到与我问题相关的建议追问，
**So that** 我可以换一种方式获取答案，而不是直接放弃。

## Acceptance Criteria

**Scenario: 拒识展示建议追问**
- Given 用户发送了问题
- When 云端返回拒识（内容未找到或配置不支持）
- Then 对话区展示拒识文案
- And 下方展示 2-3 个与当前问题语义相关的建议追问
- And 每个建议追问可点击

**Scenario: 点击建议追问**
- Given 拒识后展示了建议追问
- When 用户点击某个建议追问
- Then 以用户消息形式发送该追问
- And 进入正常的问答流程

**Scenario: 云端未返回建议追问**
- Given 云端拒识但未返回建议追问
- When 拒识结果返回
- Then 展示拒识文案
- And 展示 APP 端预设的通用建议追问列表

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 建议追问来源可调整 |
| Valuable | pass | 减少拒识挫败感 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 可模拟拒识场景 |

## Sizing Hint

S — 涉及云端协同 + APP 兜底

## Status

Confirmed

---

*Created: 2026-09-02*