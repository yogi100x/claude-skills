# Explainability Design

Design user-facing explanations for AI-powered features that build trust and meet regulatory requirements.

## Context Sync Protocol

1. Read model cards for AI features being explained
2. Read `.claude/product-marketing-context.md` for user sophistication level

## Decision Tree: Explanation Type

```
Who needs the explanation?
├── End users (affected by AI decisions)
│   └── Simple, actionable: "We recommended this because..."
├── Expert users (data scientists, reviewers)
│   └── Technical: Feature importance, confidence scores, model details
├── Regulators / Auditors
│   └── Comprehensive: Methodology, validation, fairness metrics
└── Internal team
    └── Debug-oriented: Attention weights, token probabilities, decision traces
```

## Explanation Patterns

| Pattern | Best For | Example |
|---------|----------|---------|
| **Feature attribution** | "Why this recommendation?" | "Based on your React experience and SF location" |
| **Counterfactual** | "What would change the outcome?" | "With 2 more years of experience, you'd score higher" |
| **Example-based** | "What's similar?" | "Similar candidates scored 85-92 on this assessment" |
| **Confidence indicator** | "How sure are you?" | "High confidence (92%)" or "Best guess — limited data" |
| **Process explanation** | "How does this work?" | "We analyze 6 factors: skills, experience, location..." |
| **Comparison** | "Why this over that?" | Side-by-side score breakdown |

## Implementation Guidelines

```
User-facing explanation checklist:
✓ Written in plain language (no ML jargon)
✓ Specific to this decision (not generic)
✓ Actionable (user can improve outcome)
✓ Honest about uncertainty
✓ Doesn't expose gaming vectors
✓ Consistent across similar decisions
✓ Available at point of decision
```

## Anti-Patterns to Avoid

- **A4: No explanation for consequential decisions** — GDPR Art. 22 requires explanations for automated decisions.
- **A6: Technical explanations for non-technical users** — Match explanation to audience.
- **A11: Explanations that enable gaming** — Don't reveal exact weights or thresholds that can be manipulated.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Clarity** | Plain language, specific to decision | Somewhat clear | Technical jargon |
| **Accuracy** | Explanation reflects actual model behavior | Approximately correct | Misleading |
| **Actionability** | User can improve outcome | Some guidance | No actionable info |
| **Completeness** | Key factors explained, uncertainty disclosed | Major factors | Incomplete |
| **Consistency** | Similar decisions get similar explanations | Mostly consistent | Inconsistent |
| **Accessibility** | Available at point of decision, multiple formats | Available but hard to find | Not available |
| **Gaming resistance** | Doesn't expose exploitable details | Some risk | Easily gamed |

**28+ = Trust-building | 21-27 = Needs user testing | <21 = May erode trust**

## Cross-Skill References

- **Upstream:** `model-card` (model details), `prompt-engineering` (explanation generation)
- **Downstream:** `human-oversight-protocol` (reviewer explanations)
- **Council:** Submit to `council-ai` for explanation quality review
