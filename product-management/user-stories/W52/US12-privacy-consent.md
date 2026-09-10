# User Story: US12 隐私协议与数据声明

**Source**: NFR1 数据隐私与合规

**As a** 合规官，
**I want to** 用户首次进入 AI 助手页时展示隐私协议弹窗，
**So that** 用户明确知晓数据采集范围和使用目的，合规使用。

## Acceptance Criteria

**Scenario: 首次进入展示隐私协议（在助手页内）**
- Given 用户首次点击悬浮入口进入卡车助手
- When 进入对话页
- Then 在对话页内弹出隐私协议弹窗，覆盖整个页面
- And 弹窗展示数据采集范围（对话内容、FAQ 点击数据）和使用目的（优化答案质量）
- And 用户需点击"同意并继续"才能关闭弹窗进入对话
- And 用户点击"不同意"则关闭弹窗，返回 APP 首页，toast "请同意隐私协议后继续使用"

**Scenario: 非首次使用**
- Given 用户已同意过隐私协议
- When 用户再次进入卡车助手
- Then 不展示隐私协议弹窗，直接进入对话页

**Scenario: 隐私协议查看入口**
- Given 用户已在对话页
- When 用户需要查看隐私协议
- Then 可通过设置/菜单中查看隐私协议全文

**Scenario: 同意状态持久化**
- Given 用户已同意隐私协议
- When 用户关闭 APP 后重新打开
- Then 隐私协议同意状态保持，不再弹出

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

## W52 变更说明

- 隐私协议弹窗改为在对话页内弹出（原：在首页弹出后跳转）
- 点击"不同意"返回首页而非停留在原地
- 同意状态通过 sessionStorage 持久化

---

*Created: 2026-09-02*
*Updated: 2026-09-03 (W52)*