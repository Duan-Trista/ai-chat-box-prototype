# Feature: F9 历史会话内容预览

## Description

历史会话列表展示每条会话的摘要信息（首个问题 + 时间），而非仅展示时间戳，帮助用户快速定位目标会话。

## Source

- **Capability**: C2 - 对话体验管理
- **Journey**: J2 Phase 2 - 追溯历史
- **~F Reference**: C2 ~F4 历史会话加载 — ✅ verified

## Problem Solved

当前历史会话列表仅展示时间戳，用户不知道哪条会话里问了什么，需逐条点进去翻找（J2 Pain Point #11）。

## User Value

一眼看到每条会话问了什么，快速定位目标会话，像翻聊天记录一样自然。

## Scope

**Includes:**
- 历史会话列表展示会话摘要：首个问题（截断） + 时间
- 按时间倒序排列

**Excludes:**
- 完整对话预览（点击进入后查看完整内容）
- 会话标签/分类

## Phase

MVP

## Dependencies

None

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*