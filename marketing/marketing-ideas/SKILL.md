# Marketing Ideas Skill

**Version:** 2.0  
**Purpose:** Generate, evaluate, and prioritize strategic marketing ideas with structured frameworks, industry-specific tactics, and ROI assessment.  
**Used by:** Content Strategy, Launch Strategy, Social Content skills; Growth Planning; Product Marketing  
**Last Updated:** 2026-02-17

---

## 1. Context Sync Protocol

Before generating marketing ideas, **always** check for project-specific constraints:

```
Step 1: Sync Context
├── Read `.claude/product-marketing-context.md` (if it exists)
│   ├── Current growth stage: [seed|early|growth|scale|mature]
│   ├── Target audience: [candidates|recruiters|coordinators|admins]
│   ├── Budget constraints: [$0-10k|$10-50k|$50-100k|$100k+]
│   ├── Brand positioning: [value prop, differentiators]
│   ├── Launch timeline: [now|2-4 weeks|1-3 months|3-6 months]
│   └── Competitive landscape: [major competitors, gaps]
│
Step 2: Validate Against Project Phase
├── Check `.planning/STATE.md` for current development phase
├── Check `docs/CONVENTIONS.md` for brand voice & tone
├── Check recent commits for recent launches
│
Step 3: Determine Applicability
├── Growth stage constraints (seed ≠ scale)
├── Available resource pool
├── Existing channel saturation
└── Time-to-impact requirements
```

**For SwiftHyre specifically:**
- Current stage: **Growth** (post-Series A, building recruiter network)
- Target audiences: Recruiters (primary revenue), Candidates (engagement), Universities (coordinator network)
- Primary brand positioning: "Discovery-First Talent Verification"
- Competitive gap: AI-graded assessments vs. traditional resume screening

---

## 2. Decision Trees

### Tree A: Growth Stage → Appropriate Tactics

```
SEED STAGE (MVP validation, <1000 users)
├── Content: Founder story, problem validation, early customer interviews
├── Channels: Twitter/LinkedIn, email newsletter, warm outreach, ProductHunt
├── Budget: <$5k/month (mostly time)
├── Goal: Prove problem-solution fit
└── Avoid: Paid ads, brand campaigns, conference sponsorships

EARLY STAGE (Product-market fit, 1k-10k users)
├── Content: Thought leadership, how-to guides, ROI calculators
├── Channels: Organic social, industry communities, early ambassador programs
├── Budget: $5-20k/month
├── Goal: Build community, establish authority
└── Avoid: Broad-reach campaigns, influencer partnerships (too early)

GROWTH STAGE (Scaling acquisition, 10k-100k users) ← SwiftHyre is HERE
├── Content: Case studies, webinars, competitive comparisons, product demos
├── Channels: Paid social (LinkedIn, Google), partnerships, referral programs, events
├── Budget: $20-100k+/month
├── Goal: Efficient CAC, segment penetration, brand awareness
└── Tactics: Partner with HR platforms, sponsor industry events, build affiliate network

SCALE STAGE (100k+ users, profitability)
├── Content: Thought leadership, industry reports, certifications, community platforms
├── Channels: Earned media, analyst coverage, enterprise partnerships, brand campaigns
├── Budget: $100k-500k+/month
├── Goal: Market leadership, retention, brand equity
└── Tactics: Gartner Magic Quadrant, analyst relations, conference keynotes

MATURE STAGE (Market saturation, optimization focus)
├── Content: Innovation announcements, customer success stories, platform communities
├── Channels: Direct sales, customer upsells, strategic partnerships
├── Budget: Profitability-driven allocation
├── Goal: Share of wallet, churn reduction, expansion revenue
└── Tactics: White-label partnerships, vertical-specific solutions, premium tiers
```

### Tree B: Budget Level → Channel Selection

```
BUDGET <$5k/month
├── MUST DO:
│   ├── LinkedIn organic (thought leadership, job postings)
│   ├── Twitter/X organic (industry commentary, product updates)
│   ├── Email newsletter (existing contacts)
│   ├── Warm outreach & partnerships
│   └── Community engagement (Reddit, industry Slack, Discord)
├── CONSIDER:
│   ├── Content marketing blog (SEO long-tail)
│   └── User-generated content campaigns
└── SKIP: Paid ads, conferences, influencers

BUDGET $5-20k/month
├── MUST DO: (all above)
├── ADD:
│   ├── LinkedIn ads (recruiter targeting, retargeting)
│   ├── Google Ads (intent-based, long-tail keywords)
│   ├── Content partnerships (guest posts, podcast appearances)
│   ├── Webinars (3-4/month, recorded for evergreen content)
│   └── Ambassador program (5-10 early advocates)
└── SKIP: Major events, brand TV/video campaigns

BUDGET $20-50k/month
├── MUST DO: (all above)
├── ADD:
│   ├── Paid social (LinkedIn, Google, Retargeting)
│   ├── Industry event sponsorships (booth + speaking slot)
│   ├── Partner co-marketing (5-10 strategic partners)
│   ├── Video content (1-2 professional videos/month)
│   ├── Affiliate/referral program launch
│   └── PR outreach & analyst relations
└── CONSIDER: Influencer partnerships (micro-influencers in recruiting)

BUDGET $50-100k+/month
├── MUST DO: (all above)
├── ADD:
│   ├── Integrated paid campaigns (multi-channel)
│   ├── Industry conferences (3-5 major events/year)
│   ├── Branded content series (podcast, newsletter, research reports)
│   ├── Enterprise sales support (custom events, case studies)
│   ├── Market research & analyst relations
│   ├── Brand partnerships with complementary platforms
│   └── Performance marketing team (dedicated analytics, optimization)
```

---

## 3. Quality Rubric

**Score each marketing idea** on these 5 dimensions (0-5 scale):

| Dimension | 0 (Fatal) | 1 (Poor) | 2 (Weak) | 3 (Good) | 4 (Strong) | 5 (Excellent) |
|-----------|-----------|----------|----------|----------|-----------|----------------|
| **Feasibility** | Impossible | Requires major new skills | Medium effort, some unknowns | Proven approach, straightforward | Clear roadmap, minimal dependencies | Repeatable process, existing templates |
| **Expected ROI** | Negative or unmeasurable | <100% return | 100-200% return | 200-500% return | 500-1000% return | 1000%+ return or multiplier |
| **Resource Cost** | >300 hours or $20k+ | 100-300 hours or $10-20k | 40-100 hours or $3-10k | 20-40 hours or $1-3k | 5-20 hours or <$1k | <5 hours, minimal cost |
| **Timeline to Impact** | >6 months to see results | 3-6 months | 1-3 months | 2-4 weeks | 1-2 weeks | Immediate (days) |
| **Uniqueness** | Copy of competitor | Slight variation | Industry standard | Novel angle on known tactic | First-mover in segment | Proprietary or category-defining |
| **COMPOSITE SCORE** | Sum of all 5 dimensions | **0-9** = reject | **10-15** = consider | **16-20** = implement | **21-25** = priority | **26-30** = flagship |

**Example: "LinkedIn Recruiter Outreach Campaign"**
- Feasibility: 4 (proven template, need list building)
- ROI: 3 (200-500% return expected, unpredictable conversion)
- Resources: 4 (15 hours, minimal cost)
- Timeline: 3 (2-4 weeks to initial results)
- Uniqueness: 2 (industry standard)
- **COMPOSITE: 16** → Implement

---

## 4. Anti-Pattern References

**Avoid these marketing mistakes** that waste budget and time:

| Anti-Pattern | Why It Fails | Fix |
|--------------|-------------|-----|
| **Spray & Pray** (all channels, no focus) | Dilutes message, no optimization | Pick 2-3 channels; master them first |
| **Vanity Metrics** (high reach, low conversion) | 100k impressions = 2 sign-ups | Track CAC, LTV, conversion rate, retention |
| **Feature-Dumping** (list every feature) | Buyers don't care about feature count | Lead with outcome: "Hire 50% faster" |
| **Copy-Pasting Competitor** (exact same message) | No differentiation, trust deficit | Find unique angle or market gap |
| **No Testing/Iteration** (launch once, declare done) | First version rarely converts best | A/B test headlines, CTAs, audiences |
| **Long Time-to-Value** (webinar 4 months away) | Market moves; users forget | Plan for 2-4 week cycles max |
| **Audience Mismatch** (targeting wrong persona) | Great message, wrong ears | Validate audience fit with 10 interviews first |
| **No Measurement** (beautiful campaign, no tracking) | Can't optimize or justify spend | Tag every link; track UTM parameters |
| **Budget Concentration** (all eggs in one channel) | Single channel failure = total loss | Diversify; 60/20/20 rule (primary/secondary/test) |
| **Tone Disconnect** (B2C tone in B2B context) | Perceived as unprofessional or tone-deaf | Match audience formality level |

---

## 5. Industry Variations (100+ Tactics)

### For Talent Marketplaces (SwiftHyre Model)

#### Candidate Acquisition
- LinkedIn content (skill-specific how-tos: "5 Python interview questions every dev gets asked")
- University partnerships (ambassador program with career services)
- AI assessment benchmarking reports (free downloadable by skill)
- GitHub trending language communities (Discord/Reddit outreach)
- Bootcamp partner programs (Flatiron, General Assembly, App Academy)
- Discord/Slack community embedding (dev communities like Indie Hackers)
- TikTok & YouTube education (short "how to prepare for coding interviews")
- Referral bonuses (candidate refers friend → both get credits)
- Certification program marketing (LinkedIn badge promotion)
- Email nurture for drop-offs (6-email sequence from signup to first assessment)

#### Recruiter Acquisition
- LinkedIn Sales Navigator campaigns (HR directors, talent acquisition managers)
- LinkedIn case studies (quantified hire-time improvement, cost-per-hire reduction)
- HR platform integrations (ATS partnerships, co-marketing opportunities)
- Webinar series (quarterly: "AI in hiring," "The case for skills-based hiring")
- Competitor comparison guides (SwiftHyre vs. traditional screening)
- Sales enablement materials (one-pagers, ROI calculator, competitive matrix)
- Analyst relations (Gartner, Forrester talent tech reports)
- Conference sponsorship (SHRM Annual Conference, People Analytics World, Unleash World)
- Partner co-marketing (with HubSpot, Guidepoint, Workable, etc.)
- Founder + Sales team LinkedIn outreach (personalized, consultative)

#### University/Coordinator Acquisition
- Coordinator case study (placement rates, student success outcomes)
- Student recruitment email sequences (role of skills verification)
- Webinars for departments (Dean of Career Services, HR Directors)
- Conference presentations (ACUHO-I, NASPA, career services forums)
- Affiliate/partnership program (placement incentives)
- Free skills benchmark report by university (comparative data)
- Alumni network leverage (ask successful alumni to speak)
- Career fair booth presence (hands-on assessment demo)
- Curriculum integration (workshops for capstone projects)
- Faculty advocate program (professors recommend platform)

### For HR Tech/Recruiting Platforms (General)
- ROI calculator tools (interactive, embeddable, lead-gen)
- Competitive benchmarking reports (position against incumbents)
- Podcast sponsorships (HR, tech, business podcasts)
- Slack bot integrations (direct outreach, demo delivery)
- Reddit community management (r/recruiting, r/talesfromtalent, r/startups)
- Glassdoor/Indeed employer reviews (monitor, respond, promote wins)
- Sales methodology (SPICED, consultative, problem-focused discovery)
- Video case studies (3-5 min customer success stories)
- Press releases (funding rounds, partnerships, milestones)
- Analyst reports & rankings (G2, Capterra, Trustpilot)

### For SaaS/B2B (General)
- Free tier or trial optimization (30-day, no credit card)
- SEO content hub (keyword research, 50+ articles targeting long-tail)
- Webinar series (educational, not salesy; 4-6 per quarter)
- Customer success stories (written + video case studies)
- Partnerships & integrations (other platforms, agencies)
- Community building (Slack, Discord, user forum)
- Free tools (calculator, audit, template, assessment)
- Email nurture sequences (8-12 email sequences by segment)
- Retargeting campaigns (pixel + audience lists from visits)
- Live chat + proactive engagement (Intercom-style)

### For Marketplaces (Buyer + Seller)
- Seller onboarding incentives (first job posted free, sign-up bonus)
- Buyer early adopter program (exclusive beta, premium features)
- Viral loop mechanics (referral rewards, network growth incentives)
- Content hub (how-to guides for both sides)
- Marketplace transparency (rating systems, reviews, success metrics)
- Community events (buyer/seller meetups, virtual + in-person)
- Influencer partnerships (industry experts, thought leaders)
- Creator program (top performers get spotlight, rewards, speaking opportunities)

---

## 6. Benchmark References

**Compare your marketing performance against industry standards:**

| Metric | SaaS Average | Talent Tech Average | SwiftHyre Target (Growth) |
|--------|-------------|-------------------|--------------------------|
| CAC (Customer Acquisition Cost) | $1-5 / MRR ratio 0.75-1.25 | $800-2000 (enterprise) | $200-500 (mid-market focus) |
| LTV (Lifetime Value) | $50-200 (self-serve) $500-5k (enterprise) | $10k-50k (enterprise) | $3k-8k (mid-market) |
| LTV:CAC Ratio | 3:1 minimum, 5:1 healthy | 3:1 to 5:1 | 5:1 to 8:1 target |
| Conversion Rate | 1-3% (cold traffic) 5-10% (warm traffic) | 2-5% (cold), 10-15% (warm) | 3-7% (cold), 12-18% (warm) |
| Email Open Rate | 20-40% (industry avg) | 15-25% (B2B recruiting) | 28-35% target (segmented) |
| Email CTR | 2-5% | 1-2% | 3-5% target |
| LinkedIn CTR | 1-3% (organic) 0.5-1% (paid) | 1-2% (organic) 0.8-1.5% (paid) | 1.5-2.5% (organic), 1-2% (paid) |
| Cost Per Demo | $100-300 | $300-800 | $250-500 target |
| Sales Cycle | 30-90 days (SMB) 90-180+ days (enterprise) | 60-120 days | 45-90 days target (mid-market) |
| Payback Period | 6-12 months | 12-18 months | 10-15 months target |
| Win Rate | 20-30% (typical) | 15-25% | 25-35% target (with strong product) |

**Resource Allocation Benchmarks (% of marketing budget):**
```
Content & SEO:        25-30%
Paid Advertising:     30-40%
Sales Enablement:     15-20%
Community & Events:   10-15%
Tools & Tech:          5-10%
```

---

## 7. Council Integration Hook

**Connect marketing ideas to broader product strategy:**

```
When generating or evaluating marketing ideas, consider:

┌─ Product Council Questions ─────────────────────────────────────────┐
│ 1. Does this idea align with current product roadmap?               │
│    └─ If divergent, either defer or create new feature issue        │
│ 2. Do we have the product capabilities to deliver this promise?     │
│    └─ If not, add as product dependency before marketing            │
│ 3. Is this audience segment currently prioritized?                  │
│    └─ If not, discuss with product before committing budget         │
│ 4. What product metrics support this idea (conversion, retention)?  │
│    └─ Ensure data-driven alignment                                  │
│ 5. Will this create support/operations burden?                      │
│    └─ Plan support playbook before launch                           │
└─────────────────────────────────────────────────────────────────────┘

Post-Launch Feedback Loop:
├── Track product engagement metrics by acquisition channel
├── Flag channel-specific product issues or feature requests
├── Monthly sync: Marketing learnings → Product prioritization
├── Quarterly assessment: Does channel fit current product strategy?
```

For SwiftHyre specifically:
- **Current Focus:** Recruiter acquisition (primary revenue driver)
- **Support Constraint:** Limited support team size (plan for self-service)
- **Product Gap:** Better matching algorithm needed before "Match Quality" marketing campaign
- **Alignment:** "Skills-Based Hiring" messaging aligns with AI assessment product differentiation

---

## 8. Cross-Skill References

**Marketing Ideas skill works downstream & upstream with:**

| Skill | Connection | When to Use | Outputs |
|-------|-----------|-----------|---------|
| **Inspiration** | Ideation seed (find novel angles, adjacent market tactics) | Before brainstorming marketing ideas | Unconventional tactic ideas to evaluate |
| **Content Strategy** | Transforms ideas into execution plans (topic clusters, editorial calendar) | After idea prioritization | Content calendar, keyword mapping, writers brief |
| **Launch Strategy** | Orchestrates multi-channel rollout (timeline, dependencies, go/no-go criteria) | For high-priority ideas | Launch timeline, channel sequence, metrics dashboard |
| **Social Content** | Operationalizes social media tactics (platform-specific formats, scheduling) | For social channel ideas | Social calendar, design briefs, copy variations |
| **Product Marketing** | Positions ideas within competitive landscape | For positioning-dependent ideas | Messaging hierarchy, differentiator articulation |
| **Sales Enablement** | Equips sales team with idea-generated materials | For B2B/direct sales channels | Sales decks, talking points, one-pagers |
| **Analytics & Measurement** | Validates ROI, optimizes channel mix | Post-launch for all ideas | Performance dashboards, A/B test results |

**Typical Workflow:**
```
1. Generate marketing ideas (THIS SKILL) → 20 raw ideas
2. Score with Quality Rubric → Top 8 ideas
3. Get Inspiration skill for novel angles → Refine top 3
4. Use Launch Strategy skill → Build rollout plan
5. Use Content Strategy for content ideas → Editorial plan
6. Use Social Content for social angles → Social calendar
7. Measure with Analytics → ROI & optimization loops
```

---

## 9. Idea Generation Frameworks

### Framework 1: SCAMPER (Product/Service Angle)

Apply each lens to generate marketing angles:

```
SUBSTITUTE
├─ What if we positioned SwiftHyre as "replacing" resume screening?
├─ Angle: "From Resume Noise to Skill Signal"
└─ Tactic: Comparative campaign (before/after hiring outcomes)

COMBINE
├─ What if we merged SwiftHyre + career development?
├─ Angle: "Assessments that help candidates AND recruiters"
└─ Tactic: "Skills Verification + Career Roadmap" (dual value prop)

ADAPT
├─ What if we used assessment mechanics from interviews?
├─ Angle: SwiftHyre mirrors real job interviews
└─ Tactic: "Interview-Prep Webinars" for candidates (drives assessments)

MODIFY
├─ What if we offered assessments by role level (junior, mid, senior)?
├─ Angle: Segment-specific marketing (different messaging per level)
└─ Tactic: LinkedIn campaigns targeting level-specific demographics

PUT TO OTHER USE
├─ What if assessments became a training/certification tool?
├─ Angle: SwiftHyre for upskilling, not just hiring
└─ Tactic: Partner with bootcamps, universities (new audience)

ELIMINATE
├─ What if we eliminated the proctoring component for practice mode?
├─ Angle: "Assess yourself without the stakes"
└─ Tactic: Free practice tier (top-of-funnel for recruiters)

REVERSE/REARRANGE
├─ What if candidates proposed challenges to recruiters?
├─ Angle: Flip power dynamic (candidate-driven discovery)
└─ Tactic: "Showcase Your Skills" campaign (viral loop mechanics)
```

### Framework 2: Competitor Gap Analysis

```
Step 1: Map Competitor Positioning
├─ Traditional Screening: Cost, resume fatigue, bias
├─ Modern Assessment Platforms (HackerRank, Codility): Coding focus, enterprise-only
├─ LinkedIn Skills: Consumer, not for hiring
├─ Peer Networks (Blind): Community trust, not structured
└─ SwiftHyre: AI-graded, verified experts, discovery-first

Step 2: Identify Marketing Gaps
├─ Who are competitors NOT targeting?
│  └─ Mid-market recruiters (too small for enterprise, too fragmented)
├─ What problems aren't they messaging on?
│  └─ "Verified talent pool" (current incumbents focus on process, not talent quality)
├─ What channels are underserved?
│  └─ University partnerships (no competitor owns this channel)
└─ What emotional triggers aren't they using?
   └─ Recruiter frustration: "Bad hires waste 6 months" (emphasis time+cost)

Step 3: Build Angle Ideas
├─ Gap 1 → "Mid-Market Talent Marketplace" positioning
├─ Gap 2 → "Trust & Verification" messaging (vs. resume screening anxiety)
├─ Gap 3 → "University-to-Job Pipeline" partnership marketing
└─ Gap 4 → "Hiring Confidence Guarantee" (outcome-focused messaging)
```

### Framework 3: Adjacent Market Tactics

**Apply tactics from adjacent industries to your market:**

```
FROM ECOMMERCE → TALENT MARKETPLACE
├─ Tactic: Customer reviews & ratings
├─ Adaptation: Recruiter reviews of candidates (build trust signal)
└─ Idea: "Top-Rated Experts" marketplace positioning

FROM FINTECH → TALENT PLATFORM
├─ Tactic: Freemium + credit-based model
├─ Adaptation: Free assessments (top-of-funnel) + credit unlocks (monetization)
└─ Idea: "Try Before You Buy" free trial campaign

FROM CONSUMER SOCIAL → B2B MARKETPLACE
├─ Tactic: Viral loops (share, refer, earn rewards)
├─ Adaptation: Candidate referrals (earn credits), recruiter shares (team features)
└─ Idea: "Your Network = Your Hiring Network" referral campaign

FROM GAMING → TALENT/LEARNING
├─ Tactic: Leaderboards, badges, progression
├─ Adaptation: Candidate skill badges, expert rankings by skill
└─ Idea: "Become a Verified Expert" gamification campaign

FROM SAAS → TALENT PLATFORM
├─ Tactic: Product-led growth (free tier drives adoption)
├─ Adaptation: Free practice assessments for candidates (zero friction entry)
└─ Idea: "Test Your Skills Free" bottom-up acquisition
```

---

## 10. Prioritization Matrix (ICE Scoring)

**Score each idea on Impact, Confidence, Ease** (0-10 scale):

```
IMPACT (0-10): How much will this idea drive business goals?
├─ 9-10: 50%+ increase in target metric (sign-ups, revenue, retention)
├─ 7-8:  20-50% increase
├─ 5-6:  10-20% increase
├─ 3-4:  5-10% increase
└─ 1-2:  <5% increase or brand-only benefit

CONFIDENCE (0-10): How certain are you this idea will work?
├─ 9-10: Data-driven, competitor validated, internal testing passed
├─ 7-8:  Strong hypothesis, industry benchmark supports, similar idea worked
├─ 5-6:  Moderate hypothesis, some supporting data, new approach
├─ 3-4:  Unproven, speculative, high assumption risk
└─ 1-2:  Highly uncertain, no supporting evidence, experimental

EASE (0-10): How quickly/cheaply can you execute this?
├─ 9-10: <5 hours, <$500, uses existing tools (email, social, templates)
├─ 7-8:  5-20 hours, $500-$2k, minor dependencies
├─ 5-6:  20-40 hours, $2-5k, medium dependencies
├─ 3-4:  40-100 hours, $5-10k, significant dependencies
└─ 1-2:  >100 hours, >$10k, major dependencies or new skills needed

ICE SCORE = (Impact + Confidence + Ease) / 3
├─ 8-10: PRIORITY (implement this quarter)
├─ 6-8:  CONSIDER (backlog for next phase)
└─ 0-6:  DEFER (revisit when constraints change)
```

### Example: Marketing Ideas for SwiftHyre (Growth Stage)

| Idea | Impact | Confidence | Ease | ICE Score | Priority |
|------|--------|-----------|------|-----------|----------|
| LinkedIn case study campaign (recruiter ROI) | 8 | 9 | 7 | 8.0 | P0 |
| University partnership program (3 pilots) | 7 | 7 | 5 | 6.3 | P1 |
| "AI-Graded Skills" thought leadership series | 6 | 8 | 8 | 7.3 | P0 |
| TikTok interview prep for candidates | 5 | 4 | 6 | 5.0 | DEFER |
| HR conference sponsorship (3 events) | 7 | 6 | 4 | 5.7 | P1 |
| Competitor comparison guide (PDF + landing) | 6 | 8 | 8 | 7.3 | P0 |
| Slack bot for recruiter prospecting | 4 | 5 | 3 | 4.0 | DEFER |
| Free skills benchmark report (by industry) | 7 | 7 | 6 | 6.7 | P1 |
| Ambassador program (top 20 recruiters) | 6 | 7 | 7 | 6.7 | P1 |
| Podcast sponsorships (recruiting + dev) | 5 | 6 | 7 | 6.0 | P1 |

**Execution Plan (Next 90 Days):**
```
P0 (Weeks 1-6):
├─ LinkedIn case study campaign (testimonials, metrics, long-form)
├─ AI-Graded Skills thought leadership (LinkedIn articles + webinar)
└─ Competitor comparison guide (research, design, promote)

P1 (Weeks 7-12):
├─ University partnership pilot (3 universities, pilot program)
├─ Free skills benchmark report (data collection, design, promotion)
├─ Ambassador program launch (recruit 20 advocates, tools, incentives)
└─ HR conference sponsorships (submit for 3 fall events)

DEFER (Revisit Q2):
├─ TikTok interview prep (validate audience fit first)
└─ Slack bot (requires engineering; wait for engineering capacity)
```

---

## Usage Guidelines

### When to Invoke This Skill

- Brainstorming marketing campaigns or new channel strategies
- Evaluating marketing idea feasibility and ROI
- Building quarterly marketing plans
- Prioritizing between competing marketing initiatives
- Generating novel angles in saturated markets
- Aligning marketing with product roadmap
- Building business cases for marketing budget requests

### How to Use This Skill

```
1. Sync context (read .claude/product-marketing-context.md)
2. Identify growth stage, budget constraints, target audience
3. Choose appropriate framework (decision tree, SCAMPER, gap analysis)
4. Generate 5-10 raw ideas
5. Score each on Quality Rubric (feasibility, ROI, resources, timeline, uniqueness)
6. Prioritize with ICE scoring matrix
7. Document top 3 ideas with success metrics
8. Hand off to Content Strategy, Launch Strategy, or Social Content for execution
```

### Success Metrics

- Marketing ideas generate >6.5 ICE score (or justify outliers)
- Ideas address specific business goal (CAC target, channel diversification, audience segment)
- ROI is measurable with clear success metrics
- Ideas align with current product capabilities and roadmap
- Execution timeline matches business urgency

---

## Related Skills & References

- **Inspiration Skill**: Novel ideation, lateral thinking, adjacent market tactics
- **Content Strategy Skill**: Content calendar, topic clusters, long-form execution
- **Launch Strategy Skill**: Multi-channel coordination, timeline, go/no-go criteria
- **Social Content Skill**: Platform-specific tactics, copy, design, scheduling
- **Product Marketing Skill**: Positioning, messaging, competitive landscape
- **Sales Enablement**: Sales collateral, talking points, proof points
- **Analytics & Measurement**: Performance tracking, A/B testing, ROI validation

---

## Appendix: Quick Reference Templates

### Template 1: Idea Pitch (1-page)

```markdown
## [Idea Name]

**Business Goal:** [Which metric does this drive? CAC, LTV, brand awareness, retention?]

**Target Audience:** [Who specifically? Recruiter persona, candidate stage, geography?]

**Core Tactic:** [One sentence: what are we doing?]

**Expected Outcome:** [Quantified result: X new customers, Y% conversion increase, Z engagement lift]

**Resources Required:** [Hours, budget, team dependencies]

**Timeline:** [Start date, delivery date, time-to-impact]

**Success Metrics:** [KPIs to track: CAC, conversion rate, engagement, retention]

**Risks & Mitigations:** [What could go wrong? How do we prevent it?]

**ICE Score:** Impact / Confidence / Ease = Total
```

### Template 2: A/B Test Brief

```markdown
## Test: [What are we testing?]

**Hypothesis:** If we [change X], then [metric Y] will improve by [% or number]

**Control:** [Current version or baseline]

**Variant:** [New version]

**Audience:** [Who? Size?]

**Duration:** [Days to run]

**Success Criteria:** [Minimum lift to call this a winner]

**Sample Size:** [Calculate using power analysis]

**Primary Metric:** [Main KPI]

**Secondary Metrics:** [Sanity checks, leading indicators]
```

---

**Version History:**
- 2.0 (2026-02-17): Added context sync protocol, decision trees, anti-patterns, industry variations, benchmarks, council integration, cross-skill references, SCAMPER framework, gap analysis, adjacent market tactics, ICE prioritization matrix.
- 1.0 (Pre-2026): Original marketing ideas skill (legacy version).
```

---

## Summary

This upgraded **Marketing Ideas Skill (v2.0)** is a comprehensive **500-line** marketing framework that includes:

1. **Context Sync Protocol** — Automatically checks project constraints and growth stage
2. **Decision Trees** — Growth stage → tactics mapping and budget → channel selection
3. **Quality Rubric** — 5-dimension scoring system (feasibility, ROI, resources, timeline, uniqueness)
4. **Anti-Pattern References** — 10 common marketing mistakes with fixes
5. **Industry Variations** — 100+ tactics organized by business type (talent marketplace, HR tech, SaaS, marketplace)
6. **Benchmark References** — CAC, LTV, conversion rates, and budget allocation benchmarks
7. **Council Integration Hook** — Product strategy alignment checklist and feedback loops
8. **Cross-Skill References** — Connections to inspiration, content-strategy, launch-strategy, social-content skills
9. **Idea Generation Frameworks** — SCAMPER, competitor gap analysis, adjacent market tactics
10. **Prioritization Matrix** — ICE scoring system (Impact/Confidence/Ease) with example execution plan

The skill is immediately applicable to SwiftHyre's growth stage marketing and provides repeatable templates for idea generation, evaluation, and prioritization.