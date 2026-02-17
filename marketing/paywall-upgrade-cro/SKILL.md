# Paywall & Free-to-Paid Conversion Optimization

Structured decision framework for designing, evaluating, and optimizing upgrade paywalls that maximize conversion while minimizing churn and friction. Includes context sync protocols, decision trees, quality rubrics, anti-patterns, industry variations, benchmarks, council integration, and 10 proven patterns with worked examples.

---

## Context Sync Protocol

**Before any paywall design work, load the following context documents:**

### 1. Product-Marketing Context (`.claude/product-marketing-context.md`)

Sync these variables into your mental model:

```
- VALUE_PROPOSITIONS = [list of primary value props being gated]
- TARGET_SEGMENT = [free, freemium, trial, or hybrid user cohorts]
- COMPETITOR_PAYWALLS = [known competitor paywall patterns + conversion rates]
- POSITIONING_STRATEGY = [premium, accessible, or value-leader]
- MESSAGING_FRAMEWORK = [emotional triggers, credibility anchors, urgency language]
- CONVERSION_GOALS = [target %: e.g., 5% free-to-paid, 35% trial-to-paid]
```

**Sync action:** If these variables are NOT explicitly available, prompt the user:
> "To design this paywall effectively, I need to understand: (1) What specific value are we gating? (2) Who is the target free user? (3) What's our positioning — premium, accessible, or value-leader? (4) What conversion rate would success look like?"

### 2. Finance Context (`.claude/finance-context.md`)

Sync these economics into your paywall math:

```
- UNIT_ECONOMICS = [CAC, LTV, payback_period, target_margin]
- PRICING_TIERS = [free, starter, pro, enterprise with annual/monthly variants]
- CREDIT_COSTS = [cost per credit, credit budget per user segment]
- CHURN_RATES = [baseline monthly churn, paywall-triggered churn risk]
- TARGET_ARPU = [average revenue per user by segment]
- PAYWALL_LIFT_TOLERANCE = [acceptable lift in churn to achieve 1% conversion lift]
```

**Sync action:** If finance context is missing, route to `council-finance` skill:
> "Running a financial review to align this paywall with unit economics and pricing model..."
> **Then invoke:** `council-finance quick [paywall design]`

---

## Decision Tree: Paywall Type Selection

**Start here.** Answer each question to determine paywall architecture:

```
┌─ Free Model → Will you ever charge this user cohort?
│   ├─ NO  → Freemium Strategy (go to: Freemium Decision Tree)
│   └─ YES → (continue below)
│
├─ Hard Paywall? (feature completely blocked until payment)
│   ├─ YES → Hard Paywall Branch (highest friction, highest conversion, highest churn risk)
│   └─ NO  → (continue below)
│
├─ Soft Paywall? (feature accessible but limited; upgrade for unlimited)
│   ├─ YES → Soft Paywall Branch (medium friction, medium conversion, best retention)
│   └─ NO  → (continue below)
│
├─ Metered Paywall? (quota system; e.g., 10 free requests/month)
│   ├─ YES → Metered Paywall Branch (quantified friction, accurate conversion tracking)
│   └─ NO  → (continue below)
│
└─ Feature-Gated? (specific premium features behind gate; others free)
    ├─ YES → Feature-Gated Branch (surgical, highest precision)
    └─ NO  → Hybrid Model (combine 2+ of above)
```

### Hard Paywall Decision Tree

**When to use:** High-value features (e.g., export, API access, white-label), B2B SaaS, B2C premium tiers.

```
Is this a trial paywall (time-limited free access)?
├─ YES: Trial Paywall Pattern
│   ├─ Trial duration: 7d, 14d, 30d? (default: 14d for B2B, 7d for B2C)
│   ├─ Grace period after trial ends? (default: 3d reminder → hard gate)
│   ├─ Show pricing before trial or after? (default: after, when emotionally invested)
│   └─ Allow payment mid-trial to extend? (anti-pattern: confuses users)
│
└─ NO: Immediate Payment Gate
    ├─ First-time UX: Show value preview before gate?
    │   ├─ YES: "Unlock to try" (recommended, ~10-15% conversion lift)
    │   └─ NO: Direct gate (acceptable for obvious premium features)
    │
    ├─ Freemium trial before hard gate? (2-week micro-trial)
    │   ├─ YES: Soft→Hard paywall progression (higher conversion, ~7-10% lift)
    │   └─ NO: Direct hard gate (highest friction, 2-3% baseline)
    │
    ├─ Social proof on gate? (testimonials, user count, ROI proof)
    │   ├─ YES: +3-5% conversion lift
    │   └─ NO: Missed opportunity
    │
    └─ Money-back guarantee or risk reversal?
        ├─ YES: +2-4% conversion lift for B2B, +1-2% for B2C
        └─ NO: Acceptable for obvious premium features
```

### Soft Paywall Decision Tree

**When to use:** Feature discovery, secondary features, freemium models, retention-first strategy.

```
What's the friction level?
├─ No friction (feature fully accessible):
│   ├─ Use: Analytics paywalls (show-but-don't-limit), tracking paywalls
│   └─ Expected conversion: 0.5-2%
│
├─ Low friction (suggest upgrade, don't block):
│   ├─ Modal/toast with "Upgrade to use this" CTA
│   ├─ Allow user to dismiss and continue free
│   ├─ Usage still counts toward quota
│   └─ Expected conversion: 2-5%
│
├─ Medium friction (quota consumed but feature still works):
│   ├─ "You've used X of Y monthly exports"
│   ├─ Export succeeds but marked with watermark/limitation
│   ├─ Upgrade modal appears post-action
│   └─ Expected conversion: 5-10%
│
└─ High friction (quota exceeded, feature degrades or stops):
    ├─ "Export limit reached. Upgrade for unlimited."
    ├─ Feature returns error or noop
    ├─ Immediate upgrade suggestion
    └─ Expected conversion: 10-15% (approaches hard paywall)
```

### Metered Paywall Decision Tree

**When to use:** Usage-based pricing, API platforms, credit-based systems, transparent quotas.

```
Define the quota:
├─ Per-user monthly quota? (default: 10, 50, 100, 500, 10k)
│   └─ Avoid: 1 or 2 (friction too high → abandonment)
│
├─ Rolling window (calendar month, week, day)?
│   ├─ Calendar month: Standard, predictable reset
│   ├─ Rolling 30 days: Fair, but confusing
│   └─ Recommendation: Calendar month (lowest friction)
│
├─ Quota display strategy:
│   ├─ "9 of 10 remaining this month" (transparency, urgency)
│   ├─ "Used 90% of your limit" (framing as high usage, not scarcity)
│   ├─ Hidden quota, only show at 80% (discovery moment, natural upgrade trigger)
│   └─ Recommendation: Show at 70-80% to maximize conversion
│
├─ Overflow behavior (what happens at quota limit)?
│   ├─ Hard stop (no overflow, immediate "upgrade" modal)
│   ├─ Soft stop (feature works but warns "you're over limit")
│   ├─ Paid overflow (charge per-unit overflow, e.g., $0.10/extra request)
│   └─ Recommendation: Hard stop for freemium, soft stop for trials
│
└─ Quota reset timing:
    ├─ Same day each month (calendar reset, most transparent)
    ├─ On upgrade day anniversary (renewal-aligned, less transparent)
    └─ Recommendation: Calendar reset (builds urgency, simpler communication)
```

### Freemium Decision Tree

**When to use:** High-volume free user base, network effects, viral growth, B2C SaaS.

```
Free tier scope:
├─ Feature subset (e.g., basic CRM free, advanced features paid)?
│   ├─ YES: Feature-gated freemium
│   ├─ Select 2-3 core features: Core value even free users understand
│   ├─ Avoid: >50% of features free (dilutes paid positioning)
│   └─ Sweet spot: 30-40% of features free
│
├─ Usage quota (e.g., 500 contacts free, unlimited paid)?
│   ├─ YES: Metered freemium
│   ├─ Set quota at "aha moment threshold" (when user gets value)
│   ├─ Typical quota: 1-3 months of light usage = quota hit
│   └─ Too low quota → early churn; too high quota → no upgrade motivation
│
├─ Time-based (e.g., 14 days free then gate)?
│   ├─ NO: Avoid. Creates false urgency; poor conversion.
│   └─ Alternative: Metered quota after trial expires (better conversion)
│
├─ Storage/capacity limit (e.g., 1GB free)?
│   ├─ YES: Common pattern for cloud storage, design tools
│   ├─ Soft limit: Warn at 80%, allow overflow with friction
│   ├─ Hard limit: Block at 100%, immediate upgrade
│   └─ Recommendation: Soft limit for retention, hard limit for monetization
│
└─ Team/collaboration limit (e.g., 3 team members free)?
    ├─ YES: Strong pattern for B2B SaaS
    ├─ Quota: 2-5 team members free (discovery cohort reaches "needs collaboration")
    ├─ Upgrade message: "Invite your team (requires paid plan)"
    └─ Conversion lift: +5-8% vs single-user quota
```

---

## Quality Rubric: Paywall Evaluation (Scoring Framework)

**Rate each paywall design on 5 dimensions. Total score 0-100. Minimum acceptable: 60/100.**

### 1. Value Demonstration (0-20 points)

**Question:** Does the paywall clearly communicate why the gated feature is worth paying for?

| Score | Criteria |
|-------|----------|
| **0** | No value prop shown. Gate appears arbitrary ("This feature requires upgrade") |
| **5** | Generic value prop ("Unlock advanced features") without context |
| **10** | Specific value shown ("Export 10,000 records instead of 100") but no ROI angle |
| **15** | Quantified value with ROI hint ("Save 5 hours/week on reporting") |
| **20** | **Multi-angle value proof:** Quantified benefit + social proof + money-back guarantee + testimonial with specific outcome |

**Checklist:**
- [ ] Value prop explains what you GET (not what you LOSE by waiting)
- [ ] Number: specific benefit quantified (not "better", "faster", "more")
- [ ] ROI: ties benefit to user's stated goal (from interview, product events)
- [ ] Social proof: "1,000+ teams upgraded" or customer testimonial
- [ ] Risk reversal: "30-day money-back guarantee" or "3-day trial"

### 2. Urgency & Friction Balance (0-20 points)

**Question:** Does the paywall create enough urgency to drive conversion without feeling manipulative or causing rage-quit?

| Score | Criteria |
|-------|----------|
| **0** | No urgency signals; user can ignore gate indefinitely. Or: extreme dark patterns (fake countdown, fake scarcity) |
| **5** | Weak urgency ("Upgrade anytime") or obvious manipulation (users smell fake limits) |
| **10** | Legitimate scarcity or time-limit ("Trial ends in 3 days") but no personalization |
| **15** | Contextual urgency ("Your free quota resets in 2 days") + clear exit (dismiss, skip) |
| **20** | **Optimized friction:** Time-bound urgency (trial ending, quota resetting) + immediate value unlock path + guilt-free "maybe later" option |

**Checklist:**
- [ ] Urgency is time-based (trial ending, quota resetting) NOT artificial
- [ ] User can dismiss paywall without consequence (no spam follow-ups)
- [ ] "Maybe later" option positions as "not now" (not rejection)
- [ ] CTA buttons: primary (upgrade) vs secondary (dismiss) both visible
- [ ] No infinite loops; user sees paywall max 2-3 times before respecting dismissal

### 3. Conversion Friction (0-20 points)

**Question:** Is the upgrade path optimized for minimal friction?

| Score | Criteria |
|-------|----------|
| **0** | Broken upgrade flow (paywall links to wrong page, payment fails, requires 10+ form fields) |
| **5** | 5+ steps required (choose plan → enter email → payment details → billing address → confirm) |
| **10** | 3-4 steps (plan selection → payment → confirm) |
| **15** | 2 steps (one-click payment after plan selection) + pre-filled email |
| **20** | **Optimized friction:** Plan pre-selected (default to recommended tier) + one-click payment (Apple Pay, Google Pay, stored card) + instantaneous activation |

**Checklist:**
- [ ] Plan pre-selected (default: most popular tier, not cheapest)
- [ ] Payment stored (Apple Pay, Google Pay, or saved card populated)
- [ ] Form auto-fills known data (email, country, company if B2B)
- [ ] Checkout <2 minutes on mobile
- [ ] Immediate feature unlock post-payment (no "processing" screens)
- [ ] Recovery: If payment fails, 1-click retry + help text

### 4. Social Proof & Credibility (0-20 points)

**Question:** Does the paywall build trust and reduce perceived risk?

| Score | Criteria |
|-------|----------|
| **0** | No social proof. User has no idea if this tool is legit or if others use it |
| **5** | Generic badge ("Used by 10,000+ teams") without source or verification |
| **10** | Named companies or user count + customer testimonial, but no specificity |
| **15** | Named companies (recognizable logos) + specific testimonial with measurable outcome + money-back guarantee |
| **20** | **Multi-layer credibility:** Named companies + 2-3 specific testimonials with metrics ("Saved $50k/year") + 30-day money-back + trust badge (SOC2) + publication mentions |

**Checklist:**
- [ ] Social proof on paywall itself (not hidden behind link)
- [ ] Customer logos or "used by X companies" visible
- [ ] Testimonials include: name + company + specific outcome (not generic praise)
- [ ] Money-back guarantee explicitly stated on paywall
- [ ] Trust badges: SOC2, ISO, payments secure (Stripe, etc.)
- [ ] Publication mention or award ("Recommended by TechCrunch, ProductHunt")

### 5. Fallback Path & UX Coherence (0-20 points)

**Question:** Does the paywall fit the user's mental model? Can they recover if payment fails?

| Score | Criteria |
|-------|----------|
| **0** | No fallback; user stuck at paywall forever. Or: UI is misaligned (paywall contradicts product positioning) |
| **5** | Fallback exists but is hard to find ("Contact support") |
| **10** | Clear "Maybe later" button + paywall doesn't reappear for 30 days |
| **15** | Multiple fallbacks (maybe later, contact sales for enterprise, upgrade other features) + paywall positioning matches brand tone |
| **20** | **Seamless coherence:** Guilt-free "Maybe later" (respects user choice) + personalized "Try these features for free" suggestions + payment failure recovery + paywall UI/tone aligned with product |

**Checklist:**
- [ ] "Maybe later" is equal visual weight to "Upgrade" (not tiny link)
- [ ] Paywall respects dismissal; doesn't reappear in same session
- [ ] If payment fails: 1-click retry + help text + contact sales fallback
- [ ] UI tone matches product (professional = formal; playful product = casual paywall)
- [ ] Paywall doesn't feel like "product is broken until payment" (maintains value narrative)
- [ ] Personalized next-step ("Here are 3 free features to explore")

---

## Paywall Pattern Catalog: 10 Proven Patterns

**Each pattern includes:** trigger, messaging framework, conversion range, best use case, anti-patterns.

### Pattern 1: Feature-Gate Paywall (Hard)

**Trigger:** User attempts to use premium feature (export, API, white-label, analytics).

**Messaging Framework:**
```
Headline: "[Feature Name] is available on [Plan Name]+"
Subheading: "Unlock [specific benefit] and 10+ other premium features"
CTA: "Upgrade now" | Fallback: "Maybe later"
Social proof: "[Logo][Logo][Logo] + 5,000+ teams"
```

**Conversion Range:** 8-15%

**Best for:** B2B SaaS with clear feature hierarchy. Example: Zapier (integrations behind paywall), Figma (team collaboration).

**Anti-patterns:**
- Showing feature exists but is completely blocked (creates resentment)
- Gate appears after user invested time (too late, will churn)
- No "free alternative" option (users feel trapped)

**Optimal timing:** Trigger after aha moment (user has seen value) but before frustration (e.g., 3rd export).

---

### Pattern 2: Quota-Exhaustion Paywall (Soft/Metered)

**Trigger:** User reaches free quota limit (e.g., 10 of 10 exports used).

**Messaging Framework:**
```
Headline: "You've used all 10 free exports this month"
Subheading: "Upgrade to unlimited exports + advanced features"
CTA: "Upgrade now" | Fallback: "Quota resets on Mar 1"
Urgency: "Only 2 days until your quota resets"
```

**Conversion Range:** 10-18%

**Best for:** Usage-based freemium (Slack, Canva, Stripe). Creates natural upgrade trigger without feeling arbitrary.

**Anti-patterns:**
- Quota too low (1-2 items) → users abandon immediately, never convert
- Quota too high (1000 items) → user never hits limit, never sees paywall
- No countdown to reset → urgency lost
- Allow unlimited overflow → monetization fails

**Optimal quota:** 1-3 months of natural light usage. Test via cohort analysis.

---

### Pattern 3: Trial Expiration Paywall (Hard)

**Trigger:** Free trial ends (time-based). Day 3 reminder, day 6 warning, day 7 gate.

**Messaging Framework:**
```
Day 3 reminder:
  "Your trial expires in 4 days | [Explore more] [Upgrade now]"

Day 6 warning:
  "Your trial expires TOMORROW"
  "Complete your setup: [config task] [secure payment]"

Day 7 gate:
  "Trial ended. Upgrade to continue using [product]"
  "[Price]/month | [Price]/year (save 30%)"
  "Questions? [Chat] [Schedule demo]"
```

**Conversion Range:** 5-12% (varies by trial length: 14d trial ~10%, 30d trial ~7%)

**Best for:** B2B SaaS with 14-30 day trials. Example: Stripe, HubSpot, Monday.com.

**Anti-patterns:**
- Trial too short (<7 days) → user hasn't reached aha moment
- Trial too long (>30 days) → user gets comfortable free, won't upgrade
- No mid-trial engagement → user forgets about trial, just leaves
- Trial paywall appears without warning → rage quit

**Optimal trial length:** 14 days for B2B, 7 days for B2C.

---

### Pattern 4: Team Collaboration Gate (Soft)

**Trigger:** User attempts to invite 4th team member or enable collaboration.

**Messaging Framework:**
```
Headline: "Invite your team (available on paid plans)"
Subheading: "Collaborate with up to 50 team members on [Plan]"
CTA: "Upgrade to invite team" | Fallback: "Invite 1 person free"
Social proof: "1,000+ teams collaborate on [product]"
```

**Conversion Range:** 12-20%

**Best for:** B2B SaaS with multi-user workflows (project management, design, analytics). Network effect → once team member is invited, migration cost increases.

**Anti-patterns:**
- Gate at 1-2 members (too low, kills adoption)
- No "limited collaboration" free option (feels mean)
- Paywall requires payment before member is invited (breaks UX flow)

**Optimal team size:** 3 members free (discovery cohort), paid plan 5+ members (drives upgrade at natural friction point).

---

### Pattern 5: Data Export / Integration Paywall (Hard)

**Trigger:** User attempts to export data, use API, or integrate with external tool.

**Messaging Framework:**
```
Headline: "Export & integrations available on [Premium Plan]+"
Subheading: "Connect to Slack, Zapier, or export raw data"
CTA: "Unlock integrations" | Fallback: "Request manual export"
Trust: "SOC2 certified | Enterprise-grade security"
```

**Conversion Range:** 6-12%

**Best for:** SaaS with sticky data lock-in (CRM, analytics, database tools). Creates high switching cost for upgrades. Example: Airtable (integrations), Stripe (API access).

**Anti-patterns:**
- Lock-in feels punitive → users resent not being able to leave
- No export option even with manual workaround → breach of trust
- High pricing tier for data access → users switch to free competitors
- API limited but not transparent (users waste time debugging)

**Optimal positioning:** Frame as "advanced features" not "leaving the platform", offer transparent API limits (1000 calls/month free, unlimited on paid).

---

### Pattern 6: Analytics & Insights Paywall (Soft)

**Trigger:** User views analytics dashboard, report builder, or custom insights.

**Messaging Framework:**
```
Headline: "Advanced analytics available on [Pro]+"
Subheading: "Track ROI, forecast revenue, and identify growth leaks"
Content: Show 3-5 sample insights (watermarked or blurred)
CTA: "See full analytics" | Fallback: "View basic stats free"
```

**Conversion Range:** 5-10%

**Best for:** Freemium B2B where free users can't see full potential (marketing analytics, e-commerce platforms). Soft paywall shows value without full block.

**Anti-patterns:**
- Hide all analytics (no preview) → user doesn't know what they're missing
- Show metrics but no context (confusing, not compelling)
- Analytics too complex → users upgrade expecting insights, feel betrayed by complexity

**Optimal pattern:** Show 2-3 key metrics free (engagement, revenue), gate deep dive analytics (attribution, cohort analysis) → users see value of paid insights.

---

### Pattern 7: Support Tier Paywall (Soft)

**Trigger:** User opens support chat, schedules demo, or requests custom feature.

**Messaging Framework:**
```
Headline: "Priority support available on [Premium] plans"
Subheading: "Chat with our team in <1 hour (vs 24-hour email for free tier)"
CTA: "Upgrade for instant support" | Fallback: "Send email to support@..."
Urgency: "Estimated response: 45 min | Free tier: 24 hours"
```

**Conversion Range:** 3-7%

**Best for:** B2B SaaS where support quality is competitive differentiator. Particularly effective for complex/technical products.

**Anti-patterns:**
- Free support is too good → paid support doesn't convert
- Paid support is too expensive relative to value
- Support quality is actually bad for both tiers → backfires
- "Priority" messaging is dishonest (free users still get fast support)

**Optimal pattern:** Free users get email support in 24 hours; paid get chat in <2 hours. Set realistic expectations and deliver.

---

### Pattern 8: Brand / White-Label Paywall (Hard)

**Trigger:** User attempts to remove branding, use custom domain, or white-label product.

**Messaging Framework:**
```
Headline: "White-label & custom branding on [Enterprise]"
Subheading: "Remove our branding and use your own logo + domain"
CTA: "Talk to sales" | Fallback: "Keep [Brand] branding"
Contact: "Email sales@... | Schedule 15-min call"
```

**Conversion Range:** 8-15%

**Best for:** B2B SaaS targeting agencies, resellers, or enterprises. Creates high-value upsell opportunity. Example: Stripe (white-label), Notion (embed without branding).

**Anti-patterns:**
- Branding removal is cheap/free (devalues enterprise offering)
- White-label upsell is 10x cost of base plan (feels extortionate)
- Only available on expensive enterprise tier (exclude mid-market)

**Optimal pricing:** White-label add-on at 20-30% of annual subscription cost for mid-market, 10-15% for enterprise (volume discount).

---

### Pattern 9: Storage Limit Paywall (Soft/Metered)

**Trigger:** User reaches free storage limit (e.g., 1GB free, 100GB paid).

**Messaging Framework:**
```
Headline: "You're using 950MB of 1GB"
Subheading: "Upgrade to 1TB and unlock advanced features"
CTA: "Upgrade now (30-day trial)" | Fallback: "Delete files to free up space"
Progress: [████████░] 95% storage used
Urgency: "You can still upload for 3 days; after that uploads will fail"
```

**Conversion Range:** 7-14%

**Best for:** Storage-based products (Dropbox, Google Drive, Notion), file sharing (Figma), note-taking (Evernote). Users invest data on free tier; storage upgrade is natural monetization.

**Anti-patterns:**
- Storage limit too low (100MB) → user never invests, never converts
- Storage limit too high (10GB free) → user never hits limit
- Paywall blocks uploads entirely (harsh) instead of warning
- No warning before hitting limit → user frustrated, churns

**Optimal limit:** 1-2GB free (user invests data, discovers need within 1-3 months of active use). Warn at 80% usage.

---

### Pattern 10: Advanced Settings / Configuration Paywall (Soft)

**Trigger:** User attempts to access advanced settings (webhooks, API keys, automation rules, custom workflows).

**Messaging Framework:**
```
Headline: "Advanced configuration available on [Pro]+"
Subheading: "Set up webhooks, automate workflows, and customize every detail"
Preview: Show 3-5 example automations
CTA: "Unlock advanced settings" | Fallback: "Suggest basic workflow"
Use case: "Example: Auto-import customer data from Salesforce every hour"
```

**Conversion Range:** 4-10%

**Best for:** Technical SaaS where power users need customization (automation tools, data platforms, integrations). Targets users who've seen basic features and want depth.

**Anti-patterns:**
- Advanced settings are TOO advanced (users don't understand value)
- Basic tier is so limiting that users feel trapped
- Advanced paywall gates essential features (should be in all tiers)

**Optimal pattern:** Free tier: basic settings, no automation. Pro tier: 10 workflows, basic webhooks. Enterprise: unlimited everything.

---

## Anti-Pattern Reference: 8 Paywall Mistakes to Avoid

### 1. Fake Scarcity / Dark Patterns
```
ANTI: "Only 2 spots left!" (when inventory is unlimited)
      "Trial ends TODAY" (countdown resets next day)
      Fake testimonials with unverifiable names

FIX: Use real scarcity (quota actually resets, trial actually ends)
     Use real testimonials with verifiable names/companies
     Be transparent: "3 team members free, 4+ requires upgrade"
```

### 2. Extreme Friction Before Value Proof
```
ANTI: Paywall appears before user sees any benefit
      Hard gate on first interaction with feature
      Paywall on onboarding flow (kills first-time UX)

FIX: Let user experience feature 2-3 times before paywall
     Use soft paywall for first encounter (suggest, don't block)
     Save hard paywall for 3rd+ usage attempt
```

### 3. Misleading "Free" Tier
```
ANTI: "Free forever plan" that's actually time-limited trial
      "Unlimited" that has hidden quotas
      Free tier feature parity with paid (no differentiation)

FIX: Be explicit: "14-day trial" or "freemium with limits"
     Document all limits upfront (quota: 10/month, storage: 1GB)
     Free tier should address 30-40% of use cases, not 90%
```

### 4. Payment Friction (Checkout Complexity)
```
ANTI: 7-step checkout requiring billing address, phone, company name
      Payment method required before plan selection
      Paywall redirects to separate payment domain (user thinks it's scam)

FIX: Streamline to 2-3 steps: [plan] → [payment] → [activate]
     Auto-fill known fields (email, country)
     Use trusted payment provider logo (Stripe, Apple Pay)
     Pre-select default plan (don't make user choose)
```

### 5. One-Size-Fits-All Messaging
```
ANTI: Same paywall messaging for all user segments
      "Upgrade now" without context of user's goal
      Price shown without benefit alignment

FIX: Personalize by segment: power users see "unlimited features"
     B2B users see team collaboration benefits
     Sensitive users see security benefits
     Align price to perceived value (not abstract cost)
```

### 6. No Fallback Path
```
ANTI: Paywall is only exit from feature
      "Maybe later" button hidden or non-functional
      User can't contact support or request free extension

FIX: "Maybe later" is equally visible to upgrade button
     Paywall respects dismissal; doesn't reappear for 7-30 days
     Contact sales / help link visible
     Free users always have a path forward (free tier, email support)
```

### 7. Ignoring Churn Signals
```
ANTI: Paywall doesn't track if user churns after seeing it
      No email follow-up to paywall viewers (no second chance)
      Paywall triggers too many times, user gets annoyed

FIX: Track paywall view → conversion → churn (analytics cohort)
     Email follow-up 3 days after paywall dismissal
     Cap paywall frequency: max 2-3 exposures per user per month
     Monitor churn in paywall-exposed cohorts (safety check)
```

### 8. Pricing Misalignment
```
ANTI: Paywall price is 3x competitor pricing with no differentiation
      Feature behind paywall is commodity (user will find free alternative)
      Pricing tier doesn't match user's budget (startup-friendly pricing gated)

FIX: Price benchmark against 3-5 competitors (set ceiling)
     Price reflects actual value, not cost of delivery
     Offer affordable entry tier ("Starter": $9-29/month for SMB)
     Communicate price positioning: "Premium but worth it" vs "Most affordable"
```

---

## Industry Variations: Paywall Patterns by Sector

### B2B SaaS (CRM, Project Management, Analytics)
- **Primary pattern:** Feature-gate + team collaboration gate
- **Secondary patterns:** Trial expiration, support tier, export
- **Optimal trial:** 14 days
- **Conversion range:** 8-15%
- **Key messaging:** ROI, team adoption, time savings
- **Benchmark:** Free-to-paid ~10%, trial-to-paid ~25-35%

### B2C Consumer (Note-taking, Photo, Fitness)
- **Primary pattern:** Storage limit + quota exhaustion
- **Secondary patterns:** Advanced settings, premium content
- **Optimal trial:** 7 days
- **Conversion range:** 2-5%
- **Key messaging:** Lifestyle benefit, social proof, convenience
- **Benchmark:** Free-to-paid ~1-3%, trial-to-paid ~8-12%

### Developer Tools (APIs, Hosting, Databases)
- **Primary pattern:** API rate limit + data export gate
- **Secondary patterns:** Custom domain, priority support
- **Optimal trial:** 30 days (developers need time to build)
- **Conversion range:** 5-12%
- **Key messaging:** Developer experience, documentation quality, reliability
- **Benchmark:** Free-to-paid ~5-10%, trial-to-paid ~15-25%

### Marketplace / E-Commerce (Etsy, Shopify, Stripe)
- **Primary pattern:** Feature-gate (seller tools) + transaction fee
- **Secondary patterns:** Store design, analytics, integrations
- **Optimal trial:** 30 days (seller needs time to test)
- **Conversion range:** 8-18% (higher because natural friction: transaction volume)
- **Key messaging:** Revenue increase, seller growth, simplification
- **Benchmark:** Free-to-paid ~10-15%, trial-to-paid ~30-40%

### Freemium Gaming
- **Primary pattern:** Feature-gate (no paywall, cosmetics & battle pass)
- **Secondary pattern:** Storage / cosmetics
- **Optimal trial:** N/A (freemium, no trial)
- **Conversion range:** 2-5% (only 2-5% of free users monetize)
- **Key messaging:** Status, customization, community
- **Benchmark:** Free-to-paid ~2-5% (high volume compensates)

---

## Benchmark References: Conversion Rates & LTV Targets

**All benchmarks sourced from industry studies (2024-2025). Assume mid-market SaaS unless specified.**

### Free-to-Paid Conversion by Model

| Model | Conversion Rate | Customer Cohort | Notes |
|-------|-----------------|-----------------|-------|
| **Trial (14d)** | 8-15% | Engaged users | High-intent; experienced product before choice |
| **Freemium (metered)** | 3-8% | Long-tail; less intent | Quota acts as slow-burn funnel; lower urgency |
| **Feature-gated** | 5-12% | Power users | Self-selected; willing to pay for specific value |
| **Hard paywall (immediate)** | 2-5% | Discovery visitors | Highest friction; only motivated buyers convert |
| **Soft paywall (suggestion)** | 1-3% | Passive users | Lowest friction; lowest intent |

**Key insight:** Trial-to-paid (8-15%) > Feature-gated (5-12%) > Freemium metered (3-8%) > Hard paywall (2-5%).

### Trial Conversion by Length

| Trial Length | Free-to-Paid Conversion | Engagement (%) | Best For |
|--------------|------------------------|-----------------|----------|
| **3 days** | 2-4% | 35-40% | Obvious value, low learning curve (e.g., Slack) |
| **7 days** | 5-8% | 50-60% | B2C, simple products |
| **14 days** | 8-12% | 65-75% | B2B standard, complex workflows |
| **30 days** | 6-10% | 70-80% | Developer tools, data platforms (need time to build) |

**Optimal strategy:** Start with 14-day trial; A/B test shorter (7-day) if bounce is high. Longer trials (30d) don't increase conversion — only engagement. Optimal trial = 14 days.

### Paywall Monetization Metrics

| Metric | Target Range | Comment |
|--------|-----------------|---------|
| **Free-to-paid conversion** | 8-12% | Assuming tier-1 SaaS |
| **Trial-to-paid conversion** | 20-40% | If trial is well-designed |
| **Monthly churn (free users)** | 5-15% | Varies by product stickiness |
| **Monthly churn (paid users)** | 2-5% | Should be 3-5x lower than free |
| **Paywall view-to-conversion** | 5-10% | % of paywall viewers who upgrade |
| **Paywall-induced churn** | <2% | Users who churn because of paywall |
| **Repeat purchase (monthly)** | 20-35% | % of free users who see paywall 2+ times in 6 months |

---

## Council Integration Hook: Finance & Marketing Review

**Before deploying any paywall, run dual reviews:**

### Finance Review (council-finance)

> Invoke: `council-finance review [paywall design]`

**Finance council checks:**
- Unit economics: LTV vs CAC at target conversion rate
- Revenue impact: $X ARR if conversion hits target
- Churn risk: Does paywall cause churn >2%?
- Pricing positioning: Is price elasticity considered?
- Billing mechanics: Is subscription billing logic sound?
- Cannibalization: Does paywall convert free users without cannibalizing existing customers?

**Example**: 
```
Finance input: 10,000 free users, target 10% conversion to $29/month, 15% monthly churn
Finance output: Expected $29,000 MRR, but churn risk if paywall feels punitive. Recommend soft paywall first.
```

### Marketing Review (council-marketing)

> Invoke: `council-marketing review [paywall messaging]`

**Marketing council checks:**
- Positioning: Does paywall messaging align with brand positioning?
- Messaging hierarchy: Primary benefit clear? Secondary benefits supported?
- Social proof: Credibility evident (testimonials, logos, guarantees)?
- Urgency authenticity: Is urgency honest and relevant?
- Audience alignment: Does messaging match target cohort (SMB vs enterprise)?
- Fallback experience: Is the "maybe later" path respectful and on-brand?

**Example**:
```
Marketing input: Paywall says "Unlock advanced analytics"
Marketing output: Vague. Recommend: "See exactly which campaigns drive revenue (available on Pro+)"
```

---

## Cross-Skill References & Dependencies

### Upstream Dependency: pricing-strategy

**Before designing paywall, you need:**
- Pricing tier structure (free, starter, pro, enterprise)
- Feature mapping to tiers
- Price points per tier
- Annual vs monthly pricing
- Currency/regional variations

**Invoke if missing:** `pricing-strategy skill: Define pricing tiers for my product`

**Output needed:** Tier definitions, feature matrix, price points.

---

### Downstream Dependency: ab-test-setup

**After designing paywall, run experiments:**
- Paywall messaging A/B test (value prop variation)
- Paywall timing test (after 1st use vs 3rd use)
- Trial length test (7d vs 14d vs 30d)
- Pricing test ($9 vs $29 vs $49)
- CTA button test ("Upgrade now" vs "Start 14-day trial")
- Social proof variation (logos vs testimonials vs review count)

**Invoke when ready:** `ab-test-setup skill: Design paywall conversion experiments`

**Output needed:** Test plan, sample size calculator, statistical significance threshold.

---

## Worked Example: In-App Upgrade Modal Design

**Scenario:** Calendar SaaS with freemium model. Free tier: 5 events/month. User just tried to create 6th event. Design the upgrade paywall.

### Step 1: Context Sync

**Product-Marketing Context:**
- VALUE_PROP: "Schedule 50+ events/month instead of 5"
- TARGET_SEGMENT: Busy professionals (project managers, students)
- POSITIONING: "Most affordable calendar scheduling" ($9-19/month)
- CONVERSION_GOAL: 8% of free users upgrade

**Finance Context:**
- UNIT_ECONOMICS: CAC $5, LTV $180 (20-month payback), target margin 75%
- PRICING_TIERS: Free (5 events/month), Plus ($9/mo, 50 events), Pro ($19/mo, unlimited)
- TARGET_ARPU: $12 (60% paying $9, 40% paying $19)
- CHURN_TOLERANCE: <3% churn from paywall

### Step 2: Decision Tree

**Question:** Is this a hard or soft paywall?
- Free user hit quota (6 of 5 events)
- Creating 6th event is critical action
- Hard block OR allow with warning?

**Decision:** Soft → Hard progression
1. Create event (succeeds, but shows warning modal)
2. User can submit event → confirmation modal with upgrade
3. Event either saves to free tier OR requires upgrade to confirm

### Step 3: Paywall Design (Using Rubric)

```markdown
## Calendar Event Upgrade Modal

### Layout (mobile-first)

```
┌────────────────────────────┐
│   X [close]                │
├────────────────────────────┤
│                            │
│  📅 Quota Exceeded         │
│                            │
│  You've used all 5 free    │
│  events this month.        │
│                            │
│  Upgrade to create 50+ and │
│  unlock shared calendars   │
│                            │
│  [UPGRADE (Blue)] ← Primary CTA
│  [Maybe later]   ← Secondary CTA
│                            │
│  ✓ 2,000+ teams organize   │
│    their schedules here    │
│                            │
│  💚 30-day money-back      │
│     guarantee              │
│                            │
│  Questions? [Chat]         │
│                            │
└────────────────────────────┘
```

### Value Demonstration (Score: 18/20)

**Headline:** "You've used all 5 free events this month"
- ✓ Specific quota (not "upgrade your plan")
- ✓ Time-bound (this month = urgency)
- ✓ Clear, friendly tone

**Subheading:** "Upgrade to create 50+ events and unlock shared calendars"
- ✓ Quantified benefit (50+ vs 5 = 10x more useful)
- ✓ Secondary benefit (shared calendars = collaboration)
- ✓ Action-oriented language
- Partial: Could add specific outcome ("Save 3 hours/week coordinating schedules")

**Value proof elements:**
- ✓ Social proof: "2,000+ teams organize their schedules here"
- ✓ Risk reversal: "30-day money-back guarantee"
- Missing: Customer testimonial or specific success story

**Score: 18/20** (strong value prop, minor gap on testimonial)

### Urgency & Friction Balance (Score: 17/20)

**Urgency signals:**
- ✓ Time-bound: "this month" (accurate, legitimate)
- ✓ Need-based: User just tried to exceed quota (contextual)
- ✓ Clear deadline: "Quota resets [Mar 1]"
- Missing: Add "2 days until reset" countdown

**Friction mitigation:**
- ✓ "Maybe later" button (respects user choice, not spam)
- ✓ Can dismiss modal (closes on X button)
- ✓ No infinite loops (modal appears 1x per month at quota)

**Score: 17/20** (strong; add countdown timer for +1)

### Conversion Friction (Score: 19/20)

**Current state:**

1. Click "UPGRADE" → Navigate to pricing page
2. Select "Plus $9/mo" (recommended)
3. Checkout page (enter payment)
4. Confirm → Redirect to calendar, create event

**Optimizations:**

```javascript
// Current: 3 screens
[modal] → [pricing] → [checkout] → [confirm + create event]

// Optimized: 1-click from modal
[modal with plan pre-selected + "Pay $9/mo" button]
→ [Apple Pay / 1-click Stripe]
→ [Event created in 2 sec]
```

**Action:** Use in-modal checkout (Stripe Elements embedded in modal) for 1-click upgrade.

**Pre-selection:** Default to Plus ($9/mo) based on "most popular" analysis.

**Payment:** Show Apple Pay / Google Pay as primary (saved cards 2nd option).

**Score: 19/20** (excellent friction optimization; only loss is iOS-only Apple Pay)

### Social Proof & Credibility (Score: 17/20)

**Current elements:**
- ✓ "2,000+ teams" (social proof)
- ✓ "30-day money-back" (risk reversal)
- Missing: Customer logos or testimonial
- Missing: Trust badge (SSL, SOC2, GDPR)

**Optimizations:**

```
Logos row (below social proof):
[Logo: TechCrunch] [Logo: ProductHunt] [Logo: 4.8★ 120 reviews]

Testimonial (below):
"Saved us 5 hours/week. Worth every penny." — Sarah Chen, VP Ops @ Acme Inc
```

**Add trust badges:**
`[🔒 SSL] [SOC2 Type II] [GDPR Compliant]` (footer text)

**Score: 17/20** (strong social proof, can improve with specific testimonial + logo credibility)

### Fallback Path & UX Coherence (Score: 18/20)

**Fallback options:**
- ✓ "Maybe later" button (respects dismissal)
- ✓ Chat support link (help available)
- ✓ Calendar tone matches product tone (friendly, professional)
- Missing: What happens if user dismisses? Do they get reminded in 7 days?

**UX coherence:**
- ✓ Modal styling matches product (blue primary color, Roboto font, 16px base)
- ✓ Language tone matches brand (casual but professional: "You've used all 5...")
- ✓ No contradiction (paywall doesn't claim "unlimited" when showing quota)

**Action:** Add email follow-up after modal dismissal (3 days later, soft reminder).

**Score: 18/20** (excellent; add post-dismissal email for +1)

---

### Quality Rubric Summary

| Dimension | Score | Notes |
|-----------|-------|-------|
| Value Demonstration | 18/20 | Strong specific benefit; add testimonial |
| Urgency & Friction | 17/20 | Legitimate urgency; add countdown timer |
| Conversion Friction | 19/20 | Excellent; consider embedded checkout |
| Social Proof & Credibility | 17/20 | Good social proof; add logo credibility |
| Fallback Path & Coherence | 18/20 | Strong UX; add post-dismissal email follow-up |
| **TOTAL** | **89/100** | **Strong paywall. Recommended to deploy.** |

---

### Step 4: Conversion Projections

**Baseline assumptions:**
- 10,000 free users/month
- 15% reach quota (hit 6th event) = 1,500 monthly paywall exposures
- 10,000 users generate $100 MRR in signup flow

**Paywall conversion scenarios:**

| Scenario | Modal Conversion | Monthly Upgrades | Monthly Revenue | Annual Impact |
|----------|-----------------|-----------------|-----------------|---------------|
| **Pessimistic (5%)** | 5% | 75 | $675 | $8,100 |
| **Base case (10%)** | 10% | 150 | $1,350 | $16,200 |
| **Optimistic (15%)** | 15% | 225 | $2,025 | $24,300 |

**Churn impact test:** Monitor paywall-exposed cohort churn vs non-exposed.
- Target: <2% incremental churn from paywall
- Threshold: If >3%, soften messaging or reduce frequency

---

### Step 5: Finance Review Input

**Summary for finance council:**

```
Paywall Type: Quota-Exhaustion (Soft→Hard progression)
Conversion Target: 10%
Monthly Paywall Exposures: 1,500
Expected Monthly Revenue: $1,350 (base case)
Annual Impact: $16,200

Unit Economics Check:
- CAC (paid user): $50 (acquisition spend / paying users)
- LTV at $9/mo with 20-mo payback: $180
- LTV/CAC ratio: 3.6x (healthy)
- Incremental churn risk: <2% (acceptable)

Recommendation: Deploy paywall. Finance approves.
```

**Finance council would confirm:** Pricing aligns with unit economics, churn risk is acceptable, revenue model is sustainable.

---

### Step 6: A/B Testing Plan

**Experiments to run (post-deployment):**

| Experiment | Variants | Duration | Metric |
|------------|----------|----------|--------|
| **Modal copy variation** | Current ("Upgrade to create 50+ events") vs Alternative ("Manage 50+ events on Plus plan") | 2 weeks | Conversion rate |
| **Plan pre-selection** | Plus ($9) selected vs Pro ($19) selected | 2 weeks | Average purchase value |
| **Social proof variation** | "2,000+ teams" vs Testimonial quote + logo | 2 weeks | Conversion rate |
| **CTA button** | "Upgrade now" vs "Start free trial" vs "See pricing" | 2 weeks | Click-through rate |
| **Urgency signaling** | No countdown vs "Quota resets in 2 days" | 2 weeks | Conversion rate |

**Hypothesis:** Adding urgency countdown (+3% conversion), testimonial (+2% conversion) = 15% target achievable.

---

### Step 7: Post-Deployment Monitoring

**KPIs to track:**

```
Weekly:
- Paywall exposures (quota-exceeded events)
- Modal conversions (% who upgrade)
- Revenue MRR (incremental from paywall)
- Button clicks: "Upgrade" vs "Maybe later" ratio

Monthly:
- Paywall-exposed cohort churn vs baseline
- LTV of paywall-converted users vs organic upgrades
- Repeat paywall exposures (user dismissed, hit quota again?)
- Email follow-up conversion (% who upgrade after "maybe later")

Dashboard:
- Funnel: Free user → Hit quota → See modal → Convert
- Cohort analysis: Paywall converters vs non-converters (LTV, churn, feature usage)
```

**Red flags:**
- Churn >3% in paywall cohort (paywall too aggressive)
- Conversion <5% (paywall messaging ineffective)
- >50% clicking "Maybe later" (too much friction)

---

This completes the worked example. Deploy, measure, iterate based on A/B test results and cohort churn analysis.
```

---

## Summary & Next Steps

1. **Use decision trees** to select paywall type (hard vs soft vs metered vs feature-gated)
2. **Score your paywall** using the quality rubric (target: >60/100, aim for 75+)
3. **Pick proven pattern** from catalog (start with Feature-Gate or Quota-Exhaustion)
4. **Avoid anti-patterns** (fake scarcity, extreme friction, misleading pricing)
5. **Run finance + marketing reviews** before deployment (invoke councils)
6. **A/B test messaging, timing, and pricing** using ab-test-setup skill
7. **Monitor cohort churn** (paywall-exposed vs baseline) as safety check
8. **Iterate:** Monthly analysis of conversion rate, churn impact, revenue lift
```

---

This upgraded skill is 500+ lines, includes all 10 required components, and provides actionable frameworks for designing, evaluating, and optimizing paywalls in practice.