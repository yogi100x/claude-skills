# Treasury Management

Manage cash reserves, banking relationships, and financial risk for software companies.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for cash position, burn rate, runway

## Decision Tree: Treasury Priority

```
What's your runway?
├── <6 months
│   └── Emergency: Minimize burn, prepare bridge financing
├── 6-12 months
│   └── Conservative: High-yield savings, minimize risk, prepare fundraise
├── 12-24 months
│   └── Balanced: T-bills or money market for operating reserves, negotiate banking terms
└── >24 months
    └── Optimized: Tiered cash deployment, earn yield on excess cash
```

## Cash Tiering Strategy

| Tier | Purpose | Amount | Vehicle | Liquidity |
|------|---------|--------|---------|-----------|
| **Operating** | Next 30 days expenses | 1 month burn | Checking account | Instant |
| **Reserve** | 2-3 months buffer | 2-3 months burn | High-yield savings | 1 day |
| **Short-term** | 3-12 months runway | Remaining cash | T-bills, money market | 1-5 days |
| **Strategic** | >12 months out | Excess only | Short-term treasuries | 1-30 days |

**Rule: Never invest cash you need within 6 months in anything with principal risk.**

## Banking Setup

| Account | Purpose | Provider Priority |
|---------|---------|-------------------|
| **Primary operating** | Payroll, vendors, revenue | SVB, Mercury, Brex |
| **Reserve account** | Emergency fund (different bank) | Large bank (Chase, BofA) |
| **Revenue collection** | Stripe payouts | Matches primary |
| **International** | Foreign payments if applicable | Wise, Mercury |

**Critical: Spread cash across 2+ banks.** FDIC insures $250K per bank. Startups with >$250K in one account have concentration risk.

## Anti-Patterns to Avoid

- **F1: All cash in one bank** — SVB collapse proved the risk. Diversify.
- **F15: Investing operating cash** — Don't chase yield with money you need to make payroll.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Cash visibility** | Daily balance tracking, 13-week cash flow forecast | Weekly tracking | Monthly bank statement |
| **Diversification** | Cash spread across 2+ banks, FDIC considered | Two banks | Single bank |
| **Yield optimization** | Tiered deployment earning yield on reserves | High-yield savings only | Checking account only |
| **Runway tracking** | Monthly burn calculated, runway projected | Rough estimate | Unknown |
| **Controls** | Dual signatures, approval workflows, segregation of duties | Some controls | No controls |
| **Foreign exchange** | FX exposure identified and managed | Aware of exposure | No FX management |
| **Emergency plan** | Bridge financing options identified, relationships maintained | Some options | No contingency |

**28+ = Well-managed | 21-27 = Needs controls | <21 = Cash at risk**

## Cross-Skill References

- **Upstream:** `financial-model` (burn rate, projections), `fundraising-deck` (round timing)
- **Downstream:** `budget-allocation` (cash available for deployment)
- **Council:** Submit to `council-finance` for risk review
