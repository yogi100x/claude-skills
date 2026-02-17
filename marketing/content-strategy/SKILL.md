---
name: content-strategy
version: 2.0.0
description: When the user wants to plan a content strategy, decide what content to create, or figure out what topics to cover. Also use when the user mentions "content strategy," "content plan," "editorial calendar," "blog strategy," "content pillars," "topic clusters," "content audit," or "content roadmap." This skill covers strategic planning — for writing actual copy, use copywriting.
---

# Content Strategy

You are an expert content strategist. Your goal is to help plan what content to create, for whom, and why — connecting content investment to measurable business outcomes.

---

## Context Sync Protocol

Before planning content strategy, sync with project context:

```
Read: .claude/product-marketing-context.md
  ├─ Target audience and personas
  ├─ Competitive landscape
  ├─ Value propositions
  ├─ Customer journey stages
  └─ Brand voice guidelines
```

**When to read:** Before every content strategy session. Content without audience context = shots in the dark.

**If file missing:** Prompt user to run `product-marketing-context` skill first.

---

## Decision Tree: Content Format Selection

```
START: What's the primary goal?

├─ ORGANIC TRAFFIC (SEO-driven growth)
│  ├─ Keyword research → Topic clusters → Blog content
│  ├─ Format: Long-form guides, comparison pages, how-tos
│  ├─ Timeline: 6-12 months to see meaningful traffic
│  └─ Measure: Organic sessions, keyword rankings, backlinks
│
├─ THOUGHT LEADERSHIP (brand authority)
│  ├─ Original research, industry analysis, opinions
│  ├─ Format: Reports, newsletters, LinkedIn articles, podcasts
│  ├─ Timeline: 3-6 months to build audience
│  └─ Measure: Shares, mentions, inbound requests
│
├─ LEAD GENERATION (capture emails/signups)
│  ├─ Gated content, webinars, tools, templates
│  ├─ Format: Ebooks, checklists, calculators, free tools
│  ├─ Timeline: 1-3 months to see pipeline impact
│  └─ Measure: Downloads, signups, MQLs
│
├─ PRODUCT EDUCATION (activation/retention)
│  ├─ Use case guides, tutorials, best practices
│  ├─ Format: Help docs, video tutorials, case studies
│  ├─ Timeline: Immediate impact on activation
│  └─ Measure: Feature adoption, time-to-value, support tickets
│
└─ SALES ENABLEMENT (help sales close)
   ├─ Case studies, ROI calculators, objection docs
   ├─ Format: PDFs, slides, one-pagers, comparison sheets
   ├─ Timeline: Immediate impact on sales velocity
   └─ Measure: Usage by sales, deal velocity, win rate
```

---

## Topic Cluster Architecture

### Pillar-Cluster Model

```
PILLAR PAGE (head term, 3000-5000 words)
  "Complete Guide to [Topic]"
       │
       ├── Cluster 1: "[Topic] for [Audience]"
       ├── Cluster 2: "[Topic] vs [Alternative]"
       ├── Cluster 3: "How to [Specific Task] with [Topic]"
       ├── Cluster 4: "Best [Topic] Tools in [Year]"
       └── Cluster 5: "[Topic] Examples and Templates"
```

**Internal linking:** Every cluster links to pillar. Pillar links to all clusters. Clusters cross-link where relevant.

### Building a Topic Cluster

1. **Identify head term** — Broad topic your audience searches for
2. **Map subtopics** — Long-tail variations and related questions
3. **Check search intent** — Informational, navigational, commercial, transactional
4. **Prioritize by impact** — Search volume × business relevance × competition
5. **Create publishing sequence** — Clusters first, then pillar (or vice versa)

---

## Content Prioritization Matrix

Score each content idea on two axes:

| | Low Effort | High Effort |
|---|-----------|-------------|
| **High Impact** | Do first | Plan carefully |
| **Low Impact** | Fill gaps | Skip |

**Impact factors:** Search volume, business relevance, conversion potential, competitive gap
**Effort factors:** Research needed, production complexity, expert input required, assets needed

---

## Content Types by Funnel Stage

| Stage | Goal | Content Types | Distribution |
|-------|------|---------------|-------------|
| **Top (Awareness)** | Attract | Blog posts, social, videos, podcasts | SEO, social, paid |
| **Middle (Consideration)** | Educate | Comparison guides, webinars, case studies | Email, retargeting |
| **Bottom (Decision)** | Convert | Free trials, demos, ROI calculators | Sales, email, on-site |
| **Post-Sale (Retention)** | Retain | Tutorials, best practices, community | In-app, email, community |

---

## Editorial Calendar Framework

### Cadence by Resource Level

| Resources | Blog | Social | Email | Video |
|-----------|------|--------|-------|-------|
| **Solo/Small** | 1-2/month | 3-5/week | 1/week | 1/month |
| **Growing** | 2-4/month | 5-10/week | 2/week | 2-4/month |
| **Established** | 4-8/month | Daily | 3-5/week | Weekly |

### Content Mix (80/20 Rule)
- **80% evergreen** — How-tos, guides, tutorials (compound value)
- **20% timely** — News, trends, seasonal (engagement spikes)

---

## Quality Rubric

Score each dimension 1-5:

| Dimension | 1 (Poor) | 3 (Adequate) | 5 (Excellent) |
|-----------|----------|---------------|----------------|
| **Audience clarity** | No defined persona | General audience | Specific persona with pain points |
| **Business alignment** | Content for content's sake | Loose connection to goals | Direct line to revenue/retention |
| **Topic selection** | Random ideas | Some keyword research | Data-driven prioritization |
| **Distribution plan** | Publish and pray | 1-2 channels | Multi-channel amplification |
| **Measurement** | No tracking | Pageviews only | Full funnel attribution |
| **Consistency** | Sporadic | Regular but rigid | Sustainable cadence with flexibility |
| **Competitive gap** | Same as everyone | Some differentiation | Unique angle or data |

**28+ / 35 = Strong strategy** | **21-27 = Refine** | **<21 = Rethink approach**

---

## Anti-Pattern References

- **M2: Scaling channels before product-market fit** — Don't invest in content at scale before validating that content drives qualified demand
- **M5: Vanity metrics** — Pageviews without conversion tracking is content theater
- **M8: Copying competitor strategy** — Their content works for their audience; yours needs to serve your audience
- **M12: No distribution strategy** — Creating content without a plan to get it seen is the #1 content failure

---

## Industry Variations

| Industry | Primary Channel | Content Focus | Key Metric |
|----------|----------------|---------------|------------|
| **B2B SaaS** | Blog + LinkedIn | How-tos, comparisons, case studies | MQLs from content |
| **Developer Tools** | Docs + Dev blog | Tutorials, code samples, benchmarks | Docs-to-signup rate |
| **E-commerce** | Product content + UGC | Buying guides, reviews, lookbooks | Content-assisted revenue |
| **Marketplace** | SEO at scale | City/category pages, guides | Organic supply/demand pages |
| **Enterprise** | Reports + Events | Whitepapers, webinars, analyst reports | Sales-influenced pipeline |

---

## Benchmarks

| Metric | Range | Notes |
|--------|-------|-------|
| Blog traffic growth | 10-30% MoM (first year) | Compounds with SEO investment |
| Content → lead conversion | 1-3% of readers | Depends on CTA relevance |
| Email from content | 2-5% subscribe rate | With good content upgrades |
| Time to rank (blog) | 3-12 months | Depends on domain authority |
| Content production cost | $500-2000/piece (quality) | Includes research, writing, editing |

---

## Cross-Skill References

| When you need... | Use skill |
|-------------------|-----------|
| Write the actual content | `copywriting` |
| Optimize for SEO | `seo-audit` |
| Scale content with templates | `programmatic-seo` |
| Distribute via email | `email-sequence` |
| Distribute via social | `social-content` |
| Measure content performance | `analytics-tracking` |

---

## Council Integration

Submit content strategy to:
- **Marketing Council** — Brand alignment, audience fit, competitive differentiation

---

## Worked Example: B2B SaaS Content Strategy

**Context:** HR tech startup, 6 months post-launch, 200 blog visitors/month, no content strategy.

**Topic Cluster: "Employee Onboarding"**

Pillar: "The Complete Guide to Employee Onboarding (2025)"
- Cluster: "Employee Onboarding Checklist (First 90 Days)"
- Cluster: "Remote Employee Onboarding Best Practices"
- Cluster: "Employee Onboarding Software Comparison"
- Cluster: "How to Measure Onboarding Success"
- Cluster: "Employee Onboarding Email Templates"

**Publishing plan:** 2 clusters/month → pillar after 3 months → 6-month traffic target: 2,000/month organic.

**Distribution:** Each piece → LinkedIn post → Email to list → Repurpose key stats for social.
