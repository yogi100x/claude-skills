# Cookie Consent

Implement compliant cookie consent mechanisms for GDPR, ePrivacy Directive, and CCPA.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for analytics and tracking tools used
2. Check existing privacy policy for cookie disclosures

## Decision Tree: Consent Requirements

```
Where are your users?
├── EU/EEA
│   └── Strict opt-in consent required (ePrivacy + GDPR)
│       → No non-essential cookies until explicit consent
│       → Must offer granular category choices
├── UK
│   └── Similar to EU (UK GDPR + PECR)
│       → Same opt-in requirements
├── California (CCPA)
│   └── Opt-out model
│       → Can set cookies, must offer "Do Not Sell/Share" opt-out
├── US (other states)
│   └── Varies. Colorado, Virginia, Connecticut have opt-out models
└── Global SaaS
    └── Default to strictest (EU opt-in) for simplicity
        → Or geo-detect and apply appropriate consent model
```

## Cookie Categories

| Category | Examples | Consent Required? |
|----------|---------|-------------------|
| **Strictly necessary** | Session cookies, CSRF tokens, auth cookies | No (always allowed) |
| **Functional** | Language preference, theme, chat widget | Yes (EU), No (US) |
| **Analytics** | Google Analytics, PostHog, Mixpanel | Yes (EU), Opt-out (CCPA) |
| **Marketing** | Facebook Pixel, Google Ads, retargeting | Yes (EU), Opt-out (CCPA) |

## Implementation Patterns

### Consent Banner Requirements (EU)

```
Must have:
✓ Clear explanation of cookie use
✓ Accept All button
✓ Reject All button (equally prominent as Accept)
✓ Granular category selection option
✓ Link to cookie policy
✓ No pre-checked boxes for non-essential categories
✓ Consent stored and auditable
✓ Easy withdrawal of consent

Must NOT have:
✗ Cookie wall (blocking access without consent)
✗ Dark patterns (tiny reject button, confusing language)
✗ Pre-checked consent boxes
✗ Implied consent from scrolling or continuing to browse
```

### Technical Implementation

```
1. On page load:
   - Check for stored consent preferences
   - If no consent: block non-essential scripts/cookies
   - If consent exists: load scripts per saved preferences

2. Consent banner interaction:
   - Accept All → Set all category cookies, store consent record
   - Reject All → Set only necessary cookies, store consent record
   - Customize → Show category toggles, save selections

3. Consent storage:
   - First-party cookie with consent state (e.g., `cookie_consent={necessary:true,analytics:false,marketing:false}`)
   - Server-side consent record with timestamp for audit
   - Consent ID for proof of consent
```

## Anti-Patterns to Avoid

- **L3: Dark pattern consent** — Hiding "Reject All" or making it harder to decline than accept.
- **L5: Firing tracking scripts before consent** — Scripts must wait for consent in EU.
- **L7: No consent record** — You must prove consent was given. Store timestamp + choices.
- **L12: Cookie wall** — Blocking the site until users accept is not valid consent (most EU DPAs).

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Consent mechanism** | Opt-in with granular categories, equal-prominence buttons | Basic banner with accept/reject | Accept-only or no banner |
| **Script blocking** | Non-essential scripts blocked until consent | Most scripts blocked | Scripts fire before consent |
| **Cookie inventory** | Complete list of cookies with categories and purposes | Major cookies documented | No inventory |
| **Consent record** | Timestamped, auditable, linked to user | Basic record | No record |
| **Withdrawal** | Easy to change preferences at any time | Available but hard to find | No withdrawal mechanism |
| **Geo-compliance** | Appropriate consent model per jurisdiction | One model globally | Non-compliant for some regions |
| **User experience** | Non-intrusive, clear, fast | Functional but annoying | Blocks experience |

**28+ = Compliant and user-friendly | 21-27 = Needs refinement | <21 = Compliance risk**

## Cross-Skill References

- **Upstream:** `privacy-policy` (cookie disclosures), `analytics-tracking` (what's tracked)
- **Downstream:** `compliance-checklist` (consent audit items)
- **Council:** Submit to `council-legal` for compliance review
