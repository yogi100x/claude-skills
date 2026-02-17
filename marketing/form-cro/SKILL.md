# form-cro Skill

**Purpose:** Optimize web forms for conversion, lead capture, and user trust through evidence-based design patterns.

**Maturity Level:** Production

**Version:** 2.0

---

## Quick Context

Forms are friction points. Every field costs conversions. This skill provides:
- Decision trees for form type optimization
- Field count benchmarks by industry
- Quality scoring rubric (15-point audit)
- Anti-pattern detection and remediation
- Cross-skill integration (upstream: page-cro; downstream: ab-test-setup)
- Context sync with product-marketing documentation

---

## 1. Context Sync Protocol

Before optimizing a form, load context from `.claude/product-marketing-context.md`:

```yaml
Required Context:
  - Business model: (B2B, B2C, Marketplace, SaaS)
  - Primary conversion goal: (Lead capture, Demo booking, Purchase, Account creation)
  - Target audience: (SMB, Enterprise, Consumer, Developer)
  - Current conversion rate: (baseline for A/B testing)
  - Audience urgency level: (High, Medium, Low)
  - Budget constraint: (Cost-per-lead targets)
```

**Loading Steps:**
1. Check if `.claude/product-marketing-context.md` exists in project root
2. Extract business model, goal, and audience
3. Reference industry variation rules (Section 5) for your model
4. Confirm assumptions with stakeholders before optimization

**If Context Unavailable:**
- Assume B2B SaaS with moderate urgency
- Use conservative field count (≤7 fields for lead capture)
- Prioritize trust signals and progressive disclosure
- Recommend discovery call with marketing team

---

## 2. Decision Tree: Form Type Selection

### Entry Point: What is the form's primary purpose?

```
├─ LEAD CAPTURE (Email + Name Only)
│  ├─ Audience Urgency: HIGH
│  │  └─ Structure: 2-3 fields, single-step
│  │     - Email, Name, Company (optional)
│  │     - CTAssumption: Will re-engage in sequence
│  │
│  ├─ Audience Urgency: MEDIUM
│  │  └─ Structure: 3-5 fields, progressive disclosure
│  │     - Email, Name, Company, Phone (hidden initially)
│  │     - Show phone on second submission or after engagement
│  │
│  └─ Audience Urgency: LOW
│     └─ Structure: 5-7 fields, two-step form
│        - Step 1: Email, Name, Company
│        - Step 2: Phone, Budget, Timeline
│
├─ CONTACT REQUEST (Personalization)
│  ├─ Industry: Enterprise B2B
│  │  └─ Structure: 6-8 fields
│  │     - Name, Email, Company, Role, Phone, Industry, Use Case
│  │     - Add: LinkedIn URL (optional, for qualification)
│  │
│  ├─ Industry: SMB B2B
│  │  └─ Structure: 5-6 fields
│  │     - Name, Email, Company, Phone, Use Case
│  │
│  └─ Industry: B2C Consumer
│     └─ Structure: 3-4 fields
│        - Name, Email, Subject, Message
│
├─ DEMO REQUEST (High-Intent)
│  ├─ Product Complexity: HIGH
│  │  └─ Structure: 7-9 fields + timezone selector
│  │     - Name, Email, Company, Phone, Team Size, Use Case, Timeline
│  │     - Add: Qualification scores (budget, authority)
│  │
│  ├─ Product Complexity: MEDIUM
│  │  └─ Structure: 5-6 fields + calendar picker
│  │     - Name, Email, Company, Phone, Best Time to Call
│  │
│  └─ Product Complexity: LOW
│     └─ Structure: 4 fields + inline calendar
│        - Name, Email, Preferred Date/Time (no phone required)
│
├─ CHECKOUT (Purchase Decision)
│  ├─ Order Value: HIGH (>$500)
│  │  └─ Structure: 12-15 fields, multi-step checkout
│  │     - Billing address, Shipping address, Card, Company VAT, PO number
│  │
│  ├─ Order Value: MEDIUM ($50-500)
│  │  └─ Structure: 8-10 fields, two-step checkout
│  │     - Billing, Shipping, Card, Company name, Email
│  │
│  └─ Order Value: LOW (<$50)
│     └─ Structure: 5-6 fields, single-page checkout
│        - Email, Card, Name, Billing Address (auto-fill city/state from ZIP)
│
└─ ACCOUNT CREATION
   ├─ Competitive Friction: HIGH (many alternatives)
   │  └─ Structure: 2-3 fields, OAuth preferred
   │     - Email, Password (consider passwordless)
   │     - Defer: Company, Role, Industry to onboarding
   │
   ├─ Competitive Friction: MEDIUM
   │  └─ Structure: 4-5 fields
   │     - Email, Password, Company, Name
   │
   └─ Competitive Friction: LOW (unique product)
      └─ Structure: 5-7 fields
         - Email, Password, Company, Role, Use Case, Industry
```

---

## 3. Quality Rubric: Form Optimization Scoring

**15-Point Audit Checklist** (Score: 0-15 = Poor to Excellent)

| Dimension | Criteria | Max Points | Scoring |
|-----------|----------|-----------|---------|
| **Field Optimization** | Field count appropriate for form type | 2 | 2: Aligned with benchmarks; 1: 1-2 over; 0: >2 over |
| | Error handling & inline validation | 1 | 1: Real-time, inline messages; 0: Post-submit only |
| | Progressive disclosure (hide optional on load) | 1 | 1: Applied; 0: All fields visible |
| **Mobile UX** | Touch targets ≥48px, spacing ≥16px | 1 | 1: Meets standards; 0: <48px or cramped |
| | Mobile field labels & autofill hints | 1 | 1: Proper `inputMode`, `autocomplete`; 0: Missing |
| | Keyboard type optimization (email, tel, number) | 1 | 1: Correct; 0: All text input |
| **Trust Signals** | Privacy/security badges + copy | 1 | 1: Present (SSL, privacy policy link); 0: Missing |
| | Social proof or testimonial near CTA | 1 | 1: 2+ elements; 0: None |
| | CTAssumption clarity & value prop | 1 | 1: Clear benefit ("Get demo" not "Submit"); 0: Generic |
| **Error Handling** | Client-side validation & UX feedback | 1 | 1: Smooth, helpful; 0: Abrupt or vague |
| | Recoverable errors (re-fill, not lose data) | 1 | 1: Data persists on error; 0: Data lost |
| **Analytics & Tracking** | Form funnel events tracked | 1 | 1: Impression, field_focus, submission, success; 0: None |
| | Drop-off detection by field | 1 | 1: Tracked; 0: Not tracked |
| **Accessibility** | ARIA labels, form grouping | 1 | 1: Proper semantic HTML + ARIA; 0: Missing |
| **Load Performance** | Form JS + CSS <50KB, paint time <500ms | 1 | 1: Meets targets; 0: >50KB or >500ms |

**Scoring Interpretation:**
- 13-15: Production-ready, benchmark-beating
- 10-12: Good, ship with monitoring
- 7-9: Acceptable, plan optimizations
- <7: Risks, remediate before launch

---

## 4. Anti-Pattern References

**From shared anti-patterns library:**

| Anti-Pattern | Symptom | Remediation |
|--------------|---------|------------|
| **"Progressive Overload"** | Form grows to 12+ fields over time | Audit field necessity; move optional to stage 2; use progressive disclosure |
| **"Trust Collapse"** | No privacy/security badges near CTA | Add SSL badge, privacy link, GDPR compliance notice |
| **"Mobile Blindness"** | Optimized for desktop; mobile has <24px touch targets | Audit with DevTools device emulation; test on 5+ real devices |
| **"Field Amnesia"** | Form clears on error; user re-enters all data | Implement client-side data persistence (sessionStorage + validation before submit) |
| **"CAPTCHA Punishment"** | CAPTCHA on every form attempt (not spam-detected) | Use bot detection (invisible reCAPTCHA); only show on failure |
| **"Mystery Validation"** | Error messages like "Invalid format" with no hint | Show example: "Email must include @domain.com" |
| **"Mandatory Opt-Out"** | Email/marketing checkbox defaults to checked | Legal requirement: unchecked by default (GDPR, CAN-SPAM) |
| **"Autofill Rejection"** | `autocomplete="off"` or non-standard names | Use semantic autocomplete attributes; allow browser autofill |
| **"CTA Ambiguity"** | Button text is "Submit" or "Go" (low intent signal) | Use action-driven text: "Start Demo", "Get My Quote", "Join Now" |
| **"Asymmetric Fields"** | Field widths inconsistent; labels not aligned | Use CSS Grid or Flexbox for uniform field sizing; left-align labels |

---

## 5. Industry Variations by Business Type

### B2B SaaS (Lead Capture)

**Benchmark:** 3-5 fields for high-intent segments; 5-7 for cold traffic

**Form Structure:**
```
Step 1 (Lead Capture):
- Email (required)
- Company Name (required)
- Phone (optional, shown after Email blur)

Step 2 (Triggered after 30 sec or on hover of secondary CTA):
- Role/Title (required)
- Team Size (select: 1-10, 11-50, 51-200, 200+)
- Use Case (select: Fastest option)
- Timeline (select: This quarter, Next quarter, Exploring)
```

**Trust Signals:** SOC 2 badge, customer count, G2 rating

---

### E-Commerce (Checkout)

**Benchmark:** 8-10 fields for mobile; 12-15 for high-AOV

**Form Structure:**
```
Step 1 (Shipping):
- Email (auto-detect if logged in)
- Full Name
- Address Line 1 + 2
- City, State, ZIP (ZIP auto-fills city/state)
- Phone (optional)

Step 2 (Payment):
- Card Number (separate inputs or unified)
- Expiry + CVV
- Billing Address (auto-fill from shipping or manual)
- Save card? (checkbox)

Step 3 (Review):
- Order summary
- Promo code (optional)
- Final CTA: "Complete Purchase"
```

**Trust Signals:** SSL badge, money-back guarantee, return policy link, shipping estimator

---

### B2C SaaS (Account Creation)

**Benchmark:** 2-4 fields for passwordless; 4-6 for traditional

**Form Structure (Passwordless Recommended):**
```
Step 1:
- Email (required)
- [Verify email link sent]

Step 2 (In email):
- [One-click login link or 6-digit code]

Step 3 (On return):
- Full Name (optional, ask later in onboarding)
- Company (optional, ask later)
```

**Trust Signals:** Data encryption notice, no credit card required, free trial duration

---

### Enterprise (Contact/Demo)

**Benchmark:** 8-10 fields; qualification scores critical

**Form Structure:**
```
- Company Name (required)
- Full Name (required)
- Email (required)
- Phone (required)
- Title/Role (required)
- Department (select)
- Employee Count (select)
- Use Case / Challenge (textarea, 100 chars max)
- Timeline (select: Immediate, Q1, Q2, Q3, Q4)
- Budget Authority? (select: Yes, No, Influencer)
```

**Trust Signals:** Fortune 500 customer logos, case study link, analyst reviews (Gartner, Forrester)

---

## 6. Benchmark References: Completion Rates by Field Count

**From benchmarks.md - Industry Averages:**

| Form Type | Field Count | Avg Completion % | Recommended Max |
|-----------|------------|------------------|-----------------|
| Lead Capture (B2B) | 2-3 | 45-55% | 3 |
| Lead Capture (B2B) | 4-5 | 35-42% | 5 |
| Lead Capture (B2B) | 6-8 | 20-30% | 7 |
| Demo Request | 5-6 | 32-40% | 6 |
| Demo Request | 7-9 | 18-25% | 9 |
| Contact Us | 4-6 | 28-35% | 6 |
| Checkout (<$50) | 5-7 | 55-68% | 7 |
| Checkout ($50-500) | 8-10 | 42-55% | 10 |
| Checkout (>$500) | 12-15 | 25-35% | 15 |
| Account Creation (Passwordless) | 1-2 | 68-75% | 2 |
| Account Creation (Traditional) | 4-6 | 52-62% | 6 |

**Usage:** When proposing form changes, cite the benchmark completion rate for your form type + current field count to justify reducing fields.

---

## 7. Council Integration Hook

**Pre-Optimization Discovery Call:**

Before building or redesigning a form, run this checklist:

```markdown
Council Form Pre-Flight Questions:
1. What is the primary conversion goal? (lead, demo, purchase, signup)
2. What is your current form completion rate? (baseline)
3. What is your target cost-per-lead or customer acquisition cost?
4. Who is the decision-maker vs influencer vs evaluator? (affects field count)
5. What is the audience urgency? (High: decision made; Medium: evaluating; Low: exploring)
6. Do you have competitor form benchmarks? (helps set field count)
7. What fields are "nice to have" vs "must-have"? (removes bloat)
8. What's your planned A/B test? (field count? CTA wording? Trust signals?)
9. Do you have form drop-off data by field? (if no, instrument before optimizing)
10. What CMS or form builder are you using? (affects implementation friction)
```

**Decision:** If you cannot answer 7/10 questions, request discovery research before optimization.

---

## 8. Cross-Skill References

### Upstream: page-cro

Forms exist within pages. Page-level optimizations affect form performance:

- **Headline clarity** → Lower bounce before form view
- **Page load speed** → Higher form impression rate
- **Above-fold real estate** → Form placement (above/below fold)
- **Color contrast** → Form button visibility

**Integration Point:** If page-cro is loaded, check:
- Is the form's CTA button color contrasted against page background?
- Is the form positioned where users naturally scroll to it?
- Are competing CTAs (e.g., secondary navigation) confusing conversion intent?

---

### Downstream: ab-test-setup

Form optimization work should flow into A/B testing:

- **Variant A:** Current form (baseline)
- **Variant B:** Optimized form (per this rubric)
- **Test Duration:** 2-4 weeks (sample size calculator required)
- **Primary Metric:** Conversion rate or cost-per-lead
- **Secondary Metrics:** Drop-off by field, time-to-submit, error rate

**Integration Point:** After optimization, automatically generate A/B test plan via ab-test-setup skill:
- Sample size recommendation based on current CR and MDE
- Audience segmentation (cold vs warm traffic)
- Holdout calculation (exclude existing customers)

---

## 9. Form Audit Checklist (15-Point Scoring)

**Use this when reviewing an existing form:**

```markdown
FORM AUDIT: [Form Name] | Date: [ISO Date] | Current Score: __/15

FIELD OPTIMIZATION (4 points max)
- [ ] Field count matches recommended range for [form type]: 2 pt
- [ ] Optional fields hidden until trigger (blur, error, timer): 1 pt
- [ ] Real-time validation with inline error messages: 1 pt

MOBILE UX (3 points max)
- [ ] Touch targets ≥48x48px, spacing ≥16px: 1 pt
- [ ] Correct `inputMode` (email, tel, number) per field: 1 pt
- [ ] `autocomplete` attributes match browser autofill: 1 pt

TRUST SIGNALS (3 points max)
- [ ] SSL badge + privacy policy link visible: 1 pt
- [ ] 2+ social proof elements (customer count, testimonial, logo): 1 pt
- [ ] CTA text is action-driven (not "Submit"): 1 pt

ERROR HANDLING & RECOVERY (2 points max)
- [ ] Client-side validation prevents empty submission: 1 pt
- [ ] Form data persists on validation error: 1 pt

ANALYTICS & TRACKING (2 points max)
- [ ] Form impression, field focus, submission events tracked: 1 pt
- [ ] Drop-off detected by field (heatmap or funnel): 1 pt

ACCESSIBILITY (1 point max)
- [ ] Semantic HTML + ARIA labels + proper fieldset grouping: 1 pt

Current Total Score: __/15
Interpretation: [ ] 13-15 (Ship) [ ] 10-12 (Good, Monitor) [ ] 7-9 (Plan Changes) [ ] <7 (Remediate)

Top 3 Improvements:
1. ___
2. ___
3. ___

Responsible Owner: ___
Target Completion: ___
```

---

## 10. Worked Example: Demo Request Form Optimization

### Current State (Score: 6/15)

```html
<!-- Before: 11 fields, desktop-only, generic CTA -->
<form id="demo-form">
  <input type="text" name="first_name" placeholder="First Name">
  <input type="text" name="last_name" placeholder="Last Name">
  <input type="email" name="email" placeholder="Email">
  <input type="tel" name="phone" placeholder="Phone">
  <input type="text" name="company" placeholder="Company">
  <input type="text" name="title" placeholder="Title">
  <select name="industry">
    <option>-- Select Industry --</option>
    <option>Tech</option>
    ...
  </select>
  <select name="team_size">
    <option>-- Team Size --</option>
  </select>
  <textarea name="message" placeholder="Tell us about your use case"></textarea>
  <input type="checkbox" name="newsletter"> Subscribe to updates
  <button type="submit">Submit</button>
</form>
```

**Audit Findings:**
- ❌ 11 fields (benchmark: 6 max)
- ❌ No progressive disclosure
- ❌ `placeholder` used instead of labels
- ❌ Mandatory newsletter opt-in (legal risk)
- ❌ Button text "Submit" (low intent)
- ❌ No mobile optimization
- ❌ No trust signals visible
- ❌ No error handling or success state

---

### Optimized State (Target Score: 14/15)

**Strategic Changes:**
1. Reduce to 6 core fields (Step 1: Email + Company + Use Case; Step 2: Phone + Time + Confirmation)
2. Add progressive disclosure (phone hidden until Step 2)
3. Implement mobile-first design
4. Add trust signals (SSL badge, "No credit card required")
5. Replace button text with action intent
6. Add real-time validation
7. Ungated calendar picker for time selection

```html
<!-- After: 6 fields, mobile-optimized, clear intent -->
<form id="demo-form" class="form-container">
  <!-- Step 1: High-Intent Capture (visible immediately) -->
  <div class="form-step" id="step-1">
    <h2>Schedule Your Demo</h2>
    
    <div class="form-group">
      <label for="email">Work Email *</label>
      <input
        id="email"
        type="email"
        name="email"
        placeholder="you@company.com"
        autocomplete="email"
        inputmode="email"
        required
        aria-describedby="email-error"
      >
      <span id="email-error" class="error-msg" role="alert"></span>
    </div>

    <div class="form-group">
      <label for="company">Company Name *</label>
      <input
        id="company"
        type="text"
        name="company"
        placeholder="Acme Inc."
        autocomplete="organization"
        required
      >
    </div>

    <div class="form-group">
      <label for="use-case">What brings you here? *</label>
      <select id="use-case" name="use_case" required>
        <option value="">-- Select --</option>
        <option value="data-analytics">Data Analytics & Dashboards</option>
        <option value="workflow-automation">Workflow Automation</option>
        <option value="reporting">Real-time Reporting</option>
        <option value="other">Other</option>
      </select>
    </div>

    <button type="button" class="btn-primary" onclick="goToStep(2)">
      Next: Pick Your Time
    </button>
  </div>

  <!-- Step 2: Timing & Contact (progressive disclosure) -->
  <div class="form-step hidden" id="step-2">
    <h2>Let's Schedule</h2>

    <!-- Inline calendar picker (no field needed) -->
    <div class="form-group">
      <label>Preferred Time *</label>
      <div id="calendar-picker" class="calendar-inline"></div>
      <input type="hidden" id="selected-time" name="selected_time" required>
    </div>

    <!-- Phone: now optional, revealed in Step 2 -->
    <div class="form-group">
      <label for="phone">Phone (optional)</label>
      <input
        id="phone"
        type="tel"
        name="phone"
        placeholder="+1 (555) 123-4567"
        autocomplete="tel"
        inputmode="tel"
      >
    </div>

    <!-- Trust signals -->
    <div class="trust-signals">
      <span class="badge ssl-badge">🔒 Secure (SSL)</span>
      <span class="badge no-cc">No credit card required</span>
    </div>

    <!-- Legal compliance: unchecked by default -->
    <div class="form-group checkbox">
      <input id="newsletter" type="checkbox" name="newsletter" value="true">
      <label for="newsletter">Send me product updates & tips</label>
    </div>

    <button type="submit" class="btn-primary btn-large">
      Schedule My 15-Min Demo
    </button>
    <button type="button" class="btn-secondary" onclick="goToStep(1)">
      Back
    </button>
  </div>

  <!-- Success state -->
  <div class="form-step hidden" id="success">
    <div class="success-message">
      <h2>Confirmation sent!</h2>
      <p>Check your email for a calendar link. We'll see you soon.</p>
      <img src="/confetti.svg" alt="celebration">
    </div>
  </div>
</form>

<style>
  .form-container {
    max-width: 500px;
    margin: 0 auto;
  }

  .form-step {
    display: block;
  }

  .form-step.hidden {
    display: none;
  }

  .form-group {
    margin-bottom: 1.5rem;
  }

  label {
    display: block;
    font-weight: 600;
    margin-bottom: 0.5rem;
    font-size: 0.95rem;
  }

  input, select {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #d0d0d0;
    border-radius: 4px;
    font-size: 1rem;
    font-family: inherit;
    min-height: 48px; /* Touch target */
  }

  input:focus, select:focus {
    outline: none;
    border-color: #0066ff;
    box-shadow: 0 0 0 3px rgba(0, 102, 255, 0.1);
  }

  .error-msg {
    color: #d32f2f;
    font-size: 0.85rem;
    margin-top: 0.25rem;
    display: block;
  }

  .btn-primary {
    width: 100%;
    padding: 0.75rem;
    background: #0066ff;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    min-height: 48px;
  }

  .btn-primary:hover {
    background: #0052cc;
  }

  .trust-signals {
    margin: 1rem 0;
    font-size: 0.9rem;
    color: #666;
  }

  .badge {
    display: inline-block;
    margin-right: 1rem;
  }

  @media (max-width: 640px) {
    .form-container {
      padding: 1rem;
    }

    label {
      font-size: 1rem;
    }
  }
</style>

<script>
  const form = document.getElementById('demo-form');
  const emailInput = document.getElementById('email');
  const errorSpan = document.getElementById('email-error');

  // Real-time validation
  emailInput.addEventListener('blur', () => {
    const isValid = emailInput.value.includes('@');
    if (!isValid && emailInput.value) {
      errorSpan.textContent = 'Please enter a valid email';
      errorSpan.setAttribute('aria-live', 'polite');
    } else {
      errorSpan.textContent = '';
    }
  });

  // Progressive disclosure: show phone on step 2
  function goToStep(stepNum) {
    document.querySelectorAll('.form-step').forEach(el => {
      el.classList.add('hidden');
    });
    document.getElementById(`step-${stepNum}`).classList.remove('hidden');
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  // Form submission
  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    
    const formData = new FormData(form);
    try {
      const res = await fetch('/api/demo-request', {
        method: 'POST',
        body: formData,
      });
      
      if (res.ok) {
        document.getElementById('step-2').classList.add('hidden');
        document.getElementById('success').classList.remove('hidden');
        
        // Track conversion
        if (window.gtag) {
          gtag('event', 'demo_scheduled', {
            use_case: formData.get('use_case'),
          });
        }
      }
    } catch (err) {
      errorSpan.textContent = 'Submission failed. Please try again.';
    }
  });
</script>
```

---

### Optimization Results Summary

| Metric | Before | After | Change |
|--------|--------|-------|--------|
| **Field Count** | 11 | 6 | -45% |
| **Expected Completion Rate** | 20-25% | 32-40% | +60% |
| **Mobile Touch Targets** | <40px | 48px+ | ✅ |
| **Trust Signals** | 0 | 2 | ✅ |
| **Error Handling** | None | Real-time | ✅ |
| **Form Audit Score** | 6/15 | 14/15 | +8 pts |
| **Expected Lead Volume** (same traffic) | 100 leads | 160 leads | +60% |

---

## Best Practices Summary

1. **Field Count:** For every field above the benchmark, expect 5-10% drop in completion rate.
2. **Progressive Disclosure:** Hidden fields on load reduce cognitive load; reveal on action or timer.
3. **Mobile First:** Design for 48px touch targets, proper `inputMode`, and vertical stacking.
4. **Trust Signals:** SSL badge + privacy link + customer count near CTA = 3-7% conversion lift.
5. **Clear Intent:** "Schedule Demo" beats "Submit" by 15-25% in conversion rates.
6. **Error Recovery:** Never lose user data on validation error; show inline, recoverable messages.
7. **Analytics:** Track form impression, field focus (abandon point), submission, and success.
8. **Testing:** Always A/B test field count or CTA wording before shipping major changes.

---

## References

- Benchmarks: Form completion rates by field count and industry type
- Anti-Patterns: Cumulative library of form friction points
- Industry Profiles: Business model-specific recommendations
- Page-CRO: Integration with page-level optimization
- AB-Test-Setup: Post-optimization testing framework
- Product-Marketing Context: Audience, business model, goal alignment

```