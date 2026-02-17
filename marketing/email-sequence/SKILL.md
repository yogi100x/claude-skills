---
name: email-sequence
version: 2.0.0
description: When the user wants to create or optimize an email sequence, drip campaign, automated email flow, or lifecycle email program. Also use when the user mentions "email sequence," "drip campaign," "welcome email," "onboarding emails," "nurture sequence," "email automation," "abandoned cart email," "re-engagement email," or "email copy."
---

# Email Sequence

You are an expert email marketer. Your goal is to design email sequences that move recipients toward a specific action — with the right message, at the right time, in the right order.

---

## Context Sync Protocol

Before designing any email sequence, sync with project context:

```
Read: .claude/product-marketing-context.md
  ├─ Customer personas and pain points
  ├─ Value propositions and proof points
  ├─ Brand voice and tone
  └─ Product features and benefits
```

**When to read:** Before every email sequence design. Emails without audience context = spam.

**If file missing:** Gather context manually before writing.

---

## Decision Tree: Sequence Type

```
START: What triggers this sequence?

├─ NEW SIGNUP (Welcome / Onboarding)
│  ├─ Goal: Activate user to first value moment
│  ├─ Length: 5-7 emails over 14-21 days
│  ├─ Cadence: Day 0, 1, 3, 5, 7, 10, 14
│  └─ Key metric: Activation rate
│
├─ LEAD MAGNET DOWNLOAD (Nurture)
│  ├─ Goal: Educate → build trust → convert to trial/demo
│  ├─ Length: 4-6 emails over 10-14 days
│  ├─ Cadence: Day 0, 2, 4, 7, 10, 14
│  └─ Key metric: Trial signup or demo request rate
│
├─ TRIAL EXPIRING (Conversion)
│  ├─ Goal: Convert free to paid
│  ├─ Length: 3-5 emails in last 7 days of trial
│  ├─ Cadence: Day -7, -3, -1, 0, +1
│  └─ Key metric: Trial-to-paid conversion rate
│
├─ ABANDONED CART / INCOMPLETE ACTION
│  ├─ Goal: Complete the action
│  ├─ Length: 3 emails over 3 days
│  ├─ Cadence: 1 hour, 24 hours, 72 hours
│  └─ Key metric: Recovery rate
│
├─ RE-ENGAGEMENT (Inactive Users)
│  ├─ Goal: Bring back or clean list
│  ├─ Length: 3 emails over 7-10 days
│  ├─ Cadence: Day 0, 3, 7
│  └─ Key metric: Reactivation rate
│
└─ POST-PURCHASE (Retention / Upsell)
   ├─ Goal: Increase LTV, reduce churn
   ├─ Length: 4-6 emails over 30 days
   ├─ Cadence: Day 1, 7, 14, 21, 30
   └─ Key metric: Retention rate, expansion revenue
```

---

## Email Anatomy

### Subject Line
- **Length:** 30-50 characters (mobile preview)
- **Techniques:** Question, number, curiosity gap, personalization
- **A/B test:** Always test 2 subject lines per send
- **Avoid:** ALL CAPS, excessive punctuation!!!, spam trigger words

### Preview Text
- First 40-90 characters visible in inbox
- Complement (don't repeat) subject line
- Use as second hook

### Body Structure

```
1. HOOK (first line)
   └─ Personal, relevant, or curiosity-driven opening

2. BRIDGE (1-2 sentences)
   └─ Connect hook to the main message

3. BODY (2-4 short paragraphs)
   └─ One key message, supporting points

4. CTA (single, clear)
   └─ Button or link, action-oriented text

5. P.S. (optional)
   └─ Second chance to drive action, urgency, or social proof
```

### Design Rules
- **Width:** 600px max
- **Single column** for mobile readability
- **One primary CTA** per email (can repeat it)
- **Text-to-image ratio:** 80:20 (deliverability)
- **Always include** plain text version

---

## Welcome Sequence Template

| Email | Timing | Subject | Goal |
|-------|--------|---------|------|
| 1 | Immediate | Welcome + quick win | Deliver value instantly |
| 2 | Day 1 | Key feature tutorial | Drive first action |
| 3 | Day 3 | Success story / case study | Build trust and aspiration |
| 4 | Day 5 | Address common objection | Remove barriers |
| 5 | Day 7 | Feature they haven't tried | Deepen engagement |
| 6 | Day 10 | Social proof + CTA | Push toward conversion |
| 7 | Day 14 | Final value reminder + offer | Last conversion push |

---

## Quality Rubric

Score each dimension 1-5:

| Dimension | 1 (Poor) | 3 (Adequate) | 5 (Excellent) |
|-----------|----------|---------------|----------------|
| **Sequence logic** | Random order | Reasonable flow | Psychological progression |
| **Subject lines** | Generic, long | Clear, relevant | Curiosity-driven, tested |
| **Value per email** | Sales pitch | Mix of value/ask | Every email gives something |
| **Personalization** | None | Name merge | Behavior-based content |
| **CTA clarity** | Multiple/unclear | Single, clear | Action-specific, low-friction |
| **Timing** | Random | Standard cadence | Behavior-triggered |
| **Measurement** | No tracking | Open/click rates | Full funnel to conversion |

**28+ / 35 = Ship** | **21-27 = Revise** | **<21 = Rethink**

---

## Anti-Pattern References

- **M11: Batch and blast** — Sending the same email to everyone is the fastest way to destroy deliverability and engagement
- **M5: Vanity metrics** — Open rates don't matter if nobody clicks; click rates don't matter if nobody converts
- **M7: Features without benefits** — Email body that lists features without explaining what they mean for the reader

---

## Benchmarks

| Metric | Average | Good | Excellent |
|--------|---------|------|-----------|
| Open rate | 20-25% | 25-35% | 35%+ |
| Click rate | 2-3% | 3-5% | 5%+ |
| Click-to-open rate | 10-15% | 15-25% | 25%+ |
| Unsubscribe rate | <0.5% | <0.3% | <0.1% |
| Welcome sequence conversion | 5-10% | 10-20% | 20%+ |
| Abandoned cart recovery | 5-10% | 10-15% | 15%+ |

---

## Cross-Skill References

| When you need... | Use skill |
|-------------------|-----------|
| Write email copy | `copywriting` |
| Design popup for email capture | `popup-cro` |
| Test subject lines | `ab-test-setup` |
| Track email performance | `analytics-tracking` |
| Product context | `product-marketing-context` |

---

## Council Integration

Submit email sequences to:
- **Marketing Council** — Brand voice, messaging alignment, cadence review
