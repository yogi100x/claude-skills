# Skill Map — Dependency Graph & Usage Guide

## How to Read This Map

- **→** means "feeds into" (run the left skill before the right skill)
- **←** means "depends on" (this skill needs the left skill's output)
- Skills in **bold** are foundation skills (run first)
- Skills in *italics* are review/council skills (run after execution)

---

## Foundation Layer

These skills should be run before any execution skills:

```
**setup** → generates all context files
  ├── product-marketing-context.md → all marketing skills
  ├── finance-context.md → all finance skills
  ├── legal-context.md → all legal skills
  ├── ai-context.md → all AI governance skills
  └── tech-context.md → all tech skills
```

---

## Marketing Skills (25)

### Core Flow
```
product-marketing-context → copywriting → copy-editing
                         → pricing-strategy → paywall-upgrade-cro
                         → launch-strategy → social-content
                                           → email-sequence
                                           → paid-ads
```

### Content Pipeline
```
content-strategy → programmatic-seo → schema-markup
                → seo-audit
                → copywriting → copy-editing
```

### Conversion Optimization Pipeline
```
page-cro ──────→ ab-test-setup → analytics-tracking
signup-flow-cro → ab-test-setup
onboarding-cro ─→ ab-test-setup
form-cro ──────→ ab-test-setup
popup-cro ─────→ ab-test-setup
paywall-upgrade-cro → ab-test-setup
```

### Growth Pipeline
```
marketing-psychology → copywriting (apply mental models to copy)
                    → page-cro (apply persuasion to pages)
                    → pricing-strategy (apply pricing psychology)

referral-program → email-sequence (referral emails)
                → analytics-tracking (referral tracking)

free-tool-strategy → seo-audit (tool SEO)
                   → content-strategy (content around tool)
                   → analytics-tracking (tool metrics)
```

### Acquisition Pipeline
```
paid-ads → analytics-tracking (attribution)
        → page-cro (landing page optimization)
        → ab-test-setup (ad creative testing)

social-content → analytics-tracking
              → community engagement

competitor-alternatives → seo-audit (competitor keywords)
                       → content-strategy (content gaps)
                       → copywriting (comparison pages)
```

### Research & Intelligence
```
marketing-ideas → content-strategy (topic selection)
               → launch-strategy (launch ideas)
               → social-content (content ideas)
```

### Full Skill Dependency Table

| Skill | Reads Context | Upstream Skills | Downstream Skills |
|-------|--------------|----------------|-------------------|
| product-marketing-context | — | setup | All marketing skills |
| copywriting | product-marketing | product-marketing-context, marketing-psychology | copy-editing, page-cro |
| copy-editing | product-marketing | copywriting | — (terminal) |
| pricing-strategy | product-marketing, finance | product-marketing-context | paywall-upgrade-cro, copywriting |
| launch-strategy | product-marketing | product-marketing-context | social-content, email-sequence, paid-ads |
| content-strategy | product-marketing | product-marketing-context | programmatic-seo, seo-audit, copywriting |
| paid-ads | product-marketing, finance | analytics-tracking | page-cro, ab-test-setup |
| ab-test-setup | product-marketing | any CRO skill | analytics-tracking |
| analytics-tracking | product-marketing, tech | — (foundation) | All skills (measurement) |
| email-sequence | product-marketing | launch-strategy, onboarding-cro | analytics-tracking |
| page-cro | product-marketing | copywriting, marketing-psychology | ab-test-setup |
| signup-flow-cro | product-marketing, tech | page-cro | onboarding-cro, ab-test-setup |
| onboarding-cro | product-marketing, tech | signup-flow-cro | email-sequence, ab-test-setup |
| form-cro | product-marketing | page-cro | ab-test-setup |
| popup-cro | product-marketing | page-cro, marketing-psychology | ab-test-setup |
| paywall-upgrade-cro | product-marketing, finance | pricing-strategy | ab-test-setup |
| seo-audit | product-marketing, tech | content-strategy | programmatic-seo, schema-markup |
| programmatic-seo | product-marketing, tech | content-strategy, seo-audit | schema-markup |
| schema-markup | tech | seo-audit, programmatic-seo | — (terminal) |
| social-content | product-marketing | launch-strategy, content-strategy | analytics-tracking |
| referral-program | product-marketing, finance | onboarding-cro | email-sequence, analytics-tracking |
| free-tool-strategy | product-marketing, tech | content-strategy | seo-audit, analytics-tracking |
| marketing-ideas | product-marketing | — (inspiration) | content-strategy, launch-strategy |
| marketing-psychology | — | — (reference) | copywriting, page-cro, pricing-strategy |
| competitor-alternatives | product-marketing | — (research) | content-strategy, copywriting |

---

## Finance Skills (13)

### Core Flow
```
financial-model → unit-economics → budget-allocation
              → fundraising-deck
              → kpi-dashboard
```

### Skill Dependency Table

| Skill | Reads Context | Upstream Skills | Downstream Skills |
|-------|--------------|----------------|-------------------|
| financial-model | finance | setup | unit-economics, fundraising-deck, budget-allocation |
| unit-economics | finance | financial-model | pricing-strategy (marketing), kpi-dashboard |
| pricing-model | finance, product-marketing | unit-economics | billing-design, pricing-strategy (marketing) |
| billing-design | finance, tech | pricing-model | — |
| budget-allocation | finance | financial-model | — |
| fundraising-deck | finance, product-marketing | financial-model, unit-economics | — |
| cap-table | finance | — | fundraising-deck |
| revenue-recognition | finance, legal | financial-model | — |
| cost-optimization | finance | financial-model, kpi-dashboard | budget-allocation |
| ltd-deal-structure | finance, product-marketing | unit-economics, pricing-model | — |
| tax-strategy | finance, legal | financial-model | — |
| treasury-management | finance | financial-model | — |
| kpi-dashboard | finance | financial-model, unit-economics | — |

---

## Legal Skills (13)

### Core Flow
```
privacy-policy → cookie-consent
             → data-processing-agreement

terms-of-service → acceptable-use-policy

compliance-checklist → incident-response-plan
```

### Skill Dependency Table

| Skill | Reads Context | Upstream Skills | Downstream Skills |
|-------|--------------|----------------|-------------------|
| privacy-policy | legal | — | cookie-consent, data-processing-agreement |
| terms-of-service | legal, product-marketing | — | acceptable-use-policy |
| contract-drafting | legal, finance | — | — |
| cookie-consent | legal, tech | privacy-policy | analytics-tracking (marketing) |
| data-processing-agreement | legal | privacy-policy | — |
| ip-protection | legal | — | — |
| employment-agreement | legal | — | — |
| compliance-checklist | legal, tech | — | incident-response-plan |
| incident-response-plan | legal, tech | compliance-checklist | — |
| ai-impact-assessment | legal, ai | — | model-card (AI gov) |
| acceptable-use-policy | legal, product-marketing | terms-of-service | — |
| regulatory-filing | legal | compliance-checklist | — |
| dispute-resolution | legal | terms-of-service | — |

---

## AI Governance Skills (11)

### Core Flow
```
model-card → bias-testing → ai-monitoring-setup
          → explainability-design
          → human-oversight-protocol

prompt-engineering → red-team-protocol
```

### Skill Dependency Table

| Skill | Reads Context | Upstream Skills | Downstream Skills |
|-------|--------------|----------------|-------------------|
| model-card | ai, tech | — | bias-testing, explainability-design |
| bias-testing | ai | model-card | ai-monitoring-setup |
| prompt-engineering | ai, tech | — | red-team-protocol |
| ai-ethics-policy | ai, legal | — | model-card, human-oversight-protocol |
| algorithmic-impact-assessment | ai, legal | model-card | — |
| explainability-design | ai, tech | model-card | — |
| human-oversight-protocol | ai | ai-ethics-policy | — |
| ai-monitoring-setup | ai, tech | bias-testing | — |
| training-data-audit | ai, legal | — | model-card |
| ai-incident-response | ai, tech | ai-monitoring-setup | — |
| ai-vendor-evaluation | ai, finance | — | — |
| red-team-protocol | ai, tech | prompt-engineering | — |

---

## Tech Skills (15)

### Core Flow
```
system-architecture → api-design → webhook-design
                   → database-schema → data-migration
                   → auth-design
                   → background-job-design

testing-strategy → (all implementation skills)
error-handling → (all implementation skills)

ci-cd-pipeline → monitoring-setup → security-hardening
```

### Skill Dependency Table

| Skill | Reads Context | Upstream Skills | Downstream Skills |
|-------|--------------|----------------|-------------------|
| system-architecture | tech | — | api-design, database-schema, auth-design |
| api-design | tech | system-architecture | webhook-design, documentation |
| database-schema | tech | system-architecture | data-migration |
| auth-design | tech, legal | system-architecture | — |
| ci-cd-pipeline | tech | — | monitoring-setup |
| monitoring-setup | tech | ci-cd-pipeline | — |
| performance-optimization | tech | monitoring-setup | — |
| security-hardening | tech, legal | — | — |
| data-migration | tech | database-schema | — |
| webhook-design | tech | api-design | — |
| background-job-design | tech | system-architecture | — |
| error-handling | tech | — | all implementation skills |
| testing-strategy | tech | — | all implementation skills |
| documentation | tech | api-design | — |
| code-review-checklist | tech | — | — (reference) |

---

## Cross-Council Dependencies

These skills bridge across councils:

```
pricing-strategy (marketing) ←→ pricing-model (finance) ←→ billing-design (finance)
                                                        ←→ terms-of-service (legal)

analytics-tracking (marketing) → cookie-consent (legal)
                              → ai-monitoring-setup (AI gov)

ai-impact-assessment (legal) ←→ model-card (AI gov)
                             ←→ algorithmic-impact-assessment (AI gov)

compliance-checklist (legal) → security-hardening (tech)
                            → incident-response-plan (legal)
                            → ai-incident-response (AI gov)
```

---

## Council Review Integration

After execution, use review councils to validate:

| After Running | Review With |
|--------------|-------------|
| Any marketing skill output | `council-marketing review [output]` |
| Financial models, pricing | `council-finance review [output]` |
| Legal documents, policies | `council-legal review [output]` |
| AI features, prompts, models | `council-ai review [output]` |
| Architecture, code, APIs | `council-review [output]` |

---

## Workflow Recipes

Pre-built multi-skill sequences for common tasks:

| Workflow | Skills (in order) | Duration |
|----------|------------------|----------|
| **Launch a feature** | product-marketing-context → copywriting → launch-strategy → email-sequence → social-content → paid-ads → analytics-tracking | Full day |
| **Optimize conversions** | analytics-tracking → page-cro → ab-test-setup → copy-editing | Half day |
| **Enter new market** | competitor-alternatives → pricing-strategy → content-strategy → programmatic-seo → copywriting | Full day |
| **Fundraise** | financial-model → unit-economics → kpi-dashboard → fundraising-deck | Full day |
| **Launch legally** | privacy-policy → terms-of-service → cookie-consent → compliance-checklist | Half day |
| **Ship AI feature** | model-card → bias-testing → prompt-engineering → red-team-protocol → ai-monitoring-setup | Full day |
| **Build new service** | system-architecture → database-schema → api-design → auth-design → testing-strategy → ci-cd-pipeline | Multi-day |
