# 🔭 Builder Radar

> 追踪 29 位 AI 产品 Builder 的 shipping 动态，不做观点二传手。
> Track what 29 AI product builders SHIP, not what they THINK.

---

## 这是什么？ / What is this?

**Builder Radar** 是一个 AI Agent Skill，每日扫描 AI Builder 圈的产品发布、技术深度文、大会演讲，用三维打分体系（实时性 × 重要程度 × 火爆程度）帮你筛选出真正值得看的内容。

**Builder Radar** is an AI Agent Skill that scans the AI builder ecosystem daily — product launches, technical deep-dives, conference talks — filtered through a 3D scoring system (Freshness × Importance × Community Heat).

### 核心原则 / Core Principle

> **只追踪发货，不追踪观点。**
> 产品发布 > Demo > 技术深潜 > 官方博客 > 验证过的案例 > 大会演讲。
> 跳过：观点、预测、热帖、评论。

> **Track what people SHIP, not what they THINK.**
> Product launches > demos > technical deep-dives > official blog posts > verified case studies > conference talks.
> Skip: opinions, predictions, hot takes, commentary.

---

## 覆盖范围 / Coverage

**29 位 Builder**，分四个层级：

| Tier | 类型 | 数量 | 代表 |
|------|------|------|------|
| 🔴 Product Builder | 产品一线 | 19 | Boris Cherny, Thibault Sottiaux, Amjad Masad, Guillermo Rauch |
| 🟡 Official | 官方账号 | 2 | @ClaudeAI, @GoogleLabs |
| 🟢 Ecosystem | 生态/平台 | 7 | Garry Tan (YC), Dan Shipper (Every), Simon Willison |
| 🔵 Observer | 观察者 | 1 | Zara Zhang (follow-builders) |

覆盖产品线：Anthropic · OpenAI · Google · Replit · Vercel · Box · Notion · Roblox

---

## 目录结构 / Structure

```
builder-radar/
├── SKILL.md          # 工作流定义 / Workflow definition
├── builders.json     # 29 位 Builder 追踪库 / Builder tracking database
├── templates/
│   └── digest.md     # 日报模板 / Daily digest template
└── README.md
```

---

## 安装 / Install

```bash
# 通过 SkillHub
skillhub install builder-radar
```

---

## 输出示例 / Sample Output

日报包含：
- 🚨 今日速报（Breaking news）
- 🏆 Tier 1 必读（Composite ≥ 8.0）— 含三维打分
- 🥈 Tier 2 值得关注
- 🧭 Tier 3 可以看看
- 🔥 Heat Radar（热度地图）
- 🗑️ 已跳过（过滤记录）
- 🔍 Tracking Gaps（信息盲区）
- 📋 Next Radar（下次关注要点）

---

## 版本 / Version

**v3.2.0** — Source Link Priority 三级验证 + 3D 打分 + Heat Radar + 内容过滤器

---

*Made with ☕ by Elisedai · Published on [SkillHub](https://skillhub.cn)*
