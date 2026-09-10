# Feature: F11 历史会话搜索

## Description

提供关键词搜索历史会话功能，用户输入关键词后匹配包含该词的历史会话，按相关度排序展示。

## Source

- **Capability**: C2 - 对话体验管理
- **Journey**: J2 Phase 2 - 追溯历史
- **~F Reference**: New (Journey-discovered)

## Problem Solved

历史会话积累到几十条后，靠时间排序列表翻找已不现实——用户记得"上次问过方向盘"但记不住是哪天问的（J2 Pain Point #15）。

## User Value

像搜索聊天记录一样快速定位历史会话，不用在几十条记录里翻找。

## Scope

**Includes:**
- 历史会话列表顶部搜索框
- 关键词匹配会话内容（问题 + 答案）
- 搜索结果按相关度排序
- 搜索无结果时展示空态

**Excludes:**
- 全文模糊搜索（MVP 仅关键词匹配）
- 搜索历史记录

## Phase

MVP

## Dependencies

F9（历史会话内容预览，搜索结果展示会话摘要）

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*