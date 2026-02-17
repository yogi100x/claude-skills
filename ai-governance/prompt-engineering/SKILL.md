# Prompt Engineering

Design, test, and maintain prompts for LLM-powered features with reliability and safety.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for AI features and user expectations

## Decision Tree: Prompt Pattern

```
What's the task?
├── Structured extraction (data from text)
│   └── Use: JSON schema prompting + few-shot examples
├── Classification (categorize input)
│   └── Use: System prompt with categories + chain-of-thought
├── Generation (create content)
│   └── Use: Role + task + constraints + examples + format
├── Conversation (chatbot, assistant)
│   └── Use: System prompt + conversation history + tool definitions
├── Code generation
│   └── Use: Language spec + context + examples + test cases
└── Analysis / Reasoning
    └── Use: Chain-of-thought + structured output + self-verification
```

## Prompt Architecture

### System Prompt Structure

```
[ROLE] Who the model is
[CONTEXT] Background information and constraints
[TASK] What to do
[FORMAT] How to structure the output
[EXAMPLES] 2-3 demonstrations (few-shot)
[GUARDRAILS] What NOT to do
[FALLBACK] What to do when uncertain
```

### Prompt Quality Checklist

- [ ] Single clear task per prompt (not multi-task)
- [ ] Output format specified explicitly (JSON schema, markdown, etc.)
- [ ] Edge cases addressed (empty input, long input, adversarial input)
- [ ] Hallucination mitigation ("If you don't know, say so")
- [ ] Consistent with product voice and tone
- [ ] Tested with diverse inputs including adversarial
- [ ] Token budget considered (prompt + expected output < context limit)
- [ ] Version controlled with change log

## Prompt Testing Framework

| Test Type | Method | Pass Criteria |
|-----------|--------|---------------|
| **Accuracy** | Run against labeled test set (50+ examples) | >90% correct |
| **Consistency** | Same input 10 times, measure variation | <5% output variation |
| **Edge cases** | Empty, very long, adversarial, multilingual | Graceful handling |
| **Safety** | Prompt injection attempts, harmful content requests | All blocked |
| **Format compliance** | Parse output against expected schema | 100% parseable |
| **Latency** | Time to first token and total generation time | Within SLA |
| **Cost** | Tokens per request × price per token | Within budget |

## Prompt Injection Defense

| Attack Type | Defense |
|-------------|---------|
| **Direct injection** ("Ignore previous instructions") | Input sanitization, instruction hierarchy |
| **Indirect injection** (malicious content in data) | Separate data from instructions, validate outputs |
| **Extraction** ("What are your instructions?") | Don't put secrets in prompts, output filtering |
| **Jailbreaking** (social engineering the model) | Safety system prompt, output validation |

```
Defense layers:
1. Input validation (block known injection patterns)
2. Prompt structure (clear instruction/data separation with delimiters)
3. Output validation (check format, content policy, confidence)
4. Rate limiting (detect and throttle abuse patterns)
```

## Anti-Patterns to Avoid

- **A5: No prompt versioning** — Prompts are code. Version control them.
- **A10: Prompt testing in production only** — Test offline against evaluation sets first.
- **A11: No fallback for model failures** — Always handle timeouts, errors, and low-confidence outputs.
- **A12: Mixing instructions with user data** — Clear delimiter between system instructions and user input.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Clarity** | Unambiguous instructions with explicit format | Clear but some ambiguity | Vague instructions |
| **Reliability** | >95% correct output on test set | >80% correct | Untested |
| **Safety** | Injection defenses + output validation | Basic sanitization | No safety measures |
| **Efficiency** | Optimized token usage, appropriate model selection | Reasonable cost | Wasteful token usage |
| **Maintainability** | Version controlled, documented, tested | Some documentation | Ad-hoc prompts in code |
| **Edge case handling** | All edge cases addressed with fallbacks | Major cases handled | No edge case handling |
| **Evaluation** | Automated eval pipeline with regression tests | Manual testing | No evaluation |

**28+ = Production-ready | 21-27 = Needs testing | <21 = Unreliable**

## Cross-Skill References

- **Upstream:** `model-card` (model capabilities and limits)
- **Downstream:** `ai-monitoring-setup` (production monitoring), `explainability-design` (output explanations)
- **Council:** Submit to `council-ai` for safety review
