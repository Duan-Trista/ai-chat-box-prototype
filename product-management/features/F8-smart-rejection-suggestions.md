# Feature: F8 拒识后智能建议追问

## Description

当云端返回拒识（内容未找到或配置不支持）时，根据用户当前问题动态推荐相关的建议追问，而非展示固定的硬编码列表。

## Source

- **Capability**: C1 - 智能问答引擎
- **Journey**: J1 Phase 4 - 获得答案与操作（拒识分支）
- **~F Reference**: C1 ~F3 拒识引导 — ✅ verified

## Problem Solved

当前拒识后展示的 2-3 个建议追问是 APP 端硬编码的固定列表，可能与用户实际想问的完全不相关，用户觉得"AI 根本不懂我"（J1 Pain Point #10）。

## User Value

拒识后推荐的追问与用户当前问题相关，降低挫败感，引导用户换一种问法获取答案，而非直接放弃。

## Scope

**Includes:**
- 拒识后展示 2-3 个动态建议追问
- 建议追问基于用户当前问题语义匹配
- MVP 阶段可由云端返回建议追问，APP 端渲染

**Excludes:**
- APP 端完全自主生成建议追问（依赖云端语义匹配）
- 个性化推荐（后续迭代）

## Phase

MVP

## Dependencies

None

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*