# Feature: F3 多轮对话上下文保持

## Description

在同一会话内，多轮追问保持上下文连贯，AI 能理解"它"、"那个"等指代，用户可自然追问。历史会话点击进入后可继续追问，而非只读查看。

## Source

- **Capability**: C2 - 对话体验管理
- **Journey**: J1 Phase 2 - 提问, J2 Phase 1 - 新会话
- **~F Reference**: C2 Session 管理

## Problem Solved

当前用户追问时不确定 AI 是否还记得上一轮的问题（J1 Pain Point #3）。每次进入新会话，上次没问完的上下文断了，想继续追问需重新解释一遍（J2 Pain Point #14）。

## User Value

用户可像和人聊天一样自然追问，AI 理解上下文，不需要每次重新说明背景。历史会话可继续追问，不丢上下文。

## Scope

**Includes:**
- 同一会话内多轮上下文保持（通过 Session ID 管理）
- 历史会话点击进入后可继续追问
- 上下文超时自动失效（切后台超过 5 分钟）

**Excludes:**
- 跨会话上下文共享
- 用户手动切换上下文

## Phase

MVP

## Dependencies

F1（消息撤回后编辑重发，部分场景交叉）

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*