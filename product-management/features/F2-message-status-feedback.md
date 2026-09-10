# Feature: F2 消息发送与加载状态反馈

## Description

从用户发送消息到答案生成完毕，全程展示分阶段状态（发送中 → 正在查找车书 → 正在组织答案 → 完成），消除等待焦虑，让用户知道系统在做什么。

## Source

- **Capability**: C1 - 智能问答引擎
- **Journey**: J1 Phase 2 - 提问, J1 Phase 3 - 等待答案
- **~F Reference**: New (Journey-discovered)

## Problem Solved

当前用户发送消息后，不知道系统是否收到（J1 Pain Point #2）。等待答案时只有一个"思考中"动画，无法区分"在搜"和"卡死"（J1 Pain Point #4）。卡车场景网络不稳定，等待焦虑高。

## User Value

分阶段展示进度，用户知道系统正在工作而非卡死，减少被迫等待的焦虑感，知道大概还要等多久。

## Scope

**Includes:**
- 发送中状态（消息气泡+转圈）
- 已发送/已送达状态
- 加载阶段展示"正在查找车书..."→"正在组织答案..."
- 发送失败状态（气泡变灰+感叹号+重试按钮）

**Excludes:**
- 具体的预计等待时间（依赖云端响应速度）
- 网络质量检测（由 F4 覆盖）

## Phase

MVP

## Dependencies

None

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*