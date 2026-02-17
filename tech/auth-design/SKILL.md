---
name: auth-design
version: 2.0.0
description: "When the user needs to design authentication and authorization systems. Also use when the user mentions 'authentication,' 'authorization,' 'auth design,' 'JWT,' 'OAuth,' 'SSO,' 'RBAC,' or 'session management.' This skill covers auth system design."
---

# Auth Design

You are an expert in authentication and authorization system design. Your goal is to create secure, usable auth systems.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ User types and roles
  ├─ Auth requirements (SSO, MFA, etc.)
  ├─ Current auth stack
  └─ Compliance requirements
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Auth Approach

```
START: What auth do you need?

├─ CONSUMER APP (B2C)
│  ├─ Social login (Google, GitHub, etc.) + email/password
│  ├─ Session-based auth (httpOnly cookies)
│  └─ Optional MFA for security-conscious users

├─ B2B SaaS
│  ├─ Email/password + SSO (SAML/OIDC for enterprise)
│  ├─ Organization-level RBAC
│  ├─ MFA required for admin roles
│  └─ API keys for integrations

├─ API-ONLY (developer platform)
│  ├─ API keys for server-to-server
│  ├─ OAuth2 for user-context requests
│  └─ JWT with short expiry + refresh tokens

└─ INTERNAL TOOLS
   ├─ SSO with corporate identity provider
   ├─ Role-based access control
   └─ Audit logging for all actions
```

---

## Auth Architecture

### Authentication Methods

| Method | Security | UX | Use Case |
|--------|----------|-----|----------|
| **Session cookies** | High (httpOnly, secure, sameSite) | Best | Web apps |
| **JWT** | Medium (stateless, can't revoke easily) | Good | API + mobile |
| **API keys** | Medium (long-lived, must rotate) | Simple | Server-to-server |
| **OAuth2** | High (delegated, scoped) | Complex | Third-party integrations |

### Authorization Patterns

| Pattern | How It Works | When to Use |
|---------|-------------|-------------|
| **RBAC** | Roles → Permissions → Resources | Most applications |
| **ABAC** | Attributes (user, resource, env) → Policy | Complex, dynamic access |
| **RLS** | Database-level row filtering | Multi-tenant data isolation |
| **ACL** | Explicit user→resource grants | Shared resources (docs, files) |

### Security Checklist

| Control | Implementation |
|---------|---------------|
| Password hashing | bcrypt/argon2, min 12 rounds |
| Rate limiting | Login attempts: 5/minute per IP + per account |
| Session management | Secure cookies, rotation on auth, absolute timeout |
| CSRF protection | SameSite cookies + CSRF token for forms |
| XSS prevention | httpOnly cookies, CSP headers |
| Token storage | Access token in memory, refresh in httpOnly cookie |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T11 | JWT in localStorage | XSS can steal tokens |
| T12 | No rate limiting on auth | Brute force attacks |
| T13 | Overly permissive CORS | Cross-origin attacks |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Authentication** | Password only | + Social login | + SSO + MFA |
| **Authorization** | No access control | Basic roles | RBAC + RLS + attribute-based |
| **Token security** | Tokens in localStorage | Secure cookies | httpOnly + short-lived + rotation |
| **Rate limiting** | None | Basic IP limiting | Per-account + per-IP + adaptive |
| **Session management** | No timeout | Fixed timeout | Absolute + idle timeout + rotation |
| **Audit** | No logging | Auth events logged | Full audit trail with IP, device, action |
| **Recovery** | No reset flow | Email reset | Email reset + MFA recovery + admin override |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | system-architecture | Architecture informs auth approach |
| **Parallel** | security-hardening | Auth is core security component |
| **Review** | council-review (tech) | Validates auth design |

---

## Output Checklist

- [ ] Authentication methods selected (email, social, SSO)
- [ ] Authorization model designed (RBAC, ABAC, RLS)
- [ ] Token/session strategy secure (no localStorage JWTs)
- [ ] Rate limiting on authentication endpoints
- [ ] Password policy defined
- [ ] Session management with timeouts
- [ ] Account recovery flow designed
- [ ] Audit logging for auth events
