# Feature: F1 消息撤回后编辑重发

## Description

用户发送消息后发现打错字，撤回后原消息文本自动回填到输入框，用户修改后可直接重新发送，无需重新手打。

## Source

- **Capability**: C2 - 对话体验管理
- **Journey**: J1 Phase 2 - 提问, J2 Phase 3 - 消息操作
- **~F Reference**: C2 ~F5 消息操作 — ✅ verified

## Problem Solved

当前用户发送消息后才发现打错字，撤回后需重新手打全部内容（J1 Pain Point #1）。同时撤回操作与流式答案生成存在时间冲突——答案已开始上屏，用户不确定撤回的是问题还是整个对话（J2 Pain Point #12）。

## User Value

卡车司机在车上打字容易出错（手指粗、车身震动），撤回后自动回填节省重新输入时间，降低操作挫败感。

## Scope

**Includes:**
- 发送后允许撤回消息（在答案生成前）
- 撤回后原消息文本自动回填到输入框
- 用户修改后可直接重新发送

**Excludes:**
- 答案已生成后的撤回（与 F5 对话状态恢复协同）
- 已发送消息的编辑（仅撤回后重发）

## Phase

MVP

## Dependencies

None

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*