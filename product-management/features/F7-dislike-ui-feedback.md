# Feature: F7 点踩 UI 反馈

## Description

用户点击不点赞按钮后，展示 toast "感谢反馈"，让用户知道操作已被记录。

## Source

- **Capability**: C3 - 答案交互与反馈
- **Journey**: J1 Phase 4 - 获得答案与操作
- **~F Reference**: C3 ~F7 点赞/不点赞 — ✅ verified

## Problem Solved

当前用户点踩后没有任何 UI 反馈，用户觉得"点了也没用"，降低反馈意愿（J1 Pain Point #9）。

## User Value

简单的 UI 反馈让用户知道操作被记录，提升反馈意愿，帮助团队收集更多答案质量数据。

## Scope

**Includes:**
- 点踩后 toast "感谢反馈"
- 点赞后 toast "感谢反馈"（保持一致性）

**Excludes:**
- 点踩后展开原因选择（MVP 阶段不做）
- 点赞/不点赞可撤销（后续迭代）

## Phase

MVP

## Dependencies

None

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*