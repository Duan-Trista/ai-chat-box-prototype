# User Story: US15b 欢迎引导与分类 FAQ

**Source**: 设计范畴

**As a** 卡车司机，
**I want to** 进入对话页后看到清晰的欢迎语和分类 FAQ，
**So that** 我知道能问什么、怎么开始，不用自己摸索。

## Acceptance Criteria

**Scenario: 欢迎语展示**
- Given 用户进入对话页
- When 页面加载完成
- Then 展示欢迎语："你好，我是卡车助手，有什么可以帮你的？"

**Scenario: 分类标签与 FAQ**
- Given 用户在对话页
- When 页面加载完成
- Then 欢迎语下方展示分类标签栏（一期至少包含"车书"标签，后续可扩展"保养"、"用车"）
- And 默认选中第一个标签
- And 选中标签后展示对应的常用问题 FAQ 列表
- And FAQ 列表中每个问题可点击，点击后以用户消息形式发送

**Scenario: 切换分类标签**
- Given 用户在看"车书"分类的 FAQ
- When 用户点击另一个分类标签
- Then 标签切换，FAQ 列表随之切换

**Scenario: FAQ 点击数据收集**
- Given 用户点击了某个 FAQ
- When 消息发送
- Then 记录该 FAQ 的点击事件（见 US22a）

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 文案、标签数量可调整 |
| Valuable | pass | 降低首次使用门槛 |
| Estimable | pass | 范围清晰 |
| Small | pass | 标签 + 列表 |
| Testable | pass | 所有交互可测 |

## Sizing Hint

S

## Status

Confirmed

## W52 变更说明

- 移除欢迎卡片（横向滑动的问题卡片，与 FAQ 功能重叠）
- 仅保留分类 FAQ 作为引导入口
- 欢迎语和 FAQ 仅首次进入展示，后续进入展示聊天记录（见 US26）

---

*Created: 2026-09-02*
*Updated: 2026-09-03 (W52)*