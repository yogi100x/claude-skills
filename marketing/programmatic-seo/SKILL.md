# Programmatic SEO Skill

## Overview

Programmatic SEO (pSEO) is the automated generation of high-volume, data-driven landing pages optimized for search visibility. This skill provides a structured framework for designing, implementing, and maintaining pSEO systems that balance search intent, data quality, user experience, and technical SEO best practices.

**When to use this skill:** Building data-driven page templates, implementing dynamic content pipelines, optimizing crawlability, designing comparison matrices, creating glossaries or directories.

**Cross-skill dependencies:**
- **Upstream:** `content-strategy` (audience mapping, keyword research), `seo-audit` (technical baseline, indexability checks)
- **Downstream:** `schema-markup` (JSON-LD generation, rich snippets), `analytics` (tracking pSEO performance)

---

## 1. Context Sync Protocol

Before designing any pSEO system, synchronize project context from two authoritative sources:

### 1.1 Read Product-Marketing Context

File: `.claude/product-marketing-context.md`

Extract:
- **Target personas:** Who are the searchers? (e.g., "B2B SaaS buyers", "DIY home repair enthusiasts")
- **Value proposition:** Core differentiation vs competitors
- **Conversion goals:** Primary (signup, trial, demo) vs secondary (content engagement, email capture)
- **Brand voice guidelines:** Tone (formal, casual, playful), vocabulary preferences
- **Competitive positioning:** 2-3 top competitors and their pSEO strategies
- **Messaging pillars:** 3-5 key claims to reinforce across pages

### 1.2 Read Tech Context

File: `.claude/tech-context.md`

Extract:
- **Data availability:** What database tables, APIs, or external sources feed page content?
- **Performance constraints:** Max query time for page generation (typically <500ms for CDN cache-ability)
- **Existing taxonomy:** Category hierarchies, tag systems, product classifications
- **Infrastructure:** CMS, headless framework, database (Supabase, Postgres, etc.)
- **SEO tooling:** GA4 property ID, GSC verification method, rank tracking tool
- **Budget constraints:** Crawl quota, CDN bandwidth, third-party API costs

### 1.3 Context Sync Checklist

Before proceeding to page design:

```
[ ] Product-Marketing Context file exists and is current (updated <30 days ago)
[ ] Tech Context file exists and data sources are documented
[ ] Conversion goals are aligned across marketing and product teams
[ ] Performance SLA confirmed (page generation time budget)
[ ] Data schema reviewed for completeness and quality
[ ] Indexing strategy (all pages? segmented by popularity?) defined
[ ] Budget allocation for content creation, tooling, and maintenance approved
```

---

## 2. Decision Tree: Selecting Page Type & Architecture

Use this decision tree to determine the optimal pSEO page template and data source strategy:

```
START: What search intent are you targeting?

├─ COMPARISON / VERSUS
│  ├─ Data source: Product DB + user reviews + pricing API
│  ├─ Template: [Product A] vs [Product B]
│  ├─ Example: "Figma vs Sketch", "Python vs JavaScript"
│  ├─ Unique requirement: Side-by-side comparison matrix
│  ├─ Conversion path: Feature comparison → Product trial → Signup
│  └─ Implementation: See Section 8.2
│
├─ DIRECTORY / LISTING
│  ├─ Data source: Category tables + aggregated metrics
│  ├─ Template: [Category] listings (e.g., "Best [X] in [Location]")
│  ├─ Example: "Best React Developers in San Francisco", "Top 100 Startups"
│  ├─ Unique requirement: Faceted filtering, pagination, sort options
│  ├─ Conversion path: Listing page → Profile view → Contact unlock → Signup
│  └─ Implementation: See Section 8.3
│
├─ GLOSSARY / EXPLAINER
│  ├─ Data source: Content DB + external API (e.g., Wikipedia, domain-specific corpus)
│  ├─ Template: [Term] definition + context + related terms
│  ├─ Example: "What is Smart Contract?", "Guide to Kubernetes"
│  ├─ Unique requirement: Semantic linking, related term clusters
│  ├─ Conversion path: Definition → Educational content → Tools → Signup
│  └─ Implementation: See Section 8.4
│
├─ TEMPLATE PAGE (Location / Category / Attribute)
│  ├─ Data source: Master data tables + computed metrics
│  ├─ Template: [Location/Category] landing (e.g., "[City] Tech Jobs", "[Framework] Tutorials")
│  ├─ Example: "React Jobs in New York", "Remote UX Designer Positions"
│  ├─ Unique requirement: Geo-targeting, facet optimization, high conversion intent
│  ├─ Conversion path: Landing page → Filtered results → Application → Signup
│  └─ Implementation: See Section 8.1
│
└─ AGGREGATE / INSIGHT PAGE
   ├─ Data source: Analytics DB + time-series metrics
   ├─ Template: Trends, rankings, statistics (e.g., "Best [Category] 2026")
   ├─ Example: "Top 50 React Developers by GitHub Stars", "Q1 2026 Tech Hiring Trends"
   ├─ Unique requirement: Freshness mechanism, time-series data, leaderboard UX
   ├─ Conversion path: Insights → Profile exploration → Contact request → Signup
   └─ Implementation: See Section 8.5
```

**Decision factors:**
- **Search volume:** High volume (>500/mo) → Template pages; Lower volume (<100/mo) → Glossary/Explainer
- **Update frequency:** Daily changes → Aggregate pages with CDN cache invalidation; Static → Template pages with weekly refreshes
- **Data complexity:** Requires joins across 3+ tables → Aggregate; Simple lookups → Template/Directory
- **User intent:** Comparison → Versus; Discovery → Directory; Learning → Glossary; Action → Template

---

## 3. Quality Rubric: Scoring pSEO Pages

Every pSEO page should be evaluated against this rubric (0-5 scale per dimension, target ≥4.0):

### 3.1 Uniqueness & Differentiation (Weight: 25%)

| Score | Signal |
|-------|--------|
| **5** | Content answers query competitors don't; includes proprietary data (e.g., internal API benchmarks, exclusive interviews) |
| **4** | Page covers main topic comprehensively; adds 1-2 unique angles (e.g., local data, ROI calculator) |
| **3** | Page is standard template; covers topic adequately but not exceptionally |
| **2** | Thin content; mostly template with minimal customization |
| **1** | Duplicate of competitor page or other internal pages |

**Quality gates:**
- Competitor content analysis: Page should rank in top 5 unique insights vs top 3 search results
- Word count: 1,800-3,500 words (templates); 500-1,000 words (glossary entries)
- Proprietary data: ≥1 unique dataset, statistic, or insight per page

### 3.2 Data Quality (Weight: 25%)

| Score | Signal |
|-------|--------|
| **5** | Data verified against authoritative source; updated within past 7 days; error rate <0.1% |
| **4** | Data from reliable internal DB; updated within 30 days; spot-checked accuracy |
| **3** | Data mostly accurate; some inconsistencies; updated quarterly |
| **2** | Data sourced from external API with no freshness control; occasional errors |
| **1** | Data stale, unreliable, or unverified |

**Quality gates:**
- Data source documentation: Every stat/claim must cite source with publication date
- Validation pipeline: Automated checks for null values, outliers, schema compliance
- Freshness SLA: Template pages ≤30 days old; Aggregate pages ≤7 days old

### 3.3 Internal Linking Strategy (Weight: 20%)

| Score | Signal |
|-------|--------|
| **5** | 8-15 contextual internal links; links use target keywords as anchor text; deep links to conversion funnels |
| **4** | 5-8 relevant internal links; mix of branded and keyword anchors; links to related pages |
| **3** | 3-5 internal links; some generic anchors ("learn more"); links to homepage/main category |
| **2** | 1-2 internal links; mostly navigation links, no contextual linking |
| **1** | No internal links or only footer navigation |

**Linking architecture pattern:**
```
Template Page (e.g., "React Jobs in SF")
  ├─ Related categories: "React Jobs in NYC", "React Tutorials" (top 2)
  ├─ Conversion funnel: "How to Hire React Developers", "React Developer Salary" (mid-content)
  ├─ Related glossary: "What is React?", "Fiber Architecture" (bottom)
  └─ CTA: "Browse all locations" (footer)
```

### 3.4 Indexability & Technical SEO (Weight: 15%)

| Score | Signal |
|-------|--------|
| **5** | Mobile-optimized (<3s LCP); structured data (schema); proper canonicals; sitemap inclusion |
| **4** | Fast mobile experience; schema present; canonical set; in sitemap |
| **3** | Mobile-friendly; basic schema; canonical present; sitemap may be incomplete |
| **2** | Slow mobile; missing schema; canonical issues; not in sitemap |
| **1** | Mobile broken; robots.txt blocks; noindex tag; duplicate canonicals |

**Technical gates:**
- Page Speed: LCP <2.5s, CLS <0.1, FID <100ms (Core Web Vitals)
- Schema markup: Use `BreadcrumbList`, `Article`, `Product`, or `FAQPage` as appropriate
- Mobile: Responsive design, touch-friendly CTAs, readable font sizes

### 3.5 Conversion Path Clarity (Weight: 15%)

| Score | Signal |
|-------|--------|
| **5** | Clear CTA hierarchy; 3+ conversion options (signup, demo, contact); analytics tracked |
| **4** | Primary + secondary CTA; conversion funnel optimized; tracked in GA4 |
| **3** | Basic CTA present; conversion goal defined; may lack secondary options |
| **2** | CTA unclear or generic; minimal conversion optimization |
| **1** | No CTA or conversion intent |

**Conversion architecture:**
```
Top of page: Hero CTA (primary: "Join as [X]")
Mid-content: Feature showcase CTA (secondary: "See profiles")
Bottom: Email signup or demo request
Exit intent: Modal with value prop + email capture
```

---

## 4. Anti-Pattern References

Avoid these common pSEO mistakes that hurt SEO and UX:

### 4.1 Data Quality Anti-Patterns

| Anti-Pattern | Impact | Fix |
|--------------|--------|-----|
| **Stale data unchanged for 3+ months** | CTR drops 15-25% when users encounter outdated info; trust signal degrades | Implement automated data freshness monitoring; set SLA ≤30 days; flag stale pages in GSC |
| **Duplicate content across pages** | Google penalizes with rel=canonical confusion; pages cannibalize each other's rankings | Ensure ≥80% unique content per template instance; use faceted parameters (e.g., `?location=sf&role=senior`) |
| **Null/missing values visible to users** | "n/a", blank cells, or "TBD" frustrate users; reduce dwell time | Implement conditional rendering; hide sections with <50% data coverage; use placeholders sparingly |
| **Unattributed or fake data** | User trust erodes; potential legal liability for false claims | Every stat must cite source + date; use confidence scores for estimates; disclose methodology |

### 4.2 Template Design Anti-Patterns

| Anti-Pattern | Impact | Fix |
|--------------|--------|-----|
| **Over-parameterized URLs** | `?location=sf&role=senior&level=5&salary=120k&...` creates crawl bloat; Googlebot wastes budget on parameter combinations | Limit URL parameters to 2-3 primary facets; use hash-based filtering for UI interactivity; consolidate parameter values |
| **Template pages without UVP differentiation** | All pages read identically; no semantic difference between "[City] Jobs" pages; CTR flatlines | Customize intro paragraph, hero image, or call-out stats per page; use geo/category-specific language |
| **Missing H1 or multiple H1s** | Search engines struggle to determine page topic; CTR and ranking suffer | Exactly 1 H1 per page; should include primary keyword; structure headings H1→H2→H3 hierarchy |
| **"Thin" landing pages (<500 words, no context)** | Low time-on-page; high bounce rate; fails to build topical authority | Minimum 1,500 words per template; include context sections (e.g., market overview, hiring trends); add interactive elements |

### 4.3 Conversion Anti-Patterns

| Anti-Pattern | Impact | Fix |
|--------------|--------|-----|
| **CTA button only at bottom** | Users leave before scrolling; low conversion; no exit-intent capture | Place CTA sticky header, mid-content, and bottom; use exit-intent modal; vary messaging |
| **Generic CTA text ("Click here", "Learn more")** | Low intent signal; reduces CTR by 30-40% vs keyword-rich CTAs | Use action verbs + value: "Find React Developers", "Browse 250+ Candidates", "Start Hiring Today" |
| **Friction in signup flow** | Multi-step forms reduce conversion by 50%+ per additional field | Max 3 fields on first form; use progressive profiling (ask questions post-signup) |
| **No mobile-specific CTA** | Mobile users can't interact; conversion drops on phones | Use sticky mobile footer CTA; tap-friendly buttons (≥44px); SMS/WhatsApp options for B2C |

### 4.4 SEO Anti-Patterns

| Anti-Pattern | Impact | Fix |
|--------------|--------|-----|
| **Keyword stuffing in template** | Google flags as spam; manual action penalty risk | Keyword density 0.5-2%; use semantic variations and LSI keywords; prioritize user readability |
| **All pages orphaned (no internal linking)** | Pages don't receive link equity; low indexing rate | Map internal link topology; prioritize links from high-authority pages; use breadcrumbs |
| **Robots.txt blocks pSEO subdirectory** | Entire pSEO section unindexed despite GSC approval | Verify robots.txt allows `/talent/`, `/jobs/`, etc.; use GSC to explicitly request indexing |
| **No structured data** | Google can't distinguish page type; rich snippets unavailable | Add schema: `Article` (how-tos), `BreadcrumbList` (navigation), `Product` (comparisons), `FAQPage` (glossaries) |

---

## 5. Industry Variations

pSEO strategies differ significantly by vertical. Customize approach based on industry:

### 5.1 SaaS & B2B Tech

**Persona:** Technical decision-makers, CIOs, developers
**Primary intent:** Problem-solution matching, vendor evaluation, pricing comparison
**Key page types:**
- Comparison: "[Our product] vs [Competitor]", "Top 5 [Solutions] for [Use case]"
- Directory: "Best [Tool type] for [Company size/Industry]"
- Glossary: Technical definitions ("What is API Gateway?")

**Data sources:** Product DB, pricing APIs, user reviews, GitHub stars
**Content style:** Technical depth, ROI calculators, case studies
**Conversion:** Free trial, feature demo, pricing contact
**Update frequency:** Weekly (pricing changes), daily (competitor comparisons)

### 5.2 E-Commerce & Retail

**Persona:** Price-conscious buyers, comparison shoppers, trend-seekers
**Primary intent:** Product discovery, deal hunting, category exploration
**Key page types:**
- Directory: "Best [Product type] under $[price]", "[Category] for [use case]"
- Comparison: "[Brand A] vs [Brand B]", "Pro/con lists"
- Aggregate: "Top trending [category]", "[Category] sales rankings"

**Data sources:** Product catalog, pricing feeds, review aggregators, sales data
**Content style:** Buyer-friendly, listicles, trend reports, "best of" curated content
**Conversion:** Add-to-cart, affiliate links, email signup for deals
**Update frequency:** Daily (prices, stock); real-time (trending)

### 5.3 Professional Services & Talent

**Persona:** Job seekers, recruiters, freelance clients
**Primary intent:** Talent discovery, skill matching, market rate research
**Key page types:**
- Directory: "Top [skill] professionals in [location]", "[Specialization] for hire"
- Template: "[Skill] jobs in [location]", "[Role] salary guide"
- Aggregate: "2026 hiring trends", "Skill demand rankings"

**Data sources:** Application DB, profile data, salary surveys, hiring metrics
**Content style:** Transparent, data-driven, empowering
**Conversion:** Profile views, contact unlock, job applications, platform signup
**Update frequency:** Real-time (new candidates); weekly (trend reports)

### 5.4 Local Services & Directories

**Persona:** Local searchers, service buyers, community members
**Primary intent:** Local discovery, service comparison, review reading
**Key page types:**
- Directory: "[Service type] near [location]", "[Service] reviews in [city]"
- Template: "[Service type] in [neighborhood]", "[Category] experts by rating"
- Glossary: Local terminology, service explanations

**Data sources:** Google My Business, local listings, review APIs, location data
**Content style:** Conversational, community-focused, review-driven
**Conversion:** Direct calls, appointment booking, map clicks
**Update frequency:** Real-time (new businesses); weekly (reviews, ratings)

### 5.5 Publishing & Content Media

**Persona:** Information seekers, researchers, learners
**Primary intent:** Topic exploration, education, thought leadership
**Key page types:**
- Glossary: Comprehensive definitions with multimedia
- Aggregate: "Definitive guides to [topic]", "Expert roundups"
- Directory: "[Topic] resources", "Top [topic] writers/publications"

**Data sources:** Content DB, expert interviews, external data sources, historical archives
**Content style:** Authoritative, comprehensive, multimedia-rich
**Conversion:** Email signup, subscription, content consumption
**Update frequency:** Weekly (new content); evergreen updates (refreshes)

---

## 6. Benchmark References: SEO Time-to-Rank

Understand realistic timelines for pSEO page indexing and ranking:

### 6.1 Crawl & Indexing Timeline

| Scenario | Time to Index | Time to Rank (Top 50) |
|----------|---------------|-----------------------|
| **High-authority domain, new pSEO section, >500K backlinks** | 1-3 days | 2-4 weeks |
| **Established domain, pSEO subsection, 50-500K backlinks** | 3-7 days | 4-12 weeks |
| **Newer domain (<2 years), pSEO launch, <50K backlinks** | 2-4 weeks | 12-24 weeks |
| **Subdomain or new TLD (rare)** | 2-8 weeks | 24+ weeks |

**Acceleration tactics:**
- XML sitemap submission to GSC (indexes 40% faster)
- Internal linking from high-authority pages (5x crawl acceleration)
- External backlinks (if domain-level, can reduce time by 50%)
- Structured data (schema.org markup signals importance to Googlebot)

### 6.2 Ranking Velocity by Page Type

| Page Type | Avg. Time to Top 20 | Key Ranking Factor |
|-----------|--------------------|--------------------|
| **Template pages (location/category)** | 6-8 weeks | Content length, internal links, local signals |
| **Comparison pages** | 8-12 weeks | Uniqueness, data recency, brand mentions |
| **Directory/listing pages** | 4-6 weeks | Breadth (item count), freshness, structured data |
| **Glossary/explainer pages** | 12-16 weeks | Semantic depth, backlinks, authority |
| **Aggregate/trend pages** | 2-4 weeks | Newness, data exclusivity, media mentions |

**Key insight:** Aggregate pages rank fastest because search engines favor fresh content; glossary pages rank slowest because they compete with Wikipedia and established references.

### 6.3 Keyword Difficulty & Expected Ranking

| Keyword Difficulty | Volume | Avg. Ranking Position (Weeks) |
|-------------------|--------|--------------------------------|
| **Easy** (0-20 difficulty) | <100/mo | Position 1-5 (2-4 weeks) |
| **Medium** (20-50 difficulty) | 100-500/mo | Position 5-15 (6-10 weeks) |
| **Hard** (50-80 difficulty) | 500-5K/mo | Position 15-30 (12-20 weeks) |
| **Very Hard** (80-100 difficulty) | 5K+/mo | Position 30-50+ (20+ weeks) |

**Strategy:** Prioritize medium-difficulty keywords for fastest ROI; use glossary pages for high-difficulty keywords to build topical authority.

---

## 7. Council Integration Hook

Integrate this skill with your organization's content governance via the **Council system**:

### 7.1 Council Approvals Required

Before launching pSEO sections, get sign-off from:

```
COUNCIL_pSEO_LAUNCH
├─ Content Strategy Lead: "Does keyword mix align with brand strategy?"
├─ SEO Specialist: "Are there canonical/crawl budget issues?"
├─ Product Manager: "Are conversion funnels correct?"
├─ Legal/Privacy: "Do we own all data? Are sources properly attributed?"
└─ Analytics: "Are GA4 events tracking properly?"
```

### 7.2 Council Quality Gates

Every pSEO page must pass Council's Quality Rubric (Section 3) before publication:

```yaml
qualityGate:
  uniqueness: 4.0+       # ≥4 unique angles vs competitors
  dataQuality: 4.5+      # ≥4.5 verified data, <7 days old
  internalLinking: 4.0+  # ≥4 contextual internal links
  indexability: 4.0+     # ≥4 Core Web Vitals compliance
  conversionPath: 4.0+   # ≥4 clear CTA hierarchy
  overallScore: 4.2+     # Minimum 4.2 average across all dimensions
```

### 7.3 Council Feedback Workflow

1. **Submit:** Create pSEO page in staging; generate audit report (Section 7.4)
2. **Review:** Council members score page against Quality Rubric (5 days)
3. **Iterate:** Address feedback; re-submit until all dimensions ≥4.0
4. **Approve:** Council lead signs off; page moves to production
5. **Monitor:** Track performance weekly; escalate if scoring drops <3.5

### 7.4 Council Audit Report Template

```markdown
## pSEO Page Audit Report

**Page:** [URL] | **Template:** [Type] | **Created:** [Date]

### Quality Scores
- Uniqueness: 4.2/5.0 ✓
- Data Quality: 4.1/5.0 ✓
- Internal Linking: 3.8/5.0 ⚠️
- Indexability: 4.5/5.0 ✓
- Conversion Path: 4.0/5.0 ✓
- **Overall: 4.1/5.0 ✓**

### Recommendations
1. Add 2 more internal links to conversion funnel (currently at 3)
2. Verify data source freshness (last updated [date])
3. Consider adding comparison matrix vs top 2 competitors

### Council Decision
- [ ] Approve (all dimensions ≥4.0)
- [ ] Conditional Approve (with revisions)
- [ ] Reject (major issues; resubmit after revision)

**Approver:** [Name] | **Date:** [Date]
```

---

## 8. Template Architecture Patterns

Implement pSEO with these five proven page templates. Each includes data model, URL structure, and content outline.

### 8.1 Template Page: Location/Category Landing

**Example:** "React Jobs in San Francisco", "Remote UX Designer Positions"

**URL structure:** `/talent/[skill]/[location]` or `/jobs/[category]/[region]`

**Data model:**
```sql
CREATE TABLE pSEO_talent_pages (
  id UUID PRIMARY KEY,
  skill_id UUID REFERENCES skills(id),
  location_id UUID REFERENCES locations(id),
  title TEXT,
  meta_description TEXT,
  keyword_target TEXT,
  candidate_count INT,
  avg_salary DECIMAL,
  avg_experience INT,
  top_companies TEXT[],
  market_snapshot JSONB,  -- {"hiring_trend": "+15%", "avg_response_time": "2h"}
  last_updated TIMESTAMP
);
```

**Content outline:**
```
1. Hero Section (200 words)
   - Keyword-rich headline: "[Skill] Jobs in [Location]"
   - Snapshot stats: "250+ [Skill] jobs | Avg salary $[X]K | [Y]% hiring growth"
   - CTA: "Start hiring" / "Apply now"

2. Market Overview (400 words)
   - Hiring trends (supply/demand)
   - Salary ranges (entry/mid/senior)
   - Top companies hiring in location
   - Skills most in demand

3. How to Hire / Application Process (300 words)
   - For recruiters: "3-step hiring process"
   - For candidates: "How to get hired as [skill]"
   - Timeline expectations

4. Candidate Showcase (200 words + cards)
   - Feature 3-5 top-rated candidates
   - Brief bio, skills, availability
   - CTA: "View all [Skill] candidates in [Location]"

5. FAQ (300 words)
   - "What's the average salary for [skill] in [location]?"
   - "How long does it take to hire a [skill]?"
   - "What skills do I need for [role]?"

6. Related Pages (50 words)
   - Internal links: "React Jobs in NYC", "React Tutorials"
   - CTA: "Browse other locations / skills"
```

**Update frequency:** Weekly (candidate count, salary, companies); monthly (market trends)

**Example implementation:**
```typescript
// Generate page at build time or on-demand
export async function generatePSEOPage(skill: string, location: string) {
  const data = await getPSEOData(skill, location);
  
  return {
    title: `${skill} Jobs in ${location} | [Platform]`,
    description: `${data.candidateCount}+ ${skill} professionals hiring in ${location}. Avg salary $${data.avgSalary}K.`,
    content: renderTemplate('talent-landing', {
      skill,
      location,
      candidates: data.topCandidates,
      marketSnapshot: data.marketSnapshot,
      faqs: generateFAQsForPage(skill, location),
    }),
    canonical: `/talent/${slugify(skill)}/${slugify(location)}`,
  };
}
```

---

### 8.2 Template Page: Comparison / Versus

**Example:** "Figma vs Sketch", "Python vs JavaScript for Web Development"

**URL structure:** `/compare/[product-a]-vs-[product-b]` or `/versus/[option-1]/[option-2]`

**Data model:**
```sql
CREATE TABLE pSEO_comparison_pages (
  id UUID PRIMARY KEY,
  subject_a_id UUID REFERENCES products(id),
  subject_b_id UUID REFERENCES products(id),
  comparison_matrix JSONB,  -- { "feature": [val_a, val_b], ... }
  user_sentiment JSONB,     -- { "votes_a": 1250, "votes_b": 980 }
  last_updated TIMESTAMP,
  views INT DEFAULT 0,
  conversions INT DEFAULT 0
);

CREATE TABLE comparison_criteria (
  id UUID PRIMARY KEY,
  category TEXT,  -- "Pricing", "Features", "Performance"
  metric TEXT,    -- "Starting price", "Max team size"
  weight INT      -- Influence on ranking
);
```

**Content outline:**
```
1. Hero Section (100 words)
   - Headline: "[Option A] vs [Option B]: Detailed Comparison"
   - Subheading: "Which is better for [use case]?"

2. Quick Comparison Table (interactive)
   - 8-12 key criteria side-by-side
   - Color coding (winner, neutral, loser)
   - Row-level CTA buttons ("See more")

3. Detailed Breakdowns (2,000+ words, 5-7 sections)
   - Pricing comparison (with calculator)
   - Feature comparison (pros/cons per option)
   - Performance benchmarks
   - Learning curve / ease of use
   - Integrations & ecosystem
   - Customer support & community

4. User Verdict (300 words)
   - Real user reviews aggregated
   - Sentiment breakdown (% favor A vs B)
   - Use case recommendations ("Choose A if...", "Choose B if...")

5. Frequently Asked Comparisons (FAQ)
   - "Can I migrate from A to B?"
   - "Which is cheaper in the long run?"
   - "Is one better for enterprise?"

6. Related Comparisons
   - "X vs Z", "Y vs Z"
   - Adjacent tool categories
```

**Update frequency:** Weekly (pricing changes, reviews); monthly (feature updates)

**Key UX patterns:**
- Sticky header with toggle between table view and card view
- Filtering by criteria (show only pricing, feature set, performance)
- User rating toggle (show only top/bottom-rated aspects)
- Export comparison as PDF

---

### 8.3 Template Page: Directory / Listing

**Example:** "Top 100 React Developers in San Francisco", "Best SaaS Tools for Startups"

**URL structure:** `/directory/[category]` or `/browse/[category]?facets=[...]`

**Data model:**
```sql
CREATE TABLE pSEO_directory_pages (
  id UUID PRIMARY KEY,
  category_id UUID REFERENCES categories(id),
  location_id UUID REFERENCES locations(id),  -- Optional
  filter_facets JSONB,  -- {"skill": ["React", "Vue"], "level": ["senior"], "salary": "100-150k"}
  item_count INT,
  last_updated TIMESTAMP,
  featured_items UUID[],  -- First 5 items always featured
  created_at TIMESTAMP
);
```

**Content outline:**
```
1. Hero Section (150 words)
   - Headline: "Browse [Category] in [Location]"
   - Faceted filter UI (checkboxes for skill, level, salary, etc.)
   - Sorting options (rating, experience, availability, cost)

2. Result Stats (50 words)
   - "[Number] [category] found matching your criteria"
   - "Refine results: [active filters]"

3. Item Cards (20-50 per page, paginated)
   - Featured badge (first 5-10 items)
   - Image, name, headline, rating
   - 3 key attributes (skill, location, availability)
   - CTA button (View profile, Contact, Save)

4. Pagination / Load More
   - Page 1: Items 1-20
   - "Load more" infinite scroll or pagination
   - Jump to page X

5. Sidebar Filters (repeated on scroll)
   - Skills (checkbox tree)
   - Location (map or list)
   - Experience level (slider)
   - Availability (toggle)
   - Rating (star filter)
   - Cost / Salary (range slider)

6. SEO Content Block (300 words, below fold)
   - Context: "Why hire from this category?", market stats
   - "How to choose the right [item type]?"
   - Related categories & links

7. FAQ
   - "How do I filter by [facet]?"
   - "How many [items] are available?"
```

**Update frequency:** Real-time (facet counts); daily (featured items rotation)

**Facet optimization strategy:**
- Max 6-8 facets (too many confuse users)
- Sort facets by popularity (most-searched first)
- Show facet counts (`Skill: React (450)`)
- Lazy-load facet values (show top 10, "show more")

---

### 8.4 Template Page: Glossary / Definition

**Example:** "What is Kubernetes? A Developer's Guide", "Smart Contracts Explained"

**URL structure:** `/glossary/[term]` or `/learn/[topic]/definition`

**Data model:**
```sql
CREATE TABLE pSEO_glossary_pages (
  id UUID PRIMARY KEY,
  term TEXT UNIQUE,
  slug TEXT UNIQUE,
  definition_short TEXT,  -- <150 words
  content_full TEXT,       -- 1,000-2,000 words
  related_terms UUID[],    -- Links to 5-10 related glossary pages
  use_cases TEXT[],        -- Real-world application examples
  external_references JSONB, -- [{"source": "Wikipedia", "url": "..."}]
  difficulty_level TEXT,   -- "Beginner", "Intermediate", "Advanced"
  last_updated TIMESTAMP,
  view_count INT DEFAULT 0,
  bounce_rate DECIMAL      -- Aggregated metric
);
```

**Content outline:**
```
1. Hero Definition (100 words)
   - Headline: "What is [Term]?"
   - One-sentence TL;DR in highlighted box
   - Context: "Key concept in [domain]"

2. Simple Explanation (300 words)
   - Use analogy to familiar concept
   - Break down into digestible parts
   - Avoid jargon; define complex terms inline

3. Technical Deep Dive (600-800 words, 3-4 subsections)
   - How it works (architecture, process, components)
   - History / evolution (when was it created, why?)
   - Key use cases (where is it applied?)
   - Pros and cons (when to use / not use)

4. Real-World Examples (400 words)
   - 2-3 concrete examples with context
   - Code snippet if applicable (syntax highlighted)
   - Link to tool/framework that uses it

5. Related Concepts (200 words)
   - Define 3-5 closely related terms
   - Show hierarchical relationship ("Parent concept: X", "Sub-concept: Y")
   - Each with inline link to glossary page

6. Interactive Component (optional)
   - Explainer video or diagram
   - Interactive tool (calculator, simulator, quiz)

7. FAQ
   - "How does [term] differ from [similar term]?"
   - "When should I use [term]?"

8. Further Learning (200 words)
   - Recommended tutorials, courses, docs
   - Books, YouTube channels
   - Communities, forums
```

**Update frequency:** Quarterly (content reviews); on-demand (term popularity)

**Glossary UX patterns:**
- Floating "Related Terms" sidebar (sticky on scroll)
- Breadcrumb: "Home > Technology > [Category] > [Term]"
- "Define any term" inline widget (hover tooltip definitions)
- Related pages at bottom with preview cards

---

### 8.5 Template Page: Aggregate / Insight / Trend

**Example:** "Top 50 React Developers by GitHub Stars", "Q1 2026 Tech Hiring Trends"

**URL structure:** `/insights/[trend-topic]` or `/rankings/[category]/[time-period]`

**Data model:**
```sql
CREATE TABLE pSEO_aggregate_pages (
  id UUID PRIMARY KEY,
  title TEXT,
  topic TEXT,
  time_period TEXT,  -- "Q1 2026", "2025", "YTD"
  snapshot_date TIMESTAMP,
  data_source JSONB,  -- {"tables": ["candidates"], "aggregation": "GROUP BY skill"}
  rankings JSONB,     -- [{"rank": 1, "item": "React", "metric": 5000}]
  is_recurring BOOLEAN,  -- True = regenerate on schedule
  recurrence INTERVAL,   -- "1 month", "1 week"
  last_generated TIMESTAMP,
  next_generation TIMESTAMP
);
```

**Content outline:**
```
1. Hero Section (150 words)
   - Headline: "Top [N] [Topic] in [Time Period]"
   - Snapshot stats: "[Item] leads with [metric]", "Growth: +[X]% YoY"
   - Publication date: "Last updated: [date]"
   - Note: "Methodology: [brief explanation]"

2. Methodology Section (200 words, collapsible)
   - Data sources (databases, APIs, external data)
   - Metrics definition (how was scoring done?)
   - Time period (date range included)
   - Limitations & disclaimers

3. Top 10 Highlight (500 words, visual)
   - Podium: #1, #2, #3 (card-based, visual badges)
   - #4-10 compact list with mini cards
   - Key insight per top item

4. Full Rankings (2,000 words)
   - Interactive table/list (sortable, filterable)
   - Rank | Item | Primary Metric | Secondary Metric | Change YoY
   - Pagination or infinite scroll (#1-50, then #51-100)

5. Trend Analysis (600 words, 3-4 charts)
   - Year-over-year growth chart
   - Skill demand distribution (pie/bar chart)
   - Rising stars (biggest movers)
   - Market insights (Why did X rise? Why did Y fall?)

6. Category Breakdowns (optional)
   - Segment by geography, company size, industry
   - Separate top 10 lists per segment

7. Related Rankings & Trends
   - "Top [Category 2] in [Time]"
   - "Rising skills in [Industry]"

8. Download / Share
   - "Download full rankings as CSV/PDF"
   - Share buttons (Twitter, LinkedIn, email)
```

**Update frequency:** Weekly for fast-moving trends; monthly for stable rankings; automated regeneration for recurring insights

**Key metrics to highlight:**
- Rank movement (↑5, ↓3, = unchanged)
- YoY change percentage
- Confidence score (if data is estimated)
- Related segments (if searchable by geography, company size, etc.)

---

## 9. Data Pipeline Design for Dynamic Content

Implement a robust data pipeline to keep pSEO pages fresh and accurate:

### 9.1 Data Architecture

```
Data Sources
    ├─ Internal DB (PostgreSQL/Supabase)
    ├─ APIs (external data providers)
    └─ User-Generated Data (reviews, ratings)
           ↓
    [Data Ingestion Layer]
    ├─ ETL jobs (daily/hourly batch)
    ├─ Real-time webhooks (events)
    └─ Scheduled syncs (3rd-party APIs)
           ↓
    [Data Transformation]
    ├─ Aggregations (COUNT, AVG, SUM)
    ├─ Enrichment (combine multiple sources)
    ├─ Validation (schema, quality checks)
    └─ Deduplication (handle duplicates)
           ↓
    [pSEO Content Layer]
    ├─ Cache layer (Redis, CDN)
    ├─ Template rendering (interpolate data)
    └─ Static generation (pre-build pages)
           ↓
    [Deployment]
    ├─ HTML pages (CDN + sitemap)
    ├─ Schema.org markup (JSON-LD)
    └─ Metadata (title, description, canonical)
```

### 9.2 Data Quality Checks

Implement automated validation before page rendering:

```typescript
interface DataQualityCheck {
  name: string;
  check: (data: any) => boolean;
  errorMessage: string;
  severity: 'WARN' | 'ERROR' | 'CRITICAL';
  action: 'PUBLISH' | 'HOLD' | 'REJECT';
}

const pSEOQualityChecks: DataQualityCheck[] = [
  {
    name: 'No null values in key fields',
    check: (data) => !hasNullInKeyFields(data),
    errorMessage: 'Missing required data: name, rating, or location',
    severity: 'CRITICAL',
    action: 'REJECT',
  },
  {
    name: 'Data freshness (<30 days)',
    check: (data) => isPast30DaysOld(data.lastUpdated),
    errorMessage: 'Data older than 30 days',
    severity: 'WARN',
    action: 'PUBLISH',  // Warn but allow
  },
  {
    name: 'Minimum content length (1,500 words)',
    check: (data) => countWords(data.content) >= 1500,
    errorMessage: 'Page content too thin',
    severity: 'ERROR',
    action: 'HOLD',
  },
  {
    name: 'Valid structured data (schema)',
    check: (data) => validateSchema(data.schema),
    errorMessage: 'Invalid JSON-LD schema',
    severity: 'ERROR',
    action: 'HOLD',
  },
];
```

### 9.3 Update Frequency Strategy

| Page Type | Data Freshness SLA | Update Trigger | Implementation |
|-----------|-------------------|-----------------|-----------------|
| **Template pages** | ≤30 days | Daily batch job at 2 AM | Cron + Cloud Function |
| **Comparison pages** | ≤7 days | Weekly + event-driven (price change) | Scheduled + Webhook |
| **Directory/listing** | Real-time | On item creation/update | Event stream + Cache invalidation |
| **Glossary pages** | ≤90 days | Monthly review cycle | Quarterly batch review |
| **Aggregate/trend pages** | ≤24 hours | Daily recompute if >2% change | Nightly batch + threshold trigger |

### 9.4 Cache Strategy

```typescript
// Redis cache with TTL based on page type
const cacheConfig = {
  'template-pages': { ttl: 86400, invalidateOn: ['item_updated', 'item_deleted'] },
  'comparison-pages': { ttl: 604800, invalidateOn: ['price_changed'] },
  'directory-pages': { ttl: 3600, invalidateOn: ['item_added', 'item_removed', 'filter_facet_changed'] },
  'glossary-pages': { ttl: 2592000, invalidateOn: ['content_updated'] },
  'aggregate-pages': { ttl: 86400, invalidateOn: ['ranking_recalculated'] },
};

// On data change
async function invalidateCache(pageType: string, dataId: string) {
  const config = cacheConfig[pageType];
  if (!config) return;
  
  // Invalidate cache entries matching this data
  const keys = await redis.keys(`${pageType}:*:${dataId}`);
  if (keys.length > 0) await redis.del(...keys);
  
  // Trigger page regeneration (if static site)
  if (pageType === 'template-pages') {
    await triggerPageBuild(pageType, dataId);
  }
}
```

### 9.5 Monitoring & Alerting

Track pSEO health metrics:

```typescript
interface pSEOMetrics {
  totalPages: number;
  averagePageScore: number;  // From Quality Rubric (Section 3)
  pagesWithStaleData: number; // Data >SLA days old
  crawlBudgetUsed: number;    // % of crawl budget
  averagePageLoadTime: number; // LCP metric
  conversionRate: number;     // CTR to signup/contact
  bounceRate: number;
  averageSEOTraffic: number;  // Monthly sessions
}

// Alerting thresholds
const alerts = [
  { metric: 'averagePageScore', threshold: 3.5, severity: 'WARN' },
  { metric: 'pagesWithStaleData', threshold: 10, severity: 'ERROR' },
  { metric: 'averagePageLoadTime', threshold: 2500, severity: 'WARN' },
  { metric: 'conversionRate', threshold: 0.5, severity: 'WARN' },
];
```

---

## 10. Quick Reference Checklist

Before launching any pSEO page:

```
[ ] Context sync complete (product-marketing context, tech context)
[ ] Page type selected via decision tree (Section 2)
[ ] Quality Rubric scores ≥4.0 in all dimensions (Section 3)
[ ] Anti-patterns reviewed and avoided (Section 4)
[ ] Template structure matches one of 5 templates (Section 8)
[ ] Data pipeline validated and tested (Section 9)
[ ] Internal linking strategy implemented (≥4 contextual links)
[ ] Structured data (schema.org) added to page
[ ] Mobile experience tested (LCP <2.5s, touch-friendly CTAs)
[ ] Conversion tracking configured in GA4
[ ] Canonical URL set and robots.txt verified
[ ] Page added to XML sitemap
[ ] Council quality audit passed (≥4.2 overall score)
[ ] Deploy to production with CDN cache headers
[ ] Monitor for 2 weeks; track rankings, traffic, conversions
[ ] Schedule quarterly review for content freshness
```

---

## Cross-Skill Dependencies

**Invoke before starting:**
- `content-strategy`: Keyword research, audience mapping, content calendar
- `seo-audit`: Technical baseline (Core Web Vitals, crawlability, indexability)

**Invoke during implementation:**
- `schema-markup`: Generate JSON-LD structured data for pages
- `analytics`: Set up GA4 event tracking for pSEO funnels

**Invoke after deployment:**
- `seo-audit`: Post-launch crawl audit, ranking verification
- `analytics`: Performance tracking, conversion funnel analysis

---

## Key Takeaways

1. **Sync context first** — Always read product-marketing and tech contexts before designing pSEO
2. **Use decision trees** — Let search intent, data complexity, and update frequency guide page type selection
3. **Score ruthlessly** — Apply Quality Rubric to every page; aim for ≥4.0 across all dimensions
4. **Avoid anti-patterns** — Stale data, thin content, poor linking, and conversion friction kill pSEO ROI
5. **Tailor to industry** — pSEO strategies differ by vertical (SaaS, e-commerce, talent, local, publishing)
6. **Monitor benchmarks** — Understand realistic timelines (2-4 weeks for easy keywords, 12-16 for glossaries)
7. **Implement robust pipelines** — Dynamic content requires automated data validation, caching, and freshness checks
8. **Align with Council** — Get governance sign-off before launch; track performance continuously
9. **Build for conversion** — Every page needs clear CTA hierarchy and conversion tracking
10. **Think long-term** — pSEO is compound growth; small improvements in data quality and content depth compound over months

---

## Revision History

- **v2.0** (2026-02-17): Added Context Sync Protocol, Decision Trees, Quality Rubric, Industry Variations, Benchmarks, Council Integration, 5 Template Patterns, Data Pipeline Architecture
- **v1.0**: Initial pSEO skill framework
```

This upgraded skill provides comprehensive guidance for enterprise programmatic SEO implementation with governance, quality controls, and industry-specific strategies.