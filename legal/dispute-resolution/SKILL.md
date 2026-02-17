# Dispute Resolution

Design and implement dispute resolution processes for customer conflicts, contract disputes, and platform issues.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for business model and customer types
2. Review terms of service for existing dispute provisions

## Decision Tree: Resolution Method

```
What type of dispute?
├── Customer complaint (billing, service quality)
│   └── Internal resolution: Support → escalation → credit/refund
├── Contract dispute (vendor, partner)
│   └── Negotiation → mediation → arbitration → litigation
├── Platform dispute (marketplace: buyer vs seller)
│   └── Internal dispute resolution → escrow release → appeal
├── IP dispute (infringement claim)
│   └── DMCA process → negotiation → litigation
├── Employment dispute
│   └── Internal HR → mediation → arbitration → litigation
└── Regulatory dispute
    └── Respond to inquiry → negotiate → formal proceedings
```

## Dispute Resolution Escalation

| Level | Method | Cost | Time | Binding? |
|-------|--------|------|------|----------|
| **1. Direct negotiation** | Parties discuss directly | Free | Days-weeks | No |
| **2. Mediation** | Neutral mediator facilitates | $2-10K | Weeks | No (unless settlement) |
| **3. Arbitration** | Arbitrator decides | $5-50K | Months | Yes (usually) |
| **4. Litigation** | Court decides | $50K-$500K+ | Months-years | Yes |

## Arbitration Clause Template Elements

```
Key provisions:
- Administering body (AAA, JAMS, ICC)
- Number of arbitrators (1 for <$250K, 3 for larger)
- Seat/venue of arbitration
- Governing law
- Language
- Class action waiver (US — check enforceability)
- Small claims exception (allow small claims court)
- Emergency relief preservation (allow court injunctions)
```

## Platform Dispute Resolution (Marketplaces)

| Step | Action | Timeline |
|------|--------|----------|
| 1 | Buyer/seller attempts resolution directly | 3 days |
| 2 | Escalate to platform support | 2 days for initial response |
| 3 | Platform investigates (evidence from both sides) | 5 business days |
| 4 | Platform decision issued | Same day as investigation |
| 5 | Appeal (one per party) | 5 days to file, 3 days to decide |
| 6 | Final decision | Binding |

## Anti-Patterns to Avoid

- **L8: No dispute resolution clause** — Defaults to expensive litigation in unpredictable jurisdiction.
- **L10: Mandatory arbitration without small claims exception** — Courts may void overly restrictive clauses.
- **L12: One-sided dispute resolution** — Courts scrutinize unfair terms in consumer contracts.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Process clarity** | Step-by-step with timelines for all dispute types | Key processes defined | Ad-hoc handling |
| **Fairness** | Balanced process for both parties | Mostly fair | One-sided |
| **Accessibility** | Low-cost initial resolution, small claims preserved | Some accessible options | Expensive for users |
| **Documentation** | Templates, evidence procedures, decision records | Basic documentation | No records |
| **Enforceability** | Legal review confirms enforceability | Likely enforceable | Untested |
| **Escalation path** | Clear escalation with different resolution methods | Some escalation | Single method |
| **Speed** | Initial response SLA, resolution timeline | General timeline | No timeline |

**28+ = Fair and enforceable | 21-27 = Needs legal review | <21 = Dispute handling risk**

## Cross-Skill References

- **Upstream:** `terms-of-service` (dispute clause), `contract-drafting` (contract disputes)
- **Downstream:** `compliance-checklist` (dispute tracking)
- **Council:** Submit to `council-legal` for enforceability review
