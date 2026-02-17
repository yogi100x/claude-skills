# AI Vendor Evaluation

Evaluate and select third-party AI services, APIs, and models for product integration.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for AI feature requirements
2. Read `.claude/finance-context.md` for budget constraints

## Decision Tree: Build vs Buy

```
Should you build or buy?
├── Core differentiator (AI IS your product)
│   └── Build: Custom models, proprietary data advantage
├── Feature enhancement (AI improves your product)
│   └── Buy first, build later if unit economics demand it
├── Commodity capability (translation, OCR, speech-to-text)
│   └── Buy: Use best-in-class API
└── Experimental (testing AI in new area)
    └── Buy: Validate with API before investing in custom
```

## Evaluation Framework

### 1. Technical Fit

| Criteria | Weight | Evaluation Method |
|----------|--------|-------------------|
| **Accuracy** | High | Benchmark on your data (not vendor's benchmarks) |
| **Latency** | High | Test p50, p95, p99 in your environment |
| **Throughput** | Medium | Load test at 2x expected peak |
| **Context/input limits** | Medium | Test with your largest inputs |
| **Output quality** | High | Blind evaluation by domain experts |
| **Customization** | Medium | Fine-tuning, prompt engineering, RAG support |
| **Integration** | Medium | SDK quality, documentation, examples |

### 2. Reliability & Security

| Criteria | Weight | Evaluation Method |
|----------|--------|-------------------|
| **Uptime SLA** | High | Historical uptime, SLA terms |
| **Data privacy** | High | DPA available? Data retention? Where processed? |
| **SOC 2 / ISO 27001** | High | Certifications verified |
| **Data usage** | Critical | Does vendor train on your data? Opt-out available? |
| **Disaster recovery** | Medium | Multi-region? Failover? |

### 3. Business Viability

| Criteria | Weight | Evaluation Method |
|----------|--------|-------------------|
| **Pricing** | High | Cost per unit at your scale (not just list price) |
| **Pricing model** | Medium | Per-token, per-call, subscription, usage-based |
| **Lock-in risk** | High | Proprietary formats? Switching cost? |
| **Company stability** | Medium | Funding, revenue, market position |
| **Support quality** | Medium | Response time, escalation path, dedicated CSM |

### 4. Compliance & Ethics

| Criteria | Weight | Evaluation Method |
|----------|--------|-------------------|
| **Bias documentation** | Medium | Model cards, fairness testing published? |
| **Content safety** | High | Safety features, content filtering |
| **Regulatory compliance** | High | GDPR, EU AI Act readiness |
| **Transparency** | Medium | Model details, training data disclosures |

## Vendor Comparison Template

| Criteria | Vendor A | Vendor B | Vendor C |
|----------|----------|----------|----------|
| Accuracy (your data) | X% | Y% | Z% |
| Latency p50 | Xms | Yms | Zms |
| Cost per 1K calls | $X | $Y | $Z |
| Data privacy | ✓/✗ | ✓/✗ | ✓/✗ |
| Trains on your data? | ✓/✗ | ✓/✗ | ✓/✗ |
| SLA uptime | X% | Y% | Z% |
| **Total score** | X/100 | Y/100 | Z/100 |

## Anti-Patterns to Avoid

- **A6: Choosing based on vendor benchmarks only** — Test on YOUR data with YOUR use cases.
- **A10: No data processing agreement** — Every AI vendor processing personal data needs a DPA.
- **A11: Ignoring vendor lock-in** — Abstract the vendor behind an interface. Plan for switching.
- **A12: No cost projection** — AI costs scale non-linearly. Model costs at 10x current usage.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Evaluation rigor** | Multi-criteria scoring on your data | Some testing | Vendor demo only |
| **Data privacy** | DPA signed, data usage verified | DPA requested | No data privacy review |
| **Cost modeling** | Projected costs at multiple scale points | Current cost known | No cost analysis |
| **Lock-in assessment** | Abstraction layer, switching plan | Aware of risk | Full lock-in |
| **Compliance** | SOC 2, GDPR, content safety verified | Some compliance checked | No compliance review |
| **Comparison** | 3+ vendors compared systematically | 2 vendors compared | Single vendor |
| **POC** | Proof of concept with production-like data | Basic testing | No POC |

**28+ = Informed decision | 21-27 = Needs more evaluation | <21 = Risky selection**

## Cross-Skill References

- **Upstream:** `product-marketing-context` (requirements), `ai-ethics-policy` (vendor requirements)
- **Downstream:** `data-processing-agreement` (vendor DPA), `ai-monitoring-setup` (vendor monitoring)
- **Council:** Submit to `council-ai` + `council-finance` for joint review
