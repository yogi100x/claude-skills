# Privacy Policy

Draft clear, compliant privacy policies covering GDPR, CCPA, and other data protection regulations.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for what data you collect and why
2. Read `.claude/finance-context.md` for business model (affects data usage disclosures)

## Decision Tree: Policy Scope

```
Where are your users?
├── US only
│   └── CCPA/CPRA (California) + state laws
│       → Required: Data collected, purpose, sale/sharing, opt-out rights
├── EU/EEA users
│   └── GDPR required
│       → Required: Legal basis, DPO if needed, data transfers, DSAR process
├── Global SaaS
│   └── GDPR + CCPA + others
│       → Required: Comprehensive policy covering all jurisdictions
└── Children's data possible
    └── COPPA (US) / Age-appropriate design (UK)
        → Required: Parental consent, age verification, enhanced protections
```

## Policy Structure

| Section | Must Include | GDPR | CCPA |
|---------|-------------|------|------|
| **Identity** | Company name, contact, DPO (if applicable) | Required | Required |
| **Data collected** | Categories with specific examples | Required | Required |
| **Purpose** | Why each data type is collected | Required | Required |
| **Legal basis** | Consent, contract, legitimate interest, etc. | Required | N/A |
| **Data sharing** | Third parties, categories, purposes | Required | Required ("sale" definition) |
| **Retention** | How long each data type is kept | Required | Recommended |
| **User rights** | Access, deletion, portability, opt-out | Required | Required |
| **International transfers** | Safeguards for cross-border data flow | Required | N/A |
| **Cookies** | Types, purposes, consent mechanism | Required | Required |
| **Security** | Measures taken to protect data | Required | Recommended |
| **Children** | Age restrictions, COPPA compliance | Required | Required |
| **Updates** | How policy changes are communicated | Required | Required |

## GDPR Legal Bases

| Legal Basis | When to Use | Example |
|-------------|-------------|---------|
| **Consent** | Optional data, marketing emails | Newsletter subscription |
| **Contract** | Necessary for service delivery | Account email for login |
| **Legitimate interest** | Business need, balanced with rights | Analytics, fraud prevention |
| **Legal obligation** | Required by law | Tax records, KYC |

## Data Inventory Template

Before writing the policy, catalog all data:

```
| Data Point | Source | Purpose | Legal Basis | Retention | Shared With |
|------------|--------|---------|-------------|-----------|-------------|
| Email | Signup form | Account, comms | Contract | Account life + 30 days | SendGrid, Intercom |
| IP address | Auto-collected | Security, analytics | Legit interest | 90 days | Cloudflare |
| Payment info | Checkout | Billing | Contract | Per Stripe retention | Stripe |
```

## Anti-Patterns to Avoid

- **L1: Copy-paste privacy policy** — Generic templates miss your specific data practices. Always customize.
- **L2: Overclaiming data rights** — Don't claim rights to use data you don't actually need.
- **L3: No update notification mechanism** — Users must be notified of material changes.
- **L7: Inconsistent with actual practices** — Policy must match what your code actually does.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Completeness** | All required sections for target jurisdictions | Major sections present | Missing key sections |
| **Specificity** | Names specific data points, third parties, retention periods | Categories mentioned | Vague generalities |
| **Readability** | Plain language, layered disclosure, scannable | Readable but dense | Legalese wall of text |
| **Legal basis** | Each data use has documented legal basis | Some bases documented | No legal basis stated |
| **User rights** | Clear process for exercising all applicable rights | Rights listed | Rights mentioned vaguely |
| **Accuracy** | Matches actual code and data flows | Mostly accurate | Aspirational or outdated |
| **Accessibility** | Available in user's language, easy to find | Easy to find | Buried in footer |

**28+ = Compliance-ready | 21-27 = Needs legal review | <21 = Compliance risk**

## Cross-Skill References

- **Upstream:** `product-marketing-context` (data practices), `analytics-tracking` (what's tracked)
- **Downstream:** `cookie-consent` (consent implementation), `data-processing-agreement` (vendor contracts)
- **Council:** Submit to `council-legal` for compliance review
