# IP Protection

Identify and protect intellectual property assets for software companies.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for product name, features, brand assets

## Decision Tree: IP Type

```
What do you need to protect?
├── Brand name / Logo
│   └── Trademark registration
│       → Search USPTO/EUIPO, file application, monitor infringement
├── Source code / Algorithms
│   └── Trade secret + copyright (automatic)
│       → NDAs, access controls, employment agreements with IP assignment
├── Inventions / Novel methods
│   └── Patent (if novel and non-obvious)
│       → Provisional patent (12 months protection), then full application
├── Content / Documentation
│   └── Copyright (automatic upon creation)
│       → Register for enhanced enforcement, add copyright notices
└── Database / Data compilation
    └── Database rights (EU) + trade secret
        → Access controls, licensing terms
```

## IP Protection Matrix

| Asset | Protection Type | Cost | Timeline | Enforcement |
|-------|----------------|------|----------|-------------|
| **Company name** | Trademark | $250-$1,500 per class | 6-18 months | Cease & desist, litigation |
| **Logo** | Trademark + copyright | $250-$1,500 | 6-18 months | Same as above |
| **Source code** | Copyright + trade secret | $0 (automatic) | Immediate | DMCA, litigation |
| **Algorithms** | Patent or trade secret | $5K-$15K (patent) | 2-4 years (patent) | Infringement claim |
| **Domain name** | Registration | $10-$50/year | Immediate | UDRP dispute |
| **Brand content** | Copyright | $0-$500 (registration) | Immediate | DMCA takedown |

## Employee/Contractor IP Assignment

Every person who writes code or creates content must have:

```
Key clauses:
1. Work-for-hire assignment: All work created in scope of employment belongs to company
2. Invention assignment: All inventions related to business are assigned
3. Prior inventions disclosure: List anything created before joining
4. Moral rights waiver: Where applicable (EU/UK)
5. Non-compete / Non-solicit: If enforceable in jurisdiction
6. Confidentiality: Survives termination (2-5 years)
```

## Open Source Compliance

| License Type | Can Use? | Must Disclose Source? | Patent Grant? |
|-------------|----------|----------------------|---------------|
| **MIT** | Yes | No | No |
| **Apache 2.0** | Yes | No | Yes |
| **BSD** | Yes | No | No |
| **GPL v2/v3** | Carefully | Yes (if distributed) | Yes (v3) |
| **AGPL** | Very carefully | Yes (even SaaS) | Yes |
| **LGPL** | Yes (with linking rules) | Modified library only | No |

**Rule: Never use AGPL-licensed code in proprietary SaaS without legal review.**

## Anti-Patterns to Avoid

- **L6: No IP assignment from contractors** — Without written assignment, contractor may own the code.
- **L10: Using AGPL code in proprietary product** — May require open-sourcing your entire codebase.
- **L11: No trademark search before naming** — Renaming after launch is expensive. Search first.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **IP inventory** | All assets cataloged with protection type | Key assets identified | No inventory |
| **Trademark** | Registered in key markets | Filed or searching | Not considered |
| **Assignment agreements** | All contributors have signed IP assignment | Most employees covered | No agreements |
| **Open source compliance** | License audit completed, policy in place | Aware of licenses used | No tracking |
| **Trade secret measures** | Access controls, NDAs, documented processes | Some measures | No protection |
| **Domain protection** | Key domains and variations secured | Primary domain only | At risk |
| **Enforcement plan** | Monitoring and response process | Reactive only | No plan |

**28+ = Well-protected | 21-27 = Gaps to address | <21 = Significant IP risk**

## Cross-Skill References

- **Upstream:** `product-marketing-context` (brand assets), `contract-drafting` (IP clauses)
- **Downstream:** `employment-agreement` (IP assignment), `terms-of-service` (IP provisions)
- **Council:** Submit to `council-legal` for IP strategy review
