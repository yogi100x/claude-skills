# Product-Marketing Context Skill

**Version:** 2.0  
**Type:** Foundation Skill  
**Audience:** Marketing strategists, PMMs, content creators, AI marketing agents  
**Dependencies:** None (all other marketing skills depend on this)  
**Last Updated:** 2026-02-17

---

## 1. Overview

The **Product-Marketing Context Skill** is the definitive foundation for all marketing operations. It establishes and maintains the authoritative context that every marketing initiative, campaign, asset, and decision must reference. This skill is responsible for:

- **Context Sync Protocol**: Reading, validating, and writing the canonical `.claude/product-marketing-context.md` file
- **Decision Trees**: Guiding users through setup, update, or review workflows
- **Quality Assurance**: Scoring context completeness, specificity, recency, and consistency
- **Anti-Pattern Detection**: Identifying and preventing vague positioning, undefined audience, messaging misalignment
- **Industry-Specific Guidance**: Scaling rubric and questions based on business type
- **Drift Detection**: Monitoring context degradation over time
- **Council Integration**: Sending context for formal marketing reviews and approvals

---

## 2. Context Sync Protocol

### 2.1 File Location and Structure

**Canonical File:** `.claude/product-marketing-context.md`

**Permissions:** 
- Read: All marketing skills, content creators, PMMs
- Write: Only this skill (via explicit user request)
- Audit: Changes tracked with timestamp and reviewer

**Structure:**
```yaml
# Product-Marketing Context
Last Synced: YYYY-MM-DD HH:MM:SS UTC
Last Reviewed By: [name/role]
Confidence Score: 0-100
Drift Detected: [yes/no with explanation]

## Product Definition
### Core Value Proposition
### Target Audience (Primary, Secondary, Tertiary)
### Competitive Position

## Market & Audience
### Market Segment Definition
### Audience Psychographics & Behaviors
### Buying Triggers
### Market Size & Growth

## Messaging Framework
### Core Messages (3-5)
### Supporting Proof Points
### Call-to-Action Framework
### Tone & Voice

## Channel Strategy
### Primary Channels & Cadence
### Audience Journey Mapping
### Content Pillars

## Competitive Intelligence
### Direct Competitors
### Positioning Gaps
### Differentiation Levers

## Goals & Metrics
### 2026 Marketing Objectives
### KPI Definitions
### Success Criteria

## Metadata
- Version: [incremented on substantial changes]
- Status: [active/review/draft]
- Next Review Date: [YYYY-MM-DD]
```

### 2.2 Sync Workflow

**When to sync (triggers):**
1. Product launch or major pivot
2. Quarterly business review (QBR)
3. Market shift detection (new competitor, audience behavior change)
4. Campaign underperformance (>15% variance from goals)
5. Scheduled 30-day review

**Sync Process:**
```
1. VALIDATE: Check current context against quality rubric (Section 3)
2. INTERVIEW: Ask targeted questions for missing/stale information (Section 9)
3. RECONCILE: Consolidate findings into `.claude/product-marketing-context.md`
4. SCORE: Run quality assessment (completeness: 0-100)
5. ALERT: Flag any drift >15 points from previous score
6. DISTRIBUTE: Notify council for review (if Confidence Score < 80)
```

---

## 3. Quality Rubric & Scoring

### 3.1 Five-Dimensional Assessment

Each dimension scores 0-25 points. Total: 0-100.

| Dimension | 25 Points | 18-24 Points | 10-17 Points | 1-9 Points | 0 Points |
|-----------|-----------|-------------|-------------|-----------|----------|
| **Completeness** | All 12 required sections present with 200+ words each; no TODOs | 11 sections; 1-2 sections <150 words | 8-10 sections present; >3 sections incomplete | <8 sections; major gaps (no competitive intel, etc.) | Missing or blank |
| **Specificity** | Quantified targets, named personas, exact positioning statements, defined metrics | Most claims quantified; 1-2 vague references | Mix of specific + vague; unclear audience definitions | Mostly generic language; unsubstantiated claims | All claims generic/aspirational |
| **Recency** | Last synced <30 days; market intel <90 days; competitive data <60 days | Last synced 31-60 days; 1-2 data sources >90 days | Last synced 61-90 days; >3 data sources stale | Last synced >90 days; major data >180 days | No timestamps; unable to verify recency |
| **Consistency** | Messaging aligns with positioning; audience defines value prop; channels match audience; metrics align with goals | 1-2 minor inconsistencies (messaging vs positioning) | 3-5 inconsistencies (channel-audience mismatch, conflicting messages) | >5 contradictions (messaging vs positioning conflict) | Contradictory or incoherent |
| **Actionability** | Clear next actions for each section; campaign brief ready; audience segments are specific enough to target | Most sections actionable; 1-2 sections require clarification | 50% of content actionable; vague audience definitions | <25% actionable; mostly aspirational | No operational guidance |

### 3.2 Scoring Methodology

```
Total Score = (Completeness + Specificity + Recency + Consistency + Actionability) / 5

Interpretation:
90-100: PRODUCTION READY — All marketing work can proceed with confidence
80-89:  REVIEW READY — Minor clarifications needed; schedule sync
70-79:  DRAFT STATUS — Major sections incomplete or stale; requires rework
60-69:  REQUIRES URGENTLY SYNC — Do not proceed with new campaigns
<60:    CRITICAL — Context unusable; halt all marketing; emergency sync required
```

---

## 4. Decision Trees

### 4.1 Initial Setup (First Time)

```
START: Is .claude/product-marketing-context.md present?
├─ NO → Go to 4.1.1 (New Setup)
└─ YES → Is it >30 days old? 
   ├─ YES → Go to 4.2 (Update Workflow)
   └─ NO → Go to 4.3 (Review Workflow)

4.1.1 NEW SETUP WORKFLOW (1-2 hours)
1. Load full 30-question interview (Section 9)
2. Conduct structured interviews with:
   - Product Lead (Sections A, B)
   - Head of Marketing (Sections C, D, E)
   - Sales Lead (Sections B, D)
   - Data/Analytics owner (Section F)
3. Generate initial context draft
4. Score using rubric (target: 75+)
5. Send to council for formal review
6. Publish to .claude/product-marketing-context.md
7. Notify all marketing skills that context is ready
```

### 4.2 Update Workflow (Ongoing)

```
TRIGGER: Is context sync required?
├─ Time-based (30+ days) → Go to A
├─ Event-based (market shift) → Go to B
├─ Performance-based (campaign miss) → Go to C
└─ Human-initiated → Go to D

A. QUARTERLY REVIEW (Scheduled)
   1. Run drift detection (Section 10)
   2. If drift >15 points: interview 5-10 key questions (targeted)
   3. Update 2-3 sections with new data
   4. Re-score (target: maintain 80+)
   5. Document changes in metadata
   6. Publish updates

B. EVENT-BASED SYNC (Market Shift, Competitor)
   1. Identify which sections affected (positioning, competitive, audience?)
   2. Conduct mini-interview (3-5 targeted questions)
   3. Update affected sections only
   4. Flag sections dependent on changes
   5. Alert council if repositioning required

C. PERFORMANCE-BASED SYNC (Campaign Underperformance)
   1. Analyze: Was miss due to wrong audience, messaging, or channel?
   2. Drill into affected context section
   3. Interview relevant stakeholder (1-2 targeted questions)
   4. Update hypothesis and next test
   5. Track learning in metadata

D. HUMAN-INITIATED UPDATE
   1. User specifies what changed (e.g., "New competitor entered", "Pivoting audience")
   2. Identify context sections to refresh
   3. Conduct targeted interview (3-7 questions)
   4. Update and re-score
   5. Confirm approval before publishing
```

### 4.3 Review Workflow (Read-Only)

```
TRIGGER: User wants to reference current context
1. Load .claude/product-marketing-context.md
2. Check Last Synced date
3. If <30 days old AND Confidence Score >80: RETURN context
4. If 31-90 days old: WARN user "Context may be stale; recommend sync"
5. If >90 days old: ALERT "Context is stale; sync required before new work"
6. Never modify without explicit user request + interview
```

---

## 5. Anti-Pattern References

### 5.1 Red Flags (Incomplete or Weak Context)

| Anti-Pattern | Impact | Detection |
|--------------|--------|-----------|
| **Vague Value Prop** | "We help businesses grow" | Contains no quantified benefit, no specificity, no target mentioned |
| **Undefined Primary Audience** | "Our customers are companies" | No firmographics, psychographics, or buying triggers defined |
| **Missing Competitive Position** | "We're different because we care" | No named competitors, no clear positioning statement, no differentiation |
| **Aspirational Metrics** | "We want to increase awareness" | No baseline, target, timeline, or measurement method |
| **Generic Messaging** | "Innovation, quality, customer-first" | Indistinguishable from 100 other companies; no proof points |
| **Misaligned Channel Strategy** | "TikTok content for B2B software" | No explanation of why this channel reaches the defined audience |
| **Single-Persona Assumption** | Only primary persona defined | No secondary/tertiary audiences; narrow perspective |
| **Stale Competitive Data** | "Last updated Q3 2025" | Competitor landscape likely shifted; positioning may be outdated |
| **No Buying Journey** | Only top-of-funnel messaging defined | Can't build mid/bottom-funnel campaigns |
| **Disconnected Metrics** | "KPIs: impressions, revenue, engagement" | No relationship between metrics; unclear what drives what |

### 5.2 Consistency Checks

When reviewing context, flag these misalignments:

```
POSITIONING ↔ MESSAGING
- If positioning says "enterprise-first" but messaging says "for everyone" → Conflict

AUDIENCE ↔ CHANNELS
- If primary audience is "executive procurement teams" but channels are "Instagram" → Mismatch

VALUE PROP ↔ PROOF POINTS
- If value prop is "50% faster" but proof points show "30% improvement" → Contradiction

GOALS ↔ CURRENT REALITY
- If goal is "enterprise market leadership" but current revenue is SMB-focused → Disconnect

MESSAGING ↔ PRODUCT
- If messaging claims "AI-powered" but product is template-based → Dishonest positioning
```

---

## 6. Industry Variations

### 6.1 B2B SaaS (Enterprise Software)

**Context Sections to Emphasize:**
- ROI calculation and TCO comparison (vs competitors)
- Buying committee composition (C-suite, department heads, IT approval)
- Implementation timeline and support requirements
- Compliance/security certifications and audit trails
- Customer reference customers and case studies

**Rubric Adjustments:**
- Specificity: Must name 3+ named competitors with positioning vs each
- Recency: Competitive data <60 days (market moves fast)
- Actionability: Must define exact ICP (firmographics: size, revenue, industry, tech stack)

### 6.2 B2C Consumer (e-commerce, apps, services)

**Context Sections to Emphasize:**
- Lifestyle alignment and emotional triggers
- Social proof (influencers, user-generated content, reviews)
- Virality loops and network effects
- Price sensitivity and willingness-to-pay
- Seasonal patterns and event-driven demand

**Rubric Adjustments:**
- Specificity: Personas must include psychographics (values, aspirations, pain points)
- Recency: Trend data <30 days (consumer behavior shifts quickly)
- Actionability: Channel strategy must specify content format + frequency

### 6.3 B2B Marketplace (two-sided networks)

**Context Sections to Emphasize:**
- Supply-side market definition (sellers, creators, professionals)
- Demand-side market definition (buyers, consumers, enterprises)
- Network effects and liquidity balance
- Unit economics (take rate, lifetime value, acquisition cost)
- Competitive positioning vs substitutes (direct competitors + adjacent solutions)

**Rubric Adjustments:**
- Completeness: Must score BOTH supply AND demand audiences
- Consistency: Messaging must appeal to both sides without contradiction
- Actionability: Channel strategy must address supply and demand separately

### 6.4 Open Source / Developer Tools

**Context Sections to Emphasize:**
- Developer experience and documentation quality
- Community engagement and contribution patterns
- Enterprise support and SLA requirements
- Security/vulnerability disclosure process
- Developer persona (hobbyist vs professional, team lead vs IC)

**Rubric Adjustments:**
- Specificity: Audience must distinguish hobbyist vs professional developers
- Recency: Tech trends <45 days (new frameworks, tools, standards emerge)
- Actionability: Channels must include GitHub, Stack Overflow, technical blogs

---

## 7. Benchmark References

### 7.1 Context Completeness Benchmarks

| Industry | Typical Score (First Sync) | Mature Score | Time to 85+ |
|----------|---------------------------|--------------|-----------|
| B2B SaaS | 62-71 | 88-95 | 45-60 days |
| B2C Consumer | 68-76 | 85-92 | 30-45 days |
| B2B Marketplace | 55-68 | 82-90 | 60-90 days |
| Enterprise Software | 59-73 | 89-97 | 60-75 days |
| DevTools | 64-74 | 86-94 | 45-60 days |

### 7.2 Sync Frequency Benchmarks

| Business Stage | Recommended Sync Frequency | Trigger Threshold |
|----------------|---------------------------|-------------------|
| Pre-Product/MVP | Weekly (rapid iteration) | Any market/product change |
| Early Growth | Bi-weekly | Market/product/competitor change |
| Growth (Series A-B) | Monthly | Planned + event-triggered |
| Mature (Series C+) | Quarterly | Planned + major market event |
| Hypergrowth | Weekly (multiple tracks) | Any product/market/competitive change |

### 7.3 Scoring Distribution

*Healthy marketing organization context scores:*

```
90-100: 15% of contexts
80-89:  50% of contexts
70-79:  25% of contexts
<70:    10% of contexts
```

If your organization scores mostly <80, context maintenance is a blocking issue.

---

## 8. Council Integration Hook

### 8.1 Formal Review Process

**When to send to council:**
- Initial context creation (first draft)
- Major repositioning (audience shift, new market entry)
- Quarterly scheduled review
- Any context score <80

**Council Submission Template:**

```markdown
# Product-Marketing Context Review Request
**Submission Date:** YYYY-MM-DD
**Submitted By:** [name/role]
**Current Confidence Score:** [0-100]
**Previous Score (if update):** [0-100]
**Drift Detected:** [yes/no, specify]

## Summary of Changes
- [Key updates: new audience, repositioning, data refresh, etc.]

## Context Snapshot
[Auto-generate: key sections of .claude/product-marketing-context.md]

## Specific Questions for Council Review
1. [Question 1]
2. [Question 2]
3. [Question 3]

## Recommended Actions
- [Action 1: e.g., "Approve and publish"]
- [Action 2: e.g., "Request clarification on X"]
- [Action 3: e.g., "Schedule competitive review before approval"]

---

Council Review Checklist:
- [ ] Positioning is differentiated and defensible
- [ ] Audience is clearly defined with actionable segments
- [ ] Messaging aligns with positioning and resonates with audience
- [ ] Competitive analysis is accurate and current
- [ ] Metrics are achievable and aligned with goals
- [ ] Channel strategy matches audience distribution
- [ ] No internal contradictions detected
- [ ] Ready for publication/distribution

**Council Decision:** [ ] APPROVED | [ ] APPROVED WITH CONDITIONS | [ ] REQUEST CHANGES | [ ] REJECT
```

### 8.2 Council Review Cadence

```
INITIAL SETUP: 1-week turnaround expected
MAJOR UPDATE: 3-5 day turnaround
QUARTERLY REVIEW: 2-week turnaround (can be batched)
EMERGENCY/EVENT-BASED: 24-hour turnaround
```

---

## 9. Context Interview Guide (30 Questions)

### Section A: Product Definition (5 questions)

1. **What is the core problem your product solves?** (Not features; the underlying pain)
2. **Who has this problem most acutely?** (Specific role, industry, company type)
3. **How do customers solve this problem today?** (Current alternatives, workarounds, status quo)
4. **What is the quantified outcome your product delivers?** (e.g., "reduces time by 40%", "saves $500k/year")
5. **What must be true about the product for the value prop to land?** (Core features, performance thresholds, integrations)

### Section B: Primary Audience Definition (5 questions)

6. **Who is the primary economic buyer?** (Title, function, who controls budget)
7. **Who is the primary user?** (May differ from buyer; their daily job, frustrations)
8. **What are 3-5 psychographic characteristics of your ideal customer?** (Values, aspirations, fears, motivations)
9. **What does a typical buying journey look like for this audience?** (Discovery → evaluation → purchase; timeline, decision criteria)
10. **What are the buying triggers that prompt this audience to search for a solution?** (Business event, pain threshold, fiscal cycle, new initiative)

### Section C: Secondary & Tertiary Audiences (3 questions)

11. **Who is the secondary audience?** (Different use case, company size, or industry; define similarly to Q6-9)
12. **Who is the tertiary audience?** (Emerging segment, expansion opportunity; define)
13. **Which audience segment has the highest lifetime value or growth potential?** (2026 priority)

### Section D: Competitive Positioning (4 questions)

14. **Who are your top 3-5 direct competitors?** (Named; brief 1-2 sentence comparison for each)
15. **For each competitor, what is their primary positioning?** (Strength, weakness, price tier)
16. **What is your differentiation vs each?** (What can you claim uniquely or credibly)
17. **Are there 2-3 "unknown" competitors (indirect substitutes)?** (Excel instead of software, freelancer instead of agency, etc.)

### Section E: Messaging & Positioning (4 questions)

18. **What is your core positioning statement?** (For [audience], [product] is the [category] that [unique value]; vs [competitor], [differentiation])
19. **What are 3-5 core messages that support the positioning?** (Each should be a complete thought, not a tagline)
20. **What are the top 3 proof points that support each message?** (Case study, stat, customer quote, demo result)
21. **What is the primary call-to-action for each audience?** (e.g., "Schedule demo", "Start free trial", "Read case study")

### Section F: Market & Goals (4 questions)

22. **What is the addressable market size (TAM)?** (Dollar value or number of potential customers)
23. **What is your 2026 marketing objective?** (Revenue target, customer acquisition goal, market share, awareness reach)
24. **What are the top 3 KPIs that indicate progress toward that objective?** (Specific metrics with targets; e.g., "MQLs: 500/month", "CAC: <$1,500")
25. **What would count as a marketing win by end of 2026?** (Qualitative + quantitative: e.g., "Top-3 in competitive set + 40% YoY growth")

---

## 10. Context Drift Detection Methodology

### 10.1 Automated Drift Signals

Run these checks **monthly**:

```
DRIFT CHECK SCHEDULE:
Every 30 days: Run 10.2 (Automated Signals)
Every 60 days: Run 10.3 (Interview-Based Assessment)
Every 90 days: Run 10.4 (Full Audit + Council Review)
```

### 10.2 Automated Signals (No Interview Needed)

| Signal | Detection | Action |
|--------|-----------|--------|
| **Stale timestamps** | Last synced >90 days ago | WARN: "Context refresh recommended" |
| **Confidence score decay** | Score dropped >10 points since last check | ALERT: "Schedule sync interview" |
| **Market event** | New competitor announced, major market analyst report | FLAG: "Event-based sync trigger" |
| **Campaign performance miss** | Actual results vs predicted >20% variance | ALERT: "Validate audience/messaging assumptions" |
| **Product change** | Feature release, pricing change, new product line | FLAG: "Positioning may need update" |
| **Audience shift** | Customer acquisition from unexpected segment | ALERT: "Audience definition may be outdated" |

### 10.3 Interview-Based Assessment (30 Min)

Ask 5 rapid-fire validation questions:

1. **Has the primary audience or their pain changed since we last synced?**
2. **Are there new competitors or has an existing competitor repositioned significantly?**
3. **Has our product roadmap shifted the value prop we communicate?**
4. **Are we reaching the audience we intended through our current channels?**
5. **Are there business events (funding, expansion, new market entry) that shift our priorities?**

**Scoring:**
- 0-1 "no" answers: No drift; continue as-is
- 2-3 "no" answers: Minor drift; schedule update within 30 days
- 4-5 "no" answers: Significant drift; immediate sync required

### 10.4 Full Audit Checklist (Quarterly)

Run the 5-dimensional rubric (Section 3) on all sections. Compare to previous quarter:

```
DRIFT CALCULATION:
Current Score - Previous Score = Drift Amount

If Drift > +10: Context improving (continues current path)
If Drift 0-10: Context stable (maintain, review on schedule)
If Drift -10 to 0: Context slowly degrading (minor update needed)
If Drift < -10: Significant drift (emergency sync required)
```

### 10.5 Drift Recovery Protocol

**When drift is detected:**

```
1. IDENTIFY which sections drifted most (use rubric breakdown)
2. PRIORITIZE top 2-3 sections by impact (positioning > audience > channels)
3. INTERVIEW stakeholders on drifted sections only (30-60 min targeted)
4. UPDATE affected sections with new data/insights
5. RE-SCORE full context (target: return to 80+)
6. DOCUMENT changes in metadata (what drifted, why, actions taken)
7. COMMUNICATE updates to council + all marketing skills
```

---

## 11. Cross-Skill References

This skill is the **FOUNDATION** for all marketing skills. All downstream marketing work depends on authoritative context.

### 11.1 Dependent Skills (Must Load This First)

```
If you are using:
├─ Messaging & Copy skill → Loads context for message library
├─ Campaign Strategy skill → Loads context for audience segments
├─ Content Strategy skill → Loads context for content pillars + audience journey
├─ Demand Gen skill → Loads context for audience + channels + funnel
├─ Brand & Positioning skill → Loads context for brand architecture
├─ Competitive Intelligence skill → Loads context for competitive landscape
├─ Persona Development skill → Loads context for audience definitions
├─ Channel Optimization skill → Loads context for channel strategy
└─ Analytics & Measurement skill → Loads context for metric definitions + goal alignment

When ANY marketing skill is invoked:
1. First, this skill loads current context from .claude/product-marketing-context.md
2. Check if context Confidence Score >80
3. If <80: WARN "Context needs sync before proceeding"
4. If >90 days old: ALERT "Context is stale; recommend refresh"
5. Load specific sections relevant to downstream skill
6. Pass context as immutable reference data
```

### 11.2 Integration Points

```markdown
MESSAGING & COPY SKILL
Loads: Core messages, proof points, tone/voice, value prop
Output: Message library, email templates, ad copy
Context Used For: Ensuring all copy aligns with positioning

CAMPAIGN STRATEGY SKILL
Loads: Audience segments, goals/KPIs, channel strategy, competitive position
Output: Campaign brief, channel mix, target metrics
Context Used For: Defining campaign scope, audience targeting, success criteria

CONTENT STRATEGY SKILL
Loads: Content pillars, audience journey, target audience, value prop
Output: Editorial calendar, content types, distribution plan
Context Used For: Prioritizing topics, matching content to buyer stage

PERSONA DEVELOPMENT SKILL
Loads: Primary/secondary/tertiary audience definitions, psychographics
Output: Detailed personas with motivations, pain points, buying journey
Context Used For: Grounding personas in actual market research
```

---

## 12. Quick Reference: Using This Skill

### 12.1 When to Invoke Product-Marketing-Context

**DO INVOKE if you are:**
- Starting new marketing work (strategy, campaign, content, etc.)
- Confused about positioning, audience, or messaging
- Making decisions that affect brand, positioning, or target audience
- Need authoritative definitions of audience, value prop, or competitive position
- Syncing context (setup, update, or drift detection)

**DON'T INVOKE if you are:**
- Writing a single blog post (load context via Messaging skill instead)
- Executing a previously-approved tactic (reference existing campaign brief)
- Doing routine optimization (A/B testing, channel optimization)

### 12.2 Output Expectations

**When you invoke this skill, you will receive:**
- Canonical `.claude/product-marketing-context.md` content (read-only or flagged for update)
- Context quality score + drift assessment
- Recommendations for next actions (proceed as-is / sync / council review)
- Specific sections relevant to your downstream task

---

## 13. Metadata & Versioning

### 13.1 Context Versioning

```
Version 1.0: Initial context setup
Version 1.1: Minor updates (added tertiary persona, updated competitor data)
Version 1.2: Channel strategy refresh, new proof points added
Version 2.0: Major repositioning (new audience OR new value prop)
Version 2.1: Secondary audience added
Version 3.0: Market entry (new market, new business model)
```

### 13.2 Change Log Template (append to context file)

```markdown
## Change Log

**[Date] - Version X.Y - [Type: Minor Update | Major Update | Drift Recovery]**
- Changed: [What changed]
- Reason: [Why it changed]
- Impact: [What downstream marketing work is affected]
- Reviewed By: [Name/Council]
- Confidence Score: [Old] → [New]

---
```

---

## 14. Troubleshooting & FAQ

### Q: Context score is 62, but we need to launch a campaign in 2 weeks. What do we do?

**A:** Score <70 means context is weak but not unusable. Proceed with caution:
1. Identify which sections scored lowest (use rubric breakdown)
2. Validate only the sections critical to your campaign (audience, messaging, channels)
3. Do a 1-hour targeted sync on those sections only
4. Tag campaign with "Context validation completed on [date]"
5. Plan full context sync within 30 days post-launch
6. Track campaign performance to identify context gaps

### Q: My audience changed dramatically. How do I update context without losing previous definitions?

**A:** Keep both in the file as historical reference:

```markdown
## Primary Audience
### Current (Effective 2026-02-17)
[New definition]

### Previous (Through 2026-02-16)
[Old definition]
**Why Changed:** [Reason]
```

Then update dependent marketing work (personas, messaging, channels) with new audience.

### Q: How do I know if a context update requires council approval?

**A:** Council approval required if:
- Confidence score changes >10 points
- Positioning or audience definition changes materially
- Any score <80 (automatic council review before publishing)
- Competitive repositioning (new competitor, major shift)

Optional council approval if:
- Proof points or proof points are refreshed
- Channel strategy tweaked (no audience change)
- Market size updated (no positioning change)

### Q: Can I have multiple contexts (one per product line / market segment)?

**A:** Yes, but with structure:

```
.claude/product-marketing-context.md          [MASTER: Corp positioning]
.claude/product-marketing-context-product-a.md [LINE: Separate audience]
.claude/product-marketing-context-product-b.md [LINE: Separate positioning]
```

**Rule:** Master context must define relationships between product lines. Each line context must reference master for shared values, brand, tone.

---

## 15. Checklist: Is Context Ready?

Before launching any marketing campaign, scorecard:

- [ ] Context file exists and last synced <60 days ago
- [ ] Confidence score >75
- [ ] No major drift detected (Section 10 check completed)
- [ ] All 5 rubric dimensions scored >15
- [ ] Primary + secondary audience clearly defined with firmographics + psychographics
- [ ] Positioning statement is differentiated and defensible
- [ ] Competitive analysis includes 3+ named competitors with comparison
- [ ] Core messages (3-5) align with positioning + proof points
- [ ] Channel strategy matches audience distribution
- [ ] Goals and KPIs are specific, measurable, and achievable
- [ ] No internal contradictions detected (Section 5.2 consistency checks passed)
- [ ] Council has reviewed if score <80 or major changes made
- [ ] All dependent marketing skills have access to updated context

**If all checks ✓, proceed. If any unchecked, schedule sync before launch.**

---

## 16. Summary: Skill Workflow

```
┌─ User invokes skill ─────────────────────────────┐
│                                                  │
├─ Is .claude/product-marketing-context.md ready? │
│  ├─ NO (first time)      → Run 4.1.1 (Setup)    │
│  ├─ STALE (>90 days)     → Run 4.2 (Update)     │
│  └─ YES (fresh)          → Run 4.3 (Review)     │
│                                                  │
├─ Load context into memory                       │
├─ Check timestamp + confidence score             │
├─ Run drift detection (if update/review)         │
├─ Score quality using rubric (Section 3)         │
│                                                  │
├─ IF Confidence >80:                             │
│  └─ Return context as AUTHORITATIVE reference   │
│     for downstream skill usage                  │
│                                                  │
├─ IF Confidence 70-79:                           │
│  └─ WARN: Context acceptable but stale; suggest │
│     refresh before major campaigns              │
│                                                  │
├─ IF Confidence <70:                             │
│  ├─ ALERT: Context insufficient                │
│  ├─ Recommend drift recovery (Section 10.5)    │
│  └─ Do not approve for high-stakes work        │
│                                                  │
└─ Return to user with recommendations ───────────┘
```

---

**End of Product-Marketing Context Skill**

---

*This skill is maintained as the canonical foundation for all SwiftHyre marketing work. For updates, questions, or drift detection, contact your Product-Marketing Council.*
```