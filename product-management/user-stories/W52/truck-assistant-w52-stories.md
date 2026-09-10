# 卡车助手 AI 问答 — User Stories (W52)

> **Date**: 2026-09-03 | **Status**: Confirmed | **Base**: W52 Prototype

## Personas

| ID | 角色 | 说明 |
|----|------|------|
| P1 | 卡车司机 | 主要用户，驾驶中遇到车辆使用问题需即时查询 |
| P2 | 车队管理员 | 管理多车，协助司机解答车辆问题 |
| P3 | 潜在购车用户 | 未绑车，了解车辆信息辅助购车决策 |

---

## US2: 消息发送与加载状态反馈

**Source**: F2 → J1 Phase 2 Pain Point #2, Phase 3 Pain Point #4

**As a** 卡车司机，
**I want to** 看到消息发送和答案加载的实时状态，
**So that** 我知道系统是否收到请求并知道大概还要等多久。

### Acceptance Criteria

**Scenario: 发送中状态**
- Given 用户输入了问题
- When 用户点击发送
- Then 对话区出现用户消息气泡，右侧显示"发送中"转圈动画
- And 输入框清空，发送按钮置灰

**Scenario: 加载中状态**
- Given 消息已发送成功
- When 系统正在处理请求
- Then 对话区出现"思考中"动画气泡
- And 动画气泡下方展示两阶段提示："正在查找车书..."→"正在组织答案..."

**Scenario: 发送失败**
- Given 用户点击了发送
- When 消息发送失败（网络断开或超时）
- Then 消息气泡变灰，右侧显示感叹号图标
- And 气泡下方展示"发送失败，点击重试"文字

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 状态文案可调整 |
| Valuable | pass | 消除等待焦虑 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有状态可模拟 |

**Sizing**: S — 三个状态机，有一定复杂度

---

## US3: 多轮对话上下文保持

**Source**: F3 → J1 Phase 2 Pain Point #3

**As a** 卡车司机，
**I want to** 在同一会话中自然追问且 AI 能理解上下文，
**So that** 我不需要每次重新解释问题背景。

### Acceptance Criteria

**Scenario: 会话内追问**
- Given 用户问"方向盘怎么调"
- And 系统返回了答案
- When 用户追问"那调多高合适"
- Then 系统理解"那"指代方向盘，基于上下文生成答案
- And 答案展示在对话区

**Scenario: 上下文超时**
- Given 用户有一个活跃会话
- When 用户切后台超过 5 分钟后返回
- Then 系统自动开始新会话
- And 展示空态欢迎语

**Scenario: 新对话**
- Given 用户点击"新对话"
- When 确认开启
- Then 清空当前对话区，展示空态欢迎语
- And 之前的上下文不再保留

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 依赖 Session 管理机制 |
| Negotiable | pass | 超时时间可调整 |
| Valuable | pass | 减少重复解释 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有场景可测 |

**Sizing**: M — 涉及 Session 管理 + 上下文维护

**W52 变更**: 移除"历史会话继续追问"场景（历史会话页面已移除）

---

## US4: 网络异常处理与重试

**Source**: F4 → J1 Phase 3 Pain Point #5

**As a** 卡车司机，
**I want to** 网络异常时看到明确提示并能一键重试，
**So that** 我不需要重新输入问题就能再次发起请求。

### Acceptance Criteria

**Scenario: 请求前检测无网络**
- Given 用户输入了问题
- When 用户点击发送
- And 设备当前无网络连接
- Then toast "网络不可用，请稍后重试"
- And 消息不发送，文本保留在输入框

**Scenario: 请求超时**
- Given 用户已发送消息
- When 请求超过 10 秒未返回
- Then 答案气泡展示"请求超时，请重试"
- And 下方展示"重试"按钮
- When 用户点击"重试"
- Then 使用相同内容重新发起请求

**Scenario: 服务器错误**
- Given 用户已发送消息
- When 服务器返回 5xx 错误
- Then 答案气泡展示"服务异常，请稍后重试"
- And 下方展示"重试"按钮

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 依赖 F2 的状态机 |
| Negotiable | pass | 超时时间可调整 |
| Valuable | pass | 减少中断感 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 可模拟网络异常 |

**Sizing**: M — 涉及网络层检测 + 多种异常分类

---

## US5: 对话状态恢复

**Source**: F5 → J1 Phase 3 Pain Point #6, Phase 4 Pain Point #8

**As a** 卡车司机，
**I want to** 切后台或跳转车书后返回时恢复对话状态，
**So that** 我不丢失已有的对话内容和上下文。

### Acceptance Criteria

**Scenario: 切后台后返回**
- Given 用户正在对话中
- And 对话区有历史消息气泡
- When 用户切到后台，5 分钟内返回
- Then 对话区恢复，所有消息气泡完整显示
- And 输入框状态恢复

**Scenario: 跳转车书后返回**
- Given 答案中包含车书章节 URL
- When 用户点击 URL 跳转到车书模块
- And 用户从车书模块返回
- Then 对话页恢复，所有消息气泡完整显示
- And 上下文保持，用户可继续追问

**Scenario: 流式答案中断后恢复**
- Given 答案正在流式上屏中
- When 用户切后台后返回
- Then 若流式连接未断开，继续接收剩余内容
- And 若流式连接已断开，展示已接收内容 + "加载中断，点击重试"

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 依赖 F3 的 Session 管理 |
| Negotiable | pass | 超时时间可调整 |
| Valuable | pass | 避免丢失对话 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 可模拟切后台/跳转场景 |

**Sizing**: S — 页面生命周期管理 + 状态缓存

---

## US6: 语音播报播放控制

**Source**: F6 → J1 Phase 4 Pain Point #7

**As a** 卡车司机，
**I want to** 语音播报时能暂停/继续/停止，
**So that** 我可以自由控制播报进度，不必干等完整听完。

### Acceptance Criteria

**Scenario: 播报中暂停与继续**
- Given 答案已生成，用户点击了语音播报
- When 播报进行中，用户点击暂停按钮
- Then 播报暂停，按钮变为继续图标
- When 用户点击继续按钮
- Then 播报从暂停位置继续

**Scenario: 播报中停止**
- Given 答案正在语音播报中
- When 用户点击停止按钮
- Then 播报立即停止，播放控制栏收起
- And 用户可再次点击语音播报从头播放

**Scenario: 播报完成**
- Given 答案正在语音播报中
- When 播报到达末尾
- Then 播放控制栏自动收起
- And 按钮恢复为初始状态

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 控制按钮样式可调整 |
| Valuable | pass | 卡车场景刚需 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有控制状态可测 |

**Sizing**: S — TTS 播放器控制

---

## US7: 点踩 UI 反馈

**Source**: F7 → J1 Phase 4 Pain Point #9

**As a** 卡车司机，
**I want to** 点踩后看到明确反馈，
**So that** 我知道我的反馈被系统记录了。

### Acceptance Criteria

**Scenario: 点赞**
- Given 答案生成完毕，底部展示点赞/不点赞按钮
- When 用户点击点赞按钮
- Then toast "感谢反馈"
- And 点赞按钮高亮，不点赞按钮置灰

**Scenario: 不点赞**
- Given 答案生成完毕，底部展示点赞/不点赞按钮
- When 用户点击不点赞按钮
- Then toast "感谢反馈"
- And 不点赞按钮高亮，点赞按钮置灰

**Scenario: 重复点击**
- Given 用户已点赞
- When 用户再次点击点赞按钮
- Then 不触发任何操作（已反馈状态不可撤销）

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | toast 文案可调整 |
| Valuable | pass | 提升反馈意愿 |
| Estimable | pass | 范围极小 |
| Small | pass | 单次交互 |
| Testable | pass | 所有状态可测 |

**Sizing**: XS — 极简交互

---

## US8: 拒识后智能建议追问

**Source**: F8 → J1 Phase 4 Pain Point #10

**As a** 卡车司机，
**I want to** 拒识后看到与我问题相关的建议追问，
**So that** 我可以换一种方式获取答案，而不是直接放弃。

### Acceptance Criteria

**Scenario: 拒识展示建议追问**
- Given 用户发送了问题
- When 云端返回拒识（内容未找到或配置不支持）
- Then 对话区展示拒识文案
- And 下方展示 2-3 个与当前问题语义相关的建议追问
- And 每个建议追问可点击

**Scenario: 点击建议追问**
- Given 拒识后展示了建议追问
- When 用户点击某个建议追问
- Then 以用户消息形式发送该追问
- And 进入正常的问答流程

**Scenario: 云端未返回建议追问**
- Given 云端拒识但未返回建议追问
- When 拒识结果返回
- Then 展示拒识文案
- And 展示 APP 端预设的通用建议追问列表

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 建议追问来源可调整 |
| Valuable | pass | 减少拒识挫败感 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 可模拟拒识场景 |

**Sizing**: S — 涉及云端协同 + APP 兜底

---

## US12: 隐私协议与数据声明

**Source**: NFR1 数据隐私与合规

**As a** 合规官，
**I want to** 用户首次进入 AI 助手页时展示隐私协议弹窗，
**So that** 用户明确知晓数据采集范围和使用目的，合规使用。

### Acceptance Criteria

**Scenario: 首次进入展示隐私协议（在助手页内）**
- Given 用户首次点击悬浮入口进入卡车助手
- When 进入对话页
- Then 在对话页内弹出隐私协议弹窗，覆盖整个页面
- And 弹窗展示数据采集范围（对话内容、FAQ 点击数据）和使用目的（优化答案质量）
- And 用户需点击"同意并继续"才能关闭弹窗进入对话
- And 用户点击"不同意"则关闭弹窗，返回 APP 首页，toast "请同意隐私协议后继续使用"

**Scenario: 非首次使用**
- Given 用户已同意过隐私协议
- When 用户再次进入卡车助手
- Then 不展示隐私协议弹窗，直接进入对话页

**Scenario: 隐私协议查看入口**
- Given 用户已在对话页
- When 用户需要查看隐私协议
- Then 可通过设置/菜单中查看隐私协议全文

**Scenario: 同意状态持久化**
- Given 用户已同意隐私协议
- When 用户关闭 APP 后重新打开
- Then 隐私协议同意状态保持，不再弹出

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 文案可调整 |
| Valuable | pass | 合规刚需 |
| Estimable | pass | 范围极小 |
| Small | pass | 弹窗 + 本地状态记录 |
| Testable | pass | 首次/非首次可测 |

**Sizing**: XS

**W52 变更**: 弹窗改为在助手页内弹出（原：首页弹出后跳转），点击"不同意"返回首页

---

## US13: 答案安全免责声明

**Source**: NFR2 答案安全免责

**As a** 合规官，
**I want to** 每条 AI 答案底部展示免责声明，
**So that** 用户知晓 AI 答案仅供参考，紧急情况应拨打 400 电话。

### Acceptance Criteria

**Scenario: 答案底部展示免责声明**
- Given 答案已生成完毕
- When 答案渲染完成
- Then 答案底部固定展示免责声明："内容由AI生成，仅供参考"

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 文案可调整 |
| Valuable | pass | 法律风险防控 |
| Estimable | pass | 范围极小 |
| Small | pass | 固定文案展示 |
| Testable | pass | 答案渲染后展示 |

**Sizing**: XS

---

## US14: 接口安全与日志脱敏

**Source**: NFR3 接口安全与日志脱敏

**As a** 安全工程师，
**I want to** 接口请求携带有效认证 Token 且上报日志不含完整 VIN，
**So that** 系统安全合规且用户隐私不泄露。

### Acceptance Criteria

**Scenario: Token 认证**
- Given 用户已登录
- When APP 向云端发起 AI 问答请求
- Then 请求头携带有效的认证 Token
- And Token 过期时自动刷新，不中断用户体验

**Scenario: Token 过期**
- Given 用户 Token 已过期
- When APP 发起请求
- Then 自动使用刷新 Token 获取新 Token
- And 使用新 Token 重试原请求
- And 整个过程对用户透明

**Scenario: 日志脱敏**
- Given 用户发起了 AI 问答请求
- When APP 上报埋点日志
- Then 日志中不包含完整 VIN（仅保留前 3 位 + 后 4 位）
- And 日志中不包含用户真实姓名、手机号等隐私信息

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 脱敏粒度可调整 |
| Valuable | pass | 安全合规刚需 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | Token 过期/日志脱敏可测 |

**Sizing**: S — Token 刷新机制 + 日志脱敏规则

---

## US15a: 悬浮入口（含拖拽吸附）

**Source**: 设计范畴

**As a** 卡车司机，
**I want to** 在 APP 首页看到悬浮小机器人入口，支持拖拽移动和边框吸附，
**So that** 我可以随时唤起卡车助手，且悬浮按钮不遮挡重要内容。

### Acceptance Criteria

**Scenario: 悬浮入口展示**
- Given 用户已登录，在 APP 首页
- When 页面加载
- Then 右下角展示悬浮小机器人图标
- And 图标不遮挡底部 Tab 栏

**Scenario: 拖拽移动**
- Given 悬浮按钮在首页展示
- When 用户按住按钮并拖拽
- Then 按钮跟随手指在屏幕范围内自由移动
- And 拖拽过程中按钮半透明，展示拖拽态
- And 按钮不会超出屏幕边界

**Scenario: 边框吸附**
- Given 用户拖拽按钮后松手
- When 按钮中心点在屏幕左半区
- Then 按钮吸附到左侧边缘（距离边缘 16px）
- When 按钮中心点在屏幕右半区
- Then 按钮吸附到右侧边缘（距离边缘 16px）
- And 吸附过程带 0.3s 过渡动画

**Scenario: 点击进入（不误触）**
- Given 悬浮按钮在首页展示
- When 用户点击按钮（移动距离 < 3px，视为点击）
- Then 触发进入卡车助手流程
- When 用户拖拽按钮（移动距离 >= 3px，视为拖拽）
- Then 不触发点击进入

**Scenario: 位置记忆**
- Given 用户拖拽按钮到某个位置后松手
- When 用户下次进入 APP 首页
- Then 按钮保持在用户上次设置的位置

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 吸附距离、动画时长可调整 |
| Valuable | pass | 产品入口 + 避免遮挡 |
| Estimable | pass | 范围清晰 |
| Small | pass | 拖拽 + 吸附 + 点击 |
| Testable | pass | 拖拽/点击/吸附可测 |

**Sizing**: S

**W52 变更**: 新增拖拽移动 + 边框吸附 + 点击/拖拽误触区分 + 位置记忆

---

## US15b: 欢迎引导与分类 FAQ

**Source**: 设计范畴

**As a** 卡车司机，
**I want to** 进入对话页后看到清晰的欢迎语和分类 FAQ，
**So that** 我知道能问什么、怎么开始，不用自己摸索。

### Acceptance Criteria

**Scenario: 欢迎语展示**
- Given 用户进入对话页
- When 页面加载完成
- Then 展示欢迎语："你好，我是卡车助手，有什么可以帮你的？"

**Scenario: 分类标签与 FAQ**
- Given 用户在对话页
- When 页面加载完成
- Then 欢迎语下方展示分类标签栏（一期至少包含"车书"标签，后续可扩展"保养"、"用车"）
- And 默认选中第一个标签
- And 选中标签后展示对应的常用问题 FAQ 列表
- And FAQ 列表中每个问题可点击，点击后以用户消息形式发送

**Scenario: 切换分类标签**
- Given 用户在看"车书"分类的 FAQ
- When 用户点击另一个分类标签
- Then 标签切换，FAQ 列表随之切换

**Scenario: FAQ 点击数据收集**
- Given 用户点击了某个 FAQ
- When 消息发送
- Then 记录该 FAQ 的点击事件（见 US22a）

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 文案、标签数量可调整 |
| Valuable | pass | 降低首次使用门槛 |
| Estimable | pass | 范围清晰 |
| Small | pass | 标签 + 列表 |
| Testable | pass | 所有交互可测 |

**Sizing**: S

**W52 变更**: 移除欢迎卡片（横向滑动的问题卡片），仅保留分类 FAQ

---

## US15c: 关键词条推荐

**Source**: 设计范畴

**As a** 卡车司机，
**I want to** 在输入框上方看到运营配置的关键词条推荐，
**So that** 我可以快速了解新功能或重要消息，点击即可发送。

### Acceptance Criteria

**Scenario: 关键词条展示**
- Given 运营在后台配置了关键词条
- When 用户进入对话页
- Then 关键词条在输入框上方固定位置展示，横向排列，支持横向滚动
- And 每个关键词条可点击

**Scenario: 点击关键词条**
- When 用户点击某个关键词条
- Then 以用户消息形式发送对应的问题/内容
- And 进入正常问答流程

**Scenario: 无关键词条配置**
- Given 运营未配置任何关键词条
- Then 关键词条区域不展示

**Scenario: 关键词条点击数据收集**
- Given 用户点击了关键词条
- When 消息发送
- Then 记录该关键词条的点击事件（见 US22a）

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 展示位置、样式可调整 |
| Valuable | pass | 运营推广入口 |
| Estimable | pass | 范围极小 |
| Small | pass | 横向列表 + 点击 |
| Testable | pass | 有/无配置可测 |

**Sizing**: XS

**W52 变更**: 关键词条位置从欢迎语下方移至输入框上方悬浮，支持横向滚动

---

## US16: 文字输入与发送

**Source**: 基础交互 — 设计范畴

**As a** 卡车司机，
**I want to** 在输入框中输入文字并发送，
**So that** 我可以向 AI 助手提问。

### Acceptance Criteria

**Scenario: 正常输入与发送**
- Given 用户在对话页
- When 用户点击输入框
- Then 键盘弹起，输入框获得焦点，页面随键盘上移
- And 输入框 placeholder 显示"输入您的问题，例如：如何调节方向盘高度？"
- When 用户输入文字后点击发送按钮
- Then 消息以气泡形式出现在对话区
- And 输入框清空

**Scenario: 空内容禁止发送**
- Given 输入框为空或仅含空格
- Then 发送按钮置灰，不可点击

**Scenario: 多行输入**
- Given 用户输入较长文字
- When 文字超过一行
- Then 输入框自动扩展高度，最多展示 4 行
- And 超过 4 行后输入框内滚动

**Scenario: 字数限制**
- Given 用户输入文字
- When 文字达到 500 字
- Then 输入框不再接受新字符
- And toast "最多输入 500 字"

**Scenario: 流式输出期间禁止发送**
- Given 答案正在流式上屏中
- When 用户在输入框输入文字
- Then 输入框可编辑但发送按钮变为停止按钮（⏹ 图标）
- And 禁止发送新消息
- When 用户点击停止按钮
- Then 流式输出中断，按钮恢复为发送按钮，用户可继续发送

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 字数限制、行数可调整 |
| Valuable | pass | 核心交互入口 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有场景可测 |

**Sizing**: S

---

## US17: 复制答案

**Source**: C3 ~F8 — 设计范畴

**As a** 卡车司机，
**I want to** 一键复制 AI 答案的完整文本，
**So that** 我可以粘贴到微信或备忘录里分享给其他人。

### Acceptance Criteria

**Scenario: 复制完整答案**
- Given 答案已生成完毕，底部展示操作按钮
- When 用户点击"复制"按钮
- Then 完整答案文本复制到系统剪贴板
- And toast "已复制"

**Scenario: 流式输出中复制**
- Given 答案正在流式上屏中
- When 用户点击"复制"按钮
- Then 复制当前已展示的文本内容
- And toast "已复制"

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | toast 文案可调整 |
| Valuable | pass | 高频使用场景 |
| Estimable | pass | 范围极小 |
| Small | pass | 单次交互 |
| Testable | pass | 可验证剪贴板内容 |

**Sizing**: XS

---

## US18: 车书章节跳转

**Source**: C3 ~F10 — 设计范畴

**As a** 卡车司机，
**I want to** 点击答案中附带的车书章节链接跳转到 APP 内车书模块对应章节，
**So that** 我可以查看完整的功能说明和操作图示。

### Acceptance Criteria

**Scenario: 答案包含车书章节链接**
- Given 答案中包含车书章节 URL
- When 答案渲染完成
- Then URL 以可点击链接形式展示
- When 用户点击链接
- Then 跳转到 APP 内车书模块对应章节

**Scenario: 从车书返回**
- Given 用户已跳转到车书模块
- When 用户返回
- Then 对话页恢复，所有消息气泡完整展示（见 US5）
- And 上下文保持，用户可继续追问

**Scenario: 答案不包含链接**
- Given 答案中不包含车书章节 URL
- Then 不展示链接入口

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 依赖 US5 的对话状态恢复 |
| Negotiable | pass | 链接样式可调整 |
| Valuable | pass | 连通车书模块 |
| Estimable | pass | 范围极小 |
| Small | pass | 路由跳转 |
| Testable | pass | 有/无链接场景可测 |

**Sizing**: XS

---

## US19: 车辆上下文标识

**Source**: 产品设计确认 — 设计范畴

**As a** 卡车司机，
**I want to** 在对话页顶部看到当前咨询的车辆信息并可切换，
**So that** 我知道 AI 回答是基于哪辆车的知识库。

### Acceptance Criteria

**Scenario: 展示当前车辆**
- Given 用户已绑定车辆
- When 用户进入对话页
- Then 顶部导航栏展示当前车辆标识（车牌号 + 车型简称）
- And 默认选中最近一次咨询的车辆

**Scenario: 切换车辆**
- Given 用户有多辆绑定车辆
- When 用户点击顶部车辆标识
- Then 弹出车辆选择列表，每辆展示车牌号 + 车型
- When 用户选择另一辆车
- Then 车辆标识更新
- And 对话区插入系统提示："已切换到「沪B·67890 G Series ICE」"
- And 后续问题基于新车辆的知识库

**Scenario: 仅有一辆车**
- Given 用户仅绑定一辆车
- Then 顶部展示车辆标识但不展示切换箭头
- And 用户无法切换

**Scenario: 未绑定车辆**
- Given 用户未绑定任何车辆
- Then 顶部展示"未选择车辆"
- When 用户点击
- Then 引导去车辆管理页绑定

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 展示样式可调整 |
| Valuable | pass | 避免张冠李戴 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 多车/单车/无车可测 |

**Sizing**: S

---

## US21: 停止生成

**Source**: 竞品参考

**As a** 卡车司机，
**I want to** 在流式答案生成中点击停止按钮中断生成，
**So that** 答案方向不对或等待太久时我可以及时止损，不必干等或退出。

### Acceptance Criteria

**Scenario: 流式输出中停止**
- Given 答案正在流式上屏中
- When 用户点击"停止生成"按钮
- Then 生成立即中断
- And 已生成的部分内容保留在对话区
- And 输入框恢复可用，用户可重新提问

**Scenario: 停止后重新提问**
- Given 用户已停止生成
- When 用户输入新问题并发送
- Then 正常进入问答流程

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 按钮位置可调整 |
| Valuable | pass | 减少无效等待 |
| Estimable | pass | 范围极小 |
| Small | pass | 单次交互 |
| Testable | pass | 可模拟流式输出场景 |

**Sizing**: XS

---

## US22a: 核心埋点（MVP）

**Source**: 产品运营需求

**As a** 产品运营，
**I want to** 采集卡车助手的核心使用行为数据，
**So that** 我可以衡量产品表现（渗透率、完成率、拒识率、点踩率）。

### Acceptance Criteria

**Scenario: MVP 核心事件**
- Given 用户在使用卡车助手
- When 发生以下事件，触发埋点上报：
  - 进入卡车助手
  - 发送问题
  - 收到答案（标记是否拒识）
  - 点赞 / 不点赞
  - 点击 FAQ
  - 点击关键词条
  - 复制答案
  - 点击语音播报
  - 停止生成
- Then 事件数据上报到埋点平台

**Scenario: 埋点数据字段**
- Given 每个埋点事件
- Then 包含：事件名称、时间戳、会话 ID、用户 ID（脱敏）、VIN（脱敏）、事件属性

**Scenario: 埋点不影响用户体验**
- Given 埋点上报
- When 上报失败
- Then 不阻塞用户操作，静默丢弃

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 事件列表可增减 |
| Valuable | pass | 支撑 Success Metrics |
| Estimable | pass | 范围清晰 |
| Small | pass | 9 个核心事件 |
| Testable | pass | 可验证埋点数据 |

**Sizing**: S

**W52 变更**: 移除已删除功能的埋点事件，保留 AI 答案操作相关事件

---

## US22b: 扩展埋点（后续迭代）

**Source**: 产品运营需求

**As a** 产品运营，
**I want to** 采集卡车助手的扩展使用行为数据，
**So that** 我可以深入分析用户行为并持续优化产品。

### Acceptance Criteria

**Scenario: 扩展事件**
- Given 用户在使用卡车助手
- When 发生以下事件，触发埋点上报：
  - 退出卡车助手
  - 点击车书链接
  - 上拉加载历史消息
  - 拖拽悬浮按钮
  - 点击"新对话"
  - 车辆切换
  - 会话时长
- Then 事件数据上报到埋点平台

**Scenario: 埋点数据字段**
- Given 每个埋点事件
- Then 包含：事件名称、时间戳、会话 ID、用户 ID（脱敏）、VIN（脱敏）、事件属性

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 事件列表可增减 |
| Valuable | pass | 深入优化数据支撑 |
| Estimable | pass | 范围清晰 |
| Small | pass | 7 个扩展事件 |
| Testable | pass | 可验证埋点数据 |

**Sizing**: S

**W52 变更**: 移除已删除功能的埋点事件，新增 W52 新增功能事件

---

## US25: 流式输出中操作按钮可用

**Source**: 竞品参考

**As a** 卡车司机，
**I want to** 在答案流式输出中就能复制和点赞，
**So that** 我不用等答案全部出完才能操作。

### Acceptance Criteria

**Scenario: 流式输出中复制**
- Given 答案正在流式上屏中
- When 用户点击答案气泡下方的"复制"按钮
- Then 复制当前已展示的文本内容
- And toast "已复制"

**Scenario: 流式输出中反馈**
- Given 答案正在流式上屏中
- When 用户点击答案气泡下方的"点赞"或"不点赞"
- Then 记录反馈，按钮高亮
- And toast "感谢反馈"

**Scenario: 流式输出中语音播报**
- Given 答案正在流式上屏中
- When 用户点击"语音播报"按钮
- Then 播报当前已生成的内容

**Scenario: 操作按钮展示时机**
- Given 答案流式输出
- When 首个字符上屏
- Then 操作按钮区域（复制、点赞、不点赞、语音播报）立即展示
- And 答案生成完毕后按钮不消失

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 按钮展示时机可调整 |
| Valuable | pass | 减少等待时间 |
| Estimable | pass | 范围极小 |
| Small | pass | 按钮展示时机调整 |
| Testable | pass | 可模拟流式输出场景 |

**Sizing**: XS

---

## US26: 首次/非首次进入差异化展示

**Source**: W52 新增

**As a** 卡车司机，
**I want to** 首次进入时看到欢迎语和 FAQ 引导，再次进入时看到上次的聊天记录，
**So that** 首次能快速上手，后续能直接继续上次的对话。

### Acceptance Criteria

**Scenario: 首次进入展示欢迎引导**
- Given 用户从未使用过卡车助手
- When 用户点击悬浮入口进入
- Then 展示欢迎语 + 分类 FAQ
- And 关键词条在输入框上方展示

**Scenario: 非首次进入展示聊天记录**
- Given 用户之前使用过卡车助手且有聊天记录
- When 用户再次点击悬浮入口进入
- Then 展示上次的聊天记录（对话区已有历史消息）
- And 输入框可用，用户可继续发送新问题
- And 不展示欢迎语和 FAQ

**Scenario: 非首次进入但无聊天记录**
- Given 用户之前使用过但已清空记录
- When 用户再次进入
- Then 展示欢迎语 + FAQ（同首次进入）

**Scenario: 点击"新对话"后**
- Given 用户点击了"新对话"
- When 确认后进入新对话
- Then 展示欢迎语 + FAQ（等同于首次进入状态）

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 展示逻辑可调整 |
| Valuable | pass | 降低首次门槛 + 减少重复操作 |
| Estimable | pass | 范围清晰 |
| Small | pass | 状态判断 + 条件渲染 |
| Testable | pass | 首次/非首次/清空后场景可测 |

**Sizing**: S

---

## US27: 上拉加载历史消息

**Source**: W52 新增

**As a** 卡车司机，
**I want to** 在对话页上拉加载更早的历史消息，
**So that** 我可以回顾之前的对话内容，无需跳转到独立的"历史会话"页面。

### Acceptance Criteria

**Scenario: 上拉加载**
- Given 用户在对话页，且有历史消息
- When 用户向上滑动到对话区顶部
- Then 展示"下拉加载更多..."提示
- And 加载完成后，更早的历史消息追加到对话区顶部
- And 滚动位置保持在当前可视区域

**Scenario: 加载中状态**
- Given 用户触发上拉加载
- When 数据正在请求中
- Then 展示加载动画 + "加载中..." 文案
- And 加载完成后动画消失

**Scenario: 没有更多历史**
- Given 所有历史消息已加载完毕
- When 用户再次上拉
- Then 展示"没有更多了"提示
- And 不再触发加载请求

**Scenario: 无历史消息**
- Given 用户没有历史消息
- When 用户进入对话页
- Then 展示欢迎语 + FAQ（首次进入状态）
- And 上拉不触发加载

**Scenario: 加载失败**
- Given 用户触发上拉加载
- When 网络请求失败
- Then 展示"加载失败，点击重试"
- And 用户点击可重新加载

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 分页大小、加载文案可调整 |
| Valuable | pass | 替代历史会话页面，减少页面跳转 |
| Estimable | pass | 范围清晰 |
| Small | pass | 分页加载 + 状态提示 |
| Testable | pass | 有/无数据、加载失败场景可测 |

**Sizing**: S

---

## US28: 流式答案渲染

**Source**: C1 ~F2

**As a** 卡车司机，
**I want to** 看到答案逐字上屏，等待时展示思考动画，
**So that** 我知道系统正在处理，不会觉得卡死或没反应。

### Acceptance Criteria

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

### INVEST Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| Independent | pass | 独立可交付 |
| Negotiable | pass | 动画样式、阶段文案可调整 |
| Valuable | pass | 消除等待焦虑，核心体验 |
| Estimable | pass | 范围清晰 |
| Small | pass | 可一次迭代完成 |
| Testable | pass | 所有状态可模拟 |

**Sizing**: M — 涉及 SSE 流式接收 + 动画渲染 + 阶段状态机

---

## Story Index

| ID | Title | Persona | Size | Status |
|----|-------|---------|------|--------|
| US2 | 消息发送与加载状态反馈 | P1, P2, P3 | S | pass |
| US3 | 多轮对话上下文保持 | P1, P2, P3 | M | pass |
| US4 | 网络异常处理与重试 | P1, P2, P3 | M | pass |
| US5 | 对话状态恢复 | P1, P2, P3 | S | pass |
| US6 | 语音播报播放控制 | P1, P2, P3 | S | pass |
| US7 | 点踩 UI 反馈 | P1, P2, P3 | XS | pass |
| US8 | 拒识后智能建议追问 | P1, P2, P3 | S | pass |
| US12 | 隐私协议与数据声明 | 合规官 | XS | pass |
| US13 | 答案安全免责声明 | 合规官 | XS | pass |
| US14 | 接口安全与日志脱敏 | 安全工程师 | S | pass |
| US15a | 悬浮入口（含拖拽吸附） | P1, P2, P3 | S | pass |
| US15b | 欢迎引导与分类 FAQ | P1, P2, P3 | S | pass |
| US15c | 关键词条推荐 | P1, P2, P3 | XS | pass |
| US16 | 文字输入与发送 | P1, P2, P3 | S | pass |
| US17 | 复制答案 | P1, P2, P3 | XS | pass |
| US18 | 车书章节跳转 | P1, P2, P3 | XS | pass |
| US19 | 车辆上下文标识 | P1, P2, P3 | S | pass |
| US21 | 停止生成 | P1, P2, P3 | XS | pass |
| US22a | 核心埋点（MVP） | 产品运营 | S | pass |
| US22b | 扩展埋点（后续迭代） | 产品运营 | S | pass |
| US25 | 流式输出中操作按钮可用 | P1, P2, P3 | XS | pass |
| US26 | 首次/非首次进入差异化展示 | P1, P2, P3 | S | pass |
| US27 | 上拉加载历史消息 | P1, P2, P3 | S | pass |
| US28 | 流式答案渲染 | P1, P2, P3 | M | pass |

---

*Created: 2026-09-03 (W52)*