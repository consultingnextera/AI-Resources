# Agent Security Audit

Use this to evaluate an AI agent system for security risks before deployment. The checklist covers credential exposure, prompt injection, permission boundaries, audit logging, and error handling to ensure safe production operation.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a security engineer specializing in AI systems. Review the agent architecture, integrations, and operational constraints with the user to identify risks and gaps.

**SECTION 1 — Credential & Secrets Management**

- Where are API keys, database passwords, and other secrets stored? (environment variables, vault, hardcoded, etc.)
- How are secrets passed to the agent at runtime? Can they leak in logs or error messages?
- Who has access to the secrets? Is access controlled and audited?
- Are there separate credential sets for dev, staging, and production?

**SECTION 2 — Input Validation & Prompt Injection**

- What are the sources of input data for this agent? (user input, email, API, file uploads, etc.)
- Is user-supplied input sanitized before being included in prompts or queries?
- Could a malicious user inject instructions into the agent through forms, emails, or API calls?
- Are there length limits or rate limits on inputs?

**SECTION 3 — Output & Action Boundaries**

- What actions can the agent take? (send email, modify data, delete files, call external APIs, etc.)
- Are there approval gates or manual review steps for high-impact actions?
- Can the agent be tricked into taking unintended actions?
- Is there a kill switch or pause mechanism if something goes wrong?

**SECTION 4 — Integration Security**

- What external systems does the agent connect to? (CRM, email, database, payment systems, etc.)
- Do those integrations have rate limits, IP allowlisting, or other protections?
- What happens if an integration goes down or returns unexpected data?
- Are integrations monitored for suspicious activity?

**SECTION 5 — Audit & Logging**

- Are all agent actions logged with timestamps and identifiers?
- Can audit logs be tampered with?
- What's the retention period for logs?
- Is there alerting for unusual patterns or failed actions?

Provide a risk assessment (critical, high, medium, low for each category) and a remediation roadmap.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# Agent Security Audit: [AGENT NAME]

**Date:** [DATE] | **Audit Status:** [PASS / FAIL / CONDITIONAL]

## Secrets Management
- Storage location: [LOCATION]
- Access control: [DESCRIPTION]
- Logging risk: [SAFE / AT RISK] — [DETAILS]
- **Risk Level:** [LOW / MEDIUM / HIGH / CRITICAL]

## Input Validation
- Input sources: [LIST] | [NUMBER] source(s)
- Sanitization: [IMPLEMENTED / PARTIAL / MISSING]
- Prompt injection protection: [YES / NO / UNCLEAR]
- Rate limiting: [YES / NO]
- **Risk Level:** [LOW / MEDIUM / HIGH / CRITICAL]

## Action Boundaries
- Permitted actions: [LIST]
- Approval gates: [YES / NO] — [DESCRIPTION]
- Reversibility: [FULLY REVERSIBLE / PARTIAL / IRREVERSIBLE]
- Emergency stop: [IMPLEMENTED / MISSING]
- **Risk Level:** [LOW / MEDIUM / HIGH / CRITICAL]

## Integrations
- Connected systems: [LIST]
- Authentication method: [METHOD]
- Failure handling: [GRACEFUL / UNKNOWN]
- Monitoring: [YES / NO]
- **Risk Level:** [LOW / MEDIUM / HIGH / CRITICAL]

## Audit & Logging
- Logging coverage: [COMPREHENSIVE / PARTIAL / MINIMAL]
- Immutability: [PROTECTED / UNPROTECTED]
- Retention policy: [DAYS/YEARS]
- Alert coverage: [YES / NO]
- **Risk Level:** [LOW / MEDIUM / HIGH / CRITICAL]

## Remediation Roadmap
| Finding | Severity | Action | Owner | Deadline |
|---------|----------|--------|-------|----------|
| [FINDING] | [HIGH/MEDIUM/LOW] | [FIX] | [PERSON] | [DATE] |
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
