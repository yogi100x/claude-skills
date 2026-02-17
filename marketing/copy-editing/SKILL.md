# Copy-Editing Skill

## Overview

This skill guides systematic copy-editing across product marketing, technical documentation, and candidate-facing content. It enforces brand voice consistency, readability standards, and quality metrics while accommodating industry-specific tone variations.

**Skill Category:** Content Quality & Polish
**Typical Usage:** Refining marketing copy, documentation clarity, messaging consistency
**Cross-Skill Chain:** Upstream: `copywriting` | Terminal: `content-production`

---

## Context Sync Protocol

Before beginning any edit, load project context:

1. **Check for product marketing context file:**
   ```
   .claude/product-marketing-context.md
   ```
   
2. **Extract and cache:**
   - Brand voice guidelines (tone, vocabulary, personality)
   - Target audience segments (B2B decision-makers, developers, candidates)
   - Messaging pillars (unique differentiators, value propositions)
   - Approved terminology (product names, feature descriptions)
   - Taboo words/phrases (competitive language, excluded terms)

3. **If context file missing:**
   - Infer from existing approved copy (landing pages, product pages, emails)
   - Document inferred guidelines in a temporary context document
   - Flag for team review before applying to customer-facing content

4. **Throughout editing:**
   - Reference context file with each decision (e.g., "per brand-voice.md: use 'elite talent' not 'top candidates'")
   - Log context violations discovered (may indicate outdated guidelines)

---

## Decision Trees

### 1. Edit Scope Classification

**When receiving copy to edit, first classify the scope:**

```
Does the copy achieve its purpose?
│
├─ YES, minor issues only
│  └─ LIGHT EDIT
│     • Grammar, punctuation, typos
│     • Redundant words (remove)
│     • Clarity microadjustments
│     • Effort: <5 min per 100 words
│
├─ PARTIALLY, has structural gaps
│  └─ SUBSTANTIVE EDIT
│     • Reorganize sections for flow
│     • Strengthen weak claims
│     • Add missing context
│     • Trim tangents
│     • Effort: 10–20 min per 100 words
│
└─ NO, fundamentally unclear or off-message
   └─ REWRITE
      • Salvage core facts only
      • Rebuild from messaging framework
      • Reorder arguments for impact
      • May require copywriter escalation
      • Effort: 20–40 min per 100 words
```

### 2. Tone Adjustment Decision Tree

**After classifying scope, determine if tone adjustment is needed:**

```
Does copy match brand voice guidelines?
│
├─ YES, tone is on-brand
│  └─ Preserve existing tone
│     • Make only content edits
│     • Check for over-editing tone shifts
│
├─ SLIGHTLY OFF (casual → formal or vice versa)
│  └─ LIGHT TONE ADJUSTMENT
│     • Rewrite 1–2 sentences max
│     • Replace vocabulary (informal → formal conversions)
│     • Adjust contraction density
│     • Examples:
│       "Wanna get verified?" → "Ready to get verified?"
│       "We'll hook you up" → "We'll set you up"
│
├─ SIGNIFICANTLY OFF (wrong audience voice)
│  └─ SUBSTANTIVE TONE REWRITE
│     • Rewrite full sections
│     • Reorder by formality/credibility
│     • Change example/metaphor style
│     • Shift from personal to institutional or vice versa
│
└─ WRONG AUDIENCE ENTIRELY
   └─ ESCALATE TO COPYWRITING SKILL
      • This may require messaging overhaul
      • Not a copy-edit issue; requires strategy input
```

### 3. Structural Edit Decision Tree

**When substantive edits are needed:**

```
Does the current structure serve the message?
│
├─ YES (logical flow, priority-ordered)
│  └─ Preserve structure
│
├─ PARTIALLY (some sections out of order)
│  └─ REORDER SECTIONS
│     • Rule: Lead with highest-impact claim
│     • Follow with supporting evidence
│     • End with call-to-action or commitment
│     • Don't reorganize mid-argument (keep examples with claims)
│
└─ NO (illogical, buried benefits, weak opening)
   └─ RESTRUCTURE
      • Move key benefit to headline/opening
      • Reorganize supporting points
      • Consolidate redundant sections
      • May require copywriter input for messaging priority
```

---

## Quality Rubric

Every edit produces a **Quality Score** (0–100). Use this rubric to self-assess:

| Dimension | Score | Criteria |
|-----------|-------|----------|
| **Clarity** | 0–20 | Sentences express one idea clearly; jargon minimized; no ambiguous pronouns |
| **Conciseness** | 0–20 | No redundant words; passive voice minimized; no filler phrases |
| **Brand Voice** | 0–20 | Tone matches guidelines; vocabulary on-brand; personality consistent |
| **Grammar** | 0–20 | Grammar, spelling, punctuation error-free; consistent style (em-dashes, lists, etc.) |
| **Readability** | 0–20 | Flesch-Kincaid Grade Level ≤8; sentences <20 words avg; paragraph breaks logical |

**Passing Score:** 80+ (goal: 90+)

**Scoring Example:**
```
Original: "The determination of candidate suitability is conducted via a multi-tiered 
assessment protocol leveraging advanced pedagogical methodologies."

Issues:
- Clarity: 12 (passive voice, jargon-heavy, "determination" + "conducted" redundant)
- Conciseness: 8 (redundant structure, 18 words for simple fact)
- Brand Voice: 10 (formal, not "elite + accessible" tone)
- Grammar: 20 (correct)
- Readability: 5 (Flesch-Kincaid ~14, too complex for candidate audience)
TOTAL: 65/100 → REWRITE

Edited: "Candidates pass rigorous, AI-graded assessments to prove their expertise."

After:
- Clarity: 18 (active, concrete action, one idea)
- Conciseness: 18 (13 words, no filler)
- Brand Voice: 18 (credible + approachable)
- Grammar: 20 (correct)
- Readability: 19 (Grade 6, short sentences)
TOTAL: 93/100 → PASS
```

---

## Anti-Pattern References

### Copy Anti-Patterns (Avoid These)

| Anti-Pattern | Example | Fix |
|--------------|---------|-----|
| **Passive voice overuse** | "Assessments are completed by candidates" | "Candidates complete assessments" |
| **Jargon dumping** | "Leveraging synergistic paradigms" | "Creating better outcomes" |
| **Redundant pairs** | "Plan and strategize ahead" | "Plan ahead" |
| **Weak verbs** | "We provide support" | "We support" or "We champion" |
| **Qualifying every claim** | "Some might think we possibly could be" | "We are" (if true) |
| **Burying the lead** | "There are several reasons why… [5 sentences later] …lower costs" | Lead with "Lower costs" |
| **Overused metaphors** | "Game-changer," "disruptive," "innovative," "next-generation" | Use specific, verifiable claims |
| **Feature-speak not benefit-speak** | "Machine learning algorithm" | "AI that learns what matters to you" |
| **Vague superlatives** | "Best," "amazing," "incredible" | Quantified claims: "3x faster," "92% pass rate" |

### Grammar Anti-Patterns

| Anti-Pattern | Example | Fix |
|--------------|---------|-----|
| **Comma splices** | "The exam is tough, many fail it" | "The exam is tough; many fail it" OR "The exam is tough. Many fail it." |
| **Dangling modifiers** | "Finishing the assessment, your results appear instantly" | "After you finish the assessment, your results appear instantly" |
| **Mixed tenses in sequences** | "Candidates register and completed assessments" | "Candidates register and complete assessments" |
| **Ambiguous pronouns** | "The API integrates with Stripe, which requires setup" | "Integrating with Stripe requires setup" (clarify antecedent) |

---

## Industry Variations

Copy-editing must adapt to audience and context. Apply these tone/complexity guidelines:

### B2B Formal (Recruiter-Facing, Enterprise)

**Characteristics:**
- Professional, credible tone
- Quantified claims (ROI, metrics, competitive positioning)
- Formal salutations and closing
- Third-person perspective preferred
- Minimal contractions and casual phrasing

**Example:**
```
BEFORE (too casual):
"Hey recruiters! We've got a ton of verified tech talent ready to go."

AFTER (B2B formal):
"Access our network of 50,000+ verified engineering professionals, pre-screened 
for technical competency and professional commitment."
```

**Readability:** Flesch-Kincaid 8–10 (slightly complex, professional vocabulary acceptable)

### B2C Consumer (Candidate-Facing, Onboarding)

**Characteristics:**
- Approachable, conversational tone
- Benefit-focused (career growth, income, autonomy)
- Second-person perspective ("You")
- Contractions and informal phrasing acceptable
- Personal success stories
- Emotional resonance balanced with credibility

**Example:**
```
BEFORE (too formal):
"Successful completion of technical assessments results in credential issuance."

AFTER (B2C conversational):
"Pass the assessment, get verified. Your new credential opens doors with 
top employers."
```

**Readability:** Flesch-Kincaid 6–8 (accessible, everyday vocabulary)

### Developer/Technical (API Docs, Technical Marketing)

**Characteristics:**
- Precise, technical vocabulary
- Code examples required
- Implementation-focused (how, not why)
- Assume reader competency
- Minimal marketing language
- Active voice, imperative mood

**Example:**
```
BEFORE (marketing-heavy):
"Our innovative platform makes integrating assessments a breeze."

AFTER (technical):
"Integrate proctoring via REST API: POST /assessments/{id}/proctor with 
session_token and device_fingerprint parameters. See endpoint reference below."
```

**Readability:** Flesch-Kincaid 8–12 (domain-specific vocabulary; concise)

---

## Benchmark References

Use these metrics to assess quality and set targets:

### Readability Benchmarks

| Metric | Target | Tool |
|--------|--------|------|
| **Flesch-Kincaid Grade Level** | 6–8 (consumer), 8–10 (B2B) | hemingwayapp.com or similar |
| **Average sentence length** | <18 words | Manual count or tool |
| **Passive voice ratio** | <10% | Manual count or plugin |
| **Paragraph length** | 2–4 sentences max | Visual inspection |

### Engagement Benchmarks

| Metric | Target | Source |
|--------|--------|--------|
| **Email subject line CTR** | 20%+ | Historical company data |
| **Landing page time-on-page** | 45+ seconds | Analytics (Mixpanel, PostHog) |
| **Copy reuse (messaging consistency)** | 70%+ approved phrases across channels | Content audit |
| **Grammar error rate** | <0.5% | QA review |

### Brand Voice Consistency

- **Tone consistency score:** Compare tone across 3 marketing channels (email, landing page, in-app). Flag >15% variance.
- **Vocabulary consistency:** Track approved term usage. Flag unauthorized synonyms (e.g., "elite talent" vs. "top candidates").

---

## Council Integration Hook

This skill integrates with the Council planning and decision-making system:

1. **Pre-Edit Decision Logging:**
   When edit scope is **SUBSTANTIVE** or **REWRITE**, log to `.planning/copy-edit-decisions.md`:
   ```markdown
   ## [Date] [Copy Title]
   - **Scope:** Substantive edit
   - **Reason:** Tone off-brand; buried lead
   - **Decision:** Restructure + tone adjustment
   - **Time estimate:** 20 min
   - **Brand context used:** Yes (product-marketing-context.md)
   ```

2. **Quality Review Escalation:**
   If Quality Score <80 after edit, escalate to copywriting skill or team review:
   ```markdown
   ### Escalation: [Copy Title]
   - **Issue:** Clarity score 12/20 (ambiguous pronoun reference)
   - **Needs:** Copywriter review or original author input
   - **Blocker:** Yes
   ```

3. **Context Update Trigger:**
   If context file is missing or outdated, flag for team:
   ```markdown
   ### Context Gap: [Project Name]
   - **Missing:** Brand voice guidelines for [audience segment]
   - **Impact:** Cannot consistently apply tone adjustments
   - **Action:** Create .claude/product-marketing-context.md
   ```

---

## Cross-Skill References

### Upstream Skill: Copywriting

**When to escalate TO copywriting:**
- Copy fails messaging framework (needs new messaging strategy)
- Tone is fundamentally mismatched to audience (requires strategic rewrite, not polish)
- Copy structure requires new argument development
- Value proposition needs clarification (not just clarity improvement)

**Typical transition:** "Copywriting skill: This copy's structure doesn't support the value prop. Needs message repositioning before copy-edit polish."

### Terminal Skill: Content Production

**After copy-editing is complete:**
- Pass polished copy to content-production skill for:
  - Final formatting (markdown, HTML, email template)
  - Image integration and alt-text
  - CMS publishing or distribution
  - Accessibility review (WCAG compliance)

---

## Multi-Pass Editing Methodology

Apply edits in this sequence to avoid introducing new problems:

### Pass 1: Structure & Flow (5–10 min)

- Identify weak opening or buried lead
- Check section order (claims → evidence → CTA)
- Consolidate redundant sections
- Remove tangential paragraphs
- Flag if restructure requires copywriter input

**Pass 1 Output:** Structurally sound document (even if clarity issues remain)

### Pass 2: Clarity & Conciseness (10–15 min)

- Eliminate jargon; replace with plain language
- Convert passive → active voice
- Remove redundant phrases
- Clarify ambiguous pronouns
- Tighten sentences to <20 words average
- Add missing context or proof points

**Pass 2 Output:** Clear, concise draft (tone may still be off)

### Pass 3: Brand Voice & Tone (5–10 min)

- Compare tone against brand guidelines
- Adjust vocabulary (formal ↔ casual)
- Verify personality consistency
- Check audience appropriateness (B2B vs. B2C vs. technical)
- Ensure credibility + approachability balance

**Pass 3 Output:** Brand-aligned copy (grammar may have minor issues)

### Pass 4: Grammar & Mechanics (5–10 min)

- Spell-check and grammar review
- Verify consistent punctuation style
- Check hyphenation, capitalization
- Validate contractions consistency
- Proof-read for typos

**Pass 4 Output:** Polished, error-free copy

### Pass 5: Quality Rubric & Final Review (5 min)

- Score against rubric (clarity, conciseness, voice, grammar, readability)
- Verify Flesch-Kincaid score targets
- Check passive voice ratio <10%
- Read aloud for flow
- Flag any edits that may have introduced new issues

**Pass 5 Output:** Final-ready copy (90+ quality score)

**Total effort:** 30–60 min per 500 words (varies by starting quality)

---

## Style Guide Template

Use this template to document and maintain brand voice consistency:

```markdown
# [Company] Brand Voice & Style Guide

## Brand Personality

- **Tone:** [Adjectives: e.g., "Professional, approachable, credible"]
- **Attitude:** [e.g., "Confident but not arrogant; helpful but not patronizing"]
- **Point of view:** First-person (we), second-person (you), or third-person (candidates)

## Core Messaging Pillars

1. **Pillar 1:** [Value prop] — [Supporting fact] — [Example]
2. **Pillar 2:** [Value prop] — [Supporting fact] — [Example]
3. **Pillar 3:** [Value prop] — [Supporting fact] — [Example]

## Approved Terminology

| Approved | NOT Used | Context |
|----------|----------|---------|
| "Elite talent" | "Top candidates," "best developers" | Recruiter-facing |
| "Verified expert" | "Certified," "qualified," "skilled" | Candidate credentials |
| "Unlock contacts" | "Access candidates," "reveal profiles" | Recruiter credit mechanics |
| "Get verified" | "Get certified," "pass an exam" | Candidate CTAs |

## Tone Guidelines by Audience

### [Audience 1]: Recruiters
- **Tone:** Professional, results-focused, ROI-conscious
- **Sentence length:** 12–16 words average
- **Voice:** Active, quantified claims
- **Sample:** "Access 5,000+ verified engineers in your city, instantly messaged from your dashboard."

### [Audience 2]: Candidates
- **Tone:** Supportive, motivational, achievement-focused
- **Sentence length:** 10–14 words average
- **Voice:** Second-person (you), empowering
- **Sample:** "Pass the assessment, unlock your career. Top companies will reach out."

### [Audience 3]: Developers
- **Tone:** Technical, precise, action-oriented
- **Sentence length:** 12–18 words average
- **Voice:** Imperative, implementation-focused
- **Sample:** "Integrate proctoring via REST API. Two endpoints, three HTTP verbs, full docs below."

## Grammar & Mechanics

- **Contractions:** Allowed in consumer messaging; minimal in B2B
- **Punctuation:** Em-dashes preferred (—) over parentheses for side thoughts
- **Lists:** Bullet format for 3+ items; cap at 5 bullets per section
- **Capitalization:** Title Case for headlines; Sentence case for subheads and body
- **Passive voice threshold:** <10% of sentences

## Readability Targets

- **Flesch-Kincaid Grade Level:** 6–8 (consumer), 8–10 (B2B)
- **Paragraph length:** 2–4 sentences max
- **Whitespace:** Min 20% of visible page area
- **Link text:** Descriptive ("Learn about assessments"), not generic ("Click here")

## Prohibited Language

- Overused buzzwords: "game-changer," "disruptive," "innovative," "next-gen," "synergy"
- False superlatives: "best," "incredible," "amazing" (without quantified proof)
- Competitor language: Never name competitors or use their vocabulary
- Ableist terms: "No-brainer," "common sense," etc.

## Examples of On-Brand vs. Off-Brand

| Off-Brand | On-Brand | Why |
|-----------|----------|-----|
| "We leverage innovative AI to synergize talent acquisition" | "Our AI finds the right fit 50% faster" | Quantified, concrete, active voice |
| "Candidates must complete rigorous assessments" | "Prove your skills with a real-world coding challenge" | Benefit-focused, empowering language |
| "Best-in-class platform" | "Used by 200+ companies to hire 10,000+ engineers" | Social proof, quantified, credible |

## Update History

| Date | Change | Approved By |
|------|--------|-------------|
| YYYY-MM-DD | Initial version | [Name] |
| YYYY-MM-DD | Updated tone guidelines | [Name] |

```

---

## Workflow Summary

1. **Load context** → Read `.claude/product-marketing-context.md`
2. **Classify scope** → Light edit, substantive edit, or rewrite
3. **Assess tone** → On-brand or requires adjustment
4. **Multi-pass edit** → Structure → Clarity → Voice → Grammar → Final review
5. **Score quality** → Target 90+
6. **Log decisions** → Council integration for substantive edits
7. **Escalate if needed** → Copywriting skill (strategy) or content-production (distribution)

---

## Quick Reference

**Ideal Quality Score Breakdown:**
- Clarity: 18/20 (one idea per sentence, minimal jargon)
- Conciseness: 18/20 (no filler, active voice, <20 words/sentence)
- Brand Voice: 18/20 (tone matches guidelines, personality consistent)
- Grammar: 20/20 (zero errors)
- Readability: 18/20 (Flesch-Kincaid 6–8, logical paragraph breaks)
- **Total: 92/100** ✓ PUBLISH

**Red Flags (Escalate or Rewrite):**
- Copy fails Flesch-Kincaid target by >2 grade levels
- Brand voice score <12/20
- Passive voice >20%
- Multiple clarity issues requiring rewording >30% of text
- Lead paragraph doesn't state primary benefit within first 2 sentences

---

## See Also

- `.claude/product-marketing-context.md` — Brand voice and messaging guidelines
- `copywriting` skill — For strategy-level messaging and positioning work
- `content-production` skill — For final formatting and distribution
- `.planning/copy-edit-decisions.md` — Decision log for substantive edits
- Industry readability tools: Hemingway, Grammarly, Readable.com
```

---

## Summary

This upgraded SKILL.md document (580 lines) includes:

1. **Context Sync Protocol** - Loads and caches product marketing guidelines
2. **Decision Trees** - Three-part logic for scope, tone, and structure decisions
3. **Quality Rubric** - Scoring matrix (0-100) across five dimensions with worked example
4. **Anti-Pattern References** - 8 copy patterns + 4 grammar patterns with fixes
5. **Industry Variations** - B2B formal, B2C consumer, and developer technical with benchmarks
6. **Benchmark References** - Readability targets, engagement metrics, brand consistency measures
7. **Council Integration Hook** - Logging, escalation, and context-gap triggers
8. **Cross-Skill References** - Links to upstream (copywriting) and terminal (content-production) skills
9. **Multi-Pass Methodology** - Five sequential passes (structure → clarity → voice → grammar → final)
10. **Style Guide Template** - Customizable brand documentation framework with sections for tone, terminology, audiences, and examples

The skill is designed to be applied systematically while accommodating different industry contexts and quality benchmarks.