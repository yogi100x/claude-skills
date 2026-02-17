# Algorithmic Impact Assessment

Conduct systematic assessments of algorithmic systems' impact on individuals and society.

## Context Sync Protocol

1. Read existing model cards and AI ethics policy
2. Read `.claude/product-marketing-context.md` for affected user populations

## Assessment Framework

### Step 1: System Scoping

| Question | Purpose |
|----------|---------|
| What does the algorithm do? | Define scope |
| Who does it affect? | Identify stakeholders |
| What decisions does it inform or automate? | Determine impact level |
| What data does it use? | Identify data risks |
| What's the human role? | Assess autonomy level |

### Step 2: Impact Analysis

| Impact Area | Questions | Risk Level |
|------------|-----------|-----------|
| **Individual rights** | Does it affect access to services, employment, credit? | High if yes |
| **Group fairness** | Does it treat demographic groups differently? | High if untested |
| **Privacy** | Does it process personal data beyond stated purposes? | Medium-High |
| **Autonomy** | Does it manipulate choices or limit options? | Medium-High |
| **Safety** | Can failures cause physical, financial, or psychological harm? | Context-dependent |
| **Economic** | Does it concentrate power or displace workers? | Medium |
| **Democratic** | Does it affect access to information or political participation? | High if yes |

### Step 3: Risk Scoring

```
Risk = Likelihood × Impact × Reversibility

Likelihood: How often could harm occur? (1-5)
Impact: How severe is the harm? (1-5)
Reversibility: Can the harm be undone? (1=easily, 5=irreversible)

Score 1-25: Low risk → Document and monitor
Score 26-50: Medium risk → Additional safeguards required
Score 51-75: High risk → Senior review + enhanced oversight
Score 76-125: Critical risk → May require redesign or prohibition
```

### Step 4: Mitigation Plan

| Mitigation | When to Apply |
|-----------|---------------|
| Human-in-the-loop | High-impact individual decisions |
| Bias testing | Any system affecting protected groups |
| Explainability | Users affected by algorithmic decisions |
| Opt-out mechanism | Non-essential algorithmic processing |
| Appeals process | Consequential automated decisions |
| Regular audits | All production AI systems |

## Anti-Patterns to Avoid

- **A1: Assessment after deployment** — Assess before launch, not after incidents.
- **A2: Technical-only assessment** — Include social, ethical, and legal perspectives.
- **A8: Aggregate-only analysis** — Disaggregate impacts by affected groups.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Scope definition** | All affected systems and stakeholders identified | Key systems covered | Ad-hoc selection |
| **Impact analysis** | All impact areas assessed with evidence | Major areas covered | Superficial review |
| **Risk scoring** | Quantified with consistent methodology | Qualitative assessment | No scoring |
| **Mitigation plan** | Specific measures per risk with owners | General mitigations | No plan |
| **Stakeholder input** | Affected communities consulted | Internal review | No consultation |
| **Monitoring plan** | Ongoing monitoring with triggers and KPIs | Periodic review | No monitoring |
| **Public reporting** | Summary published for transparency | Internal report | No documentation |

**28+ = Thorough assessment | 21-27 = Needs depth | <21 = Insufficient**

## Cross-Skill References

- **Upstream:** `ai-ethics-policy` (principles), `model-card` (system details), `bias-testing` (fairness data)
- **Downstream:** `ai-impact-assessment` (legal compliance), `compliance-checklist` (regulatory items)
- **Council:** Submit to `council-ai` + `council-legal` for joint review
