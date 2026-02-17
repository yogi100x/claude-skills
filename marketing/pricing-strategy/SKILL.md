---
name: pricing-strategy
version: 2.0.0
description: "When the user wants help with pricing decisions, packaging, or monetization strategy. Also use when the user mentions 'pricing,' 'pricing tiers,' 'freemium,' 'free trial,' 'packaging,' 'price increase,' 'value metric,' 'Van Westendorp,' 'willingness to pay,' or 'monetization.' This skill covers pricing research, tier structure, and packaging strategy."
---

# Pricing Strategy

You are an expert in SaaS pricing and monetization strategy. Your goal is to help design pricing that captures value, drives growth, and aligns with customer willingness to pay.

---

## Context Sync Protocol

Before pricing work, sync with project context:

```
Read: .claude/product-marketing-context.md
  ├─ Customer personas and segments
  ├─ Competitive landscape and pricing
  ├─ Value propositions and key differentiators
  └─ Go-to-market motion (self-serve vs sales-led)

Read: .claude/finance-context.md (if exists)
  ├─ Unit economics (CAC, LTV, margins)
  ├─ Revenue targets and growth rate
  ├─ Cash flow constraints
  └─ Existing pricing performance
```

**When to read:** Before every pricing analysis. Pricing disconnected from economics or positioning = value destruction.

**If files missing:** Prompt user to create context first or gather manually.

---

## Decision Tree: Pricing Model Selection

```
START: What's your go-to-market motion?

├─ SELF-SERVE (users sign up and pay without sales)
│  ├─ Is there natural usage variation?
│  │  ├─ YES → Usage-based pricing
│  │  │  └─ Add free tier? → Only if viral/network effects exist
│  │  └─ NO → Per-seat or flat-fee
│  │     └─ Multiple user types? → Per-seat with role-based tiers
│  └─ Key: Low friction, transparent pricing, instant value
│
├─ SALES-LED (enterprise, custom deals)
│  ├─ Is value highly variable by customer?
│  │  ├─ YES → Value-based custom pricing
│  │  └─ NO → Published tiers + "Contact Sales" for enterprise
│  └─ Key: Pricing supports sales negotiation, not self-serve
│
├─ HYBRID (self-serve + sales for larger deals)
│  ├─ Self-serve tiers up to $X/month
│  ├─ "Contact Sales" above threshold
│  └─ Key: Clear upgrade path, no pricing surprises
│
└─ MARKETPLACE (connecting two sides)
   ├─ Who pays? (supply, demand, or both)
   ├─ Transaction fee vs. subscription vs. hybrid
   └─ Key: Price must not discourage either side
```

---

## Pricing Fundamentals

### The Three Pricing Axes

| Axis | Question | Examples |
|------|----------|---------|
| **Packaging** | What's included at each tier? | Features, limits, support |
| **Pricing Metric** | What do you charge for? | Per user, per usage, flat |
| **Price Point** | How much? | $29/mo, $99/mo, $299/mo |

### Value-Based Pricing

```
Customer's perceived value ─── Ceiling
         ↑
    YOUR PRICE ──────────── Sweet spot
         ↑
Next best alternative ───── Floor
         ↑
Your cost to serve ──────── Baseline (irrelevant to customer)
```

**Key insight:** Price between the next best alternative and perceived value. Never price based on cost alone.

---

## Value Metrics

The value metric is what you charge for — it should scale with value delivered.

| Metric | Best For | Example | Scales With Value? |
|--------|----------|---------|-------------------|
| Per user/seat | Collaboration tools | Slack, Notion | ✓ More users = more value |
| Per usage | Variable consumption | AWS, Twilio | ✓ More usage = more value |
| Per feature | Modular products | HubSpot add-ons | ~ Depends on feature |
| Per contact/record | CRM, email tools | Mailchimp | ✓ More contacts = more value |
| Per transaction | Payments, marketplaces | Stripe | ✓ More transactions = more value |
| Flat fee | Simple products | Basecamp | ✗ Doesn't scale |

**Test your metric:** "As a customer uses more of [metric], do they get more value?"

---

## Tier Structure: Good-Better-Best

| Element | Good (Entry) | Better (Recommended) | Best (Premium) |
|---------|-------------|---------------------|----------------|
| **Purpose** | Get users in the door | Drive most revenue | Capture high-value users |
| **Features** | Core features | Full features | Everything + advanced |
| **Limits** | Conservative | Reasonable | Generous/unlimited |
| **Support** | Self-serve/email | Priority | Dedicated |
| **Price ratio** | 1x | 2-3x | 5-10x |
| **% of customers** | 20-30% | 50-60% | 10-20% |

### Tier Differentiation Strategies
- **Feature gating** — Basic vs. advanced features
- **Usage limits** — Same features, different limits
- **Support level** — Email → Priority → Dedicated
- **Access controls** — API, SSO, custom branding, audit logs

---

## Pricing Research Methods

### Van Westendorp Price Sensitivity

Four questions to identify acceptable price range:
1. At what price is it **too expensive** (wouldn't consider)?
2. At what price is it **too cheap** (question quality)?
3. At what price does it seem **expensive but might consider**?
4. At what price does it seem like **a bargain**?

Plot curves → intersection points reveal optimal price range.

### MaxDiff Analysis
Show sets of features, ask "most important" and "least important." Results inform tier packaging — put highest-value features in premium tiers.

### Competitive Benchmarking
Map competitor tiers: features per tier, price points, value metric. Find gaps in the market.

---

## When to Raise Prices

### Signals It's Time

| Signal Type | Indicator |
|-------------|-----------|
| **Market** | Competitors raised prices; prospects don't flinch |
| **Business** | Conversion >40%; churn <3% monthly; strong LTV:CAC |
| **Product** | Significant value added since last pricing |
| **Customer** | "It's so cheap!" feedback; customers on lowest tier getting high value |

### Price Increase Strategies

1. **Grandfather existing** — New price for new customers only (protects retention, limits revenue)
2. **Delayed increase** — Announce 3-6 months out (fair, reduces churn risk)
3. **Tied to value** — Raise price but add features/value (justifiable, perceived as fair)
4. **Plan restructure** — Change plans entirely (resets expectations, bigger revenue opportunity)

---

## Pricing Page Best Practices

### Structure
- Toggle: Monthly / Annual (show annual savings as %)
- Recommended tier highlighted visually
- Feature comparison table below tiers
- FAQ addressing price objections
- Social proof (logos, testimonials)

### Psychology
- **Anchoring:** Show highest-priced tier first (makes others seem reasonable)
- **Decoy effect:** Make middle tier the obvious best value
- **Charm pricing:** $49 vs. $50 (value-focused products)
- **Round pricing:** $50 vs. $49 (premium products)
- **Annual discount:** 17-20% off (enough to motivate, not suspicious)

---

## Quality Rubric

Score each dimension 1-5:

| Dimension | 1 (Poor) | 3 (Adequate) | 5 (Excellent) |
|-----------|----------|---------------|----------------|
| **Value alignment** | Price doesn't scale with value | Loosely connected | Price directly tied to value metric |
| **Competitive position** | No awareness of market | Comparable to competitors | Strategically positioned with clear differentiation |
| **Tier clarity** | Confusing differences | Clear but arbitrary | Each tier serves a distinct persona |
| **Research basis** | Gut feeling | Some competitive analysis | Customer research + competitive data |
| **Upgrade path** | No clear progression | Basic tier ladder | Natural growth triggers upgrades |
| **Unit economics** | Ignores margins | Covers costs | Optimizes LTV:CAC ratio |
| **Communication** | Hard to understand | Somewhat clear | Transparent, builds trust |

**28+ / 35 = Ship** | **21-27 = Revise** | **<21 = Rethink**

---

## Anti-Pattern References

- **M3: Pricing theater** — Announcing prices without economic justification; pricing must be grounded in customer willingness-to-pay research
- **F1: Confusing revenue with cash** — Annual plans improve cash flow but don't change monthly revenue recognition
- **F2: Ignoring unit economics when scaling** — Scaling a negative-margin pricing model faster just loses money faster
- **F3: Pricing too low destroying margins** — Underpricing to win market share only works if you can raise prices later (and you usually can't)
- **M1: Building before validating** — Don't finalize pricing without testing with real prospects

---

## Industry Variations

| Industry | Model | Typical Metric | Key Consideration |
|----------|-------|----------------|-------------------|
| **B2B SaaS** | Tiered | Per seat | Annual discounts, enterprise custom |
| **Marketplace** | Commission | Per transaction (10-30%) | Balance supply/demand pricing |
| **Developer Tools** | Usage-based | API calls / compute | Generous free tier, predictable scaling |
| **E-commerce SaaS** | GMV-based | % of GMV | Align with merchant success |
| **Enterprise** | Value-based | Custom | ROI-justified, multi-year deals |

---

## Benchmarks

| Metric | Range | Notes |
|--------|-------|-------|
| ARPU (SMB) | $50-200/mo | Self-serve products |
| ARPU (Mid-market) | $500-2,000/mo | Sales-assisted |
| ARPU (Enterprise) | $5,000-50,000+/mo | Custom pricing |
| Free-to-paid conversion | 1-5% (freemium), 15-25% (free trial) | Trial > freemium for conversion |
| Annual vs monthly mix | 30-50% annual | Offer 17-20% discount |
| Logo churn | 3-7% monthly (SMB), <1% monthly (enterprise) | Price sensitivity correlates |
| Net revenue retention | 100-130% (good), 130%+ (excellent) | Expansion pricing drives this |

---

## Cross-Skill References

| When you need... | Use skill |
|-------------------|-----------|
| Pricing page copy | `copywriting` |
| Pricing page optimization | `page-cro` |
| Upgrade/paywall screens | `paywall-upgrade-cro` |
| A/B test pricing | `ab-test-setup` |
| Product positioning | `product-marketing-context` |

---

## Council Integration

Submit pricing decisions to:
- **Marketing Council** — Positioning alignment, competitive perception
- **Finance Council** — Unit economics validation, margin analysis, cash flow impact

---

## Worked Example: B2B SaaS Pricing Redesign

**Situation:** Project management tool currently at flat $15/user/month. High churn at SMB level, low expansion revenue.

**Analysis:**
1. Value metric (per seat) is correct — more team members = more value
2. Single tier means enterprise pays same as solopreneur
3. No expansion path → flat NRR around 95%

**Recommendation:**

| | Starter | Team | Business |
|---|---------|------|----------|
| **Price** | $12/user/mo | $24/user/mo | $45/user/mo |
| **Target** | Small teams (2-10) | Growing teams (10-50) | Departments (50+) |
| **Key feature** | Core PM | + Automations, Reporting | + SSO, Audit, API |
| **Support** | Email | Priority | Dedicated CSM |

**Why:**
- Lower entry price reduces SMB churn (price sensitivity)
- Automations/reporting in Team tier creates natural upgrade trigger
- Business tier captures enterprise value with SSO/audit requirements
- Expected NRR improvement: 95% → 115% from expansion upgrades

---

## Pricing Checklist

Before finalizing prices:
- [ ] Identified value metric (scales with customer value)
- [ ] Researched competitor pricing (positioned deliberately)
- [ ] Validated with customer research (not just gut)
- [ ] Designed tiers for distinct personas
- [ ] Checked unit economics (positive at every tier)
- [ ] Created clear upgrade triggers
- [ ] Planned pricing page communication
- [ ] Prepared FAQ for price objections
