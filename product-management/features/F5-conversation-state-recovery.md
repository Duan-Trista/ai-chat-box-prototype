# Feature: F5 对话状态恢复

## Description

用户切后台、跳转车书模块后返回，恢复当前对话状态（气泡、上下文、流式答案进度），不丢失对话内容。

## Source

- **Capability**: C2 - 对话体验管理, C3 - 答案交互与反馈
- **Journey**: J1 Phase 3 - 等待答案, J1 Phase 4 - 获得答案与操作
- **~F Reference**: C2 Session 管理, C3 ~F10 车书章节跳转

## Problem Solved

当前等待答案时切后台，回来发现页面被系统回收，对话丢失（J1 Pain Point #6）。回答中点击 URL 跳转车书模块后返回，对话可能丢失（J1 Pain Point #8）。

## User Value

用户可自由切换 APP 或跳转车书模块，返回后对话状态完整恢复，不丢上下文，不中断体验。

## Scope

**Includes:**
- 切后台返回后恢复当前会话状态
- 跳转车书模块后返回恢复对话状态
- 流式答案中断后恢复（从断点继续或重新请求）
- 超时机制：切后台超过 5 分钟视为新会话

**Excludes:**
- 跨设备同步
- APP 被杀死后恢复（系统级限制）

## Phase

MVP

## Dependencies

F3（多轮对话上下文保持，上下文恢复联动）

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*