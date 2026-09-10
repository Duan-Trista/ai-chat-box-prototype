# User Story: US4 网络异常处理与重试

**Source**: F4 网络异常处理与重试 → J1 Phase 3 Pain Point #5

**As a** 卡车司机，
**I want to** 网络异常时看到明确提示并能一键重试，
**So that** 我不需要重新输入问题就能再次发起请求。

## Acceptance Criteria

**Scenario: 请求前检测无网络**
- Given 用户输入了问题
- When 用户点击发送
- And 设备当前无网络连接
- Then toast "网络不可用，请稍后重试"
- And 消息不发送，文本保留在输入框

**Scenario: 请求超时**
- Given 用户已发送消息
- When 请求超过 10 秒未返回
- Then 答案气泡展示"请求超时，请重试"
- And 下方展示"重试"按钮
- When 用户点击"重试"
- Then 使用相同内容重新发起请求

**Scenario: 服务器错误**
- Given 用户已发送消息
- When 服务器返回 5xx 错误
- Then 答案气泡展示"服务异常，请稍后重试"
- And 下方展示"重试"按钮

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | flag | 依赖 F2 的状态机 |
| Negotiable | pass | 超时时间可调整 |
| Valuable | pass | 减少中断感 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 可模拟网络异常 |

## Sizing Hint

M — 涉及网络层检测 + 多种异常分类

## Status

Confirmed

---

*Created: 2026-09-02*