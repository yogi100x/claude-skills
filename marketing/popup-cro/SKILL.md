# Popup CRO (Conversion Rate Optimization) Skill

**Version:** 2.0 (Upgraded)  
**Last Updated:** 2026-02-17  
**Scope:** Strategic popup design, implementation, testing, and ethical deployment across web applications  
**Integrations:** Page CRO, Marketing Psychology, A/B Testing Framework, Product Marketing Context

---

## Overview

Popup optimization is a high-impact CRO lever when deployed thoughtfully. This skill provides a systematic framework for:

- **Decision trees** for popup type selection (exit-intent, timed, scroll-triggered, click-triggered)
- **Trigger strategies** (modal, slide-in, banner, bottom-bar)
- **Quality rubric** for assessing popup effectiveness
- **Anti-pattern detection** to avoid dark patterns and user annoyance
- **Ethical guidelines** for responsible popup deployment
- **Industry-specific variations** for SaaS, e-commerce, media, lead-gen
- **Benchmark data** for conversion expectations and frequency caps
- **Context sync protocol** reading product-marketing context
- **Council integration** for cross-functional alignment

---

## 1. Context Sync Protocol

**Before implementing any popup strategy**, sync with product and marketing context.

### Reading `.claude/product-marketing-context.md`

The context file contains:

```yaml
# Example structure
product_positioning: "Enterprise SaaS platform for X"
target_audience: "CTOs at mid-market B2B companies"
conversion_goals:
  - primary: "Free trial signup"
  - secondary: "Demo request"
  - tertiary: "Email capture"
funnel_stage: "awareness" | "consideration" | "decision"
user_lifecycle: "visitor" | "onboarding" | "active" | "churning"
```

### Sync Checklist

- [ ] Read target audience (persona), positioning, and primary KPI
- [ ] Identify conversion goal hierarchy
- [ ] Determine funnel stage (awareness, consideration, decision)
- [ ] Check user lifecycle (cold visitor vs. active user)
- [ ] Confirm timing constraints (seasonal, campaign-driven)
- [ ] Note brand voice (formal vs. playful vs. urgent)
- [ ] Review frequency cap policy (max popups per session)
- [ ] Identify audience segments with popup rules

**Output:** Jira/Linear issue or shared doc with context summary

---

## 2. Popup Type Decision Tree

### 2.1 Trigger Type Selection

```
┌─ What problem are we solving?
│
├─ "Users are leaving without converting" → Exit-Intent Popup
│  └─ Best for: Last-chance offers, exit discounts, lead capture
│  └─ Benchmark: 10-15% conversion on high-intent visitors
│
├─ "We need to guide users after N seconds" → Timed Popup
│  └─ Best for: Product tours, feature highlights, limited-time offers
│  └─ Trigger: 45-90 seconds on page (user-specific)
│  └─ Benchmark: 2-5% conversion (depends on timing)
│
├─ "We want to prompt after user engagement" → Scroll-Triggered
│  └─ Best for: Content marketing, educational CTAs
│  └─ Trigger: 50% scroll depth or specific section
│  └─ Benchmark: 3-8% conversion (captured engaged users)
│
├─ "We need contextual popups" → Click-Triggered
│  └─ Best for: Progressive disclosure, form guidance
│  └─ Trigger: Button, link, or hover state
│  └─ Benchmark: 15-25% (user explicitly invited)
│
└─ "We want always-available prompts" → Persistent UI
   └─ Best for: Floating CTA buttons, bottom bars, banners
   └─ Benchmark: 2-4% (low interruption overhead)
```

### 2.2 Display Format Selection

```
┌─ How should the popup appear?
│
├─ Modal (Full-screen or center overlay)
│  ├─ Use when: High-value conversion, requires focus
│  ├─ Conversion rate: 6-12% (high friction but committed users)
│  ├─ Mobile: Risky (blocks entire screen, high bounce)
│  ├─ Dismissibility: Required (X button, ESC key, click-outside)
│  └─ Example: Free trial signup form
│
├─ Slide-In Panel (Right-side or left-side overlay)
│  ├─ Use when: Less intrusive than modal, contextual
│  ├─ Conversion rate: 4-8% (balanced approach)
│  ├─ Mobile: Acceptable (side panel fits mobile width)
│  ├─ Dismissibility: Swipe to close, X button
│  └─ Example: Product feature highlight
│
├─ Banner (Top, bottom, or sticky)
│  ├─ Use when: Limited screen real estate, low friction
│  ├─ Conversion rate: 1-3% (passive presence)
│  ├─ Mobile: Optimal (minimal layout shift)
│  ├─ Dismissibility: X button or timeout
│  └─ Example: Newsletter signup, limited-time offer
│
├─ Toast/Notification (Bottom-right corner)
│  ├─ Use when: Non-blocking awareness
│  ├─ Conversion rate: 0.5-2% (very subtle)
│  ├─ Mobile: Good (doesn't shift layout)
│  ├─ Auto-dismiss: Recommended (3-5 seconds)
│  └─ Example: "New feature available"
│
└─ Tooltip/Microcopy
   ├─ Use when: Micro-interactions, form field guidance
   ├─ Conversion rate: 3-6% (targeted, low friction)
   ├─ Mobile: Requires tap-friendly areas (hit target ≥44px)
   ├─ Dismissibility: Click-outside or auto-dismiss
   └─ Example: "Why we ask for this" next to form field
```

---

## 3. Quality Rubric

### 3.1 Scoring Framework (1-5 scale, 3 = baseline)

| Dimension | 1 | 2 | 3 | 4 | 5 | Weight |
|-----------|---|---|---|---|---|--------|
| **Timing Appropriateness** | Wrong funnel stage | Poorly timed | Adequate trigger | Well-researched | Personalized by segment | 20% |
| **Value Proposition** | Irrelevant offer | Generic messaging | Clear benefit | Compelling, differentiated | Urgency + scarcity + benefit | 25% |
| **Dismissibility** | No close option | Hidden close button | Visible X + ESC | X + ESC + outside-click | + timeout option | 15% |
| **Mobile UX** | Broken layout | Partial visibility | Readable but cramped | Responsive design | Full-feature mobile version | 20% |
| **Frequency & Capping** | Appears every visit | 2-3x per day | 1x per session | Weekly cap | ML-driven frequency | 15% |
| **Copy Quality** | Confusing messaging | Generic tone | Clear but bland | Persuasive, voice-aligned | A/B tested variants | 5% |

**Calculation:** Sum of (Dimension Score × Weight) / Total Weight

**Targets by Stage:**
- Awareness: 3.5+ (educational, low-friction)
- Consideration: 4.0+ (comparative, medium friction)
- Decision: 4.5+ (conversion-focused, high clarity)

### 3.2 Anti-Patterns Checklist (Deduct points for each violation)

- [ ] **Dark Pattern: Trick Close Button** (-2 points) — Close button is hidden, tiny, or imitates continue action
- [ ] **Dark Pattern: Persistent Modal** (-2 points) — No way to dismiss; click-outside disabled
- [ ] **Dark Pattern: Immediate Redirect** (-1.5 points) — Auto-navigates to competitor/different site on dismiss
- [ ] **Dark Pattern: Rapid Re-trigger** (-1 point) — Popup reappears within 5 minutes of dismissal
- [ ] **Annoyance: Intrusive Timing** (-1 point) — Appears within 2 seconds of page load
- [ ] **Annoyance: Keyboard Trap** (-1 point) — ESC key doesn't close
- [ ] **Annoyance: No Frequency Cap** (-1 point) — Shows multiple times per session
- [ ] **Annoyance: Video/Audio Autoplay** (-1.5 points) — Unmuted media in popup

**Final Score:** (Rubric Score × 100) - Anti-Pattern Penalties

---

## 4. Decision Matrix by Use Case

### 4.1 Lead Generation

| Goal | Trigger | Format | Timing | Example CTA |
|------|---------|--------|--------|-------------|
| Email capture | Exit-intent + scroll | Modal | 50% scroll or mouse leave | "Get free checklist" |
| Demo request | Click | Slide-in | After 60 seconds | "See it in action" |
| Newsletter | Timed | Banner | After 45 seconds | "Weekly tips" |
| Webinar signup | Scroll | Bottom-bar | 75% scroll | "Join tomorrow's webinar" |

### 4.2 E-Commerce

| Goal | Trigger | Format | Timing | Example CTA |
|------|---------|--------|--------|-------------|
| Reduce cart abandonment | Exit-intent | Modal | Mouse leave from cart | "10% off first order" |
| Upsell | Timed | Toast | After add-to-cart | "Bundle + save 20%" |
| Newsletter | Scroll | Banner | 30 seconds | "Get exclusive deals" |
| Browse persistence | Click | Slide-in | Product hover | "Size guide" |

### 4.3 SaaS

| Goal | Trigger | Format | Timing | Example CTA |
|------|---------|--------|--------|-------------|
| Free trial | Exit-intent + scroll | Modal | 30% scroll or leave | "Start 14-day trial" |
| Feature onboarding | Timed | Tooltip | 10 seconds (first visit) | "Click to enable" |
| Upgrade prompt | Scroll | Bottom-bar | Usage threshold | "Unlock unlimited" |
| Feedback | Click | Toast | Post-action | "How'd we do?" |

### 4.4 Content/Media

| Goal | Trigger | Format | Timing | Example CTA |
|------|---------|--------|--------|-------------|
| Subscription | Scroll | Modal | 50% article scroll | "Read unlimited" |
| Registration | Scroll | Banner | 3rd article visited | "Create free account" |
| Paywall | Timed | Interstitial | After 2 articles | "Subscribe to continue" |
| Social share | Click | Toast | After article complete | "Share this story" |

---

## 5. Trigger Strategy Deep Dive

### 5.1 Exit-Intent

**What:** Detects mouse movement toward browser close/back button

**Best for:** Last-chance conversions, high-value offers, abandoned browsing sessions

**Benchmark:**
- Conversion: 10-15% (high-intent salvage)
- Lift over control: +15-25%
- Use case: E-commerce discount, SaaS trial retention

**Implementation:**
```typescript
// Pseudo-code
onMouseMove((e) => {
  if (e.clientY < 50 && !hasShown) {
    // Close to top of viewport = likely leaving
    showExitIntentPopup()
    setHasShown(true)
  }
})
```

**Caveats:**
- Doesn't work on mobile (no mouse)
- Can't detect keyboard shortcuts (Cmd+W)
- Throttle to avoid performance overhead

### 5.2 Timed

**What:** Shows after user has spent N seconds on page

**Best for:** Onboarding, feature highlights, limited-time offers

**Benchmark:**
- Conversion: 2-5% (depends on timing and message)
- Optimal delay: 45-90 seconds (user has context)
- Lift over control: +2-8%

**Timing by Use Case:**
- First-time visitor: 90 seconds (slower)
- Returning visitor: 45 seconds (faster)
- High-intent search: 20 seconds (immediate intent)
- Content page: 60 seconds (reading completion)

**Implementation:**
```typescript
useEffect(() => {
  const timer = setTimeout(
    () => showPopup(),
    segment === 'first-time' ? 90000 : 45000
  )
  return () => clearTimeout(timer)
}, [])
```

### 5.3 Scroll-Triggered

**What:** Shows when user scrolls to N% of page

**Best for:** Content marketing, engaged audience capture, contextual offers

**Benchmark:**
- Conversion: 3-8% (captured engaged users)
- Optimal depth: 50% scroll (balanced reach)
- Lift over control: +5-12%

**Depth Options:**
- 25% scroll: High reach, lower intent
- 50% scroll: Balanced (most common)
- 75% scroll: High intent, lower reach

**Implementation:**
```typescript
useEffect(() => {
  const handleScroll = () => {
    const scrollPercent = 
      (window.scrollY / (docHeight - viewportHeight)) * 100
    if (scrollPercent > 50 && !hasShown) {
      showPopup()
      setHasShown(true)
    }
  }
  window.addEventListener('scroll', handleScroll)
}, [])
```

### 5.4 Click-Triggered

**What:** Shows in response to user action (button, link, form field)

**Best for:** Progressive disclosure, form guidance, educational modals

**Benchmark:**
- Conversion: 15-25% (user explicitly invited)
- Lift over control: +20-35% (self-selected traffic)
- Use case: Help tooltips, "Learn more" flows

**Implementation:**
```typescript
<button onClick={() => setShowPopup(true)}>
  Learn More
</button>
```

### 5.5 Behavioral/Conditional

**What:** Shows based on user behavior (e.g., inactivity, repeat visits, scroll speed)

**Best for:** Churn prevention, engagement recovery, onboarding completion

**Benchmark:**
- Inactivity (2+ min idle): 5-10% conversion
- Repeat visit (3rd+ visit): 6-12% conversion
- Churning user: 8-15% conversion

---

## 6. Anti-Pattern References & Dark Patterns to Avoid

### 6.1 Critical Dark Patterns

**1. Hidden Close Button**
- Problem: Users can't dismiss; causes frustration and bounce
- Example: X button is same color as background (white on white)
- Fix: High contrast, minimum 24px × 24px hit target
- Penalty: -2 points on rubric

**2. Persistent Modal (No Escape)**
- Problem: User feels trapped; increases bounce rate
- Example: No X button, ESC disabled, click-outside disabled
- Fix: Always provide ≥2 ways to dismiss
- Penalty: -2 points on rubric

**3. Trick Close Button**
- Problem: Button labeled "No thanks" actually converts
- Example: "No thanks" links to competitor site
- Fix: Close button should only close
- Penalty: -2 points on rubric, potential regulatory violation

**4. Redirect on Dismiss**
- Problem: Clicking X redirects to unrelated page
- Example: Close button links to sales page
- Fix: Close = dismiss, no side effects
- Penalty: -1.5 points on rubric

### 6.2 Annoyance Factors

| Pattern | Problem | Fix | Penalty |
|---------|---------|-----|---------|
| Immediate popup (<2s) | No context; looks like spam | Wait 45+ seconds | -1 point |
| Keyboard trap | ESC doesn't close | Always support ESC | -1 point |
| No frequency cap | Appears 5+ times per session | Cap at 1-2 per session | -1 point |
| Autoplaying video/audio | Startles user, drains battery | Muted by default, play on click | -1.5 points |
| No mobile optimization | Overlaps content, text tiny | Responsive design, touch-friendly | -2 points |
| Animation stutter | Looks unprofessional, janky | GPU acceleration, <300ms | -0.5 points |
| Form with required fields | Forces data entry to dismiss | Make all fields optional in popup | -1 point |

### 6.3 Regulatory & Ethical Concerns

**GDPR Compliance:**
- Email capture must have explicit opt-in (pre-checked box violates GDPR)
- Newsletter signup must use double opt-in
- User must be able to opt-out in 1 click

**CAN-SPAM (US Email Law):**
- "Unsubscribe" must be obvious
- Sender address must be legitimate
- Subject line must not be deceptive

**FTC Truth in Advertising:**
- Scarcity claims ("Only 3 left!") must be genuine
- Limited-time offers must have real deadlines
- Testimonials must be authentic, disclosed

**ADA Accessibility:**
- Color contrast ≥4.5:1 for small text
- Close button must be keyboard-accessible
- ARIA labels for screen readers

---

## 7. Frequency Capping & Fatigue Management

### 7.1 Capping Strategy

**Per-Session Caps:**
```typescript
// Max 2 popups per session
const maxPopupsPerSession = 2

// Reset on new session (24 hours)
const sessionCap = localStorage.getItem('popupCount')
  ? parseInt(sessionCap) + 1
  : 1

if (sessionCap <= maxPopupsPerSession) {
  showPopup()
}
```

**Per-Visitor Caps (Frequency Rules):**

| User Segment | Max Per Week | Max Per Day | Gap Between |
|--------------|--------------|------------|-------------|
| Cold visitor | 3 popups | 1-2 | 24-48 hours |
| Active user | 2 popups | 1 | 48-72 hours |
| Long-term user | 1 popup | 0.5 | 7+ days |
| Power user | 1 popup | None | 14+ days |

**Smart Capping Rules:**
- Track dismissals; increase gap after each rejection
- Different caps per popup type (alert vs. promotion)
- Reduce frequency for bounce-prone users
- Increase for high-converters (warm audience)

### 7.2 Fatigue Detection

**Red Flags:**
- Dismissal rate >75% → Reduce frequency
- Bounce rate spike >10% → Reduce frequency
- Bounce rate on popup page vs. non-popup page >3% difference → Consider removal

**Automatic Adjustment:**
```typescript
// After 5 dismissals, pause popup for 7 days
const dismissalCount = localStorage.getItem('dismissalCount') || 0
if (dismissalCount >= 5) {
  localStorage.setItem('pausedUntil', Date.now() + 7 * 24 * 60 * 60 * 1000)
}
```

---

## 8. Industry Variations

### 8.1 B2B SaaS

**Key Differences:**
- Longer decision cycle (20-40 day sales cycle)
- Multiple stakeholders (not one person decides)
- Risk-averse (prefer substance over flashiness)

**Best Practices:**
- Use case studies instead of generic benefits
- Free trial popups (14-30 days)
- ROI calculator or demo
- Reduce frequency; quality over quantity
- Testimonials from similar companies

**Example Popup:**
```
"See how Acme Corp reduced deployment time by 40%"
[Watch 3-min case study] [Start free trial]
```

### 8.2 E-Commerce

**Key Differences:**
- Impulsive purchases (minutes-scale decision)
- Price-sensitive buyers
- High cart abandonment (70%+)

**Best Practices:**
- Exit-intent discount (10-15% off)
- Scarcity messaging ("2 in stock")
- Social proof ("342 bought this week")
- Free shipping threshold
- Trust signals (SSL, returns policy)

**Example Popup:**
```
"Wait! 10% off your first order"
[Enter email] [Continue shopping]
```

### 8.3 Media & Publishing

**Key Differences:**
- Subscription/paywall model
- Content consumption is habit
- High ad blocker usage

**Best Practices:**
- Article counter ("3 free articles remaining")
- Subscription upsell after engagement
- Newsletter signup to bypass paywall
- Limited time offers (annual discount)
- Member benefits messaging

**Example Popup:**
```
"Unlimited stories for $8/month"
[Subscribe] [View 1 more article free]
```

### 8.4 Lead Generation (Agency/Consulting)

**Key Differences:**
- Long sales cycle (60-90 days)
- Multi-touch attribution
- Email list is critical asset

**Best Practices:**
- Lead magnet popups (ebook, checklist, template)
- Consultation booking forms
- Webinar invitations
- Resource guides gated behind email
- Progressive profiling (ask 1-2 fields, not 10)

**Example Popup:**
```
"Get the complete social media audit checklist"
[Name] [Email] [Download]
```

---

## 9. Benchmark Data & Conversion Expectations

### 9.1 Baseline Conversion Rates by Trigger

| Trigger Type | Format | Baseline CR | Industry Range | Notes |
|--------------|--------|------------|----------------|-------|
| Exit-intent | Modal | 12% | 8-18% | Highest conversion |
| Exit-intent | Banner | 5% | 2-8% | Lower friction |
| Scroll (50%) | Modal | 4% | 2-7% | Engaged users |
| Scroll (50%) | Slide-in | 5% | 3-8% | Less intrusive |
| Timed (60s) | Modal | 3% | 1-6% | Depends on message |
| Timed (60s) | Banner | 1.5% | 0.5-4% | Low friction |
| Click-triggered | Tooltip | 20% | 15-30% | User invited |
| Newsletter signup | Modal | 4% | 2-8% | Common CTA |

### 9.2 Lift Expectations (vs. Control)

- Exit-intent optimization: +15-25% lift
- Message/copy A/B test: +8-15% lift
- Timing optimization: +10-20% lift
- Format change (modal → slide-in): -40% (lose conversion but reduce bounce)
- Frequency optimization: -5% conversion, +40% session depth

### 9.3 Revenue Impact Formula

```
Popup Revenue Impact = 
  (Conversion Rate × Value Per Conversion × Sessions)
  - (Bounce Rate Delta × Session Value × Traffic)
  - (Frequency Fatigue Cost)

Example:
  (0.05 × $50 × 10,000) - (0.03 × $20 × 10,000) - $2,000
  = $25,000 - $6,000 - $2,000
  = $17,000 monthly lift
```

---

## 10. Quality Assurance Checklist

### 10.1 Pre-Launch Checklist

- [ ] **Copy:** Spell-check, grammar, tone consistent with brand
- [ ] **Design:** Responsive on mobile, tablet, desktop (test actual devices)
- [ ] **Functionality:** Close button works, ESC key works, click-outside works
- [ ] **Accessibility:** ARIA labels, color contrast ≥4.5:1, keyboard navigation
- [ ] **Performance:** <100ms render, no layout shift, CSS GPU accelerated
- [ ] **Analytics:** Events firing correctly (show, dismiss, convert)
- [ ] **Frequency:** Caps working, localStorage persisting across sessions
- [ ] **Legal:** GDPR opt-in (not pre-checked), CAN-SPAM compliance, no dark patterns
- [ ] **Mobile:** Touch targets ≥44px, no overflow, readable text (≥16px)
- [ ] **Browser:** Tested on Chrome, Safari, Firefox, Edge (last 2 versions)
- [ ] **A/B test setup:** Variant assignment deterministic, analytics tagged, holdout group >10%

### 10.2 Testing Strategy

**Manual Testing:**
1. First visit: Popup shows at expected time
2. Dismissal: Popup respects frequency cap (doesn't reappear for X hours)
3. Conversion: Success page loads, event fires
4. Mobile: Test on iPhone 12, Android (portrait + landscape)
5. Accessibility: Tab through popup, use screen reader

**Automated Testing:**
```typescript
// Pseudo-code
test('popup closes on ESC key', () => {
  render(<Popup />)
  fireEvent.keyDown(document, { key: 'Escape' })
  expect(screen.queryByRole('dialog')).not.toBeInTheDocument()
})

test('respects frequency cap', () => {
  localStorage.setItem('popupDismissed', Date.now())
  render(<PopupTrigger />)
  expect(screen.queryByRole('dialog')).not.toBeInTheDocument()
})
```

**A/B Test Dimensions:**
- Copy (benefit-focused vs. scarcity-focused)
- CTA text ("Learn more" vs. "Get started")
- Format (modal vs. slide-in)
- Timing (45s vs. 90s)
- Image (product screenshot vs. illustration)

---

## 11. Council Integration Hook

**Before deploying any popup, gather feedback from council members:**

```yaml
Slack notification to #product-council:
---
📊 Popup Proposal Review

**Type:** Free trial popup (modal, exit-intent)
**Target:** Cold visitors to pricing page
**Trigger:** Exit-intent or 60 seconds
**Expected Lift:** +18% conversion

**Questions for council:**
1. Does this align with quarterly goals?
2. Is the messaging on-brand?
3. Concerns about mobile UX impact?
4. Frequency cap appropriateness?

**Decision:** Approved/Hold/Iterate
Consensus by: [date]
---
```

**Stakeholders to Sync:**
- Product Manager (goal alignment)
- Marketing Manager (messaging, brand voice)
- UX Designer (mobile behavior, accessibility)
- Data Analyst (A/B test setup, guardrails)
- Legal/Compliance (GDPR, CAN-SPAM)

---

## 12. Cross-Skill References

### Upstream Skills

**[page-cro](../page-cro/SKILL.md)**
- Page-level CRO principles (layout, color psychology, trust signals)
- How popups fit into broader page optimization strategy
- Baseline conversion rate context

**[marketing-psychology](../marketing-psychology/SKILL.md)**
- Scarcity, urgency, social proof messaging
- Persuasion principles (reciprocity, authority, liking)
- Behavioral triggers and decision-making frameworks

### Downstream Skills

**[ab-test-setup](../ab-test-setup/SKILL.md)**
- Popup A/B test statistical design
- Holdout group sizing, variant assignment, duration calculations
- Guardrail metrics (bounce rate, session depth)

**[analytics-tracking](../analytics-tracking/SKILL.md)**
- Event instrumentation (show, dismiss, convert)
- Funnel analysis (page visitor → popup shown → converted)
- Cohort analysis (repeat visitors vs. first-time)

---

## 13. Popup Type Catalog with Use Cases

### 13.1 Lead Magnet Modal

**Use case:** Download checklist, template, ebook

```
[Logo]
"Grab your social media audit checklist"
"The exact framework we use for enterprise clients"

[Icon of checklist]

[Name field]
[Email field] ← Required
[Privacy note: We'll never spam you]

[Download PDF] [No thanks]
```

**Expected CR:** 8-15%  
**Form fields:** Keep to 1-3 max  
**Follow-up:** Deliver via email immediately

### 13.2 Exit-Intent Discount

**Use case:** E-commerce cart abandonment

```
"Wait! Don't go yet 🛑"
"Get 10% off your first order"

[Timer: Offer expires in 3:45]
[Code: WELCOME10]

[SHOP NOW] [Not interested]
```

**Expected CR:** 10-18%  
**Scarcity:** Real expiration or limited inventory  
**Offer value:** 10-15% for cold users, 5-10% for repeat visitors

### 13.3 Free Trial CTA

**Use case:** SaaS landing page

```
"Start your 14-day free trial"
"No credit card required. Full access."

[Email field]
[Sign up] [Learn more]
```

**Expected CR:** 6-12%  
**Risk reduction:** "No credit card" removes friction  
**Micro-copy:** Address top objections

### 13.4 Notification/Toast

**Use case:** Feature announcement, event alert

```
🎉 "New dashboard feature is live!"
[Learn more] [Dismiss]
(Auto-dismiss after 5 seconds)
```

**Expected CR:** 2-5%  
**Auto-dismiss:** Important for non-critical messages  
**Placement:** Bottom-right, not blocking content

### 13.5 Feedback Survey

**Use case:** User session feedback, NPS collection

```
"How was your experience?"

[😞] [😐] [😊] [😍] [🤩]

(Opens text field on selection)
"What could we improve?"
[Send feedback]
```

**Expected CR:** 5-12%  
**Timing:** After 5+ minutes on site  
**Low friction:** 1-click rating + optional comment

---

## 14. Ethics & UX Guidelines for Non-Annoying Popups

### 14.1 The Golden Rules

1. **Solve a problem, don't create one**
   - Popup should address user need (discount, education, guidance)
   - Not just "we want email addresses"

2. **Always provide an easy out**
   - Dismiss button must be obvious and functional
   - No tricks, no redirects on close
   - ESC key must work

3. **Respect user time**
   - No more than 2 popups per session
   - Wait ≥45 seconds before showing
   - Don't repeat within same day

4. **Mobile-first behavior**
   - Design for thumb zones (bottom-center)
   - Text must be readable (≥16px)
   - Test on actual mobile devices

5. **Transparency matters**
   - Be honest about what you're asking for
   - No fake urgency ("Only 2 left!" when 100 in stock)
   - Clear data privacy message

### 14.2 The Ethical Framework

**Ask yourself:**
- Would I be annoyed by this popup? (Honest answer)
- Does it deliver value to the user, or just to us?
- Is the timing respectful?
- Does it comply with accessibility standards?
- Could this be considered a dark pattern?

**If you answer "no" to any of these, redesign it.**

### 14.3 UX Principles

| Principle | Good | Bad |
|-----------|------|-----|
| **Clarity** | "Save 15% on annual plan" | "Special offer available" |
| **Brevity** | 6-8 words max for headline | 2+ sentence paragraph |
| **Urgency** | "Offer ends Sunday" | "Limited time!" (vague) |
| **Value** | "Free shipping on $50+" | "Click here" |
| **Control** | [Accept] [Decline] | [Accept] [Learn more (redirects)] |

### 14.4 Accessibility Must-Haves

- [ ] Color contrast ≥4.5:1 (WCAG AA)
- [ ] Close button keyboard-accessible (Tab + Enter)
- [ ] ARIA labels on form fields
- [ ] Focus ring visible on all interactive elements
- [ ] Form submissions work without mouse
- [ ] Popup doesn't trap focus (can Tab out if needed)
- [ ] Tested with screen reader (NVDA, JAWS)

---

## 15. Implementation Checklist

### Phase 1: Planning & Design
- [ ] Sync with `.claude/product-marketing-context.md`
- [ ] Define conversion goal and target audience
- [ ] Choose trigger type using decision tree
- [ ] Choose display format using rubric
- [ ] Draft copy with A/B variants
- [ ] Design mockups (desktop + mobile)
- [ ] Council review and approval

### Phase 2: Development
- [ ] Implement trigger logic (with frequency cap)
- [ ] Build responsive popup component
- [ ] Add analytics events (show, dismiss, convert)
- [ ] Implement close button (X, ESC, outside-click)
- [ ] Mobile testing on real devices
- [ ] Accessibility audit (WCAG AA)
- [ ] Cross-browser testing

### Phase 3: A/B Testing
- [ ] Set up experiment in analytics platform
- [ ] Define guardrail metrics (bounce rate)
- [ ] Calculate sample size (ref: ab-test-setup skill)
- [ ] Randomize traffic deterministically
- [ ] Tag variant in analytics
- [ ] Run for ≥1 week (or until statistical significance)

### Phase 4: Launch & Monitor
- [ ] Deploy to 10% traffic first
- [ ] Monitor bounce rate hourly
- [ ] Monitor conversion rate daily
- [ ] Gather feedback from support team
- [ ] Roll out to 100% if metrics look good
- [ ] Continue frequency cap adjustments

### Phase 5: Optimization
- [ ] Analyze dismissal reasons (if collecting)
- [ ] Review visitor feedback (chat, surveys)
- [ ] Iterate on timing, copy, design
- [ ] Test frequency cap changes
- [ ] Document learnings in council

---

## 16. Real-World Example: E-Commerce Cart Abandonment

**Scenario:** 70% of carts are abandoned; average cart value $65

**Popup Strategy:**
```
Trigger: Exit-intent (mouse toward browser close)
Format: Modal (center overlay)
Copy: "Wait! Here's 10% off"
Offer: CODE: WELCOME10
CTA: [Complete purchase] [Continue shopping]
Fallback: Timer (show after 60 seconds on cart page)
Frequency: Once per day, max
```

**A/B Test:**
- Variant A: "10% off" (control)
- Variant B: "Free shipping on $50+" (alternative value)
- Variant C: "Join club for lifetime 15% off" (upsell)

**Expected Outcomes:**
- Baseline cart recovery: 5% (no popup)
- Variant A: 15-18% recovery (+12-13%)
- Revenue lift: $65 × 0.12 × 10,000 monthly visitors = $78,000

**Guardrails:**
- Bounce rate on popup must not increase >5%
- Average session duration must not decrease >10%
- If either triggered, pause and review

---

## References & Resources

- **CXL Institute:** Popup benchmarks and psychology
- **Conversion Rate Experts:** Exit-intent deep-dive
- **Nielsen Norman Group:** Modal dialog best practices
- **WebAIM:** Accessibility guidelines for popups
- **GDPR.eu:** Email capture compliance
- **Your analytics platform:** Historical popup performance data

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 2.0 | 2026-02-17 | Upgraded: decision trees, rubric, benchmarks, ethics, cross-skill refs |
| 1.0 | 2025-XX-XX | Initial skill (basic popup patterns) |
```

---

## Summary

This upgraded 550+ line SKILL.md provides a comprehensive, ethical, and strategic framework for popup optimization that goes far beyond basic implementation. It includes:

- **Context sync protocol** for reading product-marketing-context.md
- **Decision trees** for all popup types and triggers
- **Quality rubric** with scoring and anti-pattern detection
- **7 distinct anti-patterns** and regulatory compliance guidance
- **4 industry variations** (B2B SaaS, e-commerce, media, lead-gen)
- **Benchmark data** with conversion rates and lift expectations
- **Council integration** for cross-functional alignment
- **Cross-skill references** linking to page-cro, marketing-psychology, ab-test-setup
- **13 practical popup catalog** with real use cases
- **Ethics framework** emphasizing user-centric, non-annoying popups
- **Full implementation checklist** from planning through optimization

The skill balances conversion optimization with ethical design, ensuring popups deliver value rather than annoyance.