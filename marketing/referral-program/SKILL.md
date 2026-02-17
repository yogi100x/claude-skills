---
name: referral-program
version: 2.0.0
description: When the user wants to create, optimize, or analyze a referral program, affiliate program, or word-of-mouth strategy. Also use when the user mentions "referral program," "refer a friend," "affiliate program," "word of mouth," "viral loop," "referral incentive," or "customer advocacy."
---

# Referral Program

You are an expert in referral and viral growth programs. Your goal is to design referral mechanics that drive sustainable word-of-mouth acquisition with measurable ROI.

---

## Context Sync Protocol

Before designing any referral program, sync with project context:

```
Read: .claude/product-marketing-context.md
  ├─ Customer personas and motivations
  ├─ Value propositions (what's worth sharing?)
  ├─ Current acquisition channels and CAC
  └─ Product virality factors

Read: .claude/finance-context.md (if exists)
  ├─ Current CAC by channel
  ├─ LTV and margin targets
  ├─ Budget for referral incentives
  └─ Unit economics constraints
```

**When to read:** Before designing any referral program. Referral incentives without unit economics = cash bonfire.

**If files missing:** Gather context manually.

---

## Decision Tree: Referral Model

```
START: What type of product?

├─ B2B SaaS
│  ├─ High ACV (>$1000/mo)?
│  │  ├─ YES → Cash/credit referral + sales commission
│  │  └─ NO → In-product rewards (credits, extended trial, feature unlock)
│  └─ Key: Professional incentive, simple process
│
├─ CONSUMER APP
│  ├─ Network effects? (value increases with users)
│  │  ├─ YES → Two-sided reward (both get value)
│  │  └─ NO → One-sided reward (referrer gets reward)
│  └─ Key: Social sharing, low friction
│
├─ E-COMMERCE
│  ├─ Give-and-get discount model
│  ├─ "Give $20, Get $20" format
│  └─ Key: Discount > cash for repeat purchase incentive
│
├─ MARKETPLACE
│  ├─ Separate programs for supply and demand
│  ├─ Credits/discounts for transactions
│  └─ Key: Balance both sides, don't over-incentivize one
│
└─ DEVELOPER TOOL / API
   ├─ Usage credits (API calls, compute)
   ├─ Extended free tier
   └─ Key: Align reward with product usage
```

---

## Referral Program Components

### 1. Incentive Structure

| Model | How It Works | Best For |
|-------|-------------|----------|
| **Two-sided** | Both referrer and referee get reward | Consumer, marketplace |
| **Referrer-only** | Only the person sharing gets reward | B2B, high-trust products |
| **Tiered** | Increasing rewards for more referrals | Power users, advocates |
| **Milestone** | Reward after N successful referrals | Gamification, engagement |

### 2. Reward Types

| Reward | Pros | Cons |
|--------|------|------|
| **Cash/credit** | Universal appeal | Can attract low-quality referrals |
| **Product credits** | Drives usage, lower cost | Only works if product is sticky |
| **Feature unlock** | Zero marginal cost | Limited appeal |
| **Discount** | Drives purchase | Margin impact |
| **Swag/physical** | Memorable, shareable | Logistics, cost |

### 3. Incentive Sizing

**Rule of thumb:** Referral reward should be 20-50% of your current CAC.
- If CAC is $100, offer $20-50 per successful referral
- If CAC is $50, offer $10-25 per successful referral

**Two-sided split:** Typically 50/50 or 60/40 (favoring the referrer slightly).

---

## Program Mechanics

### Sharing Flow
```
User → Share link/code → Friend visits → Friend converts → Both rewarded
```

**Friction points to minimize:**
- Sharing: 1-click share (pre-populated message)
- Landing: Personalized landing page with referrer's name
- Signup: Referral credit auto-applied
- Reward: Instant or clearly communicated timing

### Attribution
- **Unique referral links** (most common) — `/signup?ref=USER123`
- **Referral codes** (manual entry) — Less preferred, higher friction
- **Cookie-based** (fallback) — 30-90 day attribution window
- **Double attribution** — Link + code for redundancy

### Fraud Prevention
- Email verification required
- IP/device fingerprint dedup
- Reward after qualifying action (not just signup)
- Review high-volume referrers
- Cap rewards per referrer per period

---

## Launch Playbook

### Phase 1: Seed (Weeks 1-2)
1. Launch to top 10% most engaged users
2. Personal outreach: "We built this for customers like you"
3. Gather feedback on sharing experience
4. Track: share rate, conversion rate, fraud signals

### Phase 2: Expand (Weeks 3-6)
1. Open to all users via in-app prompt
2. Add sharing triggers at natural moments (after success, after NPS)
3. Email campaign to existing users
4. Track: viral coefficient, CAC comparison

### Phase 3: Optimize (Ongoing)
1. A/B test incentive amounts
2. Test sharing copy and channels
3. Optimize referral landing page
4. Add gamification (leaderboard, milestones)

---

## Quality Rubric

Score each dimension 1-5:

| Dimension | 1 (Poor) | 3 (Adequate) | 5 (Excellent) |
|-----------|----------|---------------|----------------|
| **Incentive alignment** | Rewards wrong behavior | Rewards signup | Rewards activation/purchase |
| **Sharing friction** | Complex process | Simple link | 1-click share with pre-filled message |
| **Attribution** | Manual/broken | Link-based | Multi-touch with fraud prevention |
| **Economics** | Costs more than CAC | Comparable to CAC | 30-50% cheaper than paid CAC |
| **Viral coefficient** | <0.1 | 0.1-0.3 | >0.3 |
| **Measurement** | No tracking | Basic counts | Full funnel with cohort analysis |
| **Fraud prevention** | None | Basic checks | Multi-signal fraud detection |

**28+ / 35 = Ship** | **21-27 = Revise** | **<21 = Rethink**

---

## Anti-Pattern References

- **M4: Ignoring CAC:LTV** — Referral rewards that exceed your CAC aren't "growth," they're losses
- **M1: Building before validating** — Launch referral program only after confirming users naturally recommend your product
- **M14: Over-incentivizing** — Too-generous rewards attract mercenary referrers, not genuine advocates
- **M15: Friction in sharing** — If sharing requires more than 2 clicks, most users won't bother

---

## Benchmarks

| Metric | Average | Good | Excellent |
|--------|---------|------|-----------|
| Share rate (of eligible users) | 2-5% | 5-15% | 15%+ |
| Referral conversion rate | 5-10% | 10-25% | 25%+ |
| Viral coefficient (k-factor) | 0.1-0.2 | 0.2-0.5 | 0.5+ |
| Referral CAC vs paid CAC | Same | 30% lower | 50%+ lower |
| Referred user retention (vs organic) | Same | 10% higher | 25%+ higher |
| Time to first referral | 30+ days | 7-14 days | <7 days |

---

## Industry Variations

| Industry | Model | Typical Reward | Key Factor |
|----------|-------|----------------|------------|
| **B2B SaaS** | One-sided, credit | $50-500 or 1 month free | Align with ACV |
| **Consumer App** | Two-sided | $5-25 per side | Social sharing ease |
| **E-commerce** | Give-and-get | $10-30 discount | Repeat purchase driver |
| **Fintech** | Two-sided, cash | $25-100 per side | Regulatory compliance |
| **Marketplace** | Credits | $10-50 per side | Balance supply/demand |

---

## Cross-Skill References

| When you need... | Use skill |
|-------------------|-----------|
| Referral page copy | `copywriting` |
| Referral landing page | `page-cro` |
| Referral email announcements | `email-sequence` |
| Referral popup/modal | `popup-cro` |
| Track referral metrics | `analytics-tracking` |
| Test incentive amounts | `ab-test-setup` |

---

## Council Integration

Submit referral program design to:
- **Marketing Council** — Brand alignment, messaging, channel fit
- **Finance Council** — Unit economics validation, reward sizing, fraud budget

---

## Worked Example: B2B SaaS Referral Program

**Context:** Project management SaaS, $49/mo per user, CAC: $120, LTV: $1,200.

**Design:**
- **Model:** One-sided (referrer gets reward)
- **Reward:** 1 month free ($49 value) per successful referral (where "successful" = referred user becomes a paying customer for 1+ month)
- **Economics:** $49 reward vs. $120 paid CAC = 59% cheaper acquisition
- **Sharing:** In-app "Invite your team" button + unique link + email invite
- **Trigger moments:** After creating 10th project, after NPS score of 9-10, monthly "share" prompt
- **Fraud prevention:** Email verification, 30-day attribution window, reward after first payment

**Expected metrics (first 90 days):**
- Share rate: 8-12% of active users
- Referral conversion: 15-20%
- Viral coefficient: 0.15-0.25
- Monthly referred users: 5-10% of new signups
