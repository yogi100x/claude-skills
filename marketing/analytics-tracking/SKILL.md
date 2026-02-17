# Analytics Tracking Skill

**Foundation Skill** - All product-facing skills depend on analytics for impact measurement and user understanding.

## Overview

This skill governs **event instrumentation, data quality, attribution modeling, and dashboard design** across SwiftHyre's candidate, recruiter, admin, and coordinator apps. It provides decision trees, naming conventions, quality rubrics, and integration patterns for tracking user behavior with privacy-first principles.

**Quick Decision:** Use this skill when:
- Defining new event taxonomy for a feature
- Building user funnels or attribution models
- Implementing event tracking in components/server actions
- Designing analytics dashboards or reports
- Integrating analytics with A/B testing infrastructure
- Debugging data quality issues in PostHog

---

## Context Sync Protocol

Before implementing analytics for a feature, sync context from:

### Product & Marketing Context (`.claude/product-marketing-context.md`)
- **Why**: Ensures events align with business metrics and user segments
- **Check for**: KPIs, success metrics, target user personas, business goals
- **Pattern**: Map feature objectives → business KPIs → event taxonomy

### Technical Context (`.claude/tech-context.md`)
- **Why**: Ensures events integrate with platform architecture and data pipelines
- **Check for**: Data retention policies, PII handling rules, real-time vs batch processing
- **Pattern**: Event tracking → PostHog → Trigger.dev jobs → insights delivery

### Implementation
```typescript
// At skill invocation, consult:
// 1. docs/plans/[current-feature].md for business context
// 2. apps/api/src/jobs/analytics/ for existing Trigger.dev patterns
// 3. packages/analytics/src/types/events.ts for taxonomy guidance
```

---

## Event Taxonomy Design

### Naming Convention (kebab-case)

**Pattern**: `[domain]_[action]_[object]` or `[domain]_[state_change]`

```typescript
// Domain prefixes
candidate_*         // Candidate-side actions
recruiter_*         // Recruiter-side actions
admin_*            // Admin panel actions
coordinator_*      // Coordinator portal actions
assessment_*       // Assessment/exam related
proctoring_*       // Exam monitoring
message_*          // Messaging interactions
job_*              // Job/posting related
profile_*          // User profile modifications
device_*           // Device/fingerprint related
assistant_*        // Swifty AI assistant
match_*            // Intelligent matching engine
error_*            // Error/exception tracking
button_*           // Generic UI interactions
form_*             // Form interactions
page_*             // Navigation

// Examples
candidate_onboarding_started
recruiter_talent_search_performed
assessment_question_answered
proctoring_violation_triggered
assistant_tool_result_feedback
match_score_viewed
```

### Property Naming Convention

```typescript
// Boolean properties: is_*, has_*, can_*
{
  is_verified: true
  has_saved_job: false
  can_message: true
}

// Metric properties: *_count, *_seconds, *_percentage
{
  skills_extracted_count: 12
  duration_seconds: 1800
  completion_percentage: 75
}

// Categorical properties: *, *_type, *_reason
{
  skill_name: 'React'
  violation_type: 'different_face'
  close_method: 'button' // as literal union
}

// ID properties: *_id
{
  candidate_id: 'cand_xyz'
  job_id: 'job_abc'
  attempt_id: 'attempt_123'
}

// Temporal properties: *_at (ISO 8601), *_minutes, *_hours
{
  created_at: '2026-02-17T14:30:00Z'
  response_time_minutes: 45
  idle_duration_seconds: 300
}

// Source properties: source, trigger, context
{
  source: 'dashboard' // where action originated
  trigger: 'sidebar_click' // what caused it
  context: 'job_preview' // page/feature context
}
```

### Event Property Best Practices

```typescript
// DO: Minimal, actionable properties
{
  event: 'assessment_submitted',
  properties: {
    attempt_id: 'attempt_123',
    duration_minutes: 45,
    questions_answered: 50,
    score_percentage: 82,
    passed: true,
    skill_id: 'skill_react',
  }
}

// DON'T: Bloated or redundant properties
{
  event: 'assessment_submitted',
  properties: {
    user_first_name: 'John', // Use identify() instead
    user_last_name: 'Doe',
    email: 'john@example.com',
    company: 'Acme',
    nested_data: { /* complex object */ },
  }
}

// DON'T: Free-text fields (reduces aggregation)
{
  notes: 'User was confused about Q5', // Use flagged_questions array
}

// DO: Enums and arrays
{
  flagged_questions: [5, 12, 18],
  violation_types: ['different_face', 'multiple_people'],
}
```

---

## Decision Trees

### Which Tool to Use?

```
Is this user-facing tracking?
├─ YES: Use client-side useAnalytics() hook
│   ├─ Form interactions, button clicks, page views
│   └─ Example: apps/candidate/app/assessments/[attemptId]/page.tsx
│
└─ NO: Is this server-side?
    ├─ YES: Use trackServerEvent() or trackRevenueEvent()
    │   ├─ Payment webhooks, background jobs, server actions
    │   └─ Example: apps/api/src/routes/webhooks/stripe.ts
    │
    └─ ALSO: Trigger.dev jobs for multi-step tracking
        ├─ Complex funnels, attribution pipelines
        └─ Example: apps/api/src/jobs/analytics/track-assessment-completion.ts
```

### Event Attribution Model Selection

Choose based on **when** the event matters:

```
Q: When does impact occur relative to event capture?

IMMEDIATE ATTRIBUTION (same request/component)
├─ Use: Simple property tracking
├─ Events: button_clicked, form_submitted
└─ Pattern: track(event, {source, location})

FUNNEL ATTRIBUTION (sequential events → conversion)
├─ Use: Event chains with time windows
├─ Events: assessment_started → assessment_submitted → certificate_viewed
└─ Pattern: Cohort analysis, funnel queries in PostHog

REVENUE ATTRIBUTION (delayed, requires session context)
├─ Use: First-click, last-click, or multi-touch
├─ Events: candidate_unlocked → message_sent → reply_received
└─ Pattern: Use session_id or user properties to link events

BEHAVIORAL ATTRIBUTION (feature adoption → retention)
├─ Use: Event frequency or boolean adoption flags
├─ Events: assistant_workspace_opened → assistant_tool_result_feedback
└─ Pattern: Set user property on first use, track retention separately

TIME-DECAY ATTRIBUTION (recent interactions weighted higher)
├─ Use: ML-based scoring for matching
├─ Events: match_score_viewed, candidate_card_viewed, candidate_profile_viewed
└─ Pattern: Trigger.dev job calculates decay-weighted score
```

### Choosing Between Immediate vs Deferred Event Capture

```
Is the event CRITICAL for user experience?
├─ YES (user expects immediate feedback)
│   ├─ Capture NOW (blocking)
│   ├─ Examples: assessment_submitted, profile_updated
│   └─ Pattern: track() in useCallback
│
└─ NO (event is informational)
    ├─ Capture in background (non-blocking)
    ├─ Examples: match_score_viewed, assistant_suggestion_generated
    └─ Pattern: Trigger.dev job or batch API call
```

### Privacy vs Data Utility Trade-off

```
Does event contain PII?
├─ YES (email, phone, legal name)
│   ├─ Option 1: Hash before sending (email_hash using SHA-256)
│   ├─ Option 2: Redact entirely (use user_id only)
│   └─ Example: candidateHasResume: boolean (not filename)
│
└─ NO (behavioral data)
    ├─ Capture directly
    ├─ Use enums and IDs, not free text
    └─ Example: skill_id, assessment_result (passed: true)
```

---

## Quality Rubric: Event Instrumentation Scoring

Score each feature's analytics on 0-5 scale. Target: **all features ≥ 4**.

### Event Coverage (0-5)

| Score | Criteria | Examples |
|-------|----------|----------|
| 5 | **Complete** - All user journeys instrumented with entry, interaction, and exit events | Onboarding: started → step_viewed → step_completed → finished; Assessment: started → question_answered → submitted → result_viewed |
| 4 | **Good** - Key conversion points tracked, some interactions missing | Onboarding: started → finished; Assessment: started → submitted |
| 3 | **Fair** - Entry and exit events only, no interaction granularity | Assessment: submitted (missing question_answered) |
| 2 | **Poor** - Sparse instrumentation, unclear user flow | Only "assessment_viewed" |
| 1 | **Missing** - No events or event fires but properties are empty | Track called with `{}` |
| 0 | **None** - Feature not tracked | |

**Audit**: Run PostHog insight for feature page → check "Unique Events" count in last 7 days.

### Naming Consistency (0-5)

| Score | Criteria | Anti-patterns |
|-------|----------|---|
| 5 | **Perfect** - All events follow `[domain]_[action]_[object]`, properties use conventions | `candidate_onboarding_started`, `question_answered_count` |
| 4 | **Good** - Mostly consistent, minor deviations | One event uses camelCase: `candidateOnboardingStarted` |
| 3 | **Fair** - Inconsistent verbs or property names | `start_onboarding`, `onboarding_init`, `OnboardingStarted` (mixed) |
| 2 | **Poor** - Random naming, unclear patterns | `event1`, `user_action_xyz`, `FOO_BAR` |
| 1 | **Broken** - Naming contradicts conventions | `userOnboarding` (should be `candidate_`) |
| 0 | **None** | |

**Audit**: Grep `track('` in feature code; check events.ts for pattern violations.

### Attribution Accuracy (0-5)

| Score | Criteria | Indicators |
|-------|----------|---|
| 5 | **Perfect** - Events include session_id, user_id, AND temporal/contextual metadata | session_id, attempt_id, job_post_id, timestamp, source |
| 4 | **Good** - Sufficient for funnel analysis | user_id, event timestamp, source (trigger location) |
| 3 | **Fair** - Can trace user but attribution is ambiguous | user_id only, no context on what triggered event |
| 2 | **Poor** - Attribution unclear across users | Anon session only, no user_id |
| 1 | **Broken** - Events cannot be linked to users | Missing distinct_id |
| 0 | **None** | |

**Audit**: PostHog cohort → pick 1 user → verify event chain is traceable and contextual.

### Dashboard Utility (0-5)

| Score | Criteria | Questions Answered |
|-------|----------|---|
| 5 | **Perfect** - Dashboards show adoption, engagement, retention, and conversion | "What % of users complete the flow? How long does each step take? Where do users drop off?" |
| 4 | **Good** - Adoption and conversion visible | "How many users started? How many converted?" |
| 3 | **Fair** - Event counts visible but no insights | PostHog event table shows counts |
| 2 | **Poor** - Dashboards exist but don't answer business questions | Dashboards are unfiltered, non-actionable |
| 1 | **Broken** - No dashboards or dashboards show wrong data | |
| 0 | **None** | |

**Audit**: Check PostHog → Dashboards folder → does dashboard answer "Did this feature work?" in <5 seconds?

### Data Quality (0-5)

| Score | Criteria | Red Flags |
|-------|----------|---|
| 5 | **Perfect** - Events fire consistently, properties always populated, no nulls | 0 null properties, event fires on 100% of expected interactions |
| 4 | **Good** - >95% property fill rate, consistent event firing | Occasional null in optional property |
| 3 | **Fair** - >80% property fill rate, events usually fire | Some events missing on concurrent operations |
| 2 | **Poor** - <80% fill rate, gaps in tracking | Events fire but properties sparse; events missing |
| 1 | **Broken** - Events fire but data unusable | All events have empty `{}` properties |
| 0 | **None** | |

**Audit**: PostHog → Pick top 5 events → inspect recent events JSON in Inspector tab.

---

## Anti-Pattern References

### Anti-Pattern 1: Bloated Event Properties

**Problem**: Sending unnecessary data inflates costs and reduces focus.

```typescript
// WRONG: Too much user data in every event
track('button_clicked', {
  user_id: user.id,
  user_email: user.email,
  user_name: user.name,
  user_phone: user.phone,
  company: user.company,
  signup_date: user.created_at,
  button_name: 'Submit',
  button_location: 'footer',
})

// RIGHT: Use identify() for user properties, event-specific properties only
identify({ email: user.email, company: user.company })
track('button_clicked', {
  button_name: 'Submit',
  button_location: 'footer',
})
```

### Anti-Pattern 2: Non-Actionable Events

**Problem**: Events don't map to business outcomes or product decisions.

```typescript
// WRONG: Tells you nothing about value
track('page_viewed', { path: '/dashboard' })

// RIGHT: Tells you about engagement and user intent
track('page_viewed', {
  path: '/dashboard',
  time_on_previous_page_seconds: 120,
  referrer_path: '/talent-pool',
})
```

### Anti-Pattern 3: Loose Attribution (Missing Context)

**Problem**: Can't tell which feature drove a conversion.

```typescript
// WRONG: Can't link back to the source action
track('candidate_unlocked', { candidate_id: 'cand_123' })

// RIGHT: Includes attribution chain
track('candidate_unlocked', {
  candidate_id: 'cand_123',
  unlock_source: 'talent_pool', // where unlock initiated
  talent_search_query: 'react senior', // what search led here
  time_in_pool_seconds: 450, // engagement duration
  match_score: 88, // relevance indicator
})
```

### Anti-Pattern 4: Silent Failures

**Problem**: Events fire but properties are often null/undefined.

```typescript
// WRONG: If score not calculated yet, property undefined
const score = calculateScore() // returns null if still loading
track('match_score_viewed', { overall_score: score }) // sends null

// RIGHT: Only track when data is complete
if (score !== null) {
  track('match_score_viewed', { overall_score: score })
}
```

### Anti-Pattern 5: Duplicate Events

**Problem**: Same action tracked multiple times (double-counts metrics).

```typescript
// WRONG: Assessment submitted tracked twice
const handleSubmit = async () => {
  track('assessment_submitted', {...})
  const response = await submitAssessment()
  track('assessment_submitted', {...}) // Duplicate!
}

// RIGHT: Track once with success indicator
const handleSubmit = async () => {
  track('assessment_submitted', { status: 'pending' })
  try {
    await submitAssessment()
    // Update user property or fire separate success event
    track('assessment_submission_succeeded', {...})
  } catch (err) {
    track('assessment_submission_failed', { error_reason: err.code })
  }
}
```

### Anti-Pattern 6: Free Text Over Enums

**Problem**: Free-text properties can't be aggregated or compared.

```typescript
// WRONG: Can't filter or group effectively
track('assessment_completed', {
  reason: 'User ran out of time', // 500 variations
})

// RIGHT: Use enums
track('assessment_completed', {
  completion_reason: 'timeout', // Limited set
})
```

### Anti-Pattern 7: Ignoring Privacy

**Problem**: Sending PII makes data unsafe and non-compliant.

```typescript
// WRONG: Sends email in plain text
track('profile_updated', { email: user.email })

// RIGHT: Hash or omit
track('profile_updated', {
  email_hash: await hashEmail(user.email),
  // OR just omit email entirely
  field_updated: 'bio',
})
```

---

## Industry Variations

### B2C SaaS (Candidate App)

**Focus**: Conversion funnels, engagement cohorts, feature adoption

```typescript
// Key events: Onboarding → Assessment → Certificate → Job Application
track('candidate_onboarding_started', { source })
track('assessment_started', { skill_name })
track('assessment_submitted', { score_percentage, passed })
track('certificate_downloaded', { skill_name })
track('job_application_submitted', { company_name })

// Attribution model: First-touch (which channel acquired user)
// Retention metric: Days since last assessment attempt
```

### B2B SaaS (Recruiter App)

**Focus**: Deal closure, team utilization, cost-per-hire

```typescript
// Key events: Signup → Talent Search → Candidate Unlock → Hire
track('recruiter_onboarding_started', { source })
track('talent_search_performed', { keywords, results_count })
track('candidate_unlocked', { unlock_source, cost_credits })
track('message_sent', { recipient_candidate_id })
track('hire_recorded', { job_post_id, hired_candidate_id, time_to_hire_days })

// Attribution model: Multi-touch (all searches + unlocks → hire)
// Revenue metric: Cost-per-hire (credits spent / hires)
```

### Marketplace (Job Matching)

**Focus**: Match quality, supply-demand balance, conversion rate

```typescript
// Events: Recommendation shown → candidate views → applies
track('job_recommendation_shown', { candidate_id, job_id, match_score })
track('job_viewed', { job_id, source: 'recommended' })
track('job_application_submitted', { job_id, source_event: 'recommendation' })

// Attribution model: Time-decay (recent matches weighted higher)
// Quality metric: Apply-to-match-ratio
```

---

## Benchmark References

### Funnel Benchmarks (Enterprise SaaS)

| Stage | Conversion Rate | Industry Benchmark |
|-------|---|---|
| Signup → Activated (Day 7) | 40-50% | Product-qualified leads |
| Activated → Active (Day 30) | 70-80% | Adoption rate |
| Active → Paying | 3-5% | Monetization rate |
| Paying → Retained (Month 2) | 85-90% | Retention rate |

**SwiftHyre Candidate App Funnel:**
- Signup → Onboarding Completed: **Target 60%**
- Onboarding → Assessment Started: **Target 50%**
- Assessment Started → Assessment Submitted: **Target 85%**
- Assessment Submitted → Certificate Viewed: **Target 70%**

### Attribution Model Benchmarks

| Model | Best For | Accuracy |
|-------|---|---|
| First-Touch | Awareness campaigns, discovery | 60-70% |
| Last-Touch | Conversion optimization, bottom funnel | 70-80% |
| Linear | Multi-step journeys | 75% |
| Time-Decay | Complex sales cycles | 80-85% |
| Multi-Touch (ML) | High-value transactions | 85-95% |

**SwiftHyre Recommends:**
- **Candidate**: First-touch (source of discovery)
- **Recruiter**: Multi-touch (all talent searches + unlocks → hire)
- **Matching**: Time-decay (recent interactions more relevant)

### Dashboard Health Metrics

| Metric | Green | Yellow | Red |
|--------|-------|--------|-----|
| Event capture latency | <1s | <5s | >5s |
| Event delivery rate | >99% | >95% | <95% |
| Property fill rate | >95% | >80% | <80% |
| Dashboard load time | <3s | <10s | >10s |
| Data freshness | <1hr | <4hr | >4hr |

---

## Council Integration Hook

### Analyst Council Sync Points

```typescript
// Before shipping analytics, sync with Analyst Council:

// 1. Definitions Meeting (30 min)
// Q: What question will this event answer?
// Q: How does it map to business KPI?
// Q: Is event name unambiguous across teams?

// 2. Implementation Review (15 min)
// Q: Are properties named consistently?
// Q: Is attribution clear (session_id, user_id present)?
// Q: Are we missing edge cases?

// 3. Dashboard Acceptance (15 min)
// Q: Does the dashboard answer the original question?
// Q: Can non-technical stakeholders understand it?
// Q: Is the metric actionable?

// Implementation pattern:
import { analyticsReviewChecklist } from '@repo/shared/analytics'

const review = analyticsReviewChecklist({
  featureName: 'intelligent-matching',
  businessQuestion: 'Does ML ranking increase job apply rate?',
  events: ['match_score_viewed', 'job_applied'],
  attributionModel: 'time_decay',
  dashboardLink: 'https://posthog.com/project/dashboards/xyz',
})

// MUST PASS before merge
if (!review.allClear) {
  throw new Error(review.blockers.join('\n'))
}
```

### Escalation Path

```
Data Quality Issue Detected
├─ Is fill rate <80%?
│   └─ Escalate to Engineer Council (property tracking)
├─ Is event chain broken?
│   └─ Escalate to Analytics Council (design issue)
└─ Is dashboard not answering questions?
    └─ Escalate to Product Council (business context issue)
```

---

## Cross-Skill Dependencies

**This skill is a foundation** - all other skills depend on it:

| Skill | Dependency | Pattern |
|-------|---|---|
| **frontend-design** | Tracks component interactions, conversion events | `useAnalytics()` in React components |
| **nextjs** | Server-side event tracking, page view analytics | `trackServerEvent()` in API routes |
| **react** | Client-side hook integration, user identification | `usePageView()`, `useAnalytics()` in layouts |
| **trigger-dev** | Attribution pipelines, funnel computation | Multi-step event chains, Trigger.dev jobs |
| **stripe** | Revenue event attribution | `trackRevenueEvent()` in webhook handlers |
| **postgresql** | Event data warehouse, historical analysis | Event tables, retention policies |
| **admin** | Dashboard creation, metrics reporting | PostHog insight queries, cohort analysis |

### Integration Patterns

```typescript
// Pattern 1: React Component → Event Tracking
'use client'
import { useAnalytics } from '@repo/analytics'

export function AssessmentQuestion() {
  const { track } = useAnalytics()
  
  const handleAnswer = (answer: string) => {
    track('assessment_question_answered', {
      question_id: 'q_123',
      answer_selected: answer,
      time_to_answer_seconds: 15,
    })
  }
}

// Pattern 2: Server Action → Event Tracking
'use server'
import { trackServerEvent } from '@repo/analytics/server'

export async function submitAssessment(attemptId: string) {
  const attempt = await getAttemptFromDB(attemptId)
  
  await trackServerEvent(attempt.user_id, 'assessment_submitted', {
    attempt_id: attemptId,
    duration_minutes: attempt.durationMinutes,
    score: attempt.score,
  })
}

// Pattern 3: Trigger.dev Job → Attribution Pipeline
import { tasks } from '@trigger.dev/sdk'

export async function trackMatchScoreCreation(matchId: string) {
  // Trigger async attribution job
  await tasks.trigger('compute-match-attribution', {
    match_id: matchId,
    attribution_model: 'time_decay',
  })
}
```

---

## Event Taxonomy Template

Use this template for adding new event types to `packages/analytics/src/types/events.ts`:

```typescript
// ============================================
// [FEATURE NAME] EVENTS
// ============================================

export type [FeatureName]Events = {
  // [PHASE/CATEGORY]
  
  /**
   * Fired when: [describe trigger]
   * Business question: [what decision does this event inform?]
   * Properties:
   *   - [property]: [type] - [why tracked]
   */
  event_name_one: {
    property_id: string
    property_count: number
    property_status: 'active' | 'inactive'
  }
  
  /**
   * Fired when: [describe trigger]
   * Business question: [what decision does this event inform?]
   * Properties:
   *   - [property]: [type] - [why tracked]
   */
  event_name_two: {
    duration_seconds: number
    completion_percentage: number
  }
}

// Add to AllEvents union at bottom:
// export type AllEvents = CandidateEvents & RecruiterEvents & [FeatureName]Events & ...
```

---

## Implementation Checklist

Before committing event tracking:

- [ ] **Naming**: All events follow `[domain]_[action]_[object]` pattern
- [ ] **Properties**: All properties named with conventions (is_*, *_count, *_id)
- [ ] **Quality**: Event coverage ≥ 4/5 (see rubric)
- [ ] **Types**: Events defined in `packages/analytics/src/types/events.ts`
- [ ] **Consistency**: Property names match existing events (check events.ts)
- [ ] **Attribution**: Events include session_id, user_id, and temporal context
- [ ] **Privacy**: No PII sent; sensitive data hashed or omitted
- [ ] **Testing**: Manual test in development; verify events in PostHog Inspector
- [ ] **Dashboard**: Dashboard created in PostHog to answer "Did this work?"
- [ ] **Council Review**: Analyst Council sign-off on definitions and attribution
- [ ] **Documentation**: Event added to this skill's taxonomy template

---

## Quick Reference: Event Taxonomy

**Candidate App**:
- Onboarding: `onboarding_*`
- Resume: `resume_*`
- Profile: `profile_*`
- Assessment: `assessment_*`
- Proctoring: `proctoring_*`
- Jobs: `job_*`
- Certificates: `certificate_*`
- Messaging: `message_*`

**Recruiter App**:
- Signup: `signup_*`
- Talent Discovery: `talent_*`
- Candidate Interactions: `candidate_*`
- Credit Management: `credit_*`
- Messaging: `message_*`
- Pipeline: `pipeline_*`
- AI Assistant (Swifty): `assistant_*`
- Matching: `match_*`

**Shared**:
- Navigation: `page_viewed`, `navigation_clicked`
- UI: `button_clicked`, `modal_opened`, `form_submitted`
- Errors: `error_displayed`, `error_dismissed`

---

## Environment & Setup

```bash
# Analytics dependencies
NEXT_PUBLIC_POSTHOG_KEY=phc_xxx
NEXT_PUBLIC_POSTHOG_API_HOST=https://us.i.posthog.com

# Server-side analytics
POSTHOG_API_KEY=phc_xxx

# Enable analytics in app
npm install @repo/analytics posthog-js posthog-node

# Test event capture
npm run dev
# Visit http://localhost:3000/dashboard
# Open PostHog Inspector (settings → debug)
# Verify events appear in real-time
```

---

## Resources

- **PostHog Docs**: https://posthog.com/docs
- **Event Best Practices**: https://posthog.com/tutorials/event-tracking-best-practices
- **Funnels & Cohorts**: https://posthog.com/docs/product-analytics/funnels
- **Attribution Models**: https://posthog.com/docs/data-management/user-attribution
- **SwiftHyre Analytics**: `packages/analytics/src/`
- **Existing Events**: `packages/analytics/src/types/events.ts`
```