# AI Ethics Policy

Create organizational AI ethics policies that guide responsible AI development and deployment.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for AI features and company values

## Policy Structure

### 1. Principles

| Principle | Definition | Implementation |
|-----------|-----------|----------------|
| **Fairness** | AI should not discriminate against protected groups | Bias testing, diverse data, regular audits |
| **Transparency** | Users should know when AI is involved and how it works | AI disclosure, explainability features, model cards |
| **Privacy** | AI should respect user data rights | Data minimization, consent, anonymization |
| **Safety** | AI should not cause harm | Human oversight, fallback mechanisms, testing |
| **Accountability** | Someone is responsible for AI decisions | Designated AI officer, decision logging, appeals |
| **Sustainability** | AI should consider environmental impact | Efficient model selection, compute optimization |

### 2. Governance Structure

| Role | Responsibility |
|------|---------------|
| **AI Ethics Officer** | Policy oversight, incident response, external reporting |
| **Product Teams** | Impact assessments before new AI features |
| **Engineering** | Technical safeguards, monitoring, bias testing |
| **Legal** | Regulatory compliance, terms of service |
| **Executive Sponsor** | Resource allocation, organizational accountability |

### 3. Decision Framework

```
Before deploying any AI feature, answer:
1. What decisions does this AI make or influence?
2. Who is affected? Can they opt out?
3. What happens when it's wrong?
4. Have we tested for bias?
5. Is there human oversight?
6. How do we monitor for problems?
7. Can affected individuals get an explanation and appeal?
```

### 4. Prohibited Uses

- Autonomous lethal decisions
- Mass surveillance without consent
- Social scoring of individuals
- Deceptive synthetic media without disclosure
- Manipulation of vulnerable populations
- Discrimination in hiring, lending, or housing
- Predictive policing targeting demographics

## Anti-Patterns to Avoid

- **A1: Ethics policy without enforcement** — Policy must have teeth: review gates, incident response, consequences.
- **A3: Ethics washing** — Publishing a policy while ignoring it in practice.
- **A4: No stakeholder input** — Ethics policy designed by engineers alone misses affected communities.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Principle coverage** | All key principles with specific commitments | Major principles covered | Vague aspirations |
| **Governance** | Clear roles, responsibilities, escalation paths | Some governance | No structure |
| **Enforcement** | Review gates, incident process, consequences | Some enforcement | Policy only |
| **Stakeholder input** | External consultation, diverse perspectives | Internal review | No consultation |
| **Prohibited uses** | Specific, clear bright lines | General prohibitions | No prohibitions |
| **Review cadence** | Annual review with update process | Periodic review | Static document |
| **Training** | All employees trained on AI ethics policy | Some training | No training |

**28+ = Robust policy | 21-27 = Needs governance detail | <21 = Ethics washing risk**

## Cross-Skill References

- **Upstream:** `product-marketing-context` (company values, AI features)
- **Downstream:** All AI governance skills reference this policy
- **Council:** Submit to `council-ai` for completeness review
