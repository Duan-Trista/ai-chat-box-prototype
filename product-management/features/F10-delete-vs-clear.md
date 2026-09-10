# Feature: F10 会话删除与清空分离

## Description

区分"删除当前会话"和"清空全部记录"两个操作，清空全部需要二次确认，避免用户误操作。

## Source

- **Capability**: C2 - 对话体验管理
- **Journey**: J2 Phase 4 - 清理
- **~F Reference**: C2 ~F6 清空聊天记录 — ✅ verified

## Problem Solved

当前清空与删除粒度混淆——用户可能只想删当前会话，但一键清空按钮干掉了全部历史，用户后悔（J2 Pain Point #13）。

## User Value

精确控制删除范围，想删哪条删哪条，清空全部时有二次确认，避免误操作。

## Scope

**Includes:**
- 删除当前会话（单条，从历史列表中操作）
- 清空全部记录（设置页或顶部按钮，二次确认弹窗）
- 删除/清空后不可恢复

**Excludes:**
- 回收站/撤销删除
- 定时自动清理

## Phase

MVP

## Dependencies

None

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*