---
slug: builder-radar
displayName: Builder Radar — AI Builder 前沿信息每日雷达
version: 3.2.0
summary: 每日追踪 29 位 AI 产品 Builder 的 shipping 动态，三维打分（实时性×重要程度×火爆程度），输出结构化日报。聚焦产品发布、技术深度文、大会演讲，自动过滤观点噪音。
license: MIT
name: builder-radar
description: AI builder frontier information tracker. Aggregates the latest from X posts, product blogs, and YouTube conference talks for core AI product builders. Designed for daily use — balances real-time freshness, importance, and community heat.
author: WorkBuddy
triggers:
  - "what's new in AI building"
  - "最近有什么值得看的"
  - "track builders"
  - "builder radar"
  - "追踪 AI 进展"
  - "run radar"
  - "今天有什么新东西"
  - "AI builder 动态"
---

# Builder Radar — AI builder 前沿信息每日雷达

## When to use

This skill treats information discovery as a **multi-source, multi-frequency problem**. Designed for **daily invocation**:
- Default: "run radar" / "今天有什么新东西" → full 7-step workflow
- Quick: "有什么火的内容" → heat-only scan across recent 48h
- Deep: "最近 XX 产品线有什么" → targeted deep-dive on a product line

## Core principle

> **Track what people SHIP, not what they THINK.**
>
> Product launches > demos > technical deep-dives > official blog posts > verified case studies > conference talks.
> Opinions, predictions, hot takes, commentary — skip them. They don't give you information you can act on.

## Source link priority (MANDATORY — checked BEFORE presenting)

Every item in the digest MUST include links. When collecting links, follow this priority order:

| Priority | Source type | What to link | Search method |
|----------|-------------|-------------|---------------|
| **🥇 1st** | YouTube video | `youtube.com/watch?v={id}` | If content was a talk/presentation, search "[title] [speaker] youtube". AIE / Config / buildergroop etc. talks MUST have this. |
| **🥈 2nd** | Author's blog | Direct blog URL | Search "[author name] blog [topic]" or `site:author-domain.com [keyword]`. Builder-written original posts are preferred over third-party recaps. |
| **🥉 3rd** | X/Twitter | `x.com/{user}/status/{id}` or `twitter.com/{user}/status/{id}` | Search "[author name] X [keyword]" or build from builder's known X handle. Especially critical for Thibault Sottiaux (X-only signals). |

**Rules:**
1. Always check all three before presenting. Don't stop at the first link you find.
2. If a talk has a blog version AND a YouTube video, include BOTH (blog format: `[原文](URL)`, video format: `[🎬](YOUTUBE_URL)`).
3. If NONE of the three can be found → the item is **unverified**. Demote it to Tier 3 or mark as "pending verification". Never put an unverified item in Tier 1.
4. For conference talks (AIE, Config, etc.): YouTube link is the hardest requirement. These talks exist on YouTube — if you can't find the link, search harder or mark the talk as "not yet uploaded".

## Three-dimensional scoring (v3.0)

Every item that passes the content filter is scored independently on **three axes**, each 0–10. This replaces the single composite formula from v2.0. The user sees all three scores and can decide what matters today.

### Dimension 1: 实时性 (Real-time Freshness)

How recently did this happen? Score based on time since first public appearance:

| 时间窗口 | 分数 | 说明 |
|----------|------|------|
| ≤24h | 10 | 刚发生，信息可能还在发酵 |
| 24–72h | 9 | 今天或昨天，社区还在讨论 |
| 3–7 天 | 8 | 本周内，仍有时间窗口采取行动 |
| 1–2 周 | 6 | 上周的事，基本已经消化 |
| 2–4 周 | 4 | 上个月，可能需要验证是否过时 |
| >1 月 | 2 | 需要重新验证适用性后才推荐 |

**Special rule for product launch adjacency:** If content is within 1 week of a related product launch, add +1 (cap at 10). Example: a blog post about Fable published 3 days after Fable's launch gets 8+1=9 even though it's 10 days old.

### Dimension 2: 重要程度 (Strategic Importance)

How impactful is this? What changes if you act on it vs. miss it?

| 事件类型 | 分数 | 例子 |
|----------|------|------|
| 产品架构重组 | 10 | Codex 并入 GPT，不再是独立 App |
| 重大功能发布 | 9 | GPT-5.6 三档模型全球开放 |
| 战略方向调整 | 8 | 80% 系统提示词砍掉，策略转向 |
| 重要 feature 发布 | 7 | Claude Code /checkup 命令上线 |
| 技术深度文 | 7 | Steinberger Loop Engineering 六大组件 |
| 生产案例（有数据） | 6 | Tesco 砍 94% token |
| 功能更新 | 5 | 用量限制调整、bug 修复 |
| 大会 talk | 5–7 | 取决于演讲人 tier |
| 生态信号 | 3 | VC 数据报告、landscape map |

**Cross-builder validation bonus:** If ≥2 product_builder tier sources independently discuss the same topic, +1 (cap at 10). This signals convergence.

### Dimension 3: 火爆程度 (Community Heat)

How much is the community buzzing? This is the **new** dimension in v3.0.

Heat signals to collect (additive, cap at 10):

| 信号 | 加分 | 如何获取 |
|------|------|----------|
| 被 ≥3 个 builder 独立引用/讨论 | +3 | 搜索结果中跨 source 出现 |
| 原帖 X 互动量 >1000 | +2 | WebSearch 或 WebFetch 提取 |
| YouTube 观看日均 >10K views | +2 | WebFetch 视频页提取 |
| HackerNews 首页或 >100 upvotes | +2 | WebSearch 补充搜索 |
| 多篇独立媒体报道同一事件 | +1 | 搜索结果数量判断 |
| 社区大量复现/二次创作 | +1 | 搜索结果中提到 reproductions |

**Note on heat signal collection:** WebSearch alone cannot extract exact X like counts. Use these proxies:
- Number of independent search results covering the same topic → proxies for media coverage
- Cross-reference signal: same topic appears under multiple builder searches → proxies for cross-builder mentions
- If available, WebFetch the original X post or blog to find engagement numbers in page metadata

**Heat baseline:** Start every item at 3 (it exists and passed content filter = baseline awareness). Add heat signals on top. Items with no heat signals beyond existence score 3–5 (worth knowing but not buzzing). Items scoring 8–10 mean "the entire builder community is talking about this right now."

### Composite Score

```
综合分 = 0.3 × 实时性 + 0.4 × 重要程度 + 0.3 × 火爆程度
```

Why these weights:
- **重要程度 0.4 (highest):** Because the whole point is filtering what MATTERS. A hot but trivial rumor (heat=9, importance=2) should not outrank a quiet but critical architecture change (heat=3, importance=10).
- **实时性 0.3:** For daily use this matters, but importance wins. A 2-week-old deep-dive is still more valuable than a fresh engagement bait post.
- **火爆程度 0.3:** Signals community validation but can be noisy. Kept equal to freshness to prevent hype-driven ranking.

## Content filter (mandatory, applied BEFORE scoring)

### IN — things we track
- Product launch announcements
- New feature / capability releases
- Technical deep-dives and architecture posts
- Live demos and demo recordings
- Official blog posts from product companies
- Shipping updates and changelogs
- Production case studies with verifiable data
- Conference talks with first-hand product content
- Podcast episodes featuring builder interviews (not commentary)

### OUT — things we skip
- Opinions / hot takes / predictions without product substance
- Commentary threads and engagement-bait
- Generic "the future of AI" think-pieces
- VC fundraise announcements (unless the product is AI-builder-facing)
- Job postings / hiring threads
- Drama / controversy threads
- Pure hype / clout posts

### Per-builder filtering

Each builder in `builders.json` has a `track_for` field specifying exactly what we care about. Never stray from it.

## Builder tracking database

Load `@builders.json` at the start of every session. It contains 29 builders across Anthropic, OpenAI, Google, Replit, Vercel, Box, Notion, and ecosystem. The full list originates from 张咋啦's `follow-builders` repository (github.com/zarazhangrui/follow-builders).

## Workflow

### Step 0: Load database and set temporal context

Read `builders.json`. Note today's date and calculate temporal windows:
- "≤24h" starts at: today - 1 day
- "3-7d window" starts at: today - 7 days
- "same-quarter" window starts at: start of current quarter

Also note any recent (`≤2 weeks`) major product launches that should trigger the +1 freshness bonus in Step 5.

### Step 1: Search for builder shipping signals

Run **parallel** WebSearch queries for all `product_builder` tier builders first, then `official`, then `ecosystem`.

Each search uses the builder's `search_keywords_en[0]` from `builders.json`. Add time qualifiers: "July 2026" or "latest".

**CRITICAL — capture source URLs:**
For every search result that appears promising, record the **direct URL** of the original source (not aggregator/recap pages):
- X posts → save the tweet URL (e.g., `https://x.com/{user}/status/{id}`)
- Blog posts → save the blog URL (e.g., `https://geoffreylitt.com/2026/07/02/...`)
- YouTube talks → save the full `https://youtube.com/watch?v={id}` URL
- Official announcements → save the product blog URL

These URLs MUST appear in the final digest report. No URL → treat the item as unverified and demote it.

**Search priority order:**
1. Tier-1 product_builder: Boris Cherny, Thariq Shihipar, Thibault Sottiaux, Peter Steinberger, Amjad Masad, Guillermo Rauch
2. Other product_builder (Anthropic, OpenAI, Google, Replit, Vercel, Box, Notion, Roblox)
3. Official accounts
4. Ecosystem / observer

### Step 2: Collect heat signals (NEW in v3.0)

For each item that passed the content filter, run **supplementary heat searches**:

```
"{{item_keyword}} trending 2026"
"{{item_keyword}} HackerNews"
"{{item_keyword}} community reaction"
```

Goal: estimate how many people are talking about this, not just that it happened.

**Heat proxies to extract from search results:**
- Number of independent sources (snippets from different domains covering same event)
- Any engagement numbers visible in snippets
- Cross-builder appearance (same topic under multiple builder searches)

Record these for Step 5 scoring.

### Step 3: Search for new conference talk uploads

Run parallel WebSearch queries for each conference channel in `builders.json`. Focus on talks uploaded in the last 2 weeks.

**CRITICAL — extract YouTube URLs:**
For every talk found, extract the direct YouTube video URL (`youtube.com/watch?v={id}`). These are REQUIRED for Tier 3 entries — without them the user can't actually watch the talk. If a talk is mentioned but no YouTube URL can be found, note it as a "pending verification" item rather than a confirmed Tier 3 entry.

### Step 4: Apply content filter

For EVERY result: check against global IN/OUT rules AND builder-specific `track_for`. Be strict.

### Step 5: Score all passed items on 3 dimensions

For each surviving item, assign three scores following the rubrics above:

1. **实时性**: time-window lookup from the table
2. **重要程度**: event-type lookup + cross-builder bonus if applicable
3. **火爆程度**: baseline 3 + heat signal accumulation

Then compute composite: `0.3×实时性 + 0.4×重要程度 + 0.3×火爆程度`

Sort by composite descending. For ties, prefer 重要程度.

### Step 6: Generate the digest report

Use `templates/digest.md` as the output structure. Write to:

```
{WORKSPACE}/Builder_Radar_{YYYY-MM-DD}.md
```

**Report structure (updated for v3.0):**

1. **Executive Summary / 概要** — 2-3 sentences: the single most impactful shipping signal + 3D summary
2. **Tier 1: Must Read / 必读** — composite ≥7.0. Top 3 items. Each with 3D score bars.
3. **Tier 2: Worth Knowing / 值得关注** — composite 4.0–6.9. Other shipping signals.
4. **Tier 3: New Talks / 新 Talk** — YouTube talks ready for `youtube-learning`.
5. **Heat Radar / 热度雷达** — items with 火爆程度 ≥8 but 重要程度 <7. "Hype check": tell user this is buzzing but may not be actionable.
6. **Skipped / 过滤记录** — items filtered out, to prove we scanned broadly.
7. **Tracking Gaps / 信息盲区** — product lines with zero signal.
8. **Next Steps / 下一步** — concrete actions.

### Step 7: Present the digest

Use `present_files` to show the digest. Highlight the top item's 3 scores.

Always end with: "Any of these talks you want me to process with `youtube-learning`?"

## Signal freshness convention

| Label | Meaning |
|-------|---------|
| **≤24h** | Today/yesterday — highest urgency |
| **this-week** | Within 7 days — still developing |
| **recent** | 1-2 weeks — digested but actionable |
| **stale** | >2 weeks — verify before acting |

## Pitfalls

- **Missing source links**: Every Tier 1/2/3 item MUST include a direct URL to the original source. Blog → blog URL. X post → tweet URL. Talk → YouTube URL. This is the #1 user complaint — if they can't click through to read/watch, the radar is worthless.
- **Opinion pollution**: Content filter (Step 4) is mandatory. No exceptions.
- **YouTube upload lag**: Conference talks lag 1–3 weeks after event. "No new talks" ≠ no talks exist.
- **Heat inflation**: A popular opinion thread (high heat) must still pass the content filter (low importance, likely opinion). Do NOT let high heat bypass content filter.
- **Thibault blindness**: Thibault Sottiaux's most important signals are often X-only. WebSearch picks these up indirectly with 12-24h lag. When Codex line shows zero signal, note it as a manual X-check in Tracking Gaps.
- **Product-line blindness**: After each digest, scan for new product names in results and consider adding to `builders.json`.

## Verification checklist

After generating the digest:
1. **Links check (MANDATORY)**: For EVERY Tier 1/2 item, verify in this order: (1) YouTube link if it's a talk, (2) author's blog link, (3) X/Twitter link. At least one must be provided. Conference talks MUST have YouTube URL. Tier 3 table MUST have YouTube Link for every row. No URL → fix or demote before presenting.
2. **Content filter**: Every Tier 1 item passed the IN/OUT gate? Remove any opinions.
3. **3D scores**: Are all three scores justified with evidence (not gut feel)?
4. **Heat Radar**: Any high-heat/low-importance items flagged for "hype check"?
5. **Coverage**: Every major product line got at least one search hit?
6. **Next Steps**: Concrete, executable items?

## Builder list maintenance

When a new significant builder emerges or an existing one changes role:
1. Read `builders.json`
2. Add/update following the existing schema
3. Set tier, track_for, content_types, search keywords
4. Update `last_updated`
