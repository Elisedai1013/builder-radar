# 🔭 Builder Radar

> 追踪 AI Builder 真正发布或验证了什么，并把一手原文读成可行动的深度日报。
> Track what AI builders ship or prove, then explain what builders can learn.

[![Version](https://img.shields.io/badge/version-3.5.0-blue)](https://github.com/Elisedai1013/builder-radar)
[![License](https://img.shields.io/badge/license-MIT-green)](./LICENSE)
[![Builders](https://img.shields.io/badge/builders-31-orange)](./builders.json)

## 这是什么？ / What is this?

AI Builder 圈每天都有大量 X 帖、博客、论文、Release 和视频。真正困难的不是“找到链接”，而是判断哪些内容值得读、读懂原文的证据链，并把同一事件在 X、YouTube、官方博客、论文和 GitHub 上的材料合并起来。

Builder Radar 会：

- 扫描过去 24 小时的产品发布与 shipping 信号；
- 扫描滚动 7 天的第一方研究、工程博客、论文和 Builder 实战复盘；
- 打开并精读入选原文，而不是根据搜索摘要写结论；
- 关联 X ↔ YouTube ↔ 第一方博客/论文/GitHub；
- 用实时性、重要程度、社区热度三维评分；
- 输出包含技术机制、实验数据、Builder 启示和直接来源的中文深度日报。

核心原则：

> **Track what people SHIP or PROVE, not what they merely THINK.**

产品发布、真实 Demo、研究与工程深潜、Builder 实验、数据化生产案例和一手 Talk 优先；泛观点、预测、争议、recap 和纯 hype 会被过滤。

## v3.5：Builder 资格门槛与自然热度

`AI 内容创作者` 不再自动等同于 `AI Builder`。进入 Tier 1 的来源必须属于以下一种：

- 直接构建或负责相关产品、模型、研究系统的 Core Builder；
- 在真实组织中运行该产品并给出指标、失败或流程证据的 Production Operator；
- 亲自完成相关训练、评估、安全或技术机制的 First-party Researcher；
- 对上述 Builder 进行实质访谈，并获取具体机制与运营细节的 Builder Interviewer。

只有粉丝量、工具讲解或初学者教程，没有原创构建、实验或生产证据的教育型创作者会被跳过或降级。内容还必须直接命中所研究的能力；例如泛 Codex 教程不能仅凭提到 GitHub 就充当 PR Review 深度来源。

热度也拆成两部分：

- **Observed reach**：公开播放或曝光数字；
- **Organic heat**：点赞、评论、近期频道基线、跨 Builder 引用、社区复现和独立讨论共同支持的自然热度。

品牌短视频出现高播放、低互动，或多个统计源差异很大时，会标记为疑似付费/嵌入分发，不直接获得 YouTube 热度加分。

## v3.4：Daily Deep

`Daily Deep` 是推荐默认模式。它解决了“日报很及时，但像链接目录；评分字段很多，真正的原文洞察太少”的问题。

一轮标准执行会：

1. 对照最近 7 份日报去重；
2. 完成 24h shipping 扫描与滚动 7 天一手深度扫描；
3. 在搜索条件允许时先建立至少 15 条候选池；
4. 精选 5–8 条，并尽量覆盖至少 4 个 Builder/组织；
5. 为重要条目提取 3–5 个可核验事实、数字、实验或技术机制；
6. 把评分和跨平台状态压缩呈现，把篇幅留给证据与 Builder 决策。

不足 5 条时宁缺毋滥。没有有效直链、准确日期或事实无法核验的内容不能进入正式推荐。

## 四种运行模式 / Modes

| 模式 | 适合场景 | 默认窗口 |
|------|----------|----------|
| **Daily Deep** | 每日深度雷达，推荐默认 | 24h shipping + 7d deep |
| **Quick Heat** | 快速查看社区正在热议什么 | 48h |
| **Product Deep Dive** | 深挖 Codex、Claude Code、Replit Agent 等产品线 | 14d |
| **Talk Discovery** | 找最新大会演讲并准备后续视频学习 | 14d uploads |

## 最佳使用实践 / Best Practices

### 推荐：每日自动任务

任务 Prompt 不需要复制整套规则，只需明确模式、输出位置和交付要求：

```text
执行 builder-radar 的 Daily Deep 模式。读取最近 7 份日报去重，完成 24 小时 shipping 扫描和滚动 7 天一手深度扫描，将今天的完整日报保存到 {OUTPUT_DIR}/Builder_Radar_{YYYY-MM-DD}.md，并交付文件与最重要的 3 个发现。
```

推荐频率：每天一次。深度内容使用滚动 7 天窗口并与历史日报去重，因此不需要再创建一条内容重复的“周报任务”。

### 临时检查社区热度

```text
执行 builder-radar 的 Quick Heat 模式，检查过去 48 小时最热但可能被高估的 Builder 信号，并给出原始来源。
```

### 深挖一个产品线

```text
执行 builder-radar 的 Product Deep Dive 模式，深挖最近 14 天的 Codex，关联 X、YouTube、官方博客、GitHub 和论文，输出已核验的技术与产品变化。
```

### 使用建议

- 把 Daily Deep 的输出放在固定目录，让下一次执行可以读取最近日报并去重。
- 给 Product Deep Dive 明确产品线，不要同时塞入多个宽泛主题。
- Talk Discovery 只接受直接 YouTube `watch` 链接；播放列表或二手 recap 不能替代视频。
- 第三方媒体可用于发现线索和验证热度，但最终结论必须锚定第一方材料。
- 如果某天没有足够的高价值内容，接受短日报，不要要求 Agent 为了数量补齐。

## 内容质量标准 / Editorial Quality Bar

每条重要内容必须回答：

1. 谁在什么准确日期发布了什么？
2. 核心结论是什么？
3. 有哪些具体机制、实验、数字或设计决策支持它？
4. 为什么会改变 AI Builder 的判断？
5. 接下来可以采取什么行动？
6. 原始来源在哪里，其他平台是否有同事件材料？

搜索摘要只能用来发现候选，不能支撑最终分析。

## 三维评分 / Scoring

| 维度 | 权重 | 衡量什么？ |
|------|------|-----------|
| **实时性** Freshness | 0.3 | 多久前发生？≤24h = 10，>1 月 = 2 |
| **重要程度** Importance | 0.4 | 对产品、架构或 Builder 决策的影响 |
| **火爆程度** Community Heat | 0.3 | 跨 Builder 引用、X/YouTube/HN 和社区复现 |

```text
综合分 = 0.3 × 实时性 + 0.4 × 重要程度 + 0.3 × 火爆程度
```

火爆程度 ≥8、重要程度 <7 的内容会进入 `Heat Radar`，提醒读者它很热，但未必可行动。

播放量不能单独决定火爆程度。频道粉丝数只作背景信息，优先使用近期同类视频中位播放、播放/粉丝比、实质评论、跨平台讨论和社区复现来判断自然热度。

## 跨平台关联 / Cross-platform Correlation

- X 发现发布、Demo 或技术线索后，继续搜索同事件的 YouTube 与第一方文章。
- YouTube 发现重要 Talk 后，反查演讲者 X、官方博客、论文、讲稿、幻灯片或产品页。
- 同一事件合并成一个来源包，不按平台重复收录。
- 未找到匹配内容时只标记“尚未找到/可能尚未上传”，不把无结果误判为不存在。
- 第一方原文、论文、Release 或代码是证据锚点；Talk 必须有直接 YouTube URL。

## 覆盖范围 / Coverage

当前追踪 **35 位 Builder / Production Operator**：

| Tier | 数量 | 代表 Builder |
|------|------|-------------|
| Product Builder | 24 | Boris Cherny, Thibault Sottiaux, Ryan Lopopolo, Maja Trebacz, Romain Huet, Simon Willison |
| Production Operator | 1 | Austin Ray |
| Official | 2 | Claude, Google Labs |
| Ecosystem | 7 | Swyx, Dan Shipper, Garry Tan, Matt Turck |
| Observer | 1 | Andrej Karpathy |

同时扫描 Anthropic Research/Engineering、OpenAI、Google、Replit、Vercel、Every、Simon Willison 和 Armin Ronacher 等第一方来源，以及 AI Engineer、Anthropic、OpenAI、Google DeepMind、Figma 等视频频道。

数据源维护在 [`builders.json`](./builders.json)，核心列表源自 [follow-builders](https://github.com/zarazhangrui/follow-builders)，并补充高信号独立技术 Builder。

## 输出结构 / Output

1. Executive Summary / 概要
2. Coverage Note / 扫描说明
3. Tier 1 / 本周深度必读
4. Tier 2 / 值得关注
5. Tier 3 / 新 Talk
6. Heat Radar / 热度雷达
7. Skipped / 过滤记录
8. Tracking Gaps / 信息盲区
9. Next Steps / 下一步

日报模板见 [`templates/digest.md`](./templates/digest.md)。

## 安装 / Install

```bash
git clone https://github.com/Elisedai1013/builder-radar.git
```

目录结构：

```text
builder-radar/
├── SKILL.md
├── builders.json
├── templates/
│   └── digest.md
├── README.md
└── LICENSE
```

## 版本 / Version

**v3.5.0 — Builder qualification + organic heat normalization**

| 版本 | 关键变更 |
|------|---------|
| v3.5.0 | 新增 Builder 资格门槛；区分教育型创作者与一线 Builder/研究员/生产运营者；拆分 observed reach 与 organic heat；识别疑似付费播放；新增 Ryan Lopopolo、Maja Trebacz、Romain Huet、Austin Ray |
| v3.4.0 | Daily Deep 默认模式；原文精读；候选池、去重与来源多样性；深度内容卡；新增 Simon Willison、Armin Ronacher；最佳调用实践 |
| v3.3.0 | X、YouTube、官方博客双向关联检索；同一事件合并并记录缺失平台状态 |
| v3.2.0 | 三级来源链接验证，链接缺失自动降级 |
| v3.0.0 | 三维评分与 Heat Radar |
| v2.0.0 | 内容过滤器与 Builder 追踪库 |
| v1.0.0 | 初始版本 |

## License

MIT

---

*Made with ☕ by [Elisedai](https://github.com/Elisedai1013)*
