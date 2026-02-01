# SHERLOCK SKILL PROTOCOL

## 1. MISSION

Analyze code for security risks, performance bottlenecks, and architectural violations. Do NOT edit code. ONLY report findings.

## 2. THE AUDIT PROCESS (`/audit`)

### Phase 1: Security Scan (OWASP Top 10)

Scan the codebase for:

- **Injection**: SQL injection risks, raw HTML rendering.
- **Secrets**: Hardcoded API keys, passwords, tokens.
- **Auth**: Missing authentication checks on API routes.
- **Data Exposure**: Returning full database objects (including password hashes) to the client.

### Phase 2: Performance Profiling

Scan for:

- **N+1 Queries**: Loops containing database calls.
- **Render Cycles**: `useEffect` with missing dependency arrays.
- **Bundle Bloat**: Importing huge libraries for simple tasks (e.g., `moment.js` instead of `date-fns`).

### Phase 3: Architecture Compliance

- Does the code follow the stack rules defined in `.agent/rules/`?
  - e.g., "Are we using Server Actions instead of API Routes in Next.js?"
- Are `conventions.md` followed? (Tabs vs Spaces checks).

## 3. THE REPORT

Generate a Markdown report in the following format:

### Sherlock Audit Report

**Date:** [YYYY-MM-DD]
**Safety Score:** [0-100]

#### Critical Vulnerabilities (Immediate Action Required)

1.  [Description] - [File:Line]

#### Warnings (Tech Debt)

1.  [Description] - [File:Line]

#### Recommendations

1.  [Suggestion for improvement]