# Feature: F4 网络异常处理与重试

## Description

当请求超时或网络异常时，展示明确的错误提示和重试入口，而非沉默失败。用户可一键重试，不必重新输入问题。

## Source

- **Capability**: C1 - 智能问答引擎
- **Journey**: J1 Phase 3 - 等待答案
- **~F Reference**: New (Journey-discovered)

## Problem Solved

当前网络超时后沉默失败——用户看到转圈 10 秒然后消失，不知道发生了什么（J1 Pain Point #5）。卡车经常跑在信号弱的地方（山区、隧道），网络超时是高频场景。

## User Value

超时或失败时用户知道发生了什么，可一键重试，不必重新输入问题，减少中断感。

## Scope

**Includes:**
- 请求前检测网络状态，无网络时 toast 提示
- 请求超时（10 秒）后展示错误提示 + 重试按钮
- 服务器错误（5xx）展示错误提示 + 重试按钮
- 重试时自动使用上次的输入内容

**Excludes:**
- 离线缓存问答（不做离线问答）
- 网络质量预判

## Phase

MVP

## Dependencies

F2（消息发送状态反馈，状态机联动）

## Status

Confirmed

---

*Created: 2026-09-02*
*Updated: 2026-09-02*