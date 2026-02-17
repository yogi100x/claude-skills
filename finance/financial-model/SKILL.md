---
name: financial-model
version: 2.0.0
description: "When the user needs to build financial projections, revenue models, or business plans. Also use when the user mentions 'financial model,' 'projections,' 'forecast,' 'P&L,' 'income statement,' 'cash flow statement,' 'balance sheet,' or 'financial planning.' This skill covers 3-statement models, scenario analysis, and assumption frameworks."
---

# Financial Modeling

You are an expert in startup and SaaS financial modeling. Your goal is to help build rigorous, assumption-driven financial models that inform decision-making and fundraising.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/finance-context.md
  ├─ Current revenue and growth rate
  ├─ Cost structure (fixed vs variable)
  ├─ Funding stage and runway
  └─ Key financial assumptions

Read: .claude/product-marketing-context.md (if exists)
  ├─ Pricing model and tiers
  ├─ Customer segments and personas
  └─ Go-to-market motion
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Model Type Selection

```
START: What's the primary purpose?

├─ FUNDRAISING (convince investors)
│  ├─ Stage?
│  │  ├─ Pre-seed/Seed → Bottom-up model (realistic near-term)
│  │  ├─ Series A → Top-down + bottom-up blend (TAM → capture rate)
│  │  └─ Series B+ → Full 3-statement model with scenarios
│  └─ Key: Conservative base case, show path to profitability

├─ OPERATIONAL PLANNING (guide decisions)
│  ├─ Monthly granularity for Year 1
│  ├─ Quarterly for Years 2-3
│  ├─ Annual for Years 4-5
│  └─ Key: Actuals vs forecast tracking, rolling updates

├─ SCENARIO ANALYSIS (evaluate options)
│  ├─ Base / Optimistic / Pessimistic cases
│  ├─ Sensitivity analysis on key drivers
│  └─ Key: Identify which assumptions matter most

└─ BOARD REPORTING (communicate performance)
   ├─ Variance analysis (plan vs actual)
   ├─ Updated projections based on actuals
   └─ Key: Narrative around numbers
```

---

## Core Model Architecture

### Revenue Model Components

| Component | SaaS | Marketplace | E-Commerce | Services |
|-----------|------|-------------|------------|----------|
| **Revenue Driver** | MRR × Customers | GMV × Take Rate | Orders × AOV | Hours × Rate |
| **Growth Lever** | New MRR + Expansion | Supply/Demand growth | Traffic × CVR | Headcount |
| **Churn Impact** | Logo + Revenue churn | Seller/Buyer churn | Repeat rate | Client retention |
| **Key Metric** | Net Revenue Retention | Liquidity | Customer LTV | Utilization |

### Three-Statement Model Framework

**Income Statement (P&L):**
```
Revenue
  - COGS (hosting, support, third-party costs)
= Gross Profit (target: 70-85% for SaaS)
  - Sales & Marketing
  - R&D / Engineering
  - G&A (admin, legal, finance)
= Operating Income (EBIT)
  - Interest, taxes
= Net Income
```

**Cash Flow Statement:**
```
Net Income
  + Non-cash adjustments (depreciation, stock-based comp)
  + Working capital changes
= Operating Cash Flow
  - CapEx
= Free Cash Flow
  + Financing activities (debt, equity)
= Net Cash Change
```

**Balance Sheet:**
```
Assets = Liabilities + Equity
  Cash, AR, Prepaid | AP, Deferred Revenue, Debt | Equity, Retained Earnings
```

### Assumption Framework

Build models from assumptions, not targets:

| Category | Key Assumptions | How to Validate |
|----------|----------------|-----------------|
| **Revenue** | New customers/mo, ARPU, churn rate, expansion rate | Historical data, cohort analysis |
| **Sales** | Lead volume, conversion rate, sales cycle, ACV | Pipeline data, win rates |
| **Marketing** | CAC by channel, spend allocation, payback period | Channel performance data |
| **Headcount** | Hire plan, avg salary, ramp time | Comp benchmarks, capacity models |
| **Infrastructure** | Cost per customer, scaling factor | Usage data, vendor pricing |

### SaaS Metrics Waterfall

```
Beginning MRR
  + New MRR (new customers × ARPU)
  + Expansion MRR (upsells + cross-sells)
  - Contraction MRR (downgrades)
  - Churned MRR (cancellations)
= Ending MRR

Net New MRR = New + Expansion - Contraction - Churned
Net Revenue Retention = (Ending MRR - New MRR) / Beginning MRR
```

### Scenario Analysis Framework

| Scenario | Revenue Growth | Churn | CAC | Use When |
|----------|---------------|-------|-----|----------|
| **Base** | Current trend | Current rate | Current CAC | Default planning |
| **Optimistic** | +50% of base | -25% of base | -20% of base | Best case for fundraising |
| **Pessimistic** | -30% of base | +50% of base | +30% of base | Stress testing runway |
| **Break-even** | Solve for this | Base rate | Base CAC | Find sustainability point |

---

## Anti-Pattern References

| ID | Anti-Pattern | Skill Impact |
|----|-------------|--------------|
| F1 | Confusing revenue with cash | Model shows revenue recognition but not actual cash timing |
| F2 | Ignoring unit economics | Model projects growth without validating per-unit profitability |
| F3 | Pricing too low | Revenue projections assume below-market pricing |
| F4 | No scenario analysis | Single-scenario model creates false confidence |
| F5 | Hockey stick without drivers | Growth curve not backed by bottoms-up assumptions |

---

## Industry Variations

| Business Type | Model Focus | Key Drivers | Unique Considerations |
|---------------|-------------|-------------|----------------------|
| **B2B SaaS** | MRR waterfall, cohort analysis | Net retention, CAC payback | Long sales cycles, annual contracts |
| **Marketplace** | GMV, take rate, liquidity | Supply/demand growth, unit economics | Chicken-and-egg dynamics |
| **E-Commerce** | Revenue per visitor, AOV, repeat rate | Traffic, conversion, returns | Inventory, seasonal patterns |
| **Developer Tools** | Usage growth, conversion to paid | Free→paid conversion, expansion | Bottom-up adoption, long PLG cycles |
| **Fintech** | Transaction volume, interchange | Processing volume, fraud rate | Regulatory costs, compliance |

---

## Benchmarks

| Metric | Seed | Series A | Series B+ |
|--------|------|----------|-----------|
| **Revenue** | $0-500K ARR | $1-5M ARR | $5-20M+ ARR |
| **Growth Rate** | 3x+ YoY | 2-3x YoY | 1.5-2x YoY |
| **Gross Margin** | 50-70% | 65-80% | 75-85% |
| **Burn Multiple** | 3-5x | 1.5-3x | <1.5x |
| **CAC Payback** | 18-24 months | 12-18 months | <12 months |
| **Rule of 40** | Not expected | Approaching | 40%+ |

---

## Quality Rubric

| Dimension | 1 (Weak) | 3 (Adequate) | 5 (Strong) |
|-----------|----------|-------------|------------|
| **Assumption clarity** | Hardcoded numbers | Some assumptions labeled | All assumptions explicit, sourced, adjustable |
| **Revenue logic** | Single revenue line | Multiple streams | Bottoms-up with cohorts and retention |
| **Cost modeling** | Fixed cost block | Fixed vs variable split | Per-unit COGS, scaling functions |
| **Scenario coverage** | Single scenario | Base + one alternative | Base/bull/bear with sensitivity analysis |
| **Cash flow accuracy** | Revenue = cash | Basic timing adjustments | Full cash flow with working capital |
| **Validation** | No benchmarks | Industry comparisons | Historical actuals vs. forecast tracking |
| **Presentation** | Raw spreadsheet | Formatted summary | Dashboard with charts and narrative |

**Score: /35. Ship at 28+. Revise at 21-27. Rethink below 21.**

---

## Cross-Skill References

| Relationship | Skill | How They Connect |
|-------------|-------|-----------------|
| **Feeds into** | unit-economics | Financial model provides inputs for unit economics analysis |
| **Feeds into** | fundraising-deck | Model numbers populate deck financials |
| **Feeds into** | budget-allocation | Model guides where to allocate spend |
| **Depends on** | setup | Context files provide model inputs |
| **Parallel** | kpi-dashboard | Dashboard tracks actuals vs model projections |
| **Review** | council-finance | Validates model assumptions and structure |

---

## Council Integration

After building the financial model:
1. Submit to **council-finance** for assumption validation
2. Cross-reference with **unit-economics** skill for per-unit profitability
3. If fundraising, feed into **fundraising-deck** skill
4. Track actuals using **kpi-dashboard** skill

---

## Worked Example

**Scenario:** Early-stage B2B SaaS, $50K MRR, building Series A model

**Approach:**
1. Context sync → Read existing revenue data and growth assumptions
2. Decision tree → Fundraising purpose → Top-down + bottom-up blend
3. Revenue model → MRR waterfall with 5% monthly logo churn, 110% net retention
4. Cost model → Current 8-person team scaling to 25 over 18 months
5. Three scenarios → Base (2.5x growth), Bull (3.5x), Bear (1.5x)
6. Cash flow → 18 months runway at current burn, 24 months with round

**Output format:**
```
## Financial Model Summary

### Key Assumptions
[Numbered list with source/rationale for each]

### Revenue Projections (Monthly for Y1, Quarterly Y2-Y3)
[Table with MRR waterfall]

### P&L Summary
[Annual P&L with gross margin progression]

### Cash Flow & Runway
[Monthly cash position chart]

### Scenario Comparison
[Side-by-side base/bull/bear]

### Sensitivity Analysis
[Which assumptions most impact outcomes]
```

---

## Output Checklist

Before delivering any financial model, verify:

- [ ] All assumptions are explicit and adjustable (no magic numbers)
- [ ] Revenue model is bottoms-up with cohort logic
- [ ] Costs are split fixed vs variable with scaling assumptions
- [ ] At least 3 scenarios modeled (base, optimistic, pessimistic)
- [ ] Cash flow timing accounts for payment terms and deferred revenue
- [ ] Key metrics calculated (CAC, LTV, payback, burn rate, runway)
- [ ] Benchmarks compared against stage-appropriate peers
- [ ] Model validated against historical actuals (if available)
