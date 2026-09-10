# Capability: C3 答案交互与反馈

## User Goal

对 AI 答案做操作，满足不同使用场景，同时帮助 AI 越用越好。

## Service Personas

P1 - 卡车司机, P2 - 车队管理员, P3 - 潜在购车用户

## Core Values Contributed

- 交互友好 — 丰富答案操作，覆盖不同场景
- 精准权威 — 反馈数据用于优化答案质量

## Scope

**Includes:**
- 点赞 / 不点赞（点踩不展开原因）
- 一键复制答案文本
- 语音播报答案内容
- 答案中附带的车书章节 URL，点击跳转 APP 内车书模块

**Excludes:**
- 会话结束后的评价（MVP 阶段）
- 点踩后展开原因选择（MVP 阶段）

## Dependencies

C1

## Priority

P0

## Priority Justification

用户需求第 7、10 条明确要求。点赞/不点赞是 AI 优化的基础数据来源，语音播报覆盖驾驶场景，URL 跳转连通车书模块。

## Conceptual Scenes（概念化场景）

| ID | 场景名称 | 触发情境 | 关键活动 |
|---|---|---|---|
| ~S1 | 答案反馈 | 答案生成完毕 | 用户点赞或不点赞 |
| ~S2 | 答案操作 | 答案生成完毕 | 用户复制答案、点击语音播报 |
| ~S3 | 答案跳转 | 答案包含车书章节 URL | 点击跳转 APP 内车书模块对应章节 |

> `~S` 前缀表示概念化 Scene，进入 journey-designer 后正式化为 Journey Phases。

## Feature Candidates（候选功能）

| ID | 功能名称 | 一句话描述 | 来源 |
|---|---|---|---|
| ~F7 | 点赞/不点赞 | 答案生成后展示反馈按钮 | ~S1 |
| ~F8 | 复制答案 | 一键复制完整答案文本 | ~S2 |
| ~F9 | 语音播报 | 点击播报答案内容 | ~S2 |
| ~F10 | 车书章节跳转 | 答案中附带 URL，点击跳转 APP 内车书模块 | ~S3 |

> `~F` 前缀表示候选 Feature，进入 journey-designer 后正式编号为 F{n}。

## Status

Planning

## Service Vision

V-卡车助手

---

*Created: 2026-09-02*
*Updated: 2026-09-02*