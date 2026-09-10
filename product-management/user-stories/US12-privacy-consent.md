# User Story: US12 隐私协议与数据声明

**Source**: NFR1 数据隐私与合规

**As a** 合规官，
**I want to** 用户首次使用 AI 助手时展示隐私协议弹窗，
**So that** 用户明确知晓数据采集范围和使用目的。

## Acceptance Criteria

**Scenario: 首次使用展示隐私协议**
- Given 用户首次点击悬浮入口进入卡车助手
- When 页面加载
- Then 弹出隐私协议弹窗，说明数据采集范围（对话内容、FAQ 点击数据）和使用目的（优化答案质量）
- And 用户需点击"同意"才能继续使用
- And 用户点击"不同意"则退出到 APP 首页

**Scenario: 非首次使用**
- Given 用户已同意过隐私协议
- When 用户再次进入卡车助手
- Then 不展示隐私协议弹窗，直接进入对话页

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 文案可调整 |
| Valuable | pass | 合规刚需 |
| Estimable | pass | 范围极小 |
| Small | pass | 弹窗 + 本地状态记录 |
| Testable | pass | 首次/非首次可测 |

## Sizing Hint

XS — 弹窗 + 本地状态

## Status

Confirmed

---

*Created: 2026-09-02*