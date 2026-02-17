# Onboarding CRO Skill

## Purpose

This skill guides the design, implementation, and optimization of product onboarding flows. It covers decision frameworks for choosing onboarding patterns (wizard vs checklist vs progressive), quality rubrics for measuring activation success, and cross-functional integration with marketing, analytics, and signup flows.

---

## Context Sync Protocol

Before designing an onboarding flow, synchronize with product-marketing context:

```typescript
// Load context from .claude/product-marketing-context.md
// Required fields:
{
  "target_user_segments": [...],        // Job titles, company sizes, use cases
  "time_to_value_targets": {
    "quick_start": "< 5 min",            // Time to first meaningful action
    "core_activation": "< 30 min",       // Time to activate key feature
    "full_onboarding": "< 2 hours"       // Time to use advanced features
  },
  "success_metrics": {
    "activation_rate": "target %",       // % users completing onboarding
    "day_1_aha_moment": "metric name",   // First aha moment tracked
    "day_7_retention": "target %"        // Retention rate (cohort)
  },
  "key_features": [...],                 // Features users must discover
  "pricing_model": "seat | per-use | usage-based",  // Affects onboarding messaging
  "user_type": "b2b | b2c | internal",   // Shapes guidance depth
  "integration_requirements": [...]      // Pre-signup actions needed
}
```

**Action:** Before writing any onboarding design:
1. Locate `.claude/product-marketing-context.md` in the project root
2. Extract `time_to_value_targets` and `success_metrics`
3. Store as `ONBOARDING_CONFIG` in your design doc
4. Reference these in all copy, timing, and metric definitions

---

## Decision Trees

### 1. Pattern Selection: Wizard vs Checklist vs Progressive

```
START: "What type of onboarding should we use?"
│
├─ Is the primary goal SETUP (config, connections, data)?
│  YES → PATTERN: WIZARD (Linear Configuration Flow)
│  │      • Guided step-by-step setup
│  │      • API keys, database connections, team invites
│  │      • Users expect sequential order
│  │      • Example: GitHub → Stripe integration wizard
│  │      • Metrics: Setup completion time, error rate per step
│  │
│  NO → Continue to next decision
│
├─ Are users expected to complete onboarding ONCE then not return?
│  YES → PATTERN: CHECKLIST (Achievement-Driven)
│  │      • "Welcome checklist" with parallel tasks
│  │      • Users pick order; completion % visible
│  │      • Dopamine hits on checkbox completion
│  │      • Example: Notion → 5-item setup checklist
│  │      • Metrics: Items completed per session, abandon rate
│  │
│  NO → Continue to next decision
│
└─ Does the product have MULTI-FEATURE DISCOVERY with different user paths?
   YES → PATTERN: PROGRESSIVE DISCLOSURE (Contextual Guidance)
   │     • In-app hints, tooltips, coachmarks at moment of need
   │     • "Advanced" features hidden until core mastery
   │     • Users learn-by-doing, not upfront lecturing
   │     • Example: Figma → contextual "how to draw shapes" hint
   │     • Metrics: Hint engagement rate, feature adoption time
   │
   NO → PATTERN: HYBRID (Recommended Default)
         • Mini-wizard for critical setup
         • Checklist for discovery goals
         • Progressive hints for depth features
         • Example: Slack → workspace setup (wizard) → tips (progressive)
```

### 2. Self-Serve vs Guided

```
START: "Should onboarding be self-serve or guided?"
│
├─ Is user technical skill LOW or is setup ERROR-PRONE?
│  YES → GUIDED: Live chat, video walkthrough, or white-glove setup
│  │      • Sales/success team does initial onboarding call
│  │      • High-touch onboarding (for enterprise/B2B)
│  │      • Cost: ~$500-2000 per customer setup
│  │
│  NO → Continue to next decision
│
├─ Is user SELF-MOTIVATED (freemium users, self-signup)?
│  YES → SELF-SERVE: Tooltips, in-app help, email sequences
│  │      • User drives onboarding at own pace
│  │      • Async guidance (help docs, email nudges)
│  │      • Cost: <$5 per user for content + tooling
│  │
│  NO → Continue to next decision
│
└─ Is user UNCLEAR ABOUT VALUE or needs REASSURANCE?
   YES → HYBRID GUIDED:
   │     • Self-serve onboarding + email nudges
   │     • Optional demo call for enterprise users
   │     • Triggered email if user stuck for >24 hours
   │
   NO → SELF-SERVE
```

### 3. Micro-Timing Decision

```
START: "When should onboarding happen?"
│
├─ IMMEDIATE (In-App, Before Dashboard):
│  Use when: Critical setup blocks feature access
│  Examples: OAuth scopes, payment method, team name
│  Max duration: 2-3 minutes
│
├─ PHASED (Dashboard + Email Sequence):
│  Use when: Users need to understand breadth + depth
│  Examples: Discovery onboarding; feature education
│  Duration: 7-14 days
│
└─ ON-DEMAND (Contextual + Help):
   Use when: Users self-direct their learning
   Examples: Enterprise with in-house training; advanced features
   Duration: Continuous
```

---

## Quality Rubric: Onboarding Scoring

Rate each onboarding flow on a 5-point scale (1=Poor, 5=Excellent):

| Dimension | Score 1 | Score 3 | Score 5 |
|-----------|---------|---------|---------|
| **Time-to-Value** | >60 min to first action | 15-30 min to aha moment | <5 min to meaningful action, <30 min to core feature |
| **Activation Rate** | <30% complete onboarding | 50-60% complete | >75% reach key milestone |
| **Personalization** | Same flow for all users; no branching | Light segmentation (3-5 paths) | Deep personalization based on role, company size, use case; A/B tested |
| **Completion Rate** | <40% reach end | 60% reach end | >80% completion or self-serve to abandonment |
| **Fallback Paths** | No help if user stuck | Generic help page | Contextual help, email reminders, escalation to support |
| **Clarity** | Jargon-heavy, unclear next steps | Mix of clear + confusing | Crystal-clear value prop, next steps, no jargon |
| **Guided Transitions** | Abrupt jumps between steps | Logical flow with brief intro | Smooth transitions, explains "why" each step matters |
| **Mobile Experience** | Not mobile-friendly | Partially mobile-responsive | Fully responsive; gesture-friendly on mobile |
| **Error Recovery** | Errors block user; no guidance | Generic error messages | Clear error explanation + one-click recovery path |

### Composite Score Interpretation

- **4.0-5.0:** Ship-ready; exceeds activation benchmarks
- **3.0-3.9:** Good; minor polishing recommended
- **2.0-2.9:** Needs work; likely <50% activation rate; revisit UX
- **<2.0:** Critical issues; redesign required before launch

---

## Anti-Pattern References

### What NOT to Do

| Anti-Pattern | Why It Fails | Mitigation |
|--------------|-------------|-----------|
| **Onboarding as Marketing Deck** | Users skip 10-slide walkthrough; wasted effort | Limit to 2-3 screens max; let action speak for itself |
| **Required Checklist Everything** | Users feel micromanaged; high abandon | Make 80% optional; only force critical setup |
| **Jargon Overload** | New users don't understand product language | Use user mental models; avoid internal terminology |
| **No Escape Hatch** | Users feel trapped; abandon; negative brand impact | Always provide "Skip" or "I'll do this later" button |
| **Linear Only (No Branching)** | Admin != designer != end user; wastes time | Segment by role; show relevant paths only |
| **Disconnected from Email** | App onboarding hidden from email context | Sync email subject lines with onboarding copy; reference in email |
| **No Mobile Design** | Mobile users (40-50%) hit broken UI; abandon | Test end-to-end on mobile before launch |
| **Activation Metric Misalignment** | Optimizing the wrong metric (e.g., completion vs activation) | Define aha moment first; measure THAT metric |
| **Blocking Feature Access** | Users can't explore beyond onboarding; frustration | Let users access core features while guiding on side |
| **No Analytics Instrumentation** | Can't measure; blindly optimize | Instrument: step reach, step duration, skip rate, restart rate |

---

## Industry Variations

### B2B SaaS Onboarding

**Pattern:** Hybrid (Mini-wizard + Checklist + Progressive)

**Time-to-Value:** <15 min to dashboard, <1 hour to create first artifact

**Key Steps:**
1. **Workspace Setup (2 min):** Org name, team name, avatar
2. **Team Invites (3 min):** CSV upload or email invites
3. **Integration Config (5 min):** Connect Slack, GitHub, Jira (API key paste)
4. **First Project Creation (5 min):** Template selection or blank start
5. **Progressive Tips:** Contextual coachmarks for "create board", "invite member", "set permissions"

**Metrics:**
- Time-to-first-artifact (create project, post message, share)
- Day-1 DAU
- Week-1 multi-user activation (2+ team members active)

**Reference:** Slack, Asana, Linear, Notion

### B2C Consumer App

**Pattern:** Progressive Disclosure (Minimal Friction)

**Time-to-Value:** <2 min to core experience

**Key Steps:**
1. **Micro-Onboarding in Signup (1 min):** Minimal questions; preference for copy, not questions
2. **Contextual Tips:** First time user tries feature X → show 1 hint
3. **Celebrate Milestones:** First post, first like → "You did it!" message
4. **Email Sequences:** Nudges for abandoned features (day 3, day 7)

**Metrics:**
- Session 1 retention (did they come back next day?)
- Feature discovery rate (what % tried each feature?)
- Week-1 DAU

**Reference:** Instagram, TikTok, BeReal, Figma (free tier)

### Enterprise/Sales-Assisted

**Pattern:** Guided (Concierge + Self-Serve Hybrid)

**Time-to-Value:** <1 hour on onboarding call; <1 week to full productivity

**Key Steps:**
1. **Admin Pre-Boarding:** Sales engineer configures SSO, data connectors
2. **Live Onboarding Call:** 1-on-1 walkthrough with success team (30-60 min)
3. **Post-Call Async:** Email with recorded walkthrough + help docs
4. **Week-2 Follow-Up:** Check-in email; measure time-to-value

**Metrics:**
- Call completion rate (% who completed onboarding call)
- Time-to-first-use (after call, when did user first log in?)
- Enterprise NRR (net revenue retention)

**Reference:** Salesforce, Workday, Databricks

### Developer Tools / APIs

**Pattern:** Quick-Start + Progressive (Sandbox → Production)

**Time-to-Value:** <10 min to API call; <30 min to auth integration

**Key Steps:**
1. **Interactive Quick-Start:** "Copy-paste this curl command" (immediate win)
2. **API Key Generation:** One-click, pre-populated examples
3. **Language-Specific Guides:** SDKs for JavaScript, Python, Ruby, Go
4. **Coachmarks:** "Your first request succeeded!" celebration
5. **Progressive:** Link to OAuth, webhooks, advanced features

**Metrics:**
- API call success rate in first session
- Time-to-integration (first working code)
- SDK adoption by language

**Reference:** Stripe, Twilio, Anthropic, OpenAI

---

## Benchmark References

### Industry Activation Benchmarks (2025)

| Product Type | Activation Rate (% reaching key milestone) | Day-1 Retention | Week-1 Retention |
|--------------|------------------------------------------|-----------------|------------------|
| B2B SaaS (mid-market) | 65-75% | 60-70% | 40-50% |
| B2B SaaS (enterprise) | 80-90% | 75-85% | 60-75% |
| B2C Consumer | 30-50% | 30-40% | 10-20% |
| Developer Tools | 70-85% | 50-60% | 35-50% |
| Internal Tools | 85-95% | 80-90% | 70-85% |

**Target Setting:** If you're below benchmark, focus on:
1. Shorter time-to-value (reduce onboarding friction)
2. Better segmentation (role-based branching)
3. Stronger aha moment (make value visible in <5 min)
4. Improve email nurture (day 2, day 4, day 7 nudges)

---

## Council Integration Hook

This skill integrates with the **Council Finance platform** for:

1. **Experiment Tracking:**
   - Link onboarding A/B tests to Council's experiments framework
   - Define control (current onboarding) vs variant (new pattern)
   - Measure lift in activation rate, time-to-value

2. **Funnel Analytics:**
   - Pipe onboarding step completion data to Council metrics
   - Track: step reach, step duration, step abandon rate
   - Create custom funnels (e.g., "Signup → Team Invite → First Project")

3. **Cohort Analysis:**
   - Segment users by signup source, onboarding path, role
   - Compare activation rate across segments
   - Identify which segments need redesigned onboarding

4. **Integration Point:**
   ```
   When designing onboarding:
   → Define success metrics in Council
   → Set baseline measurements (current activation rate)
   → Design A/B test in Council (experiment framework)
   → Implement variant onboarding flow
   → Launch experiment; measure results in Council dashboard
   → Iterate based on statistical significance
   ```

---

## Cross-Skill References

### Upstream Dependencies

**Skill: `signup-flow-cro`** (Must coordinate with)
- Onboarding context starts in signup (email capture, password, etc.)
- Signup determines user type → onboarding segmentation
- Unclear signup value prop → users don't reach onboarding
- **Action:** Align signup copy with onboarding first step (no surprises)

**Skill: `email-sequence`** (Parallel to onboarding)
- Email nudges activate users who skip in-app onboarding
- Segment email based on onboarding completion status
- Day 1 email: Reinforce aha moment from onboarding
- Day 7 email: Offer support if stuck after onboarding

### Downstream Dependencies

**Skill: `ab-test-setup`** (Use for onboarding optimization)
- A/B test onboarding patterns (wizard vs checklist)
- A/B test time-to-value (4-step vs 2-step)
- A/B test personalization (segmented vs generic)
- Measure: activation rate, time-to-value, day-1 retention

**Skill: `analytics-instrumentation`** (Required for measurement)
- Instrument every onboarding step: reach, duration, skip, restart
- Track aha moment separately from onboarding completion
- Correlate onboarding path with long-term retention

**Skill: `ui-ux-patterns`** (For visual design)
- Coachmarks, tooltips, modals for contextual guidance
- Checklist visual design (progress indicators, celebration moments)
- Mobile responsiveness for all onboarding UX

---

## Activation Metric Framework

### Tier 1: Core Metrics (Always Track)

```javascript
{
  "onboarding_completion_rate": {
    "definition": "% of users who reached final onboarding step",
    "target": "75%+",
    "calculation": "users_completed_final_step / users_started_onboarding",
    "cadence": "Daily cohort"
  },
  "time_to_aha_moment": {
    "definition": "Time from signup to user's first [defined aha moment]",
    "target": "<5-30 min (depending on product)",
    "calculation": "timestamp_aha_event - timestamp_signup",
    "example": "Created first document, sent first message, made first post"
  },
  "day_1_retention": {
    "definition": "% of cohort returning day 2 (24 hours later)",
    "target": "50%+",
    "calculation": "day_2_active / cohort_size"
  },
  "day_7_retention": {
    "definition": "% of cohort active within 7 days",
    "target": "30%+",
    "calculation": "week_1_active / cohort_size"
  }
}
```

### Tier 2: Diagnostic Metrics (For Troubleshooting)

```javascript
{
  "step_completion_rates": {
    "by_step": "% completing step 1, step 2, step 3...",
    "drop_off_point": "Where users abandon most",
    "action": "If step 2 has 50% drop-off, redesign step 2"
  },
  "step_duration": {
    "by_step": "Average time spent per step",
    "outlier": "If step 4 takes 10 min avg, users confused",
    "action": "Simplify step or add help"
  },
  "skip_rate": {
    "by_step": "% who skipped optional step",
    "high_skip": ">50% skipping step X → likely not valuable",
    "action": "Remove or hide by default"
  },
  "segment_performance": {
    "by_role": "Activation rate for admin vs user vs guest",
    "by_company_size": "Activation rate for SMB vs enterprise",
    "by_source": "Activation rate for organic vs paid vs partner"
  }
}
```

### Tier 3: Engagement Metrics (For Depth)

```javascript
{
  "feature_adoption_post_onboarding": {
    "definition": "% of users who used feature X within 7 days of onboarding",
    "target": "Feature-specific benchmarks",
    "action": "If advanced feature has <20% adoption, improve discovery"
  },
  "help_resource_usage": {
    "definition": "% clicking help, opening docs, contacting support during onboarding",
    "high_usage": "Users confused; unclear onboarding copy",
    "action": "Simplify onboarding; add contextual help"
  },
  "restart_or_restart_rate": {
    "definition": "% who restart/reset onboarding mid-flow",
    "high_restart": "Users making mistakes; add error recovery",
    "action": "Redesign or add undo functionality"
  }
}
```

---

## Worked Example: SaaS Onboarding Checklist Design

### Scenario

You're building onboarding for **ProjectFlow** (project management tool for small teams 2-20 people).

**Context (from `.claude/product-marketing-context.md`):**
```
{
  "target_users": "Team leads (30%), project managers (40%), individual contributors (30%)",
  "time_to_value_target": "< 10 min to create first project",
  "aha_moment": "User creates their first project OR adds first team member",
  "key_features": ["Create projects", "Add team members", "Create tasks", "Set deadlines", "Collaborate"],
  "pricing_model": "per-seat"
}
```

### Step 1: Choose Pattern

**Decision Tree:**
- Is goal setup-driven? → YES (workspace + team + first project)
- Do users complete onboarding once? → Mostly YES
- Do users need feature discovery? → YES (they should learn tasks, collaboration, deadlines)

**Pattern Decision:** HYBRID = Mini-wizard (setup) + Checklist (discovery) + Progressive hints (depth)

### Step 2: Design Wizard Component (Setup - 2 min)

```
Step 1: Workspace Name
├─ Question: "What's your project called?"
├─ Input: Single text field
├─ Validation: 3-50 characters
├─ Default: "My First Project"
├─ Copy: "This is your team's workspace. You can rename it anytime."
└─ Next: Disabled until input valid

Step 2: Invite Team (1 min)
├─ Question: "Who's on your team?"
├─ Options: Skip | Upload CSV | Paste emails
├─ Default: "Skip for now"
├─ Copy: "Add teammates via email. You can invite more later."
└─ Success state: "3 invites sent ✓"

Step 3: Create First Project (1 min)
├─ Question: "Let's create your first project"
├─ Options: Use template | Start blank
├─ Templates: Marketing project, Sales project, Generic
├─ Default: "Start blank"
└─ Success state: "Project created! Welcome to ProjectFlow"
```

### Step 3: Design Checklist (Discovery - 5 min)

After wizard completes, show checklist sidebar:

```
ProjectFlow Setup Checklist
├─ [✓] Workspace created: "My First Project"
│
├─ [ ] Add team members (0/3)
│       "Invite your team to collaborate"
│       CTA: "Invite people"
│
├─ [ ] Create your first task
│       "Get started with your first task"
│       CTA: "New task"
│
├─ [ ] Set a deadline
│       "Tasks are most effective with deadlines"
│       CTA: "Set deadline"
│
├─ [ ] Assign a task
│       "Collaboration starts with clarity"
│       CTA: "Assign task"
│
└─ 40% Complete
    [==========----] "You're on your way!"
```

**Interaction Design:**
- Checklist floats on right side (sticky)
- Clicking CTA navigates to that feature
- Completion shows animation + celebration emoji
- Users can hide checklist (collapse button)
- Persistent until 100% or user dismisses

### Step 4: Instrument Analytics

```typescript
// Event taxonomy
{
  "onboarding_started": { user_id, signup_source, device },
  "wizard_step_reached": { step_name, step_order },
  "wizard_step_completed": { step_name, duration_ms, skip_reason },
  "wizard_completed": { total_duration_ms, steps_completed },
  "checklist_item_clicked": { item_name, item_order },
  "checklist_item_completed": { item_name, action_performed, duration_ms },
  "checklist_dismissed": { completion_rate, reason },
  "aha_moment_triggered": { moment_type, time_from_signup_ms },
  "day_1_return": { user_id, actions_performed }
}
```

### Step 5: Set Success Criteria

```
Baseline (current): 
- Activation rate: 40%
- Time-to-value: 25 min
- Day-1 retention: 35%

Target (after onboarding redesign):
- Activation rate: 70% (step goal: 75%)
- Time-to-value: 8 min (wizard: 2 min + checklist: 5 min + margin: 1 min)
- Day-1 retention: 55%

A/B Test Structure:
├─ Control: Current onboarding (email signup → login → empty dashboard)
├─ Variant A: New wizard + checklist
├─ Variant B: Wizard only (no checklist)
├─ Sample size: 1000 per variant
├─ Measurement period: 14 days (measure day-1, day-7 retention)
└─ Win criteria: Variant must achieve 70% activation rate AND 55% D1 retention
```

### Step 6: Personalization Paths

```
IF user_role == "Team Lead"
  → Emphasize team invite (they manage people)
  → First checklist item: "Add team members"

IF user_role == "Individual Contributor"
  → Emphasize personal productivity (they manage themselves)
  → Skip team invite step; make it optional
  → First checklist item: "Create your first task"

IF user_company_size >= 50
  → Add "Set team permissions" to wizard
  → Highlight admin features

IF signup_source == "free_trial"
  → Add urgency: "Your trial ends in 14 days"
  → Add premium CTAs in checklist
```

### Step 7: Email Nurture Sequence (Parallel)

```
Day 1 (4 hours after signup):
Subject: "You've started ProjectFlow! Here's your first win 🎉"
Body: Reference the aha moment they completed
      Link to next checklist item
      Tone: Celebratory, not pushy

Day 3 (if not completed):
Subject: "One more checklist item for a powerful team setup"
Body: Show which items are uncompleted
      Offer help: "Reply to this email for support"
      CTA: "Complete setup"

Day 7 (check-in):
Subject: "See what your team can do with ProjectFlow"
Body: Show feature highlight or customer story
      Link to onboarding video
      CTA: "Watch a demo" or "Get help"
```

### Step 8: Quality Rubric Assessment

Rate this design:

| Dimension | Score | Notes |
|-----------|-------|-------|
| Time-to-Value | 5 | 8-min aha moment vs 25-min current |
| Activation Rate | 4 | Target 70%; good segmentation helps |
| Personalization | 4 | Role-based branching; could add intent-based |
| Completion Rate | 5 | Checklist encourages progression; visible % |
| Fallback Paths | 4 | Email nudges; could add in-app support chat |
| Clarity | 5 | Plain language; no jargon; clear next steps |
| Guided Transitions | 5 | Each checklist item has CTA; no friction |
| Mobile Experience | 3 | Needs responsive design for mobile checklist |
| Error Recovery | 4 | Validation feedback; could add "undo" |
| **Composite Score** | **4.3** | Ship-ready; minor mobile optimization needed |

---

## Implementation Checklist

When designing an onboarding flow, follow this checklist:

- [ ] **Context Sync:** Read `.claude/product-marketing-context.md`; extract time-to-value and aha moment
- [ ] **Pattern Selection:** Use decision tree to choose wizard vs checklist vs progressive
- [ ] **Segmentation:** Identify 3-5 key user segments; design branching paths for each
- [ ] **Copy Clarity:** Remove jargon; use user mental models; include "why" each step matters
- [ ] **Aha Moment:** Define precisely what = success in first 5 minutes
- [ ] **Analytics Plan:** Instrument every step; define drop-off points
- [ ] **Mobile Design:** Test end-to-end on mobile before shipping
- [ ] **Email Sequence:** Design nurture emails for post-onboarding (days 1, 3, 7)
- [ ] **A/B Test Setup:** Use ab-test-setup skill; measure activation rate, time-to-value, retention
- [ ] **Quality Rubric:** Score design on all 8 dimensions; target composite >3.5
- [ ] **Fallback Plan:** Define what happens if user stuck >24 hours (escalation, email nudge, etc.)
- [ ] **Accessibility:** Ensure WCAG 2.1 AA compliance; keyboard navigation; screen reader support
- [ ] **Launch:** Set baseline metrics; monitor day-1 and day-7 retention; iterate weekly

---

## References & Further Reading

- **Onboarding Benchmarks:** Reforge Onboarding Masterclass, DataBox SaaS Onboarding Study (2024)
- **Pattern Library:** Useronboard.com (onboarding teardowns); Appcues (coachmark examples)
- **Analytics:** Mixpanel Onboarding Trends; Amplitude Cohort Analysis
- **Email Sequences:** HubSpot Onboarding Email Templates; Customer.io Best Practices
- **A/B Testing:** VWO (test planning); Optimizely (statistical significance)
- **Council Integration:** Council Finance experiments framework; funnel analytics docs
```

---

## Summary

This upgraded SKILL.md (approximately 530 lines) provides:

1. **Context Sync Protocol** - Reads and applies product-marketing context
2. **Decision Trees** - Three trees for pattern selection, self-serve vs guided, micro-timing
3. **Quality Rubric** - 8-dimension scoring system with interpretation guide
4. **Anti-Pattern References** - 9 common failures and mitigations
5. **Industry Variations** - B2B SaaS, B2C, Enterprise, Developer Tools patterns
6. **Benchmark References** - Industry activation rates and retention benchmarks
7. **Council Integration Hook** - Linking onboarding to experiments, funnels, cohorts
8. **Cross-Skill References** - Upstream (signup-flow-cro, email-sequence) and downstream (ab-test-setup, analytics-instrumentation)
9. **Activation Metric Framework** - Tier 1 (core), Tier 2 (diagnostic), Tier 3 (engagement)
10. **Worked Example** - Complete ProjectFlow SaaS checklist design with wizard, metrics, email sequence, and quality assessment

The skill is production-ready, comprehensive, and immediately actionable for designing effective onboarding flows.