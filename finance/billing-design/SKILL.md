# Billing Design

Design billing systems that handle subscriptions, usage metering, invoicing, and payment collection correctly.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for pricing tiers and billing frequency
2. Read `.claude/product-marketing-context.md` for customer segments and self-serve vs sales-led

## Decision Tree: Billing Architecture

```
What billing complexity do you need?
├── Simple subscriptions (flat-rate tiers)
│   └── Stripe Billing with Price objects
│       → Checkout Sessions or Payment Links for acquisition
│       → Customer Portal for self-service management
├── Usage-based billing
│   └── Stripe Metered Billing or custom metering
│       → Meter events API for real-time tracking
│       → Usage records aggregated at billing cycle
├── Hybrid (subscription + usage)
│   └── Stripe subscription with metered add-on items
│       → Base subscription price + usage line items
├── Enterprise / Custom
│   └── Custom invoicing with Stripe Invoices API
│       → Quote → Invoice → Payment workflow
└── Credits / Prepaid
    └── Internal credit ledger + Stripe for purchases
        → Credit balance tracking in your database
        → Stripe for credit pack purchases only
```

## Billing System Components

### Core Data Model

```
Organizations
  └── has one Subscription (status, plan, billing_cycle)
       └── has many Invoices (amount, status, due_date)
            └── has many Line Items (description, quantity, unit_price)
  └── has one Credit Balance (amount, last_updated)
       └── has many Credit Transactions (amount, type, description)
  └── has one Payment Method (via Stripe Customer)
```

### Webhook Events to Handle

| Event | Action | Idempotency Key |
|-------|--------|-----------------|
| `checkout.session.completed` | Provision subscription, allocate credits | `session.id` |
| `invoice.payment_succeeded` | Mark invoice paid, allocate recurring credits | `invoice.id` |
| `invoice.payment_failed` | Notify customer, start dunning | `invoice.id` |
| `customer.subscription.updated` | Sync plan changes | `subscription.id + updated timestamp` |
| `customer.subscription.deleted` | Downgrade to free, revoke access | `subscription.id` |

### Idempotency Pattern

```
Every webhook handler MUST:
1. Check if event already processed (by provider_event_id)
2. If processed, return 200 immediately
3. If new, process in transaction:
   a. Record event as processed
   b. Apply business logic
   c. Commit transaction
4. Return 200 (even on business logic errors — retry won't help)
```

## Dunning (Failed Payment Recovery)

| Day | Action |
|-----|--------|
| 0 | Payment fails → Retry automatically (Stripe Smart Retries) |
| 1 | Email: "Payment failed, please update card" |
| 3 | In-app banner: "Billing issue — update payment method" |
| 7 | Email: "Action required — service may be interrupted" |
| 14 | Downgrade to free tier (preserve data) |
| 30 | Final email: "Your account has been downgraded" |

**Never delete customer data on payment failure.** Downgrade access, preserve data.

## Credit System Design

For credit-based billing (e.g., pay-per-unlock):

```
Credit Transaction Types:
  PURCHASE    — Bought credits via Stripe
  ALLOCATION  — Monthly subscription credit allocation
  SPEND       — Used credits for an action (unlock, API call)
  REFUND      — Reversed a spend (admin action)
  EXPIRY      — Credits expired (if applicable)
  ADJUSTMENT  — Manual admin adjustment

Rules:
  - Credits never go negative (check before spend)
  - Use database transactions for atomic check-and-deduct
  - Log every transaction with metadata (what was purchased/unlocked)
  - Separate purchased credits from bonus/allocated credits (for refund logic)
```

## Anti-Patterns to Avoid

- **F1: Confusing revenue with cash** — Annual prepay is deferred revenue. Don't recognize it all upfront.
- **F6: Missing idempotency** — Webhooks will be delivered multiple times. Every handler must be idempotent.
- **T8: Insufficient error handling in billing** — A billing bug loses real money. Over-invest in error handling here.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Webhook handling** | Idempotent, verified signatures, all events | Key events handled | Missing critical events |
| **State management** | Subscription state machine with all transitions | Happy path covered | Ad-hoc status updates |
| **Dunning flow** | Multi-step with grace period and data preservation | Basic retry + email | No dunning |
| **Credit integrity** | Atomic transactions, audit log, no negative balances | Basic check-and-deduct | Race conditions possible |
| **Self-service** | Portal for plan changes, payment updates, invoices | Some self-service | All changes require support |
| **Testing** | Stripe test mode, webhook simulation, edge cases | Happy path tests | Manual testing only |
| **Monitoring** | Alerts for failed payments, revenue anomalies | Basic logging | No billing monitoring |

**28+ = Production-ready | 21-27 = Needs hardening | <21 = Risk of revenue loss**

## Cross-Skill References

- **Upstream:** `pricing-model` (what to charge), `unit-economics` (margin requirements)
- **Downstream:** `revenue-recognition` (accounting treatment), `kpi-dashboard` (MRR tracking)
- **Parallel:** `auth-design` (entitlement checks), `webhook-design` (event handling patterns)
- **Council:** Submit to `council-finance` for revenue recognition compliance
