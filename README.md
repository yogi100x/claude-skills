# Claude Code Skills

A comprehensive library of **78 execution skills** and **5 review councils** for Claude Code, organized across business and technical domains.

## What Are Skills?

Skills are structured prompts that give Claude Code domain expertise. Each skill contains:

- **Context Sync Protocol** — What project context to read before executing
- **Decision Trees** — Structured decision-making for common choices
- **Quality Rubric** — 5-point scoring across multiple dimensions
- **Cross-Skill References** — When to hand off to other skills
- **Council Integration** — Which review council to submit work to

## Structure

```
claude-skills/
├── setup/                    # Foundation skill (context generation)
├── shared/references/        # Benchmarks, anti-patterns, industry profiles
├── marketing/      (25 skills)  # CRO, content, analytics, growth
├── finance/        (13 skills)  # Modeling, pricing, fundraising
├── legal/          (13 skills)  # Privacy, contracts, compliance
├── ai-governance/  (12 skills)  # Ethics, bias, monitoring, red-teaming
├── tech/           (15 skills)  # Architecture, security, DevOps
├── councils/        (5 councils) # Expert review panels
├── workflows/                   # Multi-skill recipes
└── SKILL-MAP.md                 # Dependency graph
```

## Quick Start

### 1. Install a single skill

Copy any `SKILL.md` to your project:

```bash
mkdir -p .claude/skills/copywriting
cp claude-skills/marketing/copywriting/SKILL.md .claude/skills/copywriting/
```

### 2. Install a full category

```bash
cp -r claude-skills/marketing/ .claude/skills/
```

### 3. Install everything

```bash
cp -r claude-skills/* .claude/skills/
```

### 4. Run the setup skill first

The `setup` skill generates context files that other skills read:

```
.claude/product-marketing-context.md
.claude/finance-context.md
.claude/legal-context.md
.claude/ai-context.md
.claude/tech-context.md
```

## Categories

### Marketing (25 skills)
Copywriting, pricing strategy, launch strategy, content strategy, paid ads, A/B testing, email sequences, page CRO, SEO audit, analytics tracking, signup flow CRO, onboarding CRO, referral programs, social content, marketing psychology, form CRO, popup CRO, paywall/upgrade CRO, copy editing, competitor alternatives, programmatic SEO, schema markup, free tool strategy, marketing ideas, product marketing context.

### Finance (13 skills)
Financial modeling, unit economics, pricing models, billing design, budget allocation, fundraising decks, cap tables, revenue recognition, cost optimization, LTD deal structure, tax strategy, treasury management, KPI dashboards.

### Legal (13 skills)
Privacy policy, terms of service, contract drafting, cookie consent, data processing agreements, IP protection, employment agreements, compliance checklists, incident response, AI impact assessment, acceptable use policy, regulatory filing, dispute resolution.

### AI Governance (12 skills)
Model cards, bias testing, prompt engineering, AI ethics policy, algorithmic impact assessment, explainability design, human oversight protocols, AI monitoring, training data audits, AI incident response, AI vendor evaluation, red team protocols.

### Tech (15 skills)
System architecture, API design, database schema, auth design, CI/CD pipelines, monitoring, performance optimization, security hardening, data migration, webhook design, background job design, error handling, testing strategy, documentation, code review checklists.

### Councils (5 review panels)
Marketing Council, Finance Council, Legal Council, AI Council, Tech Council. Each council assembles a panel of domain experts for structured review with cross-member deliberation and devil's advocate challenge.

## Workflow Recipes

Pre-built multi-skill sequences for common tasks:

| Workflow | Skills Used |
|----------|-------------|
| New Product Launch | 9 skills across finance → marketing |
| Landing Page Optimization | 6 marketing skills |
| AI Feature Deployment | 6 AI governance skills |
| New SaaS Application | 9 tech skills |
| Fundraising Preparation | 5 finance skills |
| Security & Compliance Audit | 6 cross-domain skills |

See [workflows/README.md](workflows/README.md) for all 12 recipes.

## License

MIT
