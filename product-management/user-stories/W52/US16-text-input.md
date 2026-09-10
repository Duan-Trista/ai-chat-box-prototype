# User Story: US16 文字输入与发送

**Source**: 基础交互 — 设计范畴

**As a** 卡车司机，
**I want to** 在输入框中输入文字并发送，
**So that** 我可以向 AI 助手提问。

## Acceptance Criteria

**Scenario: 正常输入与发送**
- Given 用户在对话页
- When 用户点击输入框
- Then 键盘弹起，输入框获得焦点，页面随键盘上移
- And 输入框 placeholder 显示"输入您的问题，例如：如何调节方向盘高度？"
- When 用户输入文字后点击发送按钮
- Then 消息以气泡形式出现在对话区
- And 输入框清空

**Scenario: 空内容禁止发送**
- Given 输入框为空或仅含空格
- Then 发送按钮置灰，不可点击

**Scenario: 多行输入**
- Given 用户输入较长文字
- When 文字超过一行
- Then 输入框自动扩展高度，最多展示 4 行
- And 超过 4 行后输入框内滚动

**Scenario: 字数限制**
- Given 用户输入文字
- When 文字达到 500 字
- Then 输入框不再接受新字符
- And toast "最多输入 500 字"

**Scenario: 流式输出期间禁止发送**
- Given 答案正在流式上屏中
- When 用户在输入框输入文字
- Then 输入框可编辑但发送按钮变为停止按钮（⏹ 图标）
- And 禁止发送新消息
- When 用户点击停止按钮
- Then 流式输出中断，按钮恢复为发送按钮，用户可继续发送

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 字数限制、行数可调整 |
| Valuable | pass | 核心交互入口 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有场景可测 |

## Sizing Hint

S — 基础输入框交互

## Status

Confirmed

---

*Created: 2026-09-02*