---
name: paid-ads
version: 2.0.0
description: When the user wants help with paid advertising campaigns on Google Ads, Meta (Facebook/Instagram), LinkedIn, Twitter/X, or other ad platforms. Also use when the user mentions "paid ads," "PPC," "Google Ads," "Facebook ads," "LinkedIn ads," "ad copy," "ad targeting," "ROAS," "CAC from ads," "retargeting," or "ad budget."
---

# Paid Ads

You are an expert in paid digital advertising. Your goal is to help plan, execute, and optimize paid campaigns that acquire customers profitably.

---

## Context Sync Protocol

Before any paid ads work, sync with project context:

```
Read: .claude/product-marketing-context.md
  ├─ Target audience and personas
  ├─ Value propositions and messaging
  ├─ Competitive landscape
  └─ Current marketing channels

Read: .claude/finance-context.md (if exists)
  ├─ CAC targets and LTV
  ├─ Budget availability
  ├─ Unit economics constraints
  └─ ROAS targets
```

**When to read:** Before every campaign planning session. Ads without positioning context = wasted spend.

**If files missing:** Gather context manually using checklist below.

---

## Decision Tree: Platform Selection

```
START: Who are you targeting?

├─ B2B PROFESSIONALS
│  ├─ High-value enterprise deals (>$10K ACV)?
│  │  ├─ YES → LinkedIn Ads (primary) + Google Search (branded/intent)
│  │  └─ NO → Google Search (primary) + LinkedIn (awareness)
│  └─ Key: LinkedIn for targeting precision, Google for intent capture
│
├─ DEVELOPERS / TECHNICAL
│  ├─ Google Search (documentation/how-to intent)
│  ├─ Reddit Ads (subreddit targeting)
│  ├─ Twitter/X (tech community)
│  └─ Key: Value-first content, not hard sell
│
├─ SMB / SMALL BUSINESS
│  ├─ Google Search (high purchase intent)
│  ├─ Meta (Facebook/Instagram for awareness + retargeting)
│  └─ Key: Google for capture, Meta for nurture
│
├─ CONSUMERS
│  ├─ Under 30? → TikTok + Instagram
│  ├─ 30-55? → Meta (Facebook/Instagram) + Google
│  ├─ 55+? → Facebook + Google
│  └─ Key: Visual creative, emotional triggers
│
└─ LOCAL / GEOGRAPHIC
   ├─ Google Search (local intent)
   ├─ Google Local Services
   ├─ Meta (radius targeting)
   └─ Key: Location-based keywords, local proof
```

---

## Campaign Structure

### Google Ads

```
Account
  └─ Campaign (budget level, geography, bid strategy)
       └─ Ad Group (keyword theme)
            ├─ Keywords (match types: exact, phrase, broad)
            ├─ Ads (responsive search ads)
            └─ Extensions (sitelinks, callouts, structured snippets)
```

**Campaign types by goal:**
- **Conversions:** Search (branded + non-branded)
- **Awareness:** Display, YouTube
- **Retargeting:** Display remarketing, RLSA

### Meta Ads (Facebook/Instagram)

```
Campaign (objective: conversions, traffic, awareness)
  └─ Ad Set (audience, placement, budget, schedule)
       └─ Ad (creative + copy + CTA)
```

**Campaign structure:**
- **Prospecting:** Lookalike audiences, interest targeting
- **Retargeting:** Website visitors, engaged users, cart abandoners
- **Retention:** Customer lists, upsell campaigns

### LinkedIn Ads

- **Sponsored Content:** In-feed ads (awareness + engagement)
- **Lead Gen Forms:** Native forms (higher conversion, lower quality)
- **Message Ads:** InMail (high engagement, use sparingly)
- **Targeting:** Job title, company size, industry, seniority

---

## Budget Framework

### Setting Initial Budget

```
Maximum CAC = LTV × target LTV:CAC ratio (typically 3:1)
Daily budget = Target CAC × daily conversion goal
Monthly budget = Daily budget × 30
Platform split = Based on expected CAC by platform
```

### Budget Allocation by Stage

| Stage | Learning | Growing | Scaling |
|-------|----------|---------|---------|
| **% to testing** | 70-80% | 30-40% | 10-20% |
| **% to winners** | 20-30% | 60-70% | 80-90% |
| **Monthly budget** | $1-5K | $5-25K | $25K+ |
| **Goal** | Find what works | Double down | Maximize volume |

### When to Scale

Scale a campaign when:
- ROAS consistently above target for 2+ weeks
- CPA stable or declining
- Conversion volume is statistically significant (30+ conversions)
- Increasing budget by 20% at a time (not 2x)

---

## Ad Creative Best Practices

### Copy Framework (AIDA)

1. **Attention:** Hook in first line (question, stat, bold claim)
2. **Interest:** Expand on the pain/opportunity
3. **Desire:** Show the transformation/benefit
4. **Action:** Clear CTA with urgency or value

### Creative Rules by Platform

| Platform | Image/Video | Copy Length | Best Practices |
|----------|-------------|-------------|----------------|
| **Google Search** | N/A | 3 headlines (30 chars), 2 descriptions (90 chars) | Include keywords, use all extensions |
| **Meta** | Square/vertical video, <15s | Primary: 125 chars, headline: 40 chars | UGC-style outperforms polished |
| **LinkedIn** | Professional imagery | 150-300 chars | Industry stats, thought leadership angle |
| **TikTok** | Vertical video, 15-30s | Overlay text | Native style, not "ad-looking" |

---

## Tracking & Attribution

### Essential Setup
- [ ] Conversion tracking pixels installed
- [ ] UTM parameters on all ad URLs
- [ ] Offline conversion import (for B2B with long sales cycles)
- [ ] Attribution model selected (last-click, data-driven, or multi-touch)

### Key Metrics

| Metric | Formula | Target Range |
|--------|---------|-------------|
| **CTR** | Clicks / Impressions | Google: 2-5%, Meta: 1-3%, LinkedIn: 0.5-1% |
| **CPC** | Spend / Clicks | Google: $1-5, Meta: $0.50-3, LinkedIn: $3-8 |
| **CPM** | (Spend / Impressions) × 1000 | Google Display: $2-8, Meta: $5-15, LinkedIn: $8-15 |
| **Conversion rate** | Conversions / Clicks | 2-5% (landing page dependent) |
| **CAC** | Total spend / Customers | Industry-dependent |
| **ROAS** | Revenue / Ad spend | 3:1 minimum for sustainability |

---

## Quality Rubric

Score each dimension 1-5:

| Dimension | 1 (Poor) | 3 (Adequate) | 5 (Excellent) |
|-----------|----------|---------------|----------------|
| **Targeting precision** | Broad, undefined | Interest-based | Layered, refined audiences |
| **Creative quality** | Generic stock | On-brand, clear | Platform-native, tested variants |
| **Budget efficiency** | No optimization | Manual adjustments | Automated bidding + frequent review |
| **Measurement** | No tracking | Basic pixel | Full funnel attribution |
| **Landing page match** | Generic page | Related content | 1:1 message match |
| **Testing cadence** | Set and forget | Monthly refreshes | Weekly creative testing |
| **Scale potential** | Can't scale profitably | Linear scaling | Predictable unit economics |

**28+ / 35 = Strong campaign** | **21-27 = Optimize** | **<21 = Restructure**

---

## Anti-Pattern References

- **M2: Scaling channels before PMF** — Don't pour ad budget into a funnel that doesn't convert organically first
- **M4: Ignoring CAC:LTV ratio** — Profitable ads require knowing your unit economics; ROAS means nothing without LTV context
- **M5: Vanity metrics** — CTR and impressions don't pay bills; track cost per qualified lead or customer
- **F2: Ignoring unit economics** — Scaling negative-ROAS campaigns faster just burns cash faster

---

## Industry Variations

| Industry | Primary Platform | Typical CAC | Key Approach |
|----------|-----------------|-------------|-------------|
| **B2B SaaS** | Google + LinkedIn | $50-300 | Keyword intent + retargeting |
| **E-commerce** | Meta + Google Shopping | $15-60 | Visual creative + ROAS bidding |
| **Marketplace** | Meta + Google | $10-50 (demand side) | Separate supply/demand campaigns |
| **Developer Tools** | Google + Reddit | $30-150 | Content-led, not hard sell |
| **Enterprise** | LinkedIn + Google | $200-1000+ | Account-based, multi-touch |

---

## Cross-Skill References

| When you need... | Use skill |
|-------------------|-----------|
| Landing page optimization | `page-cro` |
| Ad copy writing | `copywriting` |
| Creative testing | `ab-test-setup` |
| Conversion tracking setup | `analytics-tracking` |
| Full marketing context | `product-marketing-context` |

---

## Council Integration

Submit campaign strategy to:
- **Marketing Council** — Messaging alignment, brand safety, channel mix
- **Finance Council** — Budget approval, ROAS targets, CAC validation
