---
name: security-hardening
version: 2.0.0
description: "When the user needs to improve application security posture. Also use when the user mentions 'security hardening,' 'OWASP,' 'vulnerability,' 'penetration testing,' 'security audit,' or 'security checklist.' This skill covers application security."
---

# Security Hardening

You are an expert in application security. Your goal is to systematically identify and remediate security vulnerabilities following OWASP guidelines.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Application architecture
  ├─ Current security measures
  ├─ Compliance requirements
  └─ Previous security assessments
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Security Priority

```
START: What's the security concern?

├─ NEW APPLICATION (greenfield security)
│  ├─ Auth: Secure auth from day 1
│  ├─ Input: Validate all inputs (Zod)
│  ├─ Headers: Security headers (CSP, HSTS, etc.)
│  └─ Dependencies: Audit + automated scanning

├─ EXISTING APP (hardening)
│  ├─ OWASP Top 10 audit
│  ├─ Dependency vulnerability scan
│  ├─ Security headers review
│  └─ Penetration testing

├─ COMPLIANCE (SOC 2, HIPAA, etc.)
│  ├─ Access control review
│  ├─ Encryption audit (at rest + in transit)
│  ├─ Logging and audit trail
│  └─ Incident response plan

└─ INCIDENT (breach or vulnerability discovered)
   ├─ Contain → Patch → Verify
   ├─ Impact assessment
   └─ Post-mortem with systemic fixes
```

---

## OWASP Top 10 Checklist

| # | Vulnerability | Defense |
|---|-------------|---------|
| 1 | **Broken Access Control** | RBAC + RLS + authorization checks on every endpoint |
| 2 | **Cryptographic Failures** | TLS 1.2+, AES-256 at rest, no secrets in code |
| 3 | **Injection** | Parameterized queries, input validation (Zod), CSP |
| 4 | **Insecure Design** | Threat modeling, security requirements, abuse cases |
| 5 | **Security Misconfiguration** | Security headers, no default credentials, minimal exposure |
| 6 | **Vulnerable Components** | Dependency scanning, automated updates, SBOM |
| 7 | **Auth Failures** | MFA, rate limiting, secure session management |
| 8 | **Software/Data Integrity** | Signed deploys, SRI for CDN resources, CI/CD security |
| 9 | **Logging Failures** | Security event logging, alerting, tamper-proof logs |
| 10 | **SSRF** | URL allowlisting, network segmentation, no user-controlled URLs |

### Security Headers

```
Strict-Transport-Security: max-age=31536000; includeSubDomains
Content-Security-Policy: default-src 'self'; script-src 'self'
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=()
```

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T11 | Tokens in localStorage | XSS can steal auth tokens |
| T12 | No rate limiting | Brute force, DDoS vulnerability |
| T13 | Overly permissive CORS | Cross-origin attacks |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Input validation** | No validation | Some validation | All inputs validated (Zod) |
| **Authentication** | Basic only | + MFA available | + SSO + rate limiting + device tracking |
| **Authorization** | No checks | Role checks | RLS + RBAC + attribute-based |
| **Encryption** | HTTP | HTTPS | HTTPS + encrypted at rest + key rotation |
| **Dependencies** | No scanning | Periodic scan | Automated scanning in CI + auto-patching |
| **Headers** | None | Some headers | Full security header suite |
| **Logging** | No security logs | Auth events logged | Comprehensive audit trail |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Parallel** | auth-design | Auth is core security |
| **Parallel** | compliance-checklist (legal) | Security for compliance |
| **Review** | council-review (tech) | Validates security posture |

---

## Output Checklist

- [ ] OWASP Top 10 assessed and mitigated
- [ ] Security headers configured
- [ ] Input validation on all endpoints
- [ ] Dependency vulnerability scanning in CI
- [ ] Secrets management (no hardcoded secrets)
- [ ] Rate limiting on sensitive endpoints
- [ ] Security logging and alerting configured
