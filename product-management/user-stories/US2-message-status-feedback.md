# User Story: US2 消息发送与加载状态反馈

**Source**: F2 消息发送与加载状态反馈 → J1 Phase 2 Pain Point #2, Phase 3 Pain Point #4

**As a** 卡车司机，
**I want to** 看到消息发送和答案加载的实时状态，
**So that** 我知道系统是否收到请求并知道大概还要等多久。

## Acceptance Criteria

**Scenario: 发送中状态**
- Given 用户输入了问题
- When 用户点击发送
- Then 对话区出现用户消息气泡，右侧显示"发送中"转圈动画
- And 输入框清空，发送按钮置灰

**Scenario: 加载中状态**
- Given 消息已发送成功
- When 系统正在处理请求
- Then 对话区出现"思考中"动画气泡
- And 动画气泡下方展示两阶段提示："正在查找车书..."→"正在组织答案..."

**Scenario: 发送失败**
- Given 用户点击了发送
- When 消息发送失败（网络断开或超时）
- Then 消息气泡变灰，右侧显示感叹号图标
- And 气泡下方展示"发送失败，点击重试"文字

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 状态文案可调整 |
| Valuable | pass | 消除等待焦虑 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有状态可模拟 |

## Sizing Hint

S — 三个状态机，有一定复杂度

## Status

Confirmed

---

*Created: 2026-09-02*