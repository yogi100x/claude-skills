# Bias Testing

Design and execute bias testing frameworks for AI systems to ensure fairness across protected groups.

## Context Sync Protocol

1. Read existing model cards for AI features
2. Read `.claude/product-marketing-context.md` for user demographics

## Decision Tree: Testing Approach

```
What type of AI output?
├── Classification (hire/reject, approve/deny)
│   └── Test: Demographic parity, equalized odds, calibration
├── Scoring / Ranking (match scores, relevance)
│   └── Test: Score distribution parity, rank position fairness
├── Generation (text, content, recommendations)
│   └── Test: Sentiment analysis, stereotype detection, representation
├── Embedding / Search
│   └── Test: Nearest-neighbor fairness, query bias, retrieval parity
└── Pricing / Resource allocation
    └── Test: Price parity across groups, access equity
```

## Fairness Metrics

| Metric | Definition | When to Use |
|--------|-----------|-------------|
| **Demographic parity** | Equal positive outcome rates across groups | When equal outcomes desired |
| **Equalized odds** | Equal TPR and FPR across groups | When accuracy parity matters |
| **Calibration** | Same predicted probability = same actual probability | For scoring systems |
| **Individual fairness** | Similar individuals get similar outcomes | When clear similarity metrics exist |
| **Counterfactual fairness** | Outcome unchanged if protected attribute flipped | When causal reasoning applicable |

## Testing Protocol

### Step 1: Define Protected Groups
- Gender, race/ethnicity, age, disability status, geographic location
- Intersectional groups (e.g., women of color, older workers)
- Based on legal requirements and ethical considerations

### Step 2: Create Test Sets
```
For each protected group:
- Minimum 100 representative test cases
- Include intersectional combinations
- Control for confounding variables
- Use both synthetic and real-world examples
```

### Step 3: Run Tests
```
For each test:
1. Process identical inputs varying only protected attributes
2. Measure outcome distribution per group
3. Calculate fairness metrics
4. Statistical significance testing (p < 0.05)
5. Practical significance assessment (effect size > threshold)
```

### Step 4: Document & Remediate
| Finding | Severity | Action |
|---------|----------|--------|
| No significant disparity | Pass | Document and continue monitoring |
| <5% disparity | Monitor | Flag for next review cycle |
| 5-15% disparity | Warning | Investigation required within 30 days |
| >15% disparity | Critical | Block deployment, immediate remediation |

## Anti-Patterns to Avoid

- **A2: One-time bias testing** — Bias drifts with data and model changes. Test regularly.
- **A7: Testing only majority groups** — Intersectional groups often have the worst outcomes.
- **A8: Aggregate metrics only** — Aggregate accuracy can hide group-level disparities.
- **A9: No baseline comparison** — Compare to human decision-making, not perfection.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Group coverage** | All protected groups + intersections | Major groups tested | 1-2 groups |
| **Metric selection** | Multiple fairness metrics per use case | One metric | No formal metrics |
| **Test set quality** | Representative, sufficient size, controlled | Adequate size | Ad-hoc examples |
| **Statistical rigor** | Significance testing + effect sizes | Basic statistics | No statistical analysis |
| **Remediation plan** | Specific actions per finding with timeline | General plan | No remediation |
| **Monitoring cadence** | Automated regular testing | Periodic manual | One-time |
| **Documentation** | Results published with methodology | Internal report | Undocumented |

**28+ = Robust fairness testing | 21-27 = Needs expansion | <21 = Insufficient**

## Cross-Skill References

- **Upstream:** `model-card` (model details), `training-data-audit` (data biases)
- **Downstream:** `ai-monitoring-setup` (ongoing monitoring), `algorithmic-impact-assessment` (regulatory reporting)
- **Council:** Submit to `council-ai` for methodology review
