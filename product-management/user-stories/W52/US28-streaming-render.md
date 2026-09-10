# User Story: US28 流式答案渲染

**Source**: C1 ~F2 流式答案渲染

**As a** 卡车司机，
**I want to** 看到答案逐字上屏，等待时展示思考动画，
**So that** 我知道系统正在处理，不会觉得卡死或没反应。

## Acceptance Criteria

**Scenario: 思考动画**
- Given 用户发送了问题
- When 消息已发送，等待云端返回
- Then 对话区展示 AI 头像 + 思考气泡
- And 思考气泡内展示跳动圆点动画
- And 分两阶段展示状态文案："正在查找车书..." → "正在组织答案..."

**Scenario: 流式逐字上屏**
- Given 云端开始返回答案
- When 首个字符到达
- Then 思考动画消失，AI 答案气泡出现
- And 答案以逐字打字效果上屏，附带闪烁光标
- And 对话区自动滚动到最新内容

**Scenario: 答案生成完毕**
- Given 答案已完整返回
- When 最后一个字符上屏
- Then 闪烁光标消失
- And 答案底部展示"内容由AI生成，仅供参考"免责声明
- And 答案操作按钮（点赞/不点赞、复制、语音播报）展示

**Scenario: 答案包含图片**
- Given 云端返回的答案中包含图片 URL
- When 答案渲染
- Then 图片在答案文本中内嵌展示
- And 图片加载成功时正常展示

**Scenario: 图片加载失败**
- Given 答案中包含图片 URL
- When 图片加载失败（404、超时等）
- Then 展示占位图 + "图片加载失败"提示
- And 提供"点击重试"按钮
- When 用户点击重试
- Then 重新加载该图片

**Scenario: 停止生成**
- Given 答案正在流式上屏中
- When 用户点击"停止生成"按钮
- Then 流式输出立即中断（见 US21）

## INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 动画样式、阶段文案可调整 |
| Valuable | pass | 消除等待焦虑，核心体验 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有状态可模拟 |

## Sizing Hint

M — 涉及 SSE 流式接收 + 动画渲染 + 阶段状态机

## Status

Confirmed

---

*Created: 2026-09-03 (W52)*