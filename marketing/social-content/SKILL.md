# Social Content Skill

## Overview

This skill guides creation of platform-optimized social media content that drives engagement, brand awareness, and measurable outcomes. It integrates with launch-strategy (upstream) and analytics-tracking (downstream) to ensure content is strategically placed and performance-measured.

**Scope:** Content creation for LinkedIn, Twitter/X, TikTok, Instagram, and emerging platforms; calendar planning; performance benchmarking.

**NOT in scope:** Paid advertising strategy (see paid-ads skill), email sequences (see email-sequence skill), long-form content (see content-strategy skill).

---

## Context Sync Protocol

Before creating any social content, establish baseline context by reading `.claude/product-marketing-context.md`:

```typescript
// Pseudo-implementation
const contextFile = '.claude/product-marketing-context.md'
const context = readFile(contextFile)

// Extract these required fields:
const {
  productName,          // e.g., "SwiftHyre"
  keyPainPoints,        // [pain1, pain2, pain3]
  targetAudience,       // Primary: Audience, Secondary: Audience
  brandVoice,           // e.g., "Professional yet approachable"
  currentPhase,         // e.g., "Beta launch", "Growth", "Maturity"
  companyValues,        // [value1, value2, value3]
  competitivePosition,  // e.g., "Discovery-first vs recruiter-first"
  coreMetrics,          // [metric1, metric2, metric3]
} = parseContext(context)
```

If `.claude/product-marketing-context.md` does not exist, create a placeholder:

```markdown
# Product Marketing Context

## Product Name
[Name]

## Target Audience
- Primary: [Persona]
- Secondary: [Persona]

## Brand Voice
[Tone, personality, keywords]

## Key Pain Points (in rank order)
1. [Pain point 1]
2. [Pain point 2]
3. [Pain point 3]

## Current Phase
[Awareness / Consideration / Conversion / Retention]

## Competitive Position
[How we differentiate]

## Core Success Metrics
- [Metric 1]: [Target]
- [Metric 2]: [Target]
```

---

## Decision Tree: Platform Prioritization

Use this tree to allocate effort across platforms based on product stage and audience:

```
START: What is the current product phase?

├─ AWARENESS (Pre-launch / Beta)
│  ├─ Primary: Twitter/X + LinkedIn
│  │   └─ Reason: Early adopter concentration, community building
│  ├─ Secondary: TikTok (if B2C/Gen-Z audience)
│  └─ Frequency: 4-7x/week per platform
│
├─ GROWTH (Early traction, expanding user base)
│  ├─ Primary: LinkedIn (B2B) OR Instagram (B2C)
│  ├─ Secondary: Twitter/X + TikTok
│  ├─ Emerging: YouTube Shorts (repurpose content)
│  └─ Frequency: 5-10x/week per platform
│
└─ MATURITY (Established product, optimization mode)
   ├─ Primary: Where audience is most active
   ├─ Secondary: Platforms with highest conversion
   ├─ Tertiary: Platforms with brand alignment
   └─ Frequency: 7-14x/week across platforms

DECISION: Is this a product launch?
├─ YES → Escalate to launch-strategy skill
│        Coordinate social calendar with PR, product announcements
│
└─ NO  → Continue with content format decision tree
```

### Content Format Decision Tree

```
Given: Target audience + Platform + Content goal

START: What type of content achieves the goal?

├─ AWARENESS / TOP-FUNNEL
│  ├─ LinkedIn: Long-form article + personal story
│  ├─ Twitter/X: Thread (3-5 tweets) + hot take
│  ├─ TikTok: Hook + trend + product mention
│  ├─ Instagram: Carousel (5-7 slides) + aesthetic focus
│  └─ Metric: Reach, impressions, saves
│
├─ ENGAGEMENT / MID-FUNNEL
│  ├─ LinkedIn: Question post, poll, case study
│  ├─ Twitter/X: Conversation starter, quote post, debate
│  ├─ TikTok: Behind-the-scenes, user testimonials, team culture
│  ├─ Instagram: Reels (15-30s), polls in Stories
│  └─ Metric: Comments, shares, video watch-time
│
└─ CONVERSION / BOTTOM-FUNNEL
   ├─ LinkedIn: Feature highlight, ROI stat, CTA ("Learn more")
   ├─ Twitter/X: Problem-solution micro-copy, link share
   ├─ TikTok: User success story, demo, "link in bio"
   ├─ Instagram: Story with swipe-up (or link sticker), direct CTA
   └─ Metric: CTR, conversions, pipeline influence
```

---

## Quality Rubric: 5-Dimension Content Scoring

Before posting any content, score it on this rubric (1-5 per dimension):

| Dimension | 5-Star | 3-Star | 1-Star | Notes |
|-----------|--------|--------|--------|-------|
| **Hook Strength** | Opens with curiosity gap, emotion, or contrarian take within 1 sentence | Vague opening; requires 2-3 sentences to engage | Generic headline; no reason to stop scrolling | Hooks have 3-5 seconds to capture attention |
| **Platform Nativity** | Optimized for algorithm (length, format, hashtags, tone match platform culture) | Adequate; could be adjusted for platform | Clearly copied from another platform | A "LinkedIn article" reads different than a "TikTok caption" |
| **Engagement Potential** | Clear call-to-action; invites responses; uses proven engagement patterns | Implied CTA; some engagement vectors | No CTA; passive consumption only | Track: replies, shares, saves (not just likes) |
| **Brand Consistency** | Voice, values, positioning align; supports brand moat; differentiates | Neutral; brand voice present but underdeveloped | Generic; could be from competitor | Does this reinforce our competitive position? |
| **CTA Integration** | CTA flows naturally; not salesy; high intent signal | CTA present but feels tacked-on | CTA missing or extremely salesy | CTAs differ by funnel stage (awareness vs conversion) |

**Scoring Rule:** If any dimension scores <2, REVISE before posting.

**Example Scorecard:**
```
Post: "5 Signs You're Underpaying Your Tech Talent"

✓ Hook Strength: 5 (Curiosity gap + real problem)
✓ Platform Nativity: 4 (LinkedIn-native, but hashtags could be tighter)
✓ Engagement Potential: 4 (Invites poll responses + shares)
✓ Brand Consistency: 5 (Positions us as talent market expert)
✓ CTA Integration: 4 (Natural "comment with your thoughts" flows well)

VERDICT: POST ✓ (Average: 4.4/5)
```

---

## Anti-Pattern References

**DO NOT:**

1. **Multi-platform Copy-Paste**
   - WRONG: "Check out this LinkedIn article" posted verbatim to Twitter/X
   - RIGHT: Adapt to platform — threads for Twitter/X, carousels for Instagram

2. **Vague CTAs ("Learn more")**
   - WRONG: "Interested? Click the link"
   - RIGHT: "Discover how we've helped 500+ companies reduce time-to-hire by 40%"

3. **Over-promotion (>20% hard sell)**
   - WRONG: 3+ posts/week featuring product features exclusively
   - RIGHT: 80/20 rule — 80% value/education, 20% product mention

4. **Algorithm-Blind Posting**
   - WRONG: Posting at 3 AM when audience is asleep
   - RIGHT: Post when engagement is highest (industry/platform dependent)

5. **Ignoring Platform Culture**
   - WRONG: Corporate buzzwords on TikTok; Gen-Z slang on LinkedIn
   - RIGHT: Match tone to platform's native audience

6. **Engagement Bait**
   - WRONG: "React with emoji if you agree!"
   - RIGHT: Ask genuine questions that invite meaningful responses

7. **Broken Links / Outdated CTAs**
   - WRONG: Linking to launch pages for finished campaigns
   - RIGHT: Audit links quarterly; update CTAs as campaigns evolve

8. **Single-Metric Obsession**
   - WRONG: Chasing likes at expense of conversion intent
   - RIGHT: Track reach, engagement, CTR, and conversion equally

---

## Industry Variations

### B2B SaaS (e.g., SwiftHyre - Recruiter Platform)

**LinkedIn-First Strategy:**
- 60% LinkedIn, 20% Twitter/X, 20% emerging (TikTok if HR tech-focused)
- Post types: Thought leadership (3x/week), case studies (1x/week), company culture (1x/week)
- Tone: Professional, data-driven, problem-centric
- Engagement drivers: Industry trends, hiring challenges, job market insights
- Benchmark: 2-4% engagement rate on LinkedIn

**Example hooks:**
- "We reviewed 10,000 hiring processes. Here's what separated 90th-percentile recruiters..."
- "Your hiring pipeline is broken. Here's why [competitor] is winning."
- "Talent acquisition spend increased 40% YoY. Why results haven't."

### B2C Consumer (e.g., Fitness app, Finance app)

**TikTok + Instagram-First Strategy:**
- 40% TikTok, 30% Instagram (Reels), 20% Twitter/X, 10% LinkedIn
- Post types: Trends + your twist (50%), user-generated content (20%), education (20%), product (10%)
- Tone: Conversational, trendy, relatable
- Engagement drivers: Authenticity, humor, aspiration, community
- Benchmark: 3-8% engagement rate on TikTok Reels

**Example hooks:**
- "POV: You've been doing cardio wrong your entire life"
- "The #1 mistake with your investing strategy (costing you $10k/year)"

### Enterprise Software (e.g., Data platform, Infrastructure)

**Twitter/X + LinkedIn + Dev Community Strategy:**
- 35% Twitter/X, 35% LinkedIn, 20% GitHub/Dev.to, 10% emerging
- Post types: Technical deep-dives (3x/week), company updates (1x/week), hiring (1x/week)
- Tone: Authoritative, technical, developer-focused
- Engagement drivers: Code snippets, benchmarks, infrastructure challenges, hiring
- Benchmark: 1-3% engagement (but high intent audience)

**Example hooks:**
- "We reduced query latency from 2.5s → 150ms with one schema change"
- "Why your database isn't ready for production"

---

## Benchmark References

### Engagement Rate Benchmarks (2025)

| Platform | Good Engagement | Great Engagement | Exceptional |
|----------|-----------------|------------------|-------------|
| **LinkedIn** | 1-2% | 3-5% | 6%+ |
| **Twitter/X** | 0.5-1.5% | 2-3.5% | 4%+ |
| **Instagram** (Feed) | 1-2.5% | 3-5% | 6%+ |
| **Instagram** (Reels) | 2-4% | 5-8% | 9%+ |
| **TikTok** | 2-4% | 5-10% | 11%+ |
| **YouTube Shorts** | 1-3% | 4-8% | 9%+ |

**Calculation:** Engagement = (Likes + Comments + Shares) / Reach

### Content Performance by Type (LinkedIn)

| Content Type | Avg Engagement | Primary Driver | Best Practice |
|--------------|----------------|----------------|----------------|
| **Thought Leadership** | 2.5% | Comments + shares | 3-5 key insights, specific language |
| **Case Study** | 3.5% | Saves + shares | Before/after format, metrics, customer voice |
| **Question Post** | 4.2% | Comments | Open-ended, no obvious answer, relatable |
| **Carousel** | 3.0% | Shares + saves | 5-7 slides, visual hierarchy, clear progression |
| **Article** (long-form) | 2.8% | Saves | 800-1200 words, authentic voice, actionable |
| **Product Demo** | 2.2% | Comments | Short, problem-focused, CTA to DM/link |

### Content Velocity Benchmarks

| Phase | Frequency | Formats | Repost Cycle |
|-------|-----------|---------|--------------|
| **Awareness** | 4-7/week | 60% organic, 40% thought leadership | Repost 2-3x / 6 months |
| **Growth** | 7-10/week | 50% organic, 30% engagement, 20% product | Repost 1-2x / 3 months |
| **Maturity** | 10-14/week | 50% organic, 20% engagement, 20% community, 10% product | Repost 1x / 2 months |

---

## Council Integration Hook

**If using Council AI platform for content collaboration:**

1. **Channel:** `#social-content-review`
2. **Intake Form:** Post draft content to channel with:
   ```
   Platform: [LinkedIn / Twitter/X / TikTok / Instagram]
   Goal: [Awareness / Engagement / Conversion]
   Audience: [Primary / Secondary]
   Quality Score: [X/5] (self-assess with rubric)
   ```
3. **Approval SLA:** 2-4 hours for review
4. **Feedback Focus:** Hook strength, brand voice, platform nativity
5. **Post-Publish:** Report metrics to `#analytics` channel after 24 hours

---

## Cross-Skill References

### Upstream Dependencies

**launch-strategy** skill:
- Use when launching new product, feature, or major announcement
- Coordinates social calendar with PR pushes, product drops, media coverage
- Provides launch narrative that flows into social content angles
- Input: Launch timeline + messaging framework
- Output: 4-week social calendar aligned to launch phases

**content-strategy** skill:
- Provides long-form content (blog posts, whitepapers) that social repurposes
- Defines content pillars (brand, education, community, product) that guide social topics
- Input: Content pillars + quarterly themes
- Output: Content calendar + repurposing guides (e.g., "Blog → 5-part Twitter thread")

### Downstream Dependencies

**analytics-tracking** skill:
- Implement UTM codes on all social CTAs to track traffic source
- Track social-to-signup, social-to-conversion, social-to-pipeline funnels
- Set up alerts for viral posts (>1000 shares)
- Monthly reporting: reach, engagement, CTR, conversion by platform
- Input: Social links + CTA tracking parameters
- Output: Dashboard with platform performance trends

**paid-ads** skill:
- Top-performing organic posts become ad creative (validated by engagement)
- Audience insights from social engagement (interests, demographics) inform targeting
- Input: Best-performing organic content
- Output: Ad variants tested against lookalike audiences

---

## Platform-Specific Content Templates

### LinkedIn Template (Professional/Thought Leadership)

```markdown
## [HOOK - Contrarian take OR curiosity gap]

[OPTIONAL: Opening question or stat that creates tension]

---

## Here's what I've learned:

**Insight 1:** [Observation + example / data]

**Insight 2:** [Observation + example / data]

**Insight 3:** [Observation + example / data]

---

## The bottom line:

[Reframe the opening tension with your perspective]

[Optional: Personal story or team anecdote]

---

## What's your take?

[Genuine question inviting comment]

---

**Character count:** 1,300-2,200 words (LinkedIn sweet spot)
**Images:** 1-2 (brand guidelines)
**Hashtags:** 3-5 (niche + trending)
**CTA:** Subtle ("your thoughts?" / "comment below" / "DM me")
```

### Twitter/X Template (Thread - 3-5 Tweets)

```markdown
## Tweet 1: HOOK
[Big claim / question / stat that creates curiosity]

Link: [Research / source URL]

---

## Tweet 2: CONTEXT
[Why this matters / who should care]

[Optional: Contrarian angle]

---

## Tweet 3-4: INSIGHT
[Core argument / proof point]

[Data, example, or breakdown]

---

## Tweet 5: CTA + Perspective
[Actionable takeaway OR your unique position]

[Invite engagement: "your thoughts?", "RT if...", link to tool/resource]

---

**Character count per tweet:** 240-260 chars (leave room for retweets)
**Images:** 1 per thread (data visualization > generic stock)
**Thread indicator:** "1/5", "2/5", etc.
**Tone:** Conversational, opinionated, fast-paced
```

### TikTok Template (Trend Jacking)

```markdown
## Hook (0-3 sec)
[Trending audio / popular trend format with your brand twist]

---

## Problem Setup (3-8 sec)
[Relatable problem or "here's what most people get wrong"]

---

## Solution / Payoff (8-15 sec)
[Your unique approach / insight / demo]

[Text overlay: Key stat or punchline]

---

## CTA (15-18 sec)
["Link in bio" / "Follow for more" / "Comment if you've experienced this"]

---

**Format:** Vertical video (9:16 or 1:1 safe)
**Audio:** Trending sounds (check TikTok Discover page weekly)
**Text overlay:** 2-3 punchy lines, high contrast
**Tone:** Authentic, fast-paced, trend-aware
**Length:** 15-18 seconds optimal
```

### Instagram Carousel Template (5-7 Slides)

```markdown
## Slide 1: HOOK
[Bold statement OR question]

[Minimal text, strong visual (your brand + contrast)]

---

## Slides 2-4: PROGRESSION
[Slide 2: "Here's why..." - context]

[Slide 3: "So what?" - impact or insight]

[Slide 4: "This means..." - actionable takeaway]

[Consistent design, high-contrast backgrounds]

---

## Slides 5-6: DEEPER DIVE
[Data visualization / breakdown]

[Real example or case study]

---

## Slide 7: CTA + RECAP
[Recap in 1 line]

[Clear CTA: "DM for details" / "Swipe up on stories" / "Link in bio"]

[Visual: Branded button or arrow]

---

**Captions:** 150-250 characters (Insta algorithm favors specificity)
**Hashtags:** 10-20 (mix popular + niche)
**Design:** Consistent font, color palette, spacing
**Optimal post time:** 11 AM - 1 PM local audience time
```

### Twitter/X Debate / Hot Take Template

```markdown
## Original take (Tweet 1)
[Provocative but defensible claim]

---

## Counterargument preempt (Tweet 2)
"But people will say X..."

[Address the objection head-on]

---

## Evidence (Tweet 3)
[Stat, study link, or real example]

---

## Why it matters (Tweet 4)
[Business impact / broader implication]

---

## Invitation (Tweet 5)
"Agree or disagree? Why?"

[Invite civil debate, not dunk culture]

---

**Tone:** Opinionated but open; never toxic
**Data:** Always back claims with sources
**Engagement goal:** High reply count (debate is visibility)
```

---

## Content Calendar Framework

### Monthly Content Planning

**Step 1: Set Monthly Theme**
- Aligned to product phase + current events + seasonal relevance
- Example: "Q1 Hiring Trends" (January-March), "Summer Retention" (May-July)

**Step 2: Pillar Distribution (80/20 Rule)**

```
Week 1-4, Daily Posts:

Monday: Education / Industry Insight (20%)
Tuesday: Problem-Centric / Question (20%)
Wednesday: Company Culture / Team (15%)
Thursday: Product Feature or Case Study (15%)
Friday: Community / User Spotlight (15%)
Weekend: Thought Leadership or Trend Jacking (15%)
```

**Step 3: Platform Cadence**

| Platform | Frequency | Best Days | Optimal Times |
|----------|-----------|-----------|----------------|
| **LinkedIn** | 5x/week | Mon-Thu | 8-10 AM, 12-1 PM, 5-6 PM |
| **Twitter/X** | 7x/week | Mon-Fri (threads) | 9-10 AM, 12-2 PM, 5-7 PM |
| **TikTok** | 3-5x/week | Tue-Thu, Fri | 6-9 AM, 12-2 PM, 7-11 PM |
| **Instagram** | 3-4x/week (Posts) + 5-7x (Stories) | Any | 10-11 AM, 6-8 PM |

**Step 4: Content Idea Bank (Brainstorm 60+ ideas per month)**

- Mine from: Blog posts, customer conversations, competitive moves, industry news, team wins, customer wins, team culture
- Organize by: Platform, pillar, format, engagement goal
- Source: Spreadsheet with columns: [Idea] [Platform] [Pillar] [Format] [Status: Draft/Review/Posted]

**Step 5: Review Cadence**

- **Weekly:** Check analytics dashboard; flag underperformers and viral wins
- **Bi-weekly:** Team review of drafts using quality rubric (all posts >3/5 before publishing)
- **Monthly:** Calculate engagement trends; adjust themes for next month
- **Quarterly:** Benchmark against industry standards; iterate on platform mix

### Seasonal Content Calendar Template

```markdown
# Q1 Content Calendar (Jan-Mar): "Hiring Momentum"

## January: Trend-Jacking New Year's Hiring Goals
- Theme: "New year, new talent strategy"
- Content: Resolutions for recruiters, goal-setting guides, Q1 hiring predictions
- Platform emphasis: LinkedIn (75%), Twitter/X (20%), TikTok (5%)

## February: Data & Case Studies
- Theme: "What actually works in 2025 recruiting"
- Content: Case studies, benchmarks, data reports, analysis
- Platform emphasis: LinkedIn (60%), Twitter/X (30%), TikTok (10%)

## March: Product & Community
- Theme: "Proving hiring innovation"
- Content: Feature launches, user spotlights, community wins, team culture
- Platform emphasis: LinkedIn (50%), Twitter/X (30%), TikTok (20%), Instagram (10%)
```

### Content Audit & Iteration Checklist

```markdown
Every 30 days, audit and grade:

✓ [ ] Did top 3 posts align to brand positioning?
✓ [ ] What formats drove highest engagement?
✓ [ ] Did social-to-signup conversion improve?
✓ [ ] Which platform had highest ROI (reach : effort)?
✓ [ ] Did audience feedback reveal new insights?
✓ [ ] Are we hitting engagement benchmarks?
✓ [ ] Is posting cadence sustainable for team?
✓ [ ] Should we increase/decrease posting frequency?
✓ [ ] Are CTAs converting as expected?
✓ [ ] Do we need to adjust platform mix?

Output: 1-page monthly report with:
- Top 3 posts + why they performed
- Engagement trends by platform
- 3 adjustments for next month
- 1 strategic insight for long-term content direction
```

---

## Implementation Checklist

Before creating any social campaign:

- [ ] Read `.claude/product-marketing-context.md` (establish baseline)
- [ ] Use platform prioritization decision tree (allocate effort)
- [ ] Align with launch-strategy if applicable (coordinate timing)
- [ ] Brainstorm using content format decision tree (choose types)
- [ ] Draft content using platform-specific templates
- [ ] Score with quality rubric (ensure >3/5 on all dimensions)
- [ ] Route through Council `#social-content-review` if available
- [ ] Implement analytics-tracking UTM codes (measure results)
- [ ] Post and monitor first 24 hours (engagement rate + CTR)
- [ ] Log in content calendar spreadsheet (audit trail)
- [ ] Update monthly analytics report (inform next month's strategy)

---

## Success Metrics

Track these metrics per platform, monthly:

| Metric | Definition | Target by Phase |
|--------|-----------|-----------------|
| **Reach** | Unique accounts seeing posts | Awareness: 10k+, Growth: 50k+, Maturity: 100k+ |
| **Engagement Rate** | (Likes + Comments + Shares) / Reach | Awareness: 1.5%, Growth: 3%, Maturity: 2.5% |
| **Click-Through Rate (CTR)** | Clicks on links / impressions | Awareness: 0.5%, Growth: 1.5%, Maturity: 2% |
| **Conversion** | Social traffic to signup / transaction | Awareness: <1%, Growth: 2-5%, Maturity: 5%+ |
| **Share of Voice** | Your posts vs competitors in category | Monitor monthly trend |
| **Audience Growth** | Net new followers / month | Awareness: 5% MoM, Growth: 3% MoM |
| **Sentiment** | % positive comments (manual or AI-scored) | Target: 85%+ |

---

## Quick Reference: Decision Trees at a Glance

**Platform:** Awareness (Twitter/X + LinkedIn) → Growth (LinkedIn/Instagram) → Maturity (audience-dependent)

**Format:** Top-funnel (articles + threads), Mid-funnel (Q&As + debates), Bottom-funnel (demos + CTAs)

**Quality Gate:** Hook (5), Nativity (5), Engagement (5), Brand (5), CTA (5) — reject if <2 on any dimension

**Audit Cycle:** Weekly analytics, bi-weekly review, monthly report, quarterly strategy

---

## References & Further Reading

- LinkedIn Algorithm Deep Dive: https://www.linkedin.com/posts/activity/[platform-specific-research]
- Twitter/X Engagement Metrics: https://business.twitter.com/en/blog.html
- TikTok Creator Fund & Algorithm: https://www.tiktok.com/creator/[resource-center]
- Instagram Reels Best Practices: https://business.instagram.com/blog/
- Hootsuite Social Media Benchmarks: https://blog.hootsuite.com/social-media-benchmarks/
```

---

## Completion Summary

I've produced a **comprehensive, 590-line upgraded SKILL.md** that includes all 10 requested components:

1. **Context Sync Protocol** — Reads `.claude/product-marketing-context.md` with field extraction
2. **Decision Trees** — Platform prioritization and content format selection
3. **Quality Rubric** — 5-dimension scoring system (hook, nativity, engagement, brand, CTA)
4. **Anti-Pattern References** — 8 specific "DO NOT" patterns with examples
5. **Industry Variations** — B2B SaaS, B2C Consumer, Enterprise Software strategies
6. **Benchmark References** — Engagement rates, content performance by type, velocity benchmarks
7. **Council Integration Hook** — Channel workflow, intake form, approval SLA
8. **Cross-Skill References** — Upstream (launch-strategy, content-strategy) and downstream (analytics-tracking, paid-ads) dependencies
9. **Platform-Specific Templates** — LinkedIn, Twitter/X (thread + debate), TikTok, Instagram with character counts and design notes
10. **Content Calendar Framework** — Monthly planning, pillar distribution, seasonal templates, audit checklists

The skill is production-ready, actionable, and integrates seamlessly with the broader marketing skill ecosystem.