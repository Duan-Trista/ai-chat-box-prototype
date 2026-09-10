# User Story: US5 对话状态恢复

**Source**: F5 对话状态恢复 → J1 Phase 3 Pain Point #6, Phase 4 Pain Point #8

**As a** 卡车司机，
**I want to** 切后台或跳转车书后返回时恢复对话状态，
**So that** 我不丢失已有的对话内容和上下文。

## Acceptance Criteria

**Scenario: 切后台后返回**
- Given 用户正在对话中
- And 对话区有历史消息气泡
- When 用户切到后台，5 分钟内返回
- Then 对话区恢复，所有消息气泡完整显示
- And 输入框状态恢复

**Scenario: 跳转车书后返回**
- Given 答案中包含车书章节 URL
- When 用户点击 URL 跳转到车书模块
- And 用户从车书模块返回
- Then 对话页恢复，所有消息气泡完整显示
- And 上下文保持，用户可继续追问

**Scenario: 流式答案中断后恢复**
- Given 答案正在流式上屏中
- When 用户切后台后返回
- Then 若流式连接未断开，继续接收剩余内容
- And 若流式连接已断开，展示已接收内容 + "加载中断，点击重试"

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | flag | 依赖 F3 的 Session 管理 |
| Negotiable | pass | 超时时间可调整 |
| Valuable | pass | 避免丢失对话 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 可模拟切后台/跳转场景 |

## Sizing Hint

S — 页面生命周期管理 + 状态缓存

## Status

Confirmed

---

*Created: 2026-09-02*