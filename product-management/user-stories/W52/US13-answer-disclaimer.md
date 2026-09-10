# User Story: US13 答案安全免责声明

**Source**: NFR2 答案安全免责

**As a** 合规官，
**I want to** 每条 AI 答案底部展示免责声明，
**So that** 用户知晓 AI 答案仅供参考，紧急情况应拨打 400 电话。

## Acceptance Criteria

**Scenario: 答案底部展示免责声明**
- Given 答案已生成完毕
- When 答案渲染完成
- Then 答案底部固定展示免责声明："以上信息仅供参考，请以官方车主手册为准。紧急情况请拨打 400-xxx-xxxx。"

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 文案可调整 |
| Valuable | pass | 法律风险防控 |
| Estimable | pass | 范围极小 |
| Small | pass | 固定文案展示 |
| Testable | pass | 答案渲染后展示 |

## Sizing Hint

XS — 固定文案展示

## Status

Confirmed

---

*Created: 2026-09-02*