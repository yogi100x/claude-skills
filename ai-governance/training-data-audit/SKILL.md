# Training Data Audit

Audit training datasets for quality, bias, consent, and legal compliance before model training.

## Context Sync Protocol

1. Read model cards for data sources and intended use
2. Read privacy policy for data usage disclosures

## Audit Framework

### 1. Data Provenance

| Check | Questions | Risk |
|-------|-----------|------|
| **Source documentation** | Where did each dataset come from? | Unlicensed data |
| **Collection method** | How was data gathered? Web scraping, user-generated, purchased? | Consent issues |
| **Consent** | Did data subjects consent to AI training use? | GDPR violation |
| **Licensing** | What license applies? Commercial use allowed? | IP infringement |
| **Recency** | When was data collected? Is it still representative? | Stale data |

### 2. Data Quality

| Check | Method | Threshold |
|-------|--------|-----------|
| **Completeness** | Missing value analysis per field | <5% missing for key fields |
| **Accuracy** | Sample validation against ground truth | >95% accuracy |
| **Consistency** | Cross-field validation, duplicate detection | <1% duplicates |
| **Relevance** | Domain match to intended use | >90% relevant samples |
| **Label quality** | Inter-annotator agreement (if labeled) | Cohen's κ > 0.7 |

### 3. Representation Analysis

```
For each protected attribute (if available or inferable):
- Calculate distribution in training data
- Compare to target population distribution
- Flag underrepresented groups (<50% of expected proportion)
- Flag overrepresented groups (>200% of expected proportion)
```

### 4. Content Safety

| Check | Method |
|-------|--------|
| **PII detection** | Scan for emails, phone numbers, SSNs, names |
| **Toxic content** | Run content safety classifier |
| **Copyright material** | Check for verbatim copyrighted text |
| **Sensitive categories** | Flag health, financial, political, religious content |

## Anti-Patterns to Avoid

- **A2: No data audit before training** — Garbage in, garbage out. Audit before training.
- **A7: No representation analysis** — Unbalanced training data creates biased models.
- **A8: PII in training data** — Remove or anonymize PII before training.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Provenance** | All sources documented with licensing | Major sources documented | No provenance |
| **Quality metrics** | Completeness, accuracy, consistency measured | Some quality checks | No quality analysis |
| **Representation** | Demographic analysis with population comparison | Basic distribution analysis | No representation check |
| **Consent** | All data consented for AI training use | Most data consented | Consent unclear |
| **Safety screening** | PII removed, toxic content filtered, copyright checked | Some screening | No screening |
| **Documentation** | Complete data card with methodology | Summary document | No documentation |
| **Remediation** | Issues identified and resolved before training | Issues noted | Issues ignored |

**28+ = Audit-complete | 21-27 = Needs remediation | <21 = Do not train**

## Cross-Skill References

- **Upstream:** `privacy-policy` (data usage rights), `data-processing-agreement` (vendor data)
- **Downstream:** `model-card` (data section), `bias-testing` (evaluating bias from data)
- **Council:** Submit to `council-ai` + `council-legal` for joint review
