# 🔭 Builder Radar

> 追踪 29 位 AI 产品 Builder 的 shipping 动态，不做观点二传手。
> Track what 29 AI product builders SHIP, not what they THINK.

[![Version](https://img.shields.io/badge/version-3.2.0-blue)](https://github.com/Elisedai1013/builder-radar)
[![License](https://img.shields.io/badge/license-MIT-green)](./LICENSE)
[![Builders](https://img.shields.io/badge/builders-29-orange)](./builders.json)

---

## 这是什么？ / What is this?

AI Builder 圈信息噪音巨大——每天几百条推文、博客、视频，但真正**可操作的产品信号**不到 5%。

**Builder Radar** 每天自动扫描 29 位一线 AI Builder 的 X、博客、YouTube，用三维打分体系（实时性 × 重要程度 × 火爆程度）帮你筛出真正值得看的东西。

核心原则就一条：

> **只追踪发货，不追踪观点。**
> 产品发布 > Demo > 技术深潜 > 官方博客 > 验证过的案例 > 大会演讲
> 跳过：观点、预测、热帖、评论 —— 它们不给你可行动的信息。
>
> **Track what people SHIP, not what they THINK.**
> Product launches > demos > technical deep-dives > official blog posts > verified case studies > conference talks
> Skip: opinions, predictions, hot takes, commentary.

---

## 它怎么帮你筛信息？ / How does it filter?

### 三维独立打分（v3.0）

每条通过内容过滤器的信号，在三个维度上独立评分（0-10），不再用单一公式一刀切：

| 维度 | 权重 | 衡量什么？ |
|------|------|-----------|
| **实时性** Freshness | 0.3 | 多久前发生的？≤24h = 10 分，>1 月 = 2 分 |
| **重要程度** Importance | 0.4 | 对你有实际影响吗？架构重组 10 分，功能更新 5 分 |
| **火爆程度** Community Heat | 0.3 | 社区在讨论吗？跨 Builder 引用 +3，HackerNews 首页 +2 |

**为什么重要程度权重最高（0.4）？** 一条火但没营养的 rumor（热度 9，重要性 2）不该排在一条安静但致命的架构变更（热度 3，重要性 10）前面。

### 内容过滤器（打分前强制执行）

```
✅ IN                                ❌ OUT
产品发布 / Feature 上线              观点 / 热帖 / 预测
技术深潜 / 架构文                     评论 thread / 引战帖
Live Demo / 录屏                     "AI 的未来" 泛泛而谈
官方博客                             VC 融资公告（非 Builder 工具）
生产案例（有可验证数据）               招聘帖
大会演讲（一手产品内容）               纯炒作 / 流量帖
```

### 🔥 热度雷达（防跟风）

火爆程度 ≥8 但重要程度 <7 的信号会被单独标记为"hype check"——告诉你这东西很火，但未必值得你花时间。

---

## 覆盖范围 / Coverage

**29 位 Builder**，四个层级：

| Tier | 类型 | 数量 | 代表 Builder |
|------|------|------|-------------|
| 🔴 Product Builder | 产品一线 | 19 | Boris Cherny, Thibault Sottiaux, Amjad Masad, Guillermo Rauch, Peter Steinberger |
| 🟡 Official | 官方账号 | 2 | @ClaudeAI, @GoogleLabs |
| 🟢 Ecosystem | 生态 | 7 | Garry Tan (YC), Dan Shipper (Every), Simon Willison |
| 🔵 Observer | 观察者 | 1 | Zara Zhang (follow-builders) |

覆盖产品线：**Anthropic · OpenAI · Google · Replit · Vercel · Box · Notion · Roblox**

数据来源：基于 [follow-builders](https://github.com/zarazhangrui/follow-builders)，持续维护在 `builders.json`。

---

## 输出长什么样？ / Sample Output

每天生成的日报包含 8 个板块：

```
🚨 今日速报         — Breaking news，即时插入
🏆 Tier 1 必读      — Composite ≥ 7.0，含三维打分条
🥈 Tier 2 值得关注   — Composite 4.0–6.9
🧭 Tier 3 新 Talk   — 大会演讲 YouTube 链接（可对接 youtube-learning）
🔥 Heat Radar       — 火但不一定有用的内容（Hype Check）
🗑️ 已跳过           — 被过滤器挡掉的内容，证明扫过了
🔍 Tracking Gaps    — 哪个产品线本周没信号？
📋 Next Radar       — 下次该盯什么？
```

每一条 Tier 1/2 内容都附带**三级来源链接**（YouTube → 作者博客 → X 原帖），保证你能点进去看原文。

---

## 工作流概览 / Workflow at a Glance

```
Step 0: 加载追踪库 + 时间窗口计算
Step 1: 并行搜索 29 位 Builder 的 shipping 信号
Step 2: 收集社区热度信号（跨 Builder 引用、HN、媒体报道）
Step 3: 搜索新上传的大会演讲（YouTube）
Step 4: 内容过滤器（IN/OUT 门禁）
Step 5: 三维独立打分
Step 6: 生成结构化日报
Step 7: 呈现 + 提供下一步行动建议
```

完整工作流定义见 [SKILL.md](./SKILL.md)。

---

## 安装 / Install

```bash
git clone https://github.com/Elisedai1013/builder-radar.git
```

---

## 目录结构 / Structure

```
builder-radar/
├── SKILL.md          # 完整工作流定义（287 行，给 Agent 看）
├── builders.json     # 29 位 Builder 追踪库
├── templates/
│   └── digest.md     # 日报模板
└── README.md         # 你正在看的这个
```

---

## 版本 / Version

**v3.2.0** — Source Link Priority 三级验证 + 3D 独立打分 + Heat Radar + 内容过滤

| 版本 | 关键变更 |
|------|---------|
| v3.2.0 | 三级来源链接验证（YouTube → 博客 → X），链接缺失自动降级 |
| v3.0.0 | 三维独立打分替代单一公式，新增火爆程度维度 + Heat Radar |
| v2.0.0 | 内容过滤器 + builder 追踪库结构化 |
| v1.0.0 | 初始版本，基础搜索 + 报告生成 |

---

## 许可 / License

MIT

---

*Made with ☕ by [Elisedai](https://github.com/Elisedai1013)*
