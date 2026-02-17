# Human Oversight Protocol

Design human-in-the-loop and human-on-the-loop systems for AI features requiring oversight.

## Context Sync Protocol

1. Read model cards for AI risk levels
2. Read `.claude/product-marketing-context.md` for which features need oversight

## Decision Tree: Oversight Level

```
What's the AI's role?
├── Suggestion (human decides)
│   └── Human-in-the-loop: AI recommends, human approves
│       → Low overhead, high human agency
├── Default with override (AI decides, human can change)
│   └── Human-on-the-loop: AI acts, human monitors and intervenes
│       → Medium overhead, moderate human agency
├── Autonomous (AI decides and acts)
│   └── Human-over-the-loop: AI acts, human reviews periodically
│       → Low overhead, low human agency (high-risk: avoid for consequential decisions)
└── Prohibited (too risky for automation)
    └── Human-only: No AI involvement
        → High overhead, full human agency
```

## Oversight Design Matrix

| Feature Type | Suggested Level | Review Trigger | Reviewer |
|-------------|-----------------|----------------|----------|
| Content generation | Human-on-the-loop | Confidence < 80%, flagged content | Product team |
| Hiring recommendations | Human-in-the-loop | Every recommendation | Recruiter |
| Fraud detection | Human-on-the-loop | Every flag (false positive review) | Trust & safety |
| Automated grading | Human-in-the-loop for disputes | Score disputes, edge cases | Subject expert |
| Pricing decisions | Human-in-the-loop | Every change | Product/finance |
| Content moderation | Human-on-the-loop | Appeals, edge cases | Trust & safety |

## Override Protocol

```
1. AI makes decision/recommendation
2. Human reviewer sees: decision + explanation + confidence + alternatives
3. Reviewer options:
   a. Approve (log approval, proceed)
   b. Modify (log modification + reason, proceed with changes)
   c. Reject (log rejection + reason, take alternative action)
   d. Escalate (insufficient info to decide, escalate to senior reviewer)
4. All decisions logged with timestamp, reviewer ID, and rationale
```

## Anti-Patterns to Avoid

- **A3: Rubber-stamp oversight** — If humans always approve, oversight is theater. Track override rate.
- **A7: No escalation path** — Reviewers need a way to escalate edge cases.
- **A9: Automation bias** — Design UIs that don't anchor reviewers on the AI's recommendation.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Oversight level** | Appropriate to risk level per feature | Mostly appropriate | One-size-fits-all |
| **Reviewer capability** | Trained reviewers with domain expertise | Some training | Untrained reviewers |
| **Override mechanism** | Easy to override with logged rationale | Override possible | Difficult to override |
| **Escalation path** | Clear escalation with response SLA | Some escalation | No escalation |
| **Audit trail** | Complete decision log with reasoning | Basic logging | No audit trail |
| **Override rate monitoring** | Tracked and analyzed for model improvement | Tracked | Not tracked |
| **Reviewer workload** | Sustainable volume, ergonomic UI | Manageable | Overwhelmed |

**28+ = Meaningful oversight | 21-27 = Needs process refinement | <21 = Theater**

## Cross-Skill References

- **Upstream:** `ai-ethics-policy` (oversight requirements), `model-card` (risk levels)
- **Downstream:** `ai-monitoring-setup` (override rate tracking)
- **Council:** Submit to `council-ai` for protocol review
