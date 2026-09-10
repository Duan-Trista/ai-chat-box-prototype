# User Story: US23 首次使用引导

**Source**: 竞品参考 — Journey-discovered

**As a** 卡车司机，
**I want to** 首次使用卡车助手时看到简洁的功能引导，
**So that** 我知道这个功能能做什么、怎么用。

## Acceptance Criteria

**Scenario: 首次使用引导**
- Given 用户首次进入卡车助手（已同意隐私协议）
- When 对话页加载完成
- Then 展示引导浮层，包含：
  - 一句话说明："随时随地问我车书相关问题"
  - 操作提示："输入文字或点击下方问题卡片即可提问"
  - "知道了"按钮
- When 用户点击"知道了"
- Then 引导浮层消失，进入正常对话页

**Scenario: 非首次使用**
- Given 用户非首次使用
- Then 不展示引导浮层

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 引导文案可调整 |
| Valuable | pass | 降低首次使用门槛 |
| Estimable | pass | 范围极小 |
| Small | pass | 浮层 + 本地状态 |
| Testable | pass | 首次/非首次可测 |

## Sizing Hint

XS — 浮层展示 + 本地状态记录

## Status

Confirmed

---

*Created: 2026-09-02*