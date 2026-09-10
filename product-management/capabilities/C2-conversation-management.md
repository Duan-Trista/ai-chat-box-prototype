# Capability: C2 对话体验管理

## User Goal

自由管理对话，不被历史束缚，也不丢失上下文。每次进入都是新会话，但历史可追溯。

## Service Personas

P1 - 卡车司机, P2 - 车队管理员, P3 - 潜在购车用户

## Core Values Contributed

- 交互友好 — 流畅的对话体验，消息可控

## Scope

**Includes:**
- 每次进入自动开启新会话
- 上拉加载历史会话记录
- 清空聊天记录
- 已发送消息支持撤回、引用、复制、删除
- 多轮对话上下文（Session 管理）

**Excludes:**
- 会话评价（MVP 阶段）
- 会话搜索

## Dependencies

C1

## Priority

P0

## Priority Justification

用户需求第 6、9 条明确要求。每次进入新会话 + 历史可追溯是基础体验，消息操作（撤回/引用/复制/删除）是聊天类功能的标配。

## Conceptual Scenes（概念化场景）

| ID | 场景名称 | 触发情境 | 关键活动 |
|---|---|---|---|
| ~S1 | 新会话 | 每次进入页面 | 自动开启新会话，展示空态欢迎语 |
| ~S2 | 查看历史 | 用户上拉加载 | 加载历史会话，按时间倒序 |
| ~S3 | 消息操作 | 用户长按/点击已发送消息 | 撤回、引用、复制、删除 |
| ~S4 | 清空记录 | 用户点击清空按钮 | 确认后清空所有聊天记录 |

> `~S` 前缀表示概念化 Scene，进入 journey-designer 后正式化为 Journey Phases。

## Feature Candidates（候选功能）

| ID | 功能名称 | 一句话描述 | 来源 |
|---|---|---|---|
| ~F4 | 历史会话加载 | 每次进入新会话，上拉加载历史 | ~S1, ~S2 |
| ~F5 | 消息操作 | 支持撤回、引用、复制、删除已发送消息 | ~S3 |
| ~F6 | 清空聊天记录 | 一键清空所有记录 | ~S4 |

> `~F` 前缀表示候选 Feature，进入 journey-designer 后正式编号为 F{n}。

## Status

Planning

## Service Vision

V-卡车助手

---

*Created: 2026-09-02*
*Updated: 2026-09-02*