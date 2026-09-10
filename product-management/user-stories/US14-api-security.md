# User Story: US14 接口安全与日志脱敏

**Source**: NFR3 接口安全与日志脱敏

**As a** 安全工程师，
**I want to** 接口请求携带有效认证 Token 且上报日志不含完整 VIN，
**So that** 系统安全合规且用户隐私不泄露。

## Acceptance Criteria

**Scenario: Token 认证**
- Given 用户已登录
- When APP 向云端发起 AI 问答请求
- Then 请求头携带有效的认证 Token
- And Token 过期时自动刷新，不中断用户体验

**Scenario: Token 过期**
- Given 用户 Token 已过期
- When APP 发起请求
- Then 自动使用刷新 Token 获取新 Token
- And 使用新 Token 重试原请求
- And 整个过程对用户透明

**Scenario: 日志脱敏**
- Given 用户发起了 AI 问答请求
- When APP 上报埋点日志
- Then 日志中不包含完整 VIN（仅保留前 3 位 + 后 4 位）
- And 日志中不包含用户真实姓名、手机号等隐私信息

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 脱敏粒度可调整 |
| Valuable | pass | 安全合规刚需 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | Token 过期/日志脱敏可测 |

## Sizing Hint

S — Token 刷新机制 + 日志脱敏规则

## Status

Confirmed

---

*Created: 2026-09-02*