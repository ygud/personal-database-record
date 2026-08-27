# Personal OS — 个人数据库与人生轨迹记录系统

> 状态：Idea / Architecture Draft
>
> 当前阶段只记录项目理念、总体架构与发展方向，不急于实现全部功能。

---

## 1. 项目愿景

这个项目不是单纯的“个人数据库”，也不是一次性完成的“AI 个人克隆”。

我们的目标是从大学开始，逐步建立一个属于自己的、长期可迁移的 **Personal OS（个人信息与人生轨迹系统）**。

它希望持续回答三个问题：

> 我经历过什么？

> 我正在经历什么？

> 这些经历让我发生了什么变化？

系统会随着大学生活逐渐接入不同的信息来源，例如：

- 学习
- 课程
- 项目
- 竞赛
- 社团与活动
- 日记
- 笔记
- 浏览与信息消费
- 新闻
- 照片
- 邮件
- 未来出现的其他软件和服务

但这些功能不需要一次性完成。

系统应该先建立一个稳定、开放、可迁移的底座，然后不断增加新的数据源和能力。

---

# 2. 核心理念

## 2.1 Memory：记住发生过什么

个人数据库负责保存事实和原始信息。

例如：

- 某天参加了什么活动
- 完成了什么项目
- 看过什么内容
- 学习了什么
- 写过什么笔记
- 产生过什么想法
- 参加过什么竞赛
- 某个时期对什么产生了兴趣

数据库的核心职责：

> 可靠记录、关联、检索。

数据库不应该擅自替用户解释人生。

---

## 2.2 Growth：理解发生了什么变化

单纯的数据库只能形成一个越来越大的个人信息仓库。

因此系统需要独立的 **Growth Agent（成长 Agent）**。

它周期性读取一段时间内的事实数据，并整理成：

- 日总结
- 周复盘
- 月复盘
- 学期复盘
- 学年总结
- 长期成长轨迹

它回答的问题是：

> 这段时间我做了什么？

> 我发生了什么变化？

> 我一直在关注什么？

> 我遇到了哪些问题？

> 哪些事情真正推动了我的成长？

---

# 3. 事实层与成长层分离

整个系统最重要的设计之一：

```text
                    Personal OS

              ┌───────────────────┐
              │    Memory Layer   │
              │    事实 / 原始数据 │
              └─────────┬─────────┘
                        │
                        ▼
                Growth Agent
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
       Weekly         Monthly       Semester
       Review         Review         Review
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                 Growth Timeline
                    成长轨迹

这样不会一开始就把项目搞得很重。

# 4. 分层记忆
未来的数据量可能非常巨大。
例如大学四年：
大量原始事件
      ↓
Daily Summary
      ↓
Weekly Review
      ↓
Monthly Review
      ↓
Semester Review
      ↓
Year Review
      ↓
University Timeline
这样当用户询问：
“我大一做了什么？”

系统可以首先读取大一的结构化总结。
如果继续询问：
“你刚才说我参加了一个竞赛，具体是什么？”

再继续向下检索：
Year
 ↓
Semester
 ↓
Month
 ↓
Week
 ↓
Event
 ↓
Original Note / File
这是一种 Hierarchical Memory（分层记忆）。

#5. Growth Agent
Growth Agent 是整个系统中非常重要的长期组件。
它不是简单的“AI 总结器”。
它应该逐渐承担：
- 时间整理
- 经历总结
- 趋势分析
- 兴趣变化识别
- 能力变化识别
- 长期目标追踪
- 问题重复出现检测
- 行动计划追踪
但是：
AI 不应该代替用户进行最终的价值判断。

# 6. 复盘闭环
系统最终希望形成：
事件
 ↓
Agent 整理
 ↓
周 / 月复盘
 ↓
用户自己的反思
 ↓
行动计划
 ↓
下一周期
 ↓
实际行动
 ↓
Agent 对比
 ↓
新的复盘
例如：
Week 1

发现：
项目太多，经常切换

↓

用户反思：
我应该减少同时进行的项目

↓

Week 2

实际：
仍然同时进行多个项目

↓

Week 3

实际：
主动关闭两个项目

↓

Month Review

AI：
你正在逐渐改善项目切换问题
这使系统从“记录工具”逐渐变成“成长反馈系统”。

# 7. 用户自己的反思必须保留
AI 可以：
- 整理
- 提醒
- 分析
- 提问
- 发现趋势
但用户自己的：
- 感受
- 判断
- 反思
- 决定
- 人生选择
应该保留原始记录。
例如：
“这次竞赛让我发现，我并不擅长团队沟通。”

这句话应该作为用户自己的原始记录保存。
AI 可以进一步分析，但不能把 AI 的解释替换成用户原话。

# 8. 统一数据库
系统采用一个统一的 Personal Database。
不同功能共享数据库，但必须进行逻辑隔离和权限控制。
概念结构：
personal_os
│
├── core
│   ├── events
│   ├── sources
│   └── attachments
│
├── memory
│   ├── facts
│   ├── observations
│   └── profile
│
├── openbiliclaw
│   ├── discoveries
│   ├── preferences
│   └── feedback
│
├── news
│   ├── articles
│   ├── sources
│   └── digests
│
└── growth
    ├── daily_summaries
    ├── weekly_reviews
    ├── monthly_reviews
    ├── semester_reviews
    └── yearly_reviews
以上只是概念设计。
当前阶段不提前确定所有数据库表。

# 9. 模块隔离与权限控制
统一数据库不意味着所有模块拥有全部权限。
例如：
OpenBiliClaw
    ↓
只能访问其需要的数据

News Engine
    ↓
主要访问新闻相关数据

Growth Agent
    ↓
可以读取多个模块
但不能随意修改原始事实

Admin
    ↓
拥有完整管理权限
未来应通过数据库角色、Schema、API 权限等机制实现隔离。

# 10. 当前第一阶段
目前只做最重要的基础设施。
Phase 1
统一数据库
建立 Personal Database，作为以后所有功能的共同数据底座。
OpenBiliClaw
作为主动的信息探索层。
它负责：
根据对用户的理解，主动从多个平台寻找可能值得用户了解的信息。

News Engine
主动收集新闻热点。
Morning Brief
每天早晨：
新闻源
 ↓
采集
 ↓
去重 / 聚类
 ↓
AI 摘要
 ↓
结合用户兴趣筛选
 ↓
Morning Brief
 ↓
Email
目标是：
每天早上打开邮箱，就能直接阅读一份属于自己的新闻简报。

# 11. 数据存储架构
原始数据和数据库需要分离。
概念架构：
                     GitHub
                代码 / 配置 / 文档
                       │
                       ▼
Mac ───────→ OneDrive ───────→ VPS
            原始资料           计算 / 数据库 / Agent
                                  │
                                  ▼
                            Google Drive
                               异地备份

# 12. OneDrive
OneDrive 作为日常数据入口之一。
原因：
本地电脑可以正常使用 OneDrive，因此不要求本地网络环境直接向 VPS 上传所有数据。
理想流程：
Mac
 ↓
OneDrive
 ↓
VPS 自动获取
 ↓
Personal OS
这样可以降低 VPS 与本地网络环境之间的耦合。

# 13. VPS
VPS 是系统的：
- AI / Agent 运行环境
- 数据库运行环境
- 新闻采集环境
- OpenBiliClaw 运行环境
- 自动任务运行环境
但：
VPS 不是数据的唯一来源。

VPS 应该被视为一个可替换的计算节点。
# 14. Google Drive
Google Drive 用作异地备份。
未来可以备份：
- PostgreSQL 数据库
- 结构化数据
- 系统配置
- 重要原始资料
未来需要进一步增加：
- 自动备份
- 备份失败告警
- 完整性检查
- 定期恢复测试
不能只做简单的文件复制。

# 15. 灾难恢复
系统从一开始就假设 VPS 随时可能损坏。
理想情况下：
旧 VPS 损坏
      ↓
购买新 VPS
      ↓
从 GitHub 获取代码
      ↓
部署 Docker 环境
      ↓
恢复数据库
      ↓
从 OneDrive 获取原始数据
      ↓
重建索引 / Embedding
      ↓
恢复服务
因此：
VPS 可以丢，但个人数据不能丢。

# 16. GitHub 与个人数据分离
GitHub 保存：
- 代码
- 配置模板
- 数据结构
- Agent Prompt
- Docker 配置
- 文档
- 通用脚本
GitHub 不保存：
- API Key
- Cookie
- Token
- 密码
- 个人日记
- 个人画像
- 浏览记录
- 私人文件
- 私人数据库
原则：
公开代码，私有数据。

# 17. AI 个人画像
AI 可以逐渐形成个人画像，但画像不是绝对事实。
例如：
不能简单因为：
最近看了很多法律内容

就永久记录：
用户喜欢法律。

更合理的方式：
Observation
最近一段时间法律相关内容增加

Evidence
具体事件 / 浏览 / 笔记

Confidence
置信程度

Status
待观察 / 持续 / 已变化
长期画像应该建立在大量实际证据之上。

# 18. OpenBiliClaw 的定位
OpenBiliClaw 是 Personal OS 的一个信息探索模块。
它负责：
主动从互联网多个平台寻找用户可能感兴趣的信息。

而 Personal OS 负责：
保存这些信息与用户之间产生的关系。

因此：
OpenBiliClaw
       ↓
Information Discovery
       ↓
Personal OS
       ↓
Memory / Growth
OpenBiliClaw 不应该成为整个 Personal OS 的数据库所有者。
未来即使替换 OpenBiliClaw，也不应该影响整个个人数据库。
# 19. Adapter 架构
未来不知道会使用什么软件。
因此不能把系统写死在某一个软件上。
新的信息来源应该通过 Adapter 接入：
Obsidian ───────┐
Calendar ───────┤
Email ──────────┤
Photos ─────────┤
Course System ──┤
Browser ────────┤
Manual Input ───┤
                 ▼
            Personal OS
每个 Adapter 将外部数据转换成统一的数据模型。
以后即使更换软件，也不需要重建整个系统。
# 20. 当前不做什么
为了避免项目失控，当前明确：
- 不一次性开发完整 AI Personal Clone
- 不提前接入所有软件
- 不提前设计所有数据库表
- 不堆叠大量数据库
- 不把 VPS 作为唯一数据源
- 不让 AI 随意修改原始事实
- 不将个人隐私上传到公开 GitHub
- 不为了功能数量而提前开发未来需求
当前目标只有：
先把底座做好。

# 21. 长期路线图
Phase 0 — Foundation
- 建立 GitHub 仓库
- 完善项目设计文档
- 确定数据所有权原则
- 确定隐私原则
- 确定备份原则
- 确定统一数据模型
Phase 1 — Information Infrastructure
- PostgreSQL
- OpenBiliClaw
- News Engine
- Morning Brief
- Email
- OneDrive → VPS
- VPS → Google Drive
- 灾难恢复
Phase 2 — Personal Memory
- Event 模型
- Note 模型
- Artifact 模型
- AI Memory
- 时间线
- Personal Profile
- Evidence / Confidence
Phase 3 — Growth Agent
- Daily Summary
- Weekly Review
- Monthly Review
- Semester Review
- Yearly Review
- 用户反思
- 成长轨迹查询
Phase 4 — Integrations
根据大学生活实际需要逐步增加：
- Obsidian
- Calendar
- 课程
- Email
- Photos
- 项目
- 竞赛
- 社团
- 移动端输入
Phase 5 — Long-term Personal Intelligence
探索：
- 长期人生轨迹
- 能力变化
- 兴趣变化
- 行为模式
- 目标追踪
- 跨年度比较
- 长期人生复盘
# 22. 最终希望能够回答的问题
几年以后，希望可以直接问：
我大一做了什么？

我大一参加过哪些竞赛和活动？

我什么时候开始对 AI Agent 感兴趣？

我过去一年学会了什么？

大一到大二，我发生了哪些变化？

我过去反复遇到的问题是什么？

哪些目标我一直没有完成？

我的兴趣发生过什么变化？

当时我为什么做出了这个决定？

系统应该：
1. 先从结构化的成长记录回答；
2. 如果需要，再深入查询月份、周记录；
3. 最后可以追溯到具体 Event、Note 和原始资料。

# 23. 项目的最终目标
我们最终不是想建立一份静态的“个人画像”。
而是建立一条：
可以不断记录、不断理解、不断回看的个人生命轨迹。

数据库负责：
记住。

Growth Agent 负责：
理解。

用户自己负责：
反思与选择。

# 24. 一句话定义
记录事实，保存记忆；定期复盘，理解成长；让数据属于自己，让系统可以不断进化。
