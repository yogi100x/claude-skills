# Acceptable Use Policy

Define what users can and cannot do with your product to protect the platform and community.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for product type and user base

## Decision Tree: AUP Scope

```
What kind of platform?
├── SaaS tool (single-user)
│   └── Focus: Resource abuse, unauthorized access, data misuse
├── Platform with user content
│   └── Focus: Content policies, moderation, IP infringement, harassment
├── API / Developer platform
│   └── Focus: Rate limits, scraping, competitive use, redistribution
├── Marketplace
│   └── Focus: Fraud, prohibited goods/services, seller quality
└── AI-powered product
    └── Focus: Prompt injection, harmful content generation, automated abuse
```

## AUP Structure

| Section | Content |
|---------|---------|
| **Prohibited content** | Illegal, harmful, infringing, deceptive content |
| **Prohibited behavior** | Abuse, harassment, spam, unauthorized access |
| **Resource limits** | Fair use, rate limits, storage limits |
| **Account rules** | One account per person, no sharing, accurate info |
| **AI-specific rules** | No harmful prompt engineering, no bypassing safety |
| **Enforcement** | Warning → suspension → termination escalation |
| **Reporting** | How to report violations |
| **Appeals** | How to appeal enforcement actions |

## Enforcement Framework

| Severity | Examples | Action | Appeal? |
|----------|---------|--------|---------|
| **Warning** | Minor ToS violation, first offense | Email warning, content removed | N/A |
| **Temporary suspension** | Repeated violations, moderate severity | 7-30 day suspension | Yes |
| **Permanent ban** | Severe violations, illegal activity | Account terminated | Limited |
| **Legal action** | Criminal activity, significant damages | Law enforcement referral | N/A |

## Anti-Patterns to Avoid

- **L4: Vague prohibited content definitions** — Be specific about what's not allowed.
- **L6: No enforcement escalation** — Jumping straight to bans without warnings is unfair and may be unenforceable.
- **L8: No appeals process** — Users deserve a way to challenge enforcement decisions.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Specificity** | Clear, specific prohibitions with examples | Categories listed | Vague language |
| **Completeness** | All relevant areas covered for product type | Major areas covered | Missing key areas |
| **Enforcement** | Clear escalation path with timelines | Some enforcement | No enforcement process |
| **Appeals** | Documented appeals process with SLA | Appeals mentioned | No appeals |
| **Accessibility** | Easy to find, plain language, translated | Available but dense | Buried or unclear |
| **Reporting** | Easy reporting mechanism with acknowledgment | Report mechanism exists | No reporting |
| **Updates** | Version history, notification of changes | Some versioning | No version tracking |

**28+ = Clear and enforceable | 21-27 = Needs specificity | <21 = Unenforceable**

## Cross-Skill References

- **Upstream:** `terms-of-service` (legal framework), `product-marketing-context` (platform type)
- **Downstream:** `compliance-checklist` (enforcement tracking), `ai-ethics-policy` (AI-specific rules)
- **Council:** Submit to `council-legal` for enforceability review
