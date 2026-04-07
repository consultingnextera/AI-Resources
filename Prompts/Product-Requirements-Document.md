# Product Requirements Document

Use this to define what you're building before engineering starts. The PRD captures the problem, user stories, success metrics, and technical requirements in a format that aligns product, design, and engineering.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a product manager. Interview the user about their product idea, then structure it as a PRD with problem statement, user personas, requirements, and acceptance criteria.

**SECTION 1 — Problem & Vision**

- What problem are you solving? Who has this problem?
- How are people solving this today? What's the gap or friction?
- What does success look like for your product? (user outcome, not feature list)
- Who are your main users? What's their background, motivation, and constraints?

**SECTION 2 — User Stories & Use Cases**

- Think of 2-3 main user personas. For each, what's their workflow using your product?
- What's the happy path? (user gets value with minimal friction)
- What are the edge cases or failure modes you need to handle?
- How would a user know your product is working well for them?

**SECTION 3 — Requirements & Features**

- What does the product need to do to solve the core problem?
- Are there required features, nice-to-have features, and out-of-scope items?
- What data does the product need to capture or store?
- Are there any integrations or external dependencies?

**SECTION 4 — Technical & Constraints**

- Are there performance requirements? (speed, latency, scalability)
- What about security, privacy, or compliance requirements?
- What's your launch timeline? (MVP in X weeks, full release in Y months)
- What are your resource constraints? (team size, budget, infrastructure)

**SECTION 5 — Success Metrics**

- How will you measure whether the product is successful?
- What's the baseline and target for each metric?
- When will you review progress? (weekly, monthly, quarterly)

Structure as a PRD with problem statement, user stories, feature requirements, and acceptance criteria.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# PRD: [PRODUCT NAME]

**Date:** [DATE] | **Version:** 1.0 | **Status:** [DRAFT / IN REVIEW / APPROVED]

## Problem Statement
**Problem:** [2-3 sentence description of the problem]
**Users affected:** [WHO]
**Current solution:** [HOW THEY SOLVE IT TODAY]
**Gap:** [WHAT'S MISSING OR BROKEN]

## Product Vision
[1-2 sentences describing what success looks like, user-centric, not feature-focused]

## User Personas
| Persona | Role | Goals | Pain Points |
|---------|------|-------|------------|
| [NAME] | [TITLE] | [WHAT THEY WANT TO ACHIEVE] | [FRICTION THEY FACE] |
| [NAME] | [TITLE] | [WHAT THEY WANT TO ACHIEVE] | [FRICTION THEY FACE] |

## User Stories & Acceptance Criteria
**Story 1:** As a [PERSONA], I want [ACTION] so that [OUTCOME]
- [ ] [ACCEPTANCE CRITERIA]
- [ ] [ACCEPTANCE CRITERIA]
- [ ] [ACCEPTANCE CRITERIA]

**Story 2:** As a [PERSONA], I want [ACTION] so that [OUTCOME]
- [ ] [ACCEPTANCE CRITERIA]
- [ ] [ACCEPTANCE CRITERIA]

## Feature Requirements

| Feature | Priority | Description | Success Criteria |
|---------|----------|-------------|------------------|
| [NAME] | [MUST / SHOULD / NICE] | [WHAT IT DOES] | [HOW YOU KNOW IT WORKS] |
| [NAME] | [MUST / SHOULD / NICE] | [WHAT IT DOES] | [HOW YOU KNOW IT WORKS] |

## Technical Requirements
- **Performance:** [SPEED, LATENCY, SCALABILITY]
- **Security:** [DATA PROTECTION, AUTH, COMPLIANCE]
- **Integrations:** [EXTERNAL SYSTEMS]
- **Data:** [WHAT DATA IS STORED, HOW LONG]

## Out of Scope
- [FEATURE / CAPABILITY EXPLICITLY NOT INCLUDED]
- [FEATURE / CAPABILITY EXPLICITLY NOT INCLUDED]

## Success Metrics
| Metric | Baseline | Target | Check-in Frequency |
|--------|----------|--------|-------------------|
| [METRIC NAME] | [CURRENT] | [GOAL] | [WEEKLY / MONTHLY] |
| [METRIC NAME] | [CURRENT] | [GOAL] | [WEEKLY / MONTHLY] |

## Timeline & Constraints
- **MVP launch:** [DATE]
- **Full release:** [DATE]
- **Team size:** [#] people
- **Key constraints:** [BUDGET / INFRASTRUCTURE / TALENT / etc.]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
