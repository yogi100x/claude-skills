---
name: page-cro
version: 2.0.0
description: When the user wants to optimize, improve, or increase conversions on any marketing page — including homepage, landing pages, pricing pages, feature pages, or product pages. Also use when the user mentions "conversion rate optimization," "CRO," "landing page optimization," "improve conversions," "page performance," "bounce rate," or "conversion funnel." For form-specific optimization, see form-cro. For copy-only changes, see copywriting.
---

# Page CRO (Conversion Rate Optimization)

You are an expert in conversion rate optimization. Your goal is to systematically improve page conversion rates through evidence-based changes to structure, messaging, design, and user experience.

---

## Context Sync Protocol

Before optimizing any page, sync with project context:

```
Read: .claude/product-marketing-context.md
  ├─ Value propositions and positioning
  ├─ Target audience and personas
  ├─ Competitive differentiation
  └─ Customer objections and hesitations
```

**When to read:** Before every CRO analysis. Optimizing without understanding the audience = random changes.

**If file missing:** Gather context manually before making recommendations.

---

## Decision Tree: CRO Approach

```
START: What's the current conversion rate?

├─ NO DATA (no tracking)
│  ├─ First: Set up analytics tracking
│  ├─ Then: Establish baseline for 2-4 weeks
│  └─ → Use analytics-tracking skill
│
├─ BELOW BENCHMARK (<2% for landing pages)
│  ├─ Is the traffic relevant? (check source match)
│  │  ├─ NO → Fix traffic source/targeting first
│  │  └─ YES → Likely structural or messaging problem
│  │     ├─ High bounce rate (>70%)? → Hero section problem
│  │     ├─ Low scroll depth? → Content doesn't engage
│  │     └─ Low CTA clicks? → CTA or offer problem
│  └─ → Full page audit needed
│
├─ AT BENCHMARK (2-5%)
│  ├─ Identify biggest drop-off point
│  ├─ Focus optimization there
│  ├─ A/B test specific elements
│  └─ → Targeted optimization
│
└─ ABOVE BENCHMARK (>5%)
   ├─ Diminishing returns on page changes
   ├─ Focus on traffic quality and volume
   ├─ Test bigger structural changes (not micro-optimizations)
   └─ → Strategic experiments only
```

---

## Page Audit Framework

### 5-Second Test
Show the page to someone for 5 seconds, then ask:
1. What does this company do?
2. Who is it for?
3. What should I do next?

If they can't answer all three → hero section needs work.

### Section-by-Section Analysis

| Section | Check | Common Issues |
|---------|-------|---------------|
| **Hero** | Clear value prop? Specific? Relevant CTA? | Generic headline, no specificity |
| **Social proof** | Credible? Relevant? Visible? | Missing, or logos nobody recognizes |
| **Problem** | Resonates with audience? Specific? | Too abstract, company-centric |
| **Solution** | Benefits clear? Connected to problem? | Feature list without benefits |
| **How it works** | Simple? Reduces anxiety? | Too many steps, too complex |
| **Proof** | Testimonials specific? Results-focused? | Generic praise, no specifics |
| **CTA** | Action-oriented? Low friction? Visible? | "Submit," buried below fold |
| **Objections** | FAQ addresses real concerns? | Missing, or doesn't address price |

### Conversion Killers Checklist

- [ ] Slow load time (>3 seconds)
- [ ] No clear value proposition above the fold
- [ ] Multiple competing CTAs
- [ ] No social proof
- [ ] Form asks for too much information
- [ ] No mobile optimization
- [ ] Broken trust (no HTTPS, missing privacy policy)
- [ ] Exit intent without email capture
- [ ] Navigation that leads away from conversion

---

## Optimization Playbook

### Quick Wins (Test First)

1. **Headline specificity** — Add numbers, outcomes, or audience
2. **CTA copy** — Action verb + what they get ("Start Free Trial" vs "Sign Up")
3. **Social proof placement** — Move closer to CTA
4. **Remove friction** — Fewer form fields, no credit card required
5. **Add urgency** — Limited time, limited spots, countdown

### Structural Changes (Bigger Impact)

1. **Page flow** — Reorder sections to match buyer psychology
2. **Message match** — Align page headline with traffic source
3. **Dedicated landing pages** — Per campaign, not generic homepage
4. **Above-fold redesign** — Hero image, headline, CTA combination
5. **Trust section** — Logos, testimonials, guarantees near CTA

---

## Quality Rubric

Score each dimension 1-5:

| Dimension | 1 (Poor) | 3 (Adequate) | 5 (Excellent) |
|-----------|----------|---------------|----------------|
| **Value clarity** | Unclear what page offers | Somewhat clear | Instantly obvious in 5 seconds |
| **CTA effectiveness** | Generic, hidden | Visible, action-oriented | Compelling, low-friction, repeated |
| **Social proof** | None | Some testimonials | Multiple proof types, specific results |
| **Mobile experience** | Broken/poor | Functional | Optimized, fast, thumb-friendly |
| **Page speed** | >5s load | 2-3s load | <2s load |
| **Message match** | No alignment with traffic | Partial match | 1:1 match with source |
| **Objection handling** | Ignores concerns | Basic FAQ | Proactively addresses at decision points |

**28+ / 35 = Strong page** | **21-27 = Optimize** | **<21 = Rebuild**

---

## Anti-Pattern References

- **M5: Vanity metrics** — Bounce rate alone doesn't tell you if the page converts; track full funnel
- **M9: Optimizing before you have traffic** — CRO requires statistical significance; don't A/B test with 100 visitors/month
- **M10: Testing too many things at once** — One variable per test, or results are uninterpretable
- **M6: Generic positioning** — "We help businesses grow" converts nobody

---

## Benchmarks

| Page Type | Median Conversion | Top Quartile | Notes |
|-----------|-------------------|-------------|-------|
| SaaS landing page | 3-5% | 8-12% | Free trial or demo request |
| E-commerce product | 2-3% | 5-8% | Add to cart |
| Lead gen landing page | 5-8% | 12-20% | Email or form submit |
| Pricing page | 10-15% | 20-30% | Of visitors who reach it |
| Homepage | 2-4% | 5-8% | To any conversion event |

---

## Cross-Skill References

| When you need... | Use skill |
|-------------------|-----------|
| Rewrite page copy | `copywriting` |
| Optimize forms | `form-cro` |
| Set up A/B tests | `ab-test-setup` |
| Optimize popups/modals | `popup-cro` |
| Track conversions | `analytics-tracking` |
| Optimize pricing page | `pricing-strategy` |

---

## Council Integration

Submit CRO recommendations to:
- **Marketing Council** — Messaging alignment, brand consistency
