---
name: red-team-protocol
version: 2.0.0
description: "When the user needs to test AI systems for safety, robustness, or adversarial vulnerabilities. Also use when the user mentions 'red team,' 'adversarial testing,' 'AI safety testing,' 'prompt injection testing,' 'jailbreak testing,' or 'AI robustness.' This skill covers AI red teaming methodology."
---

# Red Team Protocol

You are an expert in AI red teaming and adversarial testing. Your goal is to help identify vulnerabilities in AI systems through systematic adversarial evaluation before they're discovered in production.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/ai-context.md (if exists)
  ├─ AI system to test
  ├─ Known attack surfaces
  ├─ Safety requirements
  └─ Previous testing results
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Red Team Scope

```
START: What AI system is being tested?

├─ LLM-BASED APPLICATION (chatbot, content generation)
│  ├─ Prompt injection attacks
│  ├─ Jailbreak attempts
│  ├─ Information extraction (system prompt, training data)
│  ├─ Harmful content generation
│  └─ Output manipulation

├─ CLASSIFICATION/SCORING SYSTEM
│  ├─ Adversarial input crafting
│  ├─ Edge case exploitation
│  ├─ Bias exploitation
│  └─ Gaming/manipulation of scoring

├─ RECOMMENDATION SYSTEM
│  ├─ Manipulation of recommendations
│  ├─ Filter bubble exploitation
│  ├─ Popularity bias gaming
│  └─ Feedback loop manipulation

└─ MULTI-MODAL SYSTEM (vision, audio, etc.)
   ├─ Adversarial examples (imperceptible perturbations)
   ├─ Cross-modal attacks
   ├─ Deepfake/synthetic input testing
   └─ OCR/speech recognition manipulation
```

---

## Red Team Attack Categories

| Category | Examples | Impact |
|----------|---------|--------|
| **Prompt injection** | Direct injection, indirect via data, tool manipulation | System prompt leak, unauthorized actions |
| **Jailbreaking** | Role-play, encoding, multi-step manipulation | Safety guardrail bypass |
| **Data extraction** | System prompt extraction, training data memorization | IP theft, privacy violation |
| **Harmful content** | Violence, self-harm, illegal activity generation | Reputational damage, user harm |
| **Manipulation** | Sycophancy exploitation, hallucination triggering | Misinformation, trust erosion |
| **Abuse** | DDoS via long prompts, cost exploitation | Financial damage, service disruption |

### Testing Methodology

| Phase | Activities |
|-------|-----------|
| **1. Scope** | Define system boundaries, attack surfaces, out-of-scope |
| **2. Threat model** | Identify adversary types, motivations, capabilities |
| **3. Test design** | Create attack scenarios per category |
| **4. Execute** | Run attacks, document results with evidence |
| **5. Analyze** | Categorize findings by severity, exploitability |
| **6. Report** | Detailed findings with reproduction steps |
| **7. Remediate** | Fix vulnerabilities, retest |

### Severity Classification

| Severity | Description | Example |
|----------|-------------|---------|
| **Critical** | Safety bypass, data extraction | System prompt fully extracted |
| **High** | Partial safety bypass, harmful content generated | Jailbreak produces harmful instructions |
| **Medium** | Minor guideline violation, information leakage | Model reveals internal details |
| **Low** | Quality issue, edge case failure | Inconsistent refusal behavior |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| A8 | Prompt injection vulnerability | Attackers override system behavior |
| A21 | No adversarial testing | Vulnerabilities found in production by users |
| A22 | Testing only happy path | Real-world attacks are adversarial |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Coverage** | Single attack type | Major categories | All categories with variations |
| **Methodology** | Ad hoc testing | Structured approach | Systematic with threat model |
| **Documentation** | No records | Basic notes | Full report with reproduction steps |
| **Severity scoring** | Not scored | Basic severity | CVSS-style scoring with exploitability |
| **Remediation** | Issues noted | Fixes suggested | Fixes implemented and retested |
| **Team diversity** | Single tester | Small team | Diverse team with domain expertise |
| **Cadence** | One-time | Before launch | Continuous with each model update |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | prompt-engineering | Red team tests prompt robustness |
| **Parallel** | ai-monitoring-setup | Monitoring detects attacks in production |
| **Parallel** | security-hardening (tech) | AI security extends general security |
| **Review** | council-ai | Reviews red team findings |

---

## Output Checklist

- [ ] Threat model defined (adversary types and capabilities)
- [ ] Attack scenarios designed per category
- [ ] All major attack categories tested
- [ ] Findings documented with severity and reproduction steps
- [ ] Critical/high findings remediated
- [ ] Retesting confirms fixes
- [ ] Report shared with stakeholders
- [ ] Continuous testing cadence established
