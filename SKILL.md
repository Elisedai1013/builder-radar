---
name: builder-radar
description: Daily and deep AI builder frontier tracker that scans recent shipping plus first-party research, engineering blogs, papers, builder long-form posts, GitHub releases, X posts, and YouTube talks; correlates matching sources, filters noise, scores freshness, importance, and heat, and produces a source-verified Chinese digest. Use for builder radar, AI builder daily reports, deep AI builder reading, recent launches and demos, conference-talk discovery, or tracking a specific AI product line.
---

# Builder Radar — AI builder 前沿信息每日雷达

## Operating modes

Treat discovery as a **multi-source, multi-frequency problem**. Select one mode before searching:

- **Daily Deep (recommended default):** scan shipping from the last 24 hours, then scan first-party deep content from the rolling 7 days. Extend to 14 days only for unusually valuable, still-actionable material.
- **Quick Heat:** scan the last 48 hours for high-heat signals and label hype risk. Do not produce a full deep digest.
- **Product Deep Dive:** focus on one product line, use a 14-day default window, and reconstruct its release, technical, and community evidence.
- **Talk Discovery:** focus on newly uploaded talks and return direct YouTube links plus matching X and first-party materials.

## Core principle

> **Track what people SHIP or PROVE, then explain what builders can learn.**
>
> Product launches > demos > research and engineering deep-dives > builder-written experiments > verified case studies > conference talks.
> Opinions, predictions, hot takes, commentary — skip them. They don't give you information you can act on.

## Builder qualification gate (MANDATORY — applied before source scoring)

Do not equate "AI content creator" with "AI builder." Before an item enters the candidate pool, classify the source and verify that the speaker or author has direct proximity to the work.

| Qualification | Evidence required | Editorial treatment |
|---|---|---|
| **Core builder** | Builds or leads the product, model, research system, or agent infrastructure being discussed | Eligible for Tier 1 |
| **Production operator** | Runs the product in a real organization and provides workflow details, measurements, failures, or adoption evidence | Eligible for Tier 1 |
| **First-party researcher** | Authored the research, evaluation, training method, safety system, or technical mechanism | Eligible for Tier 1 |
| **Builder interviewer** | Interviews qualified builders and elicits concrete mechanisms or operating details | Eligible when the named guests and their claims are verified |
| **Educator / commentator** | Explains tools but did not build, research, or operate the system and provides no original experiment | Normally skip or demote to Tier 3 |

Apply all of these checks:

1. **Identity:** verify the person's current role from a first-party profile, employer page, paper, repository, or event bio.
2. **Proximity:** require direct involvement in the product or a documented production deployment. A large audience alone is not evidence.
3. **Artifact:** require at least one shipped product, code/release, paper, reproducible experiment, production case study, or substantive first-party demo.
4. **Topic match:** the artifact must directly address the requested capability. A broad Codex tutorial does not qualify as a deep source about pull-request review merely because it mentions GitHub.
5. **Substance:** prefer mechanisms, numbers, failures, tradeoffs, and implementation decisions. Treat beginner walkthroughs and generic tool tours as discovery material only.

Only core builders, production operators, first-party researchers, or verified builder interviews may enter Tier 1. Record `educator-only`, `role unverified`, or `topic mismatch` explicitly in Skipped when a popular source fails this gate.

## Source link priority (MANDATORY — checked BEFORE presenting)

Every item in the digest MUST include links. When collecting links, follow this priority order:

| Priority | Source type | What to link | Search method |
|----------|-------------|-------------|---------------|
| **🥇 1st** | First-party primary artifact | Direct builder blog, research paper, product/engineering post, GitHub release, code, or changelog URL | Search the author/company domain and open the canonical artifact. This is the evidence anchor. |
| **🥈 2nd** | YouTube video | `youtube.com/watch?v={id}` | If content was a talk/presentation, search "[title] [speaker] youtube". AIE / Config / buildergroop etc. talks MUST have this. |
| **🥉 3rd** | X/Twitter | `x.com/{user}/status/{id}` or `twitter.com/{user}/status/{id}` | Search "[author name] X [keyword]" or build from builder's known X handle. Especially critical for Thibault Sottiaux (X-only signals). |

**Rules:**
1. Always check all three before presenting. Don't stop at the first link you find.
2. If a talk has a blog version AND a YouTube video, include BOTH (blog format: `[原文](URL)`, video format: `[🎬](YOUTUBE_URL)`).
3. If NONE of the three can be found → the item is **unverified**. Demote it to Tier 3 or mark as "pending verification". Never put an unverified item in Tier 1.
4. For conference talks (AIE, Config, etc.): YouTube link is the hardest requirement. These talks exist on YouTube — if you can't find the link, search harder or mark the talk as "not yet uploaded".

### Cross-platform correlation (MANDATORY)

Treat X, YouTube, and first-party blogs as connected evidence for the **same event**, not as three independent feeds.

For every promising X signal:
1. Extract the builder name, product, feature/event phrase, and any talk or demo title.
2. Search YouTube with at least two query variants, such as `"{builder} {product} {feature}"` and `"{event/title} {builder}"`.
3. Search the builder's blog and company newsroom/changelog for the same event.
4. Attach all verified matching URLs to one digest item. Do not create duplicate items per platform.
5. If no matching YouTube video is found, write **"No matching YouTube video found; it may not be uploaded yet"** in the source bundle. Absence of a search result is not proof that no video exists.

Apply the same process in reverse for every promising YouTube talk: search for the speaker's X announcement and a first-party blog, slides, transcript, or product page. Use title, speaker, event, product, and distinctive feature terms rather than a single exact-title query.

Reject false matches: a video must describe the same release, demo, talk, or technical topic—not merely mention the same builder or product.

## Editorial quality bar (MANDATORY)

The digest must read like a concise research brief, not a link directory or a filled template.

1. Open and read the original source for every selected item. Search snippets can discover candidates but cannot support the final analysis.
2. Record an exact publication date and at least one direct first-party URL. Do not use vague dates such as "recently". If the date or source cannot be verified, omit or demote the item.
3. Extract **3–5 verifiable facts, numbers, experiments, design decisions, or technical mechanisms** from each Tier 1 item. Use fewer only when the original artifact is inherently short, such as a changelog entry.
4. Explain the core claim, evidence chain, why it matters, and one concrete builder action. Do not paraphrase the headline repeatedly.
5. Use third-party reports only to discover primary sources or measure heat. Never let a recap replace the builder's post, paper, code, talk, or official engineering article.
6. Present the same event once. Merge its X, blog, paper, GitHub, and YouTube evidence into one item; do not repeat the full analysis in both a Tier section and the Talk table.
7. Keep scores and correlation status compact so evidence and mechanisms receive most of the space.

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

### Organic heat vs paid reach (MANDATORY)

Treat raw reach and organic community heat as different signals. Before awarding YouTube or social heat points:

1. Compare views with likes, comments, age, duration, channel subscribers, and the median of the channel's recent comparable uploads.
2. Flag likely paid or embedded distribution when a short brand video has very high views but unusually low likes/comments, when independent trackers disagree sharply, or when there is little matching community discussion.
3. Label the number as **observed reach** when paid distribution cannot be ruled out. Do not award the `YouTube >10K views/day` bonus from observed reach alone.
4. Use followers only as context. Prefer recent median views, view-to-follower ratio, substantive comments, independent references, and reproductions.
5. A high-reach marketing clip may support awareness, but it needs a detailed article, talk, case study, or technical artifact before it can support Tier 1 analysis.

When evidence is mixed, report both: `observed reach: high` and `organic heat: unverified/medium/low`.

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
- First-party research papers with concrete findings, code, or evaluations
- Technical deep-dives and architecture posts
- Builder-written experiments and implementation reports
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

Each builder in `builders.json` has a `track_for` field specifying what to prioritize. An unlisted builder may enter only when they publish a direct, high-value first-party artifact that passes the same filter; record them as a database-maintenance candidate.

Passing the content-type filter does not bypass the Builder qualification gate. An educator-led tutorial about an included topic is still excluded unless it contains an original build, experiment, or qualified first-party interview.

## Builder tracking database

Load `@builders.json` at the start of every session. It contains core builders and first-party source lists across Anthropic, OpenAI, Google, Replit, Vercel, Box, Notion, and the independent builder ecosystem. The list originates from 张咋啦's `follow-builders` repository and is extended with high-signal independent technical builders.

## Workflow

### Step 0: Load database and set temporal context

Read `builders.json`. Note today's date and calculate temporal windows:
- "≤24h" starts at: today - 1 day
- "3-7d window" starts at: today - 7 days
- "same-quarter" window starts at: start of current quarter

Also note any recent (`≤2 weeks`) major product launches that should trigger the +1 freshness bonus in Step 5.

For Daily Deep mode, inspect up to the 7 most recent `Builder_Radar_*.md` reports in the output directory. Build a deduplication list of previously covered events. Re-include an event only when a material new artifact, result, release, or metric appeared; state the delta.

### Step 1: Build the candidate pool

Run **parallel** WebSearch queries for all `product_builder` tier builders first, then `official`, then `ecosystem`.

Start with the builder's `search_keywords_en` entries from `builders.json`; use at least two query variants for priority builders or whenever the first query is inconclusive. Add the current month/year or `latest` rather than a hard-coded date.

In Daily Deep mode, run both passes:

1. **24-hour shipping pass:** launches, releases, demos, changelogs, and concrete product changes.
2. **Rolling 7-day deep pass:** scan `product_blog_sources` plus builder blogs for research, engineering articles, papers, implementation reports, and data-backed case studies.

When source volume permits, collect at least 15 candidates before ranking. Candidate count includes later-filtered items; never fabricate or pad the final digest to hit a quota.

**CRITICAL — capture source URLs:**
For every search result that appears promising, record the **direct URL** of the original source (not aggregator/recap pages):
- X posts → save the tweet URL (e.g., `https://x.com/{user}/status/{id}`)
- Blog posts → save the blog URL (e.g., `https://geoffreylitt.com/2026/07/02/...`)
- YouTube talks → save the full `https://youtube.com/watch?v={id}` URL
- Official announcements → save the product blog URL

These URLs MUST appear in the final digest report. No URL → treat the item as unverified and demote it.

**MANDATORY — correlate every X signal before scoring:**
For each promising X result, immediately run the cross-platform correlation workflow above. Record the YouTube queries attempted, the matching direct video URL when found, the first-party blog URL when found, and an explicit not-yet-found note otherwise. Complete this before heat scoring so YouTube views and cross-platform coverage can contribute to the heat evidence.

**Search priority order:**
1. Tier-1 product_builder: Boris Cherny, Thariq Shihipar, Thibault Sottiaux, Peter Steinberger, Amjad Masad, Guillermo Rauch
2. First-party `product_blog_sources`, especially research and engineering blogs
3. Other product_builder (Anthropic, OpenAI, Google, Replit, Vercel, Box, Notion, Roblox, independent technical builders)
4. Official accounts
5. Ecosystem / observer

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

For every discovered talk, run the reverse cross-platform correlation workflow: search the speaker's X account and first-party sites for the matching announcement, slides, transcript, demo, or product release. Merge the results into a single source bundle.

### Step 4: Apply content filter and deduplicate

For EVERY result: check against global IN/OUT rules and builder-specific `track_for`. Be strict. Merge same-event sources, remove previously covered items without a material delta, and preserve a short skipped list to prove coverage.

Before scoring, record each surviving item's qualification (`core builder`, `production operator`, `first-party researcher`, or `builder interviewer`) and its heat provenance (`organic`, `paid/embedded suspected`, or `unknown`).

### Step 5: Score all passed items on 3 dimensions

For each surviving item, assign three scores following the rubrics above:

1. **实时性**: time-window lookup from the table
2. **重要程度**: event-type lookup + cross-builder bonus if applicable
3. **火爆程度**: baseline 3 + heat signal accumulation

Then compute composite: `0.3×实时性 + 0.4×重要程度 + 0.3×火爆程度`

Sort by composite descending. For ties, prefer 重要程度.

### Step 6: Select and deeply read the final items

In Daily Deep mode, select 5–8 items when enough qualifying material exists; otherwise return fewer. Aim to cover at least 4 builders or organizations, and normally cap one organization at 2 items unless multiple developments are independently indispensable.

Open every selected first-party source and extract:

- the one-sentence core claim;
- what was shipped, tested, or discovered;
- 3–5 concrete facts, numbers, experiments, or mechanisms for substantive Tier 1 items;
- why the evidence changes a builder decision;
- one actionable takeaway;
- the verified source bundle and compact cross-platform status;
- the source qualification and whether heat is organic, observed reach, or uncertain.

### Step 7: Generate the digest report

Use `templates/digest.md` as the output structure. Write to:

```
{WORKSPACE}/Builder_Radar_{YYYY-MM-DD}.md
```

**Report structure (updated for v3.4):**

1. **Executive Summary / 概要** — 2–3 sentences: the most important signal plus the two supporting themes.
2. **Coverage Note / 扫描说明** — window, candidate count, first-party pages read, organization coverage, and dedup count.
3. **Tier 1: Must Read / 本周深度必读** — composite ≥7.0, normally top 3. Give the full evidence-and-mechanism treatment; show scores on one compact line.
4. **Tier 2: Worth Knowing / 值得关注** — composite 4.0–6.9. Use concise analysis cards, not a dense link table.
5. **Tier 3: New Talks / 新 Talk** — YouTube talks ready for `youtube-learning`; reference rather than repeat a talk already analyzed above.
6. **Heat Radar / 热度雷达** — items with 火爆程度 ≥8 but 重要程度 <7. "Hype check": tell user this is buzzing but may not be actionable.
7. **Skipped / 过滤记录** — items filtered out, to prove we scanned broadly.
8. **Tracking Gaps / 信息盲区** — product lines with zero signal.
9. **Next Steps / 下一步** — concrete actions.

### Step 8: Present the digest

Use `present_files` to show the digest. Highlight the top item's 3 scores.

Always end with: "Any of these talks you want me to process with `youtube-learning`?"

## Best-practice invocations

Use the shortest prompt that selects the mode, output location, and any special focus. Do not copy the whole workflow into the task prompt; this Skill owns the workflow and quality bar.

**Recommended daily automation:**

```text
执行 builder-radar 的 Daily Deep 模式。读取最近 7 份日报去重，完成 24 小时 shipping 扫描和滚动 7 天一手深度扫描，将今天的完整日报保存到 {OUTPUT_DIR}/Builder_Radar_{YYYY-MM-DD}.md，并交付文件与最重要的 3 个发现。
```

**Fast heat check:**

```text
执行 builder-radar 的 Quick Heat 模式，检查过去 48 小时最热但可能被高估的 Builder 信号，并给出原始来源。
```

**Product-line deep dive:**

```text
执行 builder-radar 的 Product Deep Dive 模式，深挖最近 14 天的 {PRODUCT_LINE}，关联 X、YouTube、官方博客、GitHub 和论文，输出已核验的技术与产品变化。
```

## Signal freshness convention

| Label | Meaning |
|-------|---------|
| **≤24h** | Today/yesterday — highest urgency |
| **this-week** | Within 7 days — still developing |
| **recent** | 1-2 weeks — digested but actionable |
| **stale** | >2 weeks — verify before acting |

## Pitfalls

- **Missing source links**: Every Tier 1/2/3 item MUST include a direct URL to the original source. Blog → blog URL. X post → tweet URL. Talk → YouTube URL. This is the #1 user complaint — if they can't click through to read/watch, the radar is worthless.
- **Snippet-only summaries**: Never write the final item from search-result snippets. Open and read the primary artifact.
- **Template dominance**: Scores, labels, and source-status text must not outweigh the evidence and builder insight.
- **Organization monoculture**: A broad daily digest should not become one company's changelog. Enforce diversity unless the news cycle genuinely warrants an exception.
- **Duplicate events**: Do not analyze a talk in Tier 1 and repeat the same analysis in Tier 3. Reference it once.
- **Siloed source scanning**: Never report an X signal before checking YouTube and first-party sites for the same event, and never report a YouTube talk before checking X and first-party sites. Merge matching evidence into one item.
- **Opinion pollution**: Content filter (Step 4) is mandatory. No exceptions.
- **YouTube upload lag**: Conference talks lag 1–3 weeks after event. "No new talks" ≠ no talks exist.
- **Heat inflation**: A popular opinion thread (high heat) must still pass the content filter (low importance, likely opinion). Do NOT let high heat bypass content filter.
- **Creator substitution**: Do not replace product builders, first-party researchers, or production operators with educators who merely explain the same feature. Audience size is not builder qualification.
- **Paid-view inflation**: Do not convert high brand-video views directly into community heat when likes, comments, cross-platform discussion, or recent-channel baselines do not corroborate them.
- **Thibault blindness**: Thibault Sottiaux's most important signals are often X-only. WebSearch picks these up indirectly with 12-24h lag. When Codex line shows zero signal, note it as a manual X-check in Tracking Gaps.
- **Product-line blindness**: After each digest, scan for new product names in results and consider adding to `builders.json`.

## Verification checklist

After generating the digest:
1. **Links check (MANDATORY)**: For EVERY Tier 1/2 item, verify in this order: (1) YouTube link if it's a talk, (2) author's blog link, (3) X/Twitter link. At least one must be provided. Conference talks MUST have YouTube URL. Tier 3 table MUST have YouTube Link for every row. No URL → fix or demote before presenting.
2. **Original-source check**: Was every selected primary artifact opened and read? Are dates, claims, and numbers traceable to it rather than a snippet or recap?
3. **Depth check**: Does every substantive Tier 1 item contain 3–5 concrete facts, experiments, or mechanisms plus an actionable builder takeaway?
4. **Correlation check (MANDATORY)**: For every X-derived item, is the YouTube search result recorded as a matching URL or an explicit not-yet-found note? For every YouTube-derived item, were matching X and first-party sources checked? Are cross-platform matches merged instead of duplicated?
5. **Dedup and diversity check**: Were recent reports checked? Is each event presented once? Does the selection avoid unnecessary single-company concentration?
6. **Content filter**: Every Tier 1 item passed the IN/OUT gate? Remove opinions and unverifiable claims.
7. **3D scores**: Are all three scores justified with evidence (not gut feel)?
8. **Heat Radar**: Any high-heat/low-importance items flagged for "hype check"?
9. **Coverage**: Every major product line got at least one search hit or a documented gap?
10. **Next Steps**: Concrete, executable items?
11. **Builder qualification**: Is every Tier 1 source a verified core builder, production operator, first-party researcher, or substantive builder interview?
12. **Organic heat**: Were paid/embedded reach anomalies separated from organic discussion and engagement?

## Builder list maintenance

When a new significant builder emerges or an existing one changes role:
1. Read `builders.json`
2. Add/update following the existing schema
3. Set tier, track_for, content_types, search keywords
4. Update `last_updated`
