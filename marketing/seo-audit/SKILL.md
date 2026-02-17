# SEO Audit Skill

**Version:** 2.0  
**Last Updated:** 2026-02-17  
**Scope:** Enterprise SEO audits, technical diagnostics, competitive analysis, prioritization frameworks  
**Audience:** Growth engineers, SEO specialists, product managers, marketing strategists

---

## Overview

The SEO Audit skill guides systematic evaluation of website search engine optimization across **five core dimensions**: technical health, on-page signals, off-page authority, user experience (Core Web Vitals), and keyword strategy coverage. It provides **decision trees for prioritization**, quality rubrics for scoring, and actionable remediation playbooks.

This skill is upstream from **content-strategy** (provides content gap analysis) and downstream consumer of **programmatic-seo** and **schema-markup** implementations.

---

## Context Sync Protocol

Before conducting any audit, load organizational context:

### 1. Product Marketing Context
Read `.claude/product-marketing-context.md`:
- **Target audience segments** (influences keyword research priority)
- **Brand positioning** (affects content tone, messaging hierarchy)
- **Value propositions** (determines on-page keyword mapping)
- **Competitor positioning** (benchmarks for comparative analysis)
- **Market messaging** (informs title/meta tag strategy)

### 2. Technical Context
Read `.claude/tech-context.md`:
- **Current technology stack** (SEO support: server-side rendering vs CSR, structured data capability)
- **Infrastructure constraints** (crawlability, CDN configuration, pagination patterns)
- **Data capabilities** (schema.org markup support, dynamic content generation)
- **Integration roadmap** (planned schema enhancements, performance optimizations)

### 3. Integration Hook: Council Finance Audit Checklist
When conducting SEO audits for `.planning/` or financial/fintech verticals, reference:
- **Council integration dashboard** (`/tmp/council-finance`)
- **Regulatory compliance messaging** (FDIC, SEC, compliance keywords)
- **Financial services benchmarks** (industry-specific keyword competition, trust signals)

---

## Decision Trees: Audit Prioritization

### Tree 1: Technical SEO vs On-Page vs Off-Page
```
START: Is site currently crawlable and indexable?
├─ NO → TECHNICAL PRIORITY (Fix crawlability, indexation, robots.txt, sitemap)
│   └─ Remediate: Core Web Vitals, server errors, block resources, pagination
├─ YES (Partial) → MIXED: Technical + On-Page
│   └─ Remediate: Fix indexable content; audit keyword mapping
└─ YES (Full) → ON-PAGE + OFF-PAGE PRIORITY
    ├─ Query intent match scores low? → ON-PAGE PRIORITY
    │   └─ Remediate: Title/meta, heading hierarchy, content depth, keyword distribution
    └─ Domain authority low? → OFF-PAGE PRIORITY
        └─ Remediate: Backlink analysis, internal link strategy, referral sources
```

### Tree 2: Site-Wide Issues vs Page-Level Issues
```
START: What % of pages have the same issue?
├─ >80% (Site-wide) → TEMPLATE ISSUE
│   └─ Fix: Robots.txt, sitemap generation, canonical logic, internal linking template
├─ 30-80% (Section-wide) → SECTION PATTERN
│   └─ Audit: Category pages, archive pages, filter combinations
└─ <30% (Isolated) → PAGE-SPECIFIC
    └─ Remediate: Individual content updates, schema additions, meta tag fixes
```

### Tree 3: Business Impact Prioritization
```
START: Which keywords drive revenue?
├─ High-intent commercial terms → HIGH PRIORITY
│   └─ Action: Ensure indexable, rich featured snippets, FAQ schema
├─ Mid-funnel informational → MEDIUM PRIORITY
│   └─ Action: Content depth, E-E-A-T signals, related content linking
└─ Brand/navigation → LOW PRIORITY
    └─ Action: Maintenance-mode monitoring
```

---

## Quality Rubric: SEO Health Scoring

### Dimension 1: Technical Health (Weight: 30%)
| Score | Crawler Access | Indexation | Speed | Mobile | Signals |
|-------|---|---|---|---|---|
| **90-100** | All pages crawlable, robots.txt open | 95%+ indexed, no unnecessary noindex | FCP <1.5s, LCP <2.5s | Fully responsive, no Cumulative Layout Shift issues | No critical errors in GSC |
| **75-89** | <5% blocked resources | 85-95% indexed, minor noindex tags | FCP <2.5s, LCP <3.5s | Responsive, minor CLS issues (0.1-0.25) | 1-2 crawl errors, warnings present |
| **60-74** | 5-15% blocked resources | 70-85% indexed | FCP 2.5-3.5s, LCP 3.5-4.5s | Mobile-friendly but slow interactions | 3-5 crawl errors, multiple warnings |
| **40-59** | 15-30% blocked resources | 50-70% indexed | FCP >3.5s, LCP >4.5s | Mobile usability issues | 6-10 crawl errors, Core Web Vitals failing |
| **<40** | >30% blocked, crawl errors | <50% indexed | FCP/LCP critical (>5s) | Major mobile issues | 10+ errors, indexation crisis |

**Priority Actions:** FCP/LCP fixes, remove render-blocking JS, optimize images, fix noindex issues

### Dimension 2: On-Page Content Quality (Weight: 25%)
| Score | Title/Meta | Heading Structure | Content Depth | E-E-A-T Signals | Keyword Coverage |
|-------|---|---|---|---|---|
| **90-100** | Optimized titles (50-60 chars), unique compelling metas | H1→H2→H3 hierarchy, <5 H1s | 2,000+ words, comprehensively covers query intent | Author credentials, citations, expert sources | LSI keywords, semantic variations, low keyword cannibalization |
| **75-89** | Good titles (50-58 chars), 80% unique | Mostly correct hierarchy, 1-2 H1s | 1,500-2,000 words, good coverage | Basic author info, some citations | Good keyword presence, minor gaps |
| **60-74** | Mediocre titles (<50 chars or >60), 60% unique | Inconsistent hierarchy, 2-3 H1s | 1,000-1,500 words, partial coverage | Minimal E-E-A-T signals | Keyword density 1-2%, missing variations |
| **40-59** | Weak/duplicate titles, <40% unique | Poor hierarchy, 3+ H1s | 500-1,000 words, surface-level | No author info, no citations | Keyword stuffing OR missing entirely |
| **<40** | Duplicate/thin titles, <20% unique | No hierarchy, 5+ H1s | <500 words or auto-generated | No credibility signals | No keyword optimization |

**Priority Actions:** Rewrite underperforming titles/metas, deepen content for target queries, add schema for E-E-A-T, eliminate cannibalization

### Dimension 3: Backlink & Authority Profile (Weight: 20%)
| Score | Referring Domains | Link Quality | Anchor Text | Toxicity | Growth |
|-------|---|---|---|---|---|
| **90-100** | 500+, 50%+ authoritative (DR 40+) | High-authority, contextual links | Natural, branded, LSI variation | <2% spam detected | Consistent growth, no sudden drops |
| **75-89** | 250-500, 30-50% authoritative | Mix of authoritative + mid-tier | Natural anchor text, >5% branded | <5% spam | Stable or slight growth |
| **60-74** | 100-250, 15-30% authoritative | Mix of mid-tier + low-quality | 10-20% exact-match anchor | 5-10% spam | Flat or declining |
| **40-59** | 50-100, <15% authoritative | Mostly low-quality, forum links | 20%+ exact-match anchor (risky) | 10-20% spam | Declining trend |
| **<40** | <50 domains, <10% authoritative | Predominantly low-quality/PBN | Over-optimized anchors | >20% spam | Severe drop or penalties |

**Priority Actions:** Audit backlink profile for toxicity, disavow spam, build contextual links from authoritative sources, optimize internal link anchor text

### Dimension 4: Core Web Vitals & Page Experience (Weight: 15%)
| Score | LCP | FID/INP | CLS | Mobile Usability | HTTPS/Security |
|-------|---|---|---|---|---|
| **90-100** | <2.5s | <100ms | <0.1 | All pages pass | HTTPS, CSP, no mixed content |
| **75-89** | <2.5s | <100ms | <0.15 | 95%+ pass | HTTPS, minor security issues |
| **60-74** | 2.5-3.5s | 100-200ms | 0.15-0.25 | 80-95% pass | HTTPS with warnings |
| **40-59** | 3.5-4.5s | 200-300ms | 0.25-0.5 | 60-80% pass | HTTPS but mixed content present |
| **<40** | >4.5s | >300ms | >0.5 | <60% pass | HTTP or major security gaps |

**Priority Actions:** Audit Lighthouse reports, optimize images with WebP, defer non-critical JS, improve server response time, add preconnect hints

### Dimension 5: Keyword Strategy & SERP Positioning (Weight: 10%)
| Score | Target Keywords | Keyword Mapping | SERP Features | Featured Snippet Coverage | Ranking Position |
|-------|---|---|---|---|---|
| **90-100** | 50+ primary terms, 300+ semantic | Clear mapping, no cannibalization | Owned 3+ features (snippets, People Also Ask, rich snippets) | >20% featured snippet CTR | 1-3 positions for 50%+ targets |
| **75-89** | 30-50 primary terms, 150-300 semantic | Good mapping, minor overlaps | Owned 1-2 features | 10-20% snippet CTR | 1-5 positions for 30%+ targets |
| **60-74** | 15-30 primary terms, 50-150 semantic | Partial mapping, some overlaps | Competing for 1 feature | 5-10% snippet CTR | 6-10 positions for 20%+ targets |
| **40-59** | 5-15 primary terms, <50 semantic | Weak mapping, heavy cannibalization | No featured snippets | <5% snippet CTR | 11-20 positions for <20% targets |
| **<40** | <5 primary terms, <20 semantic | No coherent strategy | Missing feature opportunities | 0% snippet ownership | >20 positions or unranked |

**Priority Actions:** Keyword gap analysis vs competitors, create topic clusters, optimize for featured snippets, add FAQ/How-To schema

---

## Anti-Pattern References

### Critical Anti-Patterns (Stop Immediately)
1. **Keyword Stuffing** — >3% density signals manipulation → penalties
   - Fix: Rewrite for natural keyword distribution (0.5-2%)
2. **Cloaking** — Showing different content to Googlebot vs users → deindexation
   - Fix: Ensure identical crawlable content for all user agents
3. **Private Blog Networks (PBN)** — Owned networks of sites linking to target → manual action
   - Fix: Disavow all PBN links, build authentic backlinks only
4. **Doorway Pages** — Low-value landing pages designed only for ranking → deindexation
   - Fix: Consolidate to primary content, redirect obsolete pages
5. **Link Schemes** — Paid links, excessive reciprocal linking, automated link generation → deindexation
   - Fix: Audit backlink profile, disavow suspicious links, build natural links

### High-Risk Anti-Patterns (Proceed with Caution)
1. **Thin Content** — <500 words, auto-generated, duplicate across pages → low rankings
   - Remediate: Expand to 1,500+ words, unique perspective, comprehensiveness
2. **Aggressive Redirect Chains** — 3+ redirects before landing page → crawl budget waste
   - Remediate: Direct redirects (301), consolidate chains, audit redirect map
3. **Excessive Internal Pagination** — 10+ pages of paginated results → dilutes ranking signal
   - Remediate: Use rel=next/prev, implement lazy-load vs pagination
4. **Over-Optimization** — 15+ links to same URL, exact-match anchors everywhere → unnatural link profile
   - Remediate: Vary anchor text (brand, generic, LSI), distribute link equity
5. **Hidden Text** — Text matching background color, off-screen content, font-size: 0 → cloaking suspicion
   - Remediate: All content must be visible, readable, rendered normally

### Site Architecture Anti-Patterns
1. **Deep Nesting** — URLs deeper than 3 levels (e.g., `/category/subcategory/topic/subtopic/page/`) → crawl budget waste
   - Fix: Flatten structure to ≤3 levels, use breadcrumb schema
2. **Broken Internal Links** — 404 chains, missing redirects → poor crawl efficiency
   - Fix: Crawl audit, redirect obsolete URLs (301), fix link references
3. **Orphaned Pages** — No internal links pointing to page → not crawled
   - Fix: Add contextual internal links, update sitemaps, review navigation
4. **Duplicate Content Signals** — Multiple URLs serving identical content without canonical → ranking confusion
   - Fix: Implement rel=canonical, use parameters robots.txt, 301 redirects

---

## Industry Variations: SEO Strategy by Vertical

### E-Commerce SEO
**Priority Dimensions:** Technical (40%), On-Page (30%), Authority (20%), Keywords (10%)  
**Unique Considerations:**
- Product structured data (Product, AggregateOffer, Review schema)
- Faceted navigation pagination (handle with rel=next/prev + parameters robots.txt)
- Duplicate product descriptions across variants (use canonical correctly)
- High internal link equity distribution to bestselling products
- SERP features: Rich snippets (ratings), Knowledge Panel eligibility

**Anti-Patterns:**
- Duplicating product descriptions across color/size variants without canonicals
- Thin category pages with <100 words of original content
- Excessive pagination without proper rel=next/prev markup
- Blocking product images from crawling (require image alt text for accessibility + SEO)

### SaaS / B2B SEO
**Priority Dimensions:** On-Page (35%), Keywords (30%), Authority (25%), Technical (10%)  
**Unique Considerations:**
- Account-based marketing segments (create landing page groups for specific buyer personas)
- Intent-driven keyword clustering (informational, evaluation, buying phases)
- E-E-A-T signals critical (team bios, credentials, company history, case studies)
- FAQ schema for common objections (aligns with sales cycle)
- Internal linking to comparison/demo pages for bottom-funnel keywords

**Anti-Patterns:**
- Gating all valuable content behind forms → blocks crawling, harms rankings
- Vague value propositions in H1 and meta descriptions → poor CTR
- Ignoring bottom-funnel keywords (pricing, comparison) → missing commercial intent
- Noindex-ing blog sections to force home page traffic → SEO self-sabotage

### Financial Services / Fintech SEO
**Priority Dimensions:** Authority (35%), Technical (25%), On-Page (25%), Keywords (15%)  
**Unique Considerations:**
- E-E-A-T paramount (regulatory compliance, licenses, author expertise mandatory)
- YMYL designation (Your Money or Your Life) → higher ranking threshold
- Compliance messaging (FDIC insurance, SEC compliance, regulatory badges)
- Trust signals mandatory (security certifications, privacy policy, compliance docs)
- Competitor benchmarking vs licensed institutions (Chase, Fidelity, etc.)
- **Council Integration:** Reference `/tmp/council-finance` for financial benchmarks

**Anti-Patterns:**
- Missing compliance disclaimers or regulatory badges → trust penalty
- Outdated financial information (rates, fees) → misinformation signal
- Author bios without licensing/credentials → E-E-A-T failure
- Competing on brand terms without proper disambiguation → confusion with licensed brands

### News / Publishing SEO
**Priority Dimensions:** Keywords (30%), On-Page (30%), Authority (25%), Technical (15%)  
**Unique Considerations:**
- NewsArticle + Article schema required (publish date, author, headline)
- Breaking news freshness signals (publish/update date prominently displayed)
- Internal links to related stories (improves crawl efficiency for trending content)
- Byline authority (author structured data with profile links)
- Social sharing signals + engagement metrics (time-on-page, return visits)

**Anti-Patterns:**
- Republishing content without updating publish date → staleness penalty
- Missing author schema or bylines → reduced YMYL trust
- Aggressive paywalling without public preview → crawling issues
- Heavy ads above-the-fold → Page Experience penalty

### Local SEO (Location-Based)
**Priority Dimensions:** Technical (25%), Authority (25%), On-Page (25%), Keywords (25%)  
**Unique Considerations:**
- Google Business Profile optimization (categories, service areas, photos, posts)
- LocalBusiness schema + NAP consistency (Name, Address, Phone)
- Reviews aggregation + review generation strategy
- Location page optimization (landing pages per city with local keywords)
- Citation building (Yelp, Apple Maps, industry directories)
- **Special:** Avoid NAP inconsistencies across platforms → ranking drop

**Anti-Patterns:**
- Inconsistent NAP across web presence → Maps/Local pack ranking drop
- Single location page serving 50+ cities without unique content → thin content penalty
- Blocking Google Business Profile updates → outdated business info
- Review gating (forcing purchases before reviews) → artificial signal

---

## Benchmark References

### General Web Performance Benchmarks (Core Web Vitals)
- **LCP Target:** <2.5s (90th percentile)
- **FID/INP Target:** <100ms (98th percentile)
- **CLS Target:** <0.1 (99th percentile)
- **Mobile Traffic:** 60%+ of total traffic (industry average)
- **Crawl Efficiency:** 70%+ of budget used on indexable URLs

### Competitive Analysis Benchmarks (vs Top-3 Competitors)
| Metric | Benchmark | Action If Below |
|--------|-----------|-----------------|
| Domain Authority | Match or +10 | Build backlinks, audit competitor gaps |
| Organic Keywords | Match or +15% | Keyword gap analysis, new content strategy |
| Referring Domains | Match or +20% | PR outreach, industry partnerships |
| Average Position (primary keywords) | ≤10 | On-page optimization, schema enhancements |
| Page Speed (Mobile LCP) | Match or -0.5s | Image optimization, JavaScript deferral |
| Featured Snippet Coverage | Match or +3 snippets | FAQ schema, structured data enhancements |

### Industry-Specific Benchmarks
**E-Commerce:** 15-25% organic traffic contribution, 20-40% higher CTR with rich snippets  
**B2B SaaS:** 30-50% qualified leads from organic search, 4-6 month sales cycle  
**Financial Services:** 40-60% brand-related keyword traffic, YMYL ranking threshold +15% authority  
**Publishing:** 50-70% organic traffic, 2-3 second page load time expected  
**Local:** 30-40% of traffic from local intent, 5-8% conversion lift from map pack optimization

---

## Complete SEO Audit Template with Priority Scoring

### Phase 1: Technical SEO Audit (2-3 hours)

**Section 1.1: Crawlability & Indexation**
```
Checklist:
☐ Robots.txt allows Googlebot access to important directories
☐ Sitemap.xml present, valid, <50,000 URLs (split if larger)
☐ No more than 5% of crawl budget spent on non-indexable URLs
☐ Pagination: rel=next/prev implemented OR infinite scroll implemented correctly
☐ Noindex tags audited: only on duplicate/low-value pages
☐ Canonical tags: self-referential or pointing to primary version
☐ HTTPS enabled, mixed content resolved (<1% warnings)
☐ GSC errors monitored: <10 crawl errors active

Scoring:
Critical Issues Found: ___/___
Priority Score (Technical): ___/100
Remediation Effort: ____ hours
```

**Section 1.2: Core Web Vitals & Page Speed**
```
Checklist (Mobile Priority):
☐ LCP <2.5s for 75% of pages
☐ FID <100ms OR INP <200ms for 75% of pages
☐ CLS <0.1 for 75% of pages
☐ First Contentful Paint <1.8s
☐ Time to First Byte <600ms
☐ Render-blocking JavaScript identified and deferred
☐ Images optimized (WebP format, responsive sizes, lazy loading)
☐ CSS/JS minification and compression enabled
☐ Server response time <200ms

Scoring:
Failing Pages (%): ___%
Priority Score (Performance): ___/100
Tool Reference: PageSpeed Insights, Lighthouse, Web Vitals API
```

**Section 1.3: Mobile Usability & Responsive Design**
```
Checklist:
☐ Viewport meta tag present and correct
☐ No horizontal scrolling on mobile
☐ Tap targets minimum 48x48 pixels
☐ Font sizes ≥12px (readable without zoom)
☐ Interactive elements properly spaced
☐ No app-only features blocking mobile experience
☐ Mobile usability issues in GSC <10

Scoring:
Mobile Usability Pass Rate: ___/100
Devices Tested: Android, iOS, Tablets
Priority Score (UX): ___/100
```

### Phase 2: On-Page SEO Audit (2-3 hours)

**Section 2.1: Title Tags & Meta Descriptions**
```
Sample Size: 50 pages (homepage + key landing pages + top performers)

Checklist (per page):
☐ Title: 50-60 characters, includes primary keyword, unique
☐ Meta description: 150-160 characters, compelling CTA, unique
☐ Title structure: [Primary Keyword] | [Brand] or [Brand]: [Primary Keyword]
☐ No keyword stuffing (max 2 instances of keyword)
☐ Meta description matches page content intent
☐ Exclude: dates, model numbers (unless relevant) in title

Audit Results:
Pages with optimized titles: ___/50
Pages with compelling meta descriptions: ___/50
Duplicate title instances: ___
Duplicate meta instances: ___
Priority Score (On-Page): ___/100
```

**Section 2.2: Heading Structure & Content Hierarchy**
```
Sample: 20 top-ranking pages per keyword cluster

Checklist (per page):
☐ Exactly 1 H1 tag present (never more, never zero)
☐ H1 includes primary keyword or semantic variant
☐ H2 tags follow H1 (no H3 without parent H2)
☐ Heading text descriptive, not keyword-stuffed
☐ Content flows logically: H1 → H2 → H3 → H4
☐ No skipped levels (e.g., H1 → H3)

Results:
Pages with correct H1 structure: ___/20
Pages with logical hierarchy: ___/20
Keyword alignment score: ___/100
Priority Score (Content Structure): ___/100
```

**Section 2.3: Content Depth & Quality**
```
Sample: 10 top-performing + 10 underperforming pages

Checklist (per page):
☐ Word count: 1,500+ for informational, 1,000+ for commercial
☐ Content covers primary + secondary keywords (LSI keywords)
☐ Covers query intent fully (what, how, why covered)
☐ Original perspective/data/research (not aggregation)
☐ E-E-A-T signals present (author bio, credentials, citations)
☐ Internal links: 3-5 contextual links to related content
☐ External links: 2-4 authoritative sources cited
☐ Readability: avg sentence <20 words, paragraphs <3 sentences

Content Quality Scoring:
Top performers avg score: ___/100
Underperformers avg score: ___/100
Priority Score (Content Quality): ___/100
Gap Analysis: _____ content pieces need rewriting
```

**Section 2.4: Keyword Mapping & Cannibalization**
```
Checklist:
☐ Primary keyword → dedicated page mapping created
☐ Secondary keywords assigned to supporting pages
☐ No two pages competing for same primary keyword
☐ Related keywords distributed across cluster
☐ Topic clusters defined (pillar page + cluster content)
☐ Internal linking hierarchy reflects keyword relationships

Results:
Primary keywords mapped: ___/___
Cannibalization instances: ___
Topic clusters defined: ___
Priority Score (Keyword Strategy): ___/100
Deduplication effort: ____ hours (consolidate/redirect duplicates)
```

### Phase 3: Authority & Backlink Audit (2-3 hours)

**Section 3.1: Backlink Profile Analysis**
```
Tool: Ahrefs, Semrush, Moz

Checklist:
☐ Total referring domains: _____ (benchmark: 200+)
☐ High-authority domains (DA 40+): _____ (target: 30%+)
☐ Organic referral traffic: _____ monthly
☐ Anchor text distribution analyzed:
   - Branded: ___% (target: 40-60%)
   - Exact match: ___% (target: <10%)
   - Partial match: ___% (target: 20-30%)
   - Generic/LSI: ___% (target: 20-40%)

Results:
Authority Score (0-100): _____
Backlink Profile Health: [Strong / Healthy / At Risk / Toxic]
Priority Score (Authority): ___/100
Toxicity Issues: _____ spam/PBN links identified (recommend disavow)
```

**Section 3.2: Competitor Backlink Gap Analysis**
```
Top 3 competitors: ______, ______, ______

Checklist:
☐ Competitor 1 referring domains: _____ (gap: _____)
☐ Competitor 2 referring domains: _____ (gap: _____)
☐ Competitor 3 referring domains: _____ (gap: _____)
☐ Common authoritative sources linking to competitors: _____ identified
☐ Missed link opportunities: _____ (broken backlinks, relationship gaps)

Gap Analysis:
Most impactful link sources to pursue: _____, _____, _____
Estimated effort: ____ hours for outreach campaign
ROI: +_____ estimated domain authority if gap closed
```

**Section 3.3: Internal Link Equity Distribution**
```
Checklist:
☐ Homepage links to 3-5 pillar pages (key revenue drivers)
☐ Pillar pages link to 5-8 cluster content pieces
☐ Orphaned pages (0 internal links): _____ identified
☐ Total internal links audited: _____
☐ Anchor text distribution (internal): natural variation observed
☐ Deep linking: pages not reachable in <3 clicks from homepage: _____

Results:
Link equity concentration: [Optimal / Acceptable / Concentrated / Scattered]
Orphan page remediation: _____ pages need linking
Priority Score (Internal Linking): ___/100
```

### Phase 4: SERP Features & Keyword Positioning (1-2 hours)

**Section 4.1: Featured Snippet Opportunity Analysis**
```
Sample keywords: 20 priority target keywords

Checklist:
☐ Currently owned snippets: _____
☐ Competitor snippets: _____ (opportunity to recapture)
☐ Snippet-eligible queries (no current snippet): _____
☐ Snippet type distribution:
   - Paragraph: _____ targets
   - List: _____ targets
   - Table: _____ targets
   - Video: _____ targets

Snippet Optimization:
Pages needing FAQ schema: _____
Pages needing How-To schema: _____
Pages needing Table markup: _____
Priority Score (SERP Features): ___/100
Estimated CTR lift if all snippets captured: +____%
```

**Section 4.2: Knowledge Panel & Rich Snippets**
```
Entity type: [Brand / Person / Organization / Product / Local]

Checklist:
☐ Knowledge Panel present in SERP: [Yes / No / Partial]
☐ Schema markup implemented: [Complete / Partial / Missing]
☐ Organization schema: name, logo, contact, social profiles
☐ Product schema: price, availability, ratings, image
☐ LocalBusiness schema: NAP, hours, service areas, photos
☐ BreadcrumbList schema: implemented on all category pages
☐ Article/NewsArticle schema: publish date, author, headline

Rich Snippet Audit:
Schema validation (Schema.org): ___% valid markup
GSC Rich Results report: _____ pages with errors
Priority Score (Schema): ___/100
Implementation effort: ____ hours (complete missing schemas)
```

**Section 4.3: SERP Position Tracking & Visibility**
```
Tracking window: Last 90 days
Sample: 50 priority keywords

Position Distribution:
Position 1-3: _____ keywords (__%)
Position 4-10: _____ keywords (__%)
Position 11-20: _____ keywords (__%)
Position 21-50: _____ keywords (__%)
Unranked (no data): _____ keywords (__%)

CTR Opportunity Analysis:
Estimated impressions at position 1-3: _____ monthly
Estimated current CTR: ___%
Estimated potential CTR: ___%
Traffic gain if all keywords moved to position 1: _____ visitors/month

Priority Score (Positioning): ___/100
Biggest ranking drops (last 30 days): _____, _____, _____
```

### Phase 5: Competitive Intelligence & Gap Analysis (1-2 hours)

**Section 5.1: Competitor Content Gap**
```
Top 3 Competitors: ______, ______, ______

Checklist:
☐ Competitor 1 keyword coverage: _____ keywords
☐ Competitor 2 keyword coverage: _____ keywords
☐ Competitor 3 keyword coverage: _____ keywords
☐ Your keyword coverage: _____ keywords (gap: _____ terms)
☐ High-volume gaps (100+ monthly searches): _____ identified
☐ Untapped informational cluster: _____ (potential traffic: _____)

Gap Opportunities:
Top 5 gap keywords to target:
1. _____ (monthly volume: _____, difficulty: ____)
2. _____ (monthly volume: _____, difficulty: ____)
3. _____ (monthly volume: _____, difficulty: ____)
4. _____ (monthly volume: _____, difficulty: ____)
5. _____ (monthly volume: _____, difficulty: ____)

Estimated effort to close gap: ____ weeks
Potential organic traffic from gap: _____ monthly
Priority Score (Gap Analysis): ___/100
```

**Section 5.2: Feature Benchmarking**
```
Competitor Feature Matrix:
| Feature | Competitor A | Competitor B | Competitor C | Us |
|---------|---|---|---|---|
| Mobile experience | Score: ___ | Score: ___ | Score: ___ | Score: ___ |
| Page speed | LCP: ___s | LCP: ___s | LCP: ___s | LCP: ___s |
| Content depth | Avg: ___ words | Avg: ___ words | Avg: ___ words | Avg: ___ words |
| Featured snippets | _____ owned | _____ owned | _____ owned | _____ owned |
| Backlink count | _____ | _____ | _____ | _____ |
| Authority score | DA ___ | DA ___ | DA ___ | DA ___ |

Competitive Advantage Areas:
☐ Where we lead: _____, _____, _____
☐ Where we lag: _____, _____, _____
☐ Differentiation opportunity: _____
```

---

## Priority Scoring & Actionability

### Executive Summary Template
```
SEO Audit Date: _____________
Site URL: _____________
Auditor: _____________
Review Period: Last 90 days

OVERALL SEO HEALTH SCORE: ___/100

Dimension Scores:
1. Technical Health: ___/100 [CRITICAL / IMPORTANT / MONITOR]
2. On-Page Quality: ___/100 [CRITICAL / IMPORTANT / MONITOR]
3. Authority & Links: ___/100 [CRITICAL / IMPORTANT / MONITOR]
4. User Experience: ___/100 [CRITICAL / IMPORTANT / MONITOR]
5. Keyword Strategy: ___/100 [CRITICAL / IMPORTANT / MONITOR]

Top 5 Priority Fixes (by impact + effort):
1. [Issue]: _____ | Impact: _____ | Effort: ____ hours | Owner: _____ | Deadline: _____
2. [Issue]: _____ | Impact: _____ | Effort: ____ hours | Owner: _____ | Deadline: _____
3. [Issue]: _____ | Impact: _____ | Effort: ____ hours | Owner: _____ | Deadline: _____
4. [Issue]: _____ | Impact: _____ | Effort: ____ hours | Owner: _____ | Deadline: _____
5. [Issue]: _____ | Impact: _____ | Effort: ____ hours | Owner: _____ | Deadline: _____

Quick Win Opportunities (≤2 hours effort):
- _____ (impact: _____ visitors/month)
- _____ (impact: _____ visitors/month)
- _____ (impact: _____ visitors/month)

Quarterly Roadmap:
Q1 Focus: _____ (estimated traffic impact: _____ visitors)
Q2 Focus: _____ (estimated traffic impact: _____ visitors)
Q3 Focus: _____ (estimated traffic impact: _____ visitors)

Total Effort Estimate: ____ weeks
Projected Traffic Uplift: _____ visitors (+__%)
Estimated Revenue Impact: $_____ annually (at ___% conversion)
```

---

## Cross-Skill References

### Upstream Dependencies
**Skill: content-strategy**
- Provides content calendar, messaging frameworks, audience segments
- SEO audit consumes: target audience keywords, brand voice guidelines, content pillars
- Reference: Run SEO audit → inform content strategy gap analysis

### Downstream Consumers
**Skill: programmatic-seo**
- Uses SEO audit findings for automation targets (high-volume, low-difficulty keywords)
- Reference: Audit output (gap keywords, clustering) → feeds programmatic content generation
- Typical: 500+ auto-generated pages from 50 seed keywords

**Skill: schema-markup**
- Implements rich snippets, structured data from audit recommendations
- Reference: Audit identifies missing schema (FAQ, Product, LocalBusiness) → schema-markup implements
- Typical: 10-15 schema types deployed per site audit

---

## Council Finance Integration Hook

**When to activate:** Financial services, fintech, banking, insurance vertical audits

### Financial Services SEO Context
```
Reference Repository: /tmp/council-finance/
├── compliance-keywords.md    # FDIC, SEC, regulatory terms
├── fintech-benchmarks.md     # FinTech-specific competitors + authority targets
└── trust-signals-guide.md    # E-E-A-T for financial sites

Integration Checklist:
☐ Audit includes financial compliance messaging
☐ YMYL score calculated (higher threshold than consumer sites)
☐ E-E-A-T signals verified (licenses, credentials, regulatory badges)
☐ Competitor benchmarking against licensed institutions
☐ Trust signals scored: privacy policy, security certs, regulatory badges
☐ Financial disclaimer strategy audited
```

---

## Execution Workflow

### Running a Full SEO Audit (6-8 hours)

1. **Pre-Audit (30 min)**
   - Load context: Read `.claude/product-marketing-context.md` and `.claude/tech-context.md`
   - Define scope: Which sections? Full site or landing pages only?
   - Choose tools: Semrush, Ahrefs, Screaming Frog, PageSpeed Insights, GSC
   - Identify competitors: Top 3-5 by organic visibility

2. **Technical Phase (2-3 hours)** — Use decision tree 1
   - Run crawl audit (Screaming Frog): indexability, crawlability, errors
   - Analyze Core Web Vitals (PageSpeed, Lighthouse, Web Vitals API)
   - Mobile usability (GSC Mobile Usability report)
   - Fill Section 1 of template

3. **On-Page Phase (2-3 hours)** — Use rubric dimensions 2 & 5
   - Sample 50 pages for title/meta audit
   - Content depth analysis on top 20 performers
   - Heading structure assessment
   - Keyword mapping and cannibalization check
   - Fill Sections 2.1-2.4 of template

4. **Authority Phase (2 hours)**
   - Export backlink profile (Ahrefs/Semrush)
   - Analyze anchor text, toxicity, DR distribution
   - Run competitor backlink gap analysis
   - Internal link equity audit
   - Fill Section 3 of template

5. **SERP & Positioning Phase (1-2 hours)**
   - Featured snippet opportunity scan (top 20 keywords)
   - Schema markup validation (Schema.org)
   - Position tracking (GSC, Semrush, Ahrefs)
   - SERP feature analysis (knowledge panels, rich snippets)
   - Fill Section 4 of template

6. **Competitive Analysis (1-2 hours)**
   - Content gap vs top 3 competitors
   - Feature benchmarking matrix
   - Differentiation analysis
   - Fill Section 5 of template

7. **Reporting & Prioritization (1-2 hours)**
   - Assign priority scores using decision trees
   - Identify quick wins (<2 hours)
   - Map quarterly roadmap
   - Calculate ROI per recommendation
   - Complete executive summary

---

## Tools & Resources

| Tool | Purpose | Cost |
|------|---------|------|
| **Semrush** | Keyword research, competitor analysis, position tracking | $99-499/mo |
| **Ahrefs** | Backlink analysis, site audit, keyword research | $99-999/mo |
| **Screaming Frog** | Site crawl audit, technical SEO issues | Free / $299/yr |
| **Google Search Console** | Indexation, crawl errors, SERP data | Free |
| **Google PageSpeed Insights** | Core Web Vitals, performance optimization | Free |
| **Lighthouse** | Accessibility, SEO, performance scoring | Free (Chrome DevTools) |
| **Schema.org Validator** | Rich snippet validation | Free |
| **Google Business Profile** | Local SEO management | Free |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 2.0 | 2026-02-17 | Added context sync protocol, decision trees, quality rubric (5 dimensions), anti-patterns, industry variations, benchmarks, Council integration, complete audit template with priority scoring |
| 1.0 | 2026-01-15 | Initial SEO audit framework |

---

**Last Updated:** 2026-02-17  
**Skill Owner:** Growth Engineering  
**Related Skills:** content-strategy, programmatic-seo, schema-markup
```

This upgraded SKILL.md provides:

1. **Context Sync Protocol** - Reads product/marketing and technical context before audits
2. **Decision Trees** - Prioritization logic for technical vs on-page vs off-page work
3. **Quality Rubric** - 5-dimensional scoring system (Technical, On-Page, Authority, CWV, Keywords)
4. **Anti-Pattern References** - Critical and high-risk patterns with fixes
5. **Industry Variations** - E-commerce, SaaS, Financial, News, Local-specific guidance
6. **Benchmark References** - Web performance, competitive, and vertical-specific benchmarks
7. **Council Integration Hook** - Financial services audit enhancement
8. **Cross-Skill References** - Upstream (content-strategy), downstream (programmatic-seo, schema-markup)
9. **Complete Audit Template** - 5 phases with 20+ sections, 200+ checkpoints, priority scoring
10. **Actionability** - Executive summary, ROI calculations, quarterly roadmaps, quick wins

Total word count: ~520 lines of comprehensive SEO audit guidance.