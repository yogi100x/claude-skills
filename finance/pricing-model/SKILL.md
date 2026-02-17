# Pricing Model

Design and validate pricing structures that capture value, drive growth, and align with business strategy.

## Context Sync Protocol

Before designing pricing:
1. Read `.claude/product-marketing-context.md` for ICP, positioning, competitors
2. Read `.claude/finance-context.md` for target margins and unit economics
3. If neither exists, run discovery before pricing

## Decision Tree: Pricing Model Selection

```
What's your go-to-market motion?
├── Self-serve (PLG)
│   ├── Value metric is usage-based? → Usage-based pricing
│   ├── Value scales with team size? → Per-seat pricing
│   └── Value is binary (has/hasn't)? → Flat-rate tiers
├── Sales-led
│   ├── Complex, variable needs? → Custom/quote-based
│   ├── Predictable needs? → Good-Better-Best tiers
│   └── Platform play? → Base + modules
├── Hybrid (PLG + Sales)
│   └── Free/cheap self-serve tier + enterprise tier with sales
└── Marketplace
    ├── Supply-constrained? → Higher seller take rate
    └── Demand-constrained? → Higher buyer incentives
```

## The Three Pricing Axes

Every pricing decision involves three independent choices:

### 1. Packaging (What's included?)

| Pattern | When to Use | Example |
|---------|-------------|---------|
| **All-inclusive** | Simple product, single ICP | Basecamp |
| **Good-Better-Best** | Multiple ICPs, clear feature tiers | Slack Free/Pro/Business+ |
| **Modular** | Complex product, varied needs | HubSpot hubs |
| **Platform + Add-ons** | Core + optional extensions | Shopify + apps |
| **Usage-based** | Value proportional to consumption | Twilio, AWS |

### 2. Pricing Metric (What unit do you charge for?)

| Metric | Best For | Risk |
|--------|----------|------|
| **Per user/seat** | Collaboration tools | Seat sharing, adoption friction |
| **Per usage** (API calls, messages) | Infrastructure, APIs | Revenue unpredictability |
| **Per feature** | Modular platforms | Complexity, nickel-and-diming perception |
| **Per outcome** (lead, hire, transaction) | Marketplaces, performance tools | Tracking complexity |
| **Flat fee** | Simple tools | Leaves money on table at scale |

### 3. Price Point (How much?)

**Value-based pricing framework:**
```
Price Floor: Your cost to deliver (minimum viable price)
Price Ceiling: Customer's next-best alternative cost
Sweet Spot: 20-30% below ceiling (capture 70-80% of value created)

Price = Cost + (Perceived Value - Cost) × Value Capture %

Target: Capture 10-30% of value created for customer
```

## Good-Better-Best Framework

| Element | Good (Free/Starter) | Better (Pro) | Best (Enterprise) |
|---------|---------------------|--------------|-------------------|
| **Purpose** | Acquisition, trial | Revenue driver (60-70% of revenue) | Expansion, large deals |
| **Price anchor** | $0 or low | 3-5x Good | 3-5x Better or custom |
| **Features** | Core value, limited | Full product | Full + admin, security, support |
| **Limits** | Usage caps, seat limits | Higher limits | Unlimited or custom |
| **Support** | Self-serve, community | Email, chat | Dedicated, SLA |
| **Target** | Individual, evaluator | Team, SMB | Department, enterprise |

**Tier naming:** Avoid "Basic" (implies inferior). Use aspirational names or simple Good/Pro/Enterprise.

## Price Research Methods

| Method | Effort | When to Use |
|--------|--------|-------------|
| **Van Westendorp** | Low | Early validation. Ask 4 price sensitivity questions. |
| **Gabor-Granger** | Low | Test specific price points for conversion likelihood. |
| **MaxDiff** | Medium | Rank feature importance to inform packaging. |
| **Conjoint Analysis** | High | Optimize feature bundles + price combinations. |
| **Competitor benchmarking** | Low | Establish market price range. Not sufficient alone. |

## Anti-Patterns to Avoid

- **F3: Pricing theater** — Spending months on pricing research instead of shipping and iterating.
- **M3: Pricing theater (marketing)** — Three tiers where middle is obviously the "right" choice with no real differentiation.
- **F2: Ignoring unit economics** — Price must cover fully-loaded cost of delivery including support.
- **F7: Anchor to competitor pricing** — Your costs and value delivery differ. Price on your value.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Value alignment** | Price tied to measurable customer value | Reasonable but not validated | Cost-plus or competitor-matching |
| **Packaging logic** | Clear tier differentiation with upgrade triggers | Tiers exist but overlap | Features arbitrarily distributed |
| **Metric choice** | Metric grows with customer value | Reasonable metric | Metric creates friction |
| **Research backing** | 2+ validation methods used | Competitor research only | Gut feeling |
| **Expansion path** | Natural upsell from usage growth | Manual upgrade prompts | No expansion mechanism |
| **Simplicity** | Customer can self-select in <30 seconds | Needs FAQ to understand | Requires sales call to understand |
| **Margin protection** | Unit economics validated per tier | Blended margin positive | Margin unknown |

**28+ = Launch-ready | 21-27 = Needs validation | <21 = Fundamental rethink**

## Cross-Skill References

- **Upstream:** `product-marketing-context` (ICP, positioning), `unit-economics` (cost structure)
- **Downstream:** `billing-design` (implementation), `financial-model` (revenue projections)
- **Parallel:** `pricing-strategy` (strategic decisions), `ltd-deal-structure` (lifetime deals)
- **Council:** Submit to `council-finance` for margin validation
