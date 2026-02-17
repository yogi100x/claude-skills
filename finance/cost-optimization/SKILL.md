# Cost Optimization

Identify and eliminate unnecessary costs while maintaining product quality and growth capacity.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for current cost structure and margins
2. Read `.claude/product-marketing-context.md` for growth priorities (don't cut growth drivers)

## Decision Tree: Optimization Approach

```
What's driving the need?
├── Runway extension (burn rate too high)
│   └── Triage: cut non-essential, renegotiate contracts, defer hires
├── Margin improvement (revenue growing, margins flat)
│   └── Focus: COGS optimization, vendor consolidation, automation
├── Efficiency (doing too much with too many resources)
│   └── Focus: Process automation, team restructuring, tool consolidation
└── Pre-fundraise (showing capital efficiency)
    └── Focus: Burn multiple, cost per unit metrics, defensible cuts
```

## Cost Audit Framework

### Infrastructure Costs

| Area | Common Waste | Quick Win |
|------|-------------|-----------|
| **Cloud hosting** | Over-provisioned instances, unused resources | Right-size instances, reserved pricing |
| **Database** | Oversized tier, no connection pooling | Downsize if usage <50%, enable pooling |
| **Third-party APIs** | Paying for unused volume, redundant services | Audit usage vs plan, negotiate annual |
| **Monitoring/logging** | Excessive log retention, duplicate tools | Reduce retention, consolidate tools |
| **AI/ML costs** | Wrong model size, no caching, redundant calls | Cache responses, use smaller models where possible |

### People Costs

| Lever | Impact | Risk |
|-------|--------|------|
| **Hiring freeze** | Immediate burn reduction | Slower feature velocity |
| **Contractor-to-FTE** | Lower cost if long-term need | Contractor flexibility lost |
| **FTE-to-contractor** | Lower cost if short-term need | Knowledge loss |
| **Offshore/nearshore** | 40-60% cost reduction for some roles | Communication overhead |
| **Automation** | Eliminate recurring manual work | Upfront investment required |

### Vendor Negotiation

```
Negotiation playbook:
1. Audit actual usage vs contracted volume
2. Get competitive quotes (even if not switching)
3. Offer: annual commitment for 20-40% discount
4. Offer: case study/testimonial for discount
5. Ask for startup/growth pricing if applicable
6. Time negotiations near vendor's quarter-end
```

## Anti-Patterns to Avoid

- **F15: Cutting growth to improve margins** — Cutting S&M spend that has positive ROI is burning value.
- **F2: Ignoring unit economics** — Cut costs that don't affect unit economics first.
- **T10: Premature optimization** — Don't optimize infrastructure costs at $10K/month. Focus on revenue.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Cost visibility** | Line-item breakdown with trend data | Category-level view | Lump-sum expenses |
| **Impact sizing** | Dollar impact estimated per optimization | Relative sizing | No sizing |
| **Risk assessment** | Each cut evaluated for growth/quality impact | Some risk consideration | Blind cost cutting |
| **Quick wins identified** | 3+ immediate actions, <1 week to implement | 1-2 quick wins | No prioritization |
| **Vendor strategy** | Negotiation plan with competitive data | Basic renegotiation | No vendor management |
| **Measurement plan** | Track cost metrics monthly after changes | One-time measurement | No follow-up |
| **Stakeholder alignment** | Trade-offs discussed with team | Informed leadership | Unilateral cuts |

**28+ = Actionable plan | 21-27 = Needs prioritization | <21 = Insufficient analysis**

## Cross-Skill References

- **Upstream:** `financial-model` (cost structure), `unit-economics` (margin data)
- **Downstream:** `budget-allocation` (reallocation), `kpi-dashboard` (tracking savings)
- **Council:** Submit to `council-finance` for risk assessment
