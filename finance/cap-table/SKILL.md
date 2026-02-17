# Cap Table

Design and manage capitalization tables tracking ownership, dilution, and equity allocation.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for round history and valuation
2. If first round, gather: founders, split rationale, vesting terms

## Decision Tree: Cap Table Scenario

```
What do you need?
├── Initial setup (pre-funding)
│   └── Founder equity split + option pool
├── Preparing for funding round
│   └── Pre-money modeling + dilution scenarios + option pool expansion
├── Post-round cleanup
│   └── Record investment, update ownership %, create new share classes
└── Secondary / Liquidity event
    └── Waterfall analysis: who gets what at various exit prices
```

## Cap Table Structure

### Share Classes

| Class | Holders | Rights | Typical Terms |
|-------|---------|--------|--------------|
| **Common** | Founders, employees | Basic voting, last in liquidation | 4-year vest, 1-year cliff |
| **Series Seed** | Seed investors | 1x liquidation preference, pro-rata | SAFE or priced round |
| **Series A** | VC investors | 1x non-participating preferred, board seat | Priced round |
| **Options (ESOP)** | Employees | Right to purchase common | ISOs or NSOs |

### Dilution Modeling

```
Pre-money valuation: $10M
Investment amount: $2.5M
Post-money valuation: $12.5M
New shares issued: Investment / Price per share

Investor ownership: $2.5M / $12.5M = 20%
Existing holders diluted by: 20% (proportionally)

Example:
  Founder A: 60% → 48% (diluted 20%)
  Founder B: 30% → 24%
  ESOP: 10% → 8%
  Series A: 0% → 20%
```

### Option Pool

| Stage | Typical ESOP Size | Notes |
|-------|-------------------|-------|
| Pre-seed | 10-15% | Created from founder shares |
| Seed | 10-15% | Often expanded pre-round (comes from existing holders) |
| Series A | 15-20% | VCs typically require expansion pre-money |
| Series B+ | Top-up to 15-20% | Replenish as grants are made |

## Vesting Schedules

**Standard 4-year vest with 1-year cliff:**
```
Month 0-11: 0% vested (cliff period)
Month 12: 25% vests (cliff release)
Month 13-48: 1/48th vests monthly (linear)
Month 48: 100% vested

Acceleration clauses:
- Single trigger: 25-50% accelerates on acquisition
- Double trigger: 50-100% accelerates on acquisition + termination
```

## Waterfall Analysis

Model exit proceeds at various valuations:

```
Exit at $50M:
1. Liquidation preferences paid first: Series A gets 1x ($2.5M)
2. Remaining $47.5M distributed pro-rata to all shareholders
   - Series A (participating): $2.5M + 20% × $47.5M = $12M
   - Series A (non-participating): max($2.5M, 20% × $50M) = $10M
   - Founders: remaining based on ownership %
```

## Anti-Patterns to Avoid

- **F9: Unequal founder splits without rationale** — 50/50 splits cause problems. Document why.
- **F10: No vesting on founder shares** — All founders should vest. Protects everyone.
- **F11: Option pool too small** — Running out of options mid-round forces painful dilution.
- **F12: Ignoring liquidation preferences** — Participating preferred can dramatically change founder economics.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Accuracy** | All shares, options, and conversions tracked precisely | Minor rounding issues | Missing share classes |
| **Scenario modeling** | 3+ exit scenarios with waterfall | Single exit scenario | No waterfall |
| **Dilution clarity** | Per-round dilution shown for all holders | Summary dilution only | No dilution tracking |
| **Option pool** | Grant tracking, vesting schedules, available pool | Pool size tracked | No option management |
| **Legal alignment** | Matches term sheets and corporate docs | Mostly aligned | Discrepancies exist |
| **Presentation** | Clean summary + detailed backup | One view only | Messy spreadsheet |
| **Forward modeling** | Next 2-3 rounds modeled with assumptions | Next round only | No forward look |

**28+ = Board/investor ready | 21-27 = Needs cleanup | <21 = Legal risk**

## Cross-Skill References

- **Upstream:** `fundraising-deck` (round terms), `financial-model` (valuation basis)
- **Downstream:** `employment-agreement` (option grants), `tax-strategy` (equity tax implications)
- **Council:** Submit to `council-finance` + `council-legal` for compliance
