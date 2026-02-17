# Model Card

Document AI/ML models with standardized model cards covering capabilities, limitations, and ethical considerations.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for AI features and use cases

## Decision Tree: Model Card Scope

```
What type of model?
├── Third-party API (OpenAI, Anthropic, Google)
│   └── Document: Which model, what you send, what you receive, your safeguards
├── Fine-tuned model
│   └── Document: Base model, training data, evaluation results, drift monitoring
├── Custom-trained model
│   └── Document: Full model card (architecture, data, training, evaluation, limitations)
└── Ensemble / Pipeline
    └── Document: Each component + system-level behavior and failure modes
```

## Model Card Template

### 1. Model Overview

| Field | Description |
|-------|------------|
| **Model name** | Internal identifier and version |
| **Model type** | Classification, generation, embedding, etc. |
| **Provider** | Self-hosted, API provider, or open-source |
| **Version** | Model version and last update date |
| **Task** | What the model does in your product |
| **Intended users** | Who interacts with model outputs |
| **Out-of-scope uses** | What the model should NOT be used for |

### 2. Training Data

| Field | Description |
|-------|------------|
| **Data sources** | Where training data came from |
| **Data size** | Number of examples, tokens, images |
| **Data composition** | Demographics, languages, domains represented |
| **Data quality** | Cleaning, filtering, validation processes |
| **Consent** | How data subjects consented to use |
| **Sensitive data** | Whether PII, protected attributes are present |

### 3. Evaluation

| Metric | Value | Benchmark | Notes |
|--------|-------|-----------|-------|
| **Accuracy** | X% | Y% (industry) | On test set of N examples |
| **Fairness** | | | Disaggregated by protected groups |
| **Latency** | Xms p50, Yms p99 | | Production conditions |
| **Cost** | $X per 1K inferences | | Including API + compute |
| **Failure rate** | X% | | Hallucination, wrong answer, refusal |

### 4. Limitations & Risks

| Limitation | Impact | Mitigation |
|-----------|--------|-----------|
| Hallucination | Users may receive incorrect information | Confidence thresholds, human review |
| Bias | Unfair treatment of underrepresented groups | Regular bias testing, diverse eval sets |
| Data freshness | Knowledge cutoff affects accuracy | RAG pipeline, regular fine-tuning |
| Context length | Long inputs may be truncated | Chunking strategy, summarization |
| Adversarial inputs | Prompt injection, jailbreaking | Input validation, output filtering |

### 5. Ethical Considerations

- Environmental impact (training compute)
- Dual-use potential
- Impact on affected communities
- Automation displacement risk

## Anti-Patterns to Avoid

- **A1: No model documentation** — Every AI feature needs at minimum a lightweight model card.
- **A5: Static model card** — Update when model changes, new failure modes discovered, or metrics shift.
- **A6: Missing limitation disclosure** — Users deserve to know what the model can't do.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Completeness** | All sections with specific details | Major sections present | Minimal documentation |
| **Evaluation rigor** | Multiple metrics, disaggregated results | Key metrics reported | No evaluation |
| **Limitations honesty** | Known limitations with mitigations | Some limitations noted | Claims of perfection |
| **Data documentation** | Source, composition, consent documented | Source mentioned | No data documentation |
| **Maintenance plan** | Update cadence, monitoring triggers | Some update plan | Static document |
| **Accessibility** | Available to users and stakeholders | Internal only | Not documented |
| **Ethical analysis** | Impact assessment with mitigations | Some ethical consideration | No ethical analysis |

**28+ = Publication-ready | 21-27 = Needs detail | <21 = Insufficient documentation**

## Cross-Skill References

- **Upstream:** `product-marketing-context` (AI feature description)
- **Downstream:** `bias-testing` (evaluation details), `explainability-design` (user-facing explanations)
- **Council:** Submit to `council-ai` for completeness review
