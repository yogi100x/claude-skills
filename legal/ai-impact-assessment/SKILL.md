# AI Impact Assessment

Evaluate the legal, ethical, and social impact of AI systems before deployment.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for AI features and use cases
2. Check if AI governance documentation exists

## Decision Tree: Assessment Scope

```
What does your AI system do?
├── Content generation (text, images, code)
│   └── Assess: IP ownership, bias in outputs, misinformation risk
├── Decision-making (hiring, lending, content moderation)
│   └── Assess: Discrimination risk, explainability, human oversight
│       → High-risk under EU AI Act
├── Personalization (recommendations, pricing)
│   └── Assess: Filter bubbles, price discrimination, manipulation
├── Surveillance / Monitoring
│   └── Assess: Privacy invasion, proportionality, consent
│       → May be prohibited under EU AI Act
└── Automation (process automation, chatbots)
    └── Assess: Job displacement, accuracy, failure modes
```

## EU AI Act Risk Classification

| Risk Level | Examples | Requirements |
|-----------|---------|-------------|
| **Unacceptable** | Social scoring, real-time biometric ID in public | Prohibited |
| **High-risk** | Hiring AI, credit scoring, law enforcement | Conformity assessment, human oversight, logging |
| **Limited risk** | Chatbots, emotion recognition | Transparency obligations (disclose AI use) |
| **Minimal risk** | Spam filters, game AI | No specific obligations |

## Assessment Framework

### 1. System Description

| Element | Document |
|---------|----------|
| Purpose | What problem does the AI solve? |
| Users | Who uses it? Who is affected by it? |
| Data | What training data? What input data at runtime? |
| Model | What type of model? How is it trained/fine-tuned? |
| Outputs | What decisions or content does it produce? |
| Human oversight | Can a human review/override outputs? |

### 2. Risk Identification

| Risk Category | Questions to Answer |
|---------------|---------------------|
| **Bias & fairness** | Does the system treat protected groups differently? Is training data representative? |
| **Privacy** | Does it process personal data? Is consent obtained? Can individuals opt out? |
| **Transparency** | Do users know they're interacting with AI? Can outputs be explained? |
| **Safety** | What happens when the system fails? What's the worst-case scenario? |
| **Accountability** | Who is responsible for AI decisions? Is there an appeals process? |
| **Environmental** | What's the compute cost? Is it proportionate to the benefit? |

### 3. Mitigation Measures

| Risk | Mitigation |
|------|-----------|
| Bias | Regular bias testing, diverse training data, fairness constraints |
| Privacy | Data minimization, anonymization, consent mechanism |
| Transparency | AI disclosure labels, explainability features |
| Safety | Human-in-the-loop, confidence thresholds, fallback mechanisms |
| Accountability | Decision logging, appeals process, designated AI officer |

## Anti-Patterns to Avoid

- **A1: Deploying AI without impact assessment** — Required by EU AI Act for high-risk systems.
- **A2: Bias testing only at launch** — Bias can drift. Test regularly.
- **A3: No human oversight mechanism** — High-risk AI must have human override capability.
- **A4: Opaque AI decisions** — Affected individuals have a right to explanation (GDPR Art. 22).

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Risk identification** | All categories assessed with evidence | Major risks identified | Superficial review |
| **Bias analysis** | Tested across protected groups with metrics | Some bias testing | No bias analysis |
| **Mitigation plan** | Specific measures with owners and timelines | General mitigations | No plan |
| **Regulatory mapping** | All applicable regulations identified | Major regulations covered | No regulatory analysis |
| **Stakeholder input** | Affected communities consulted | Internal review only | No consultation |
| **Monitoring plan** | Ongoing monitoring with metrics and thresholds | Periodic review | No monitoring |
| **Documentation** | Complete assessment with methodology | Summary document | No documentation |

**28+ = Ready for deployment | 21-27 = Needs additional analysis | <21 = Do not deploy**

## Cross-Skill References

- **Upstream:** `product-marketing-context` (AI features), `ai-ethics-policy` (ethical framework)
- **Downstream:** `algorithmic-impact-assessment` (technical assessment), `compliance-checklist` (regulatory items)
- **Council:** Submit to `council-legal` + `council-ai` for joint review
