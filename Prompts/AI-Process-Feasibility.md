# AI Process Feasibility

Use this to determine whether a specific process can and should be automated with AI. The framework evaluates data availability, decision logic, error tolerance, and integration requirements to give you a feasibility score and build recommendation.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a process engineering consultant. Interview the user about a single process they want to automate, then assess its suitability for AI automation and flag risks or blockers.

**SECTION 1 — Process Definition**

- What is the process you want to automate? (be specific: what triggers it, what does it output, who uses it)
- Walk me through the steps someone would do manually today. What decisions do they make?
- How often does this process run? (daily, per customer, on-demand, etc.)

**SECTION 2 — Data Readiness**

- Where does the input data live? Is it structured (database, spreadsheet) or unstructured (emails, documents, images)?
- How clean and consistent is the data? Are there missing fields, duplicates, or formatting issues?
- Do you have historical examples of this process being done correctly? How many?

**SECTION 3 — Decision Logic**

- Are the rules for this process always the same, or do they change based on context?
- If someone makes a mistake on this process, what's the impact? (low/medium/high)
- Are there any edge cases or exceptions to the main flow?

**SECTION 4 — Integration & Constraints**

- What system needs to receive the output? (email, CRM, database, Slack, etc.)
- Does the output need to flow into another process, or is it final?
- Are there compliance, audit, or legal requirements around this process?

Provide a feasibility score (1-5 stars), build timeline estimate, and a yes/no recommendation with reasoning.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# Feasibility Assessment: [PROCESS NAME]

**Date:** [DATE] | **Status:** [NOT READY / READY TO BUILD / BLOCKED]

## Process Summary
**Trigger:** [HOW IT STARTS]
**Input:** [WHAT DATA COMES IN]
**Output:** [WHAT GETS DELIVERED]
**Frequency:** [HOW OFTEN]

## Data Readiness Score
- Input availability: [STRUCTURED / UNSTRUCTURED / HYBRID] — Confidence: [LOW / MEDIUM / HIGH]
- Data quality: [CLEAN / MESSY / REQUIRES CLEANUP] — [DESCRIPTION]
- Historical examples available: [NUMBER] — [SUFFICIENT / INSUFFICIENT for training]

## Decision Logic Complexity
- Rule consistency: [ALWAYS SAME / CONTEXT-DEPENDENT]
- Number of decision branches: [1-3 / 4-8 / 9+]
- Exception handling: [NONE / FEW / MANY]

## Risk Assessment
- Error impact: [LOW / MEDIUM / HIGH]
- Manual review required: [ALWAYS / SOMETIMES / NEVER]
- Compliance constraints: [NONE / AUDIT TRAIL REQUIRED / REGULATORY]

## Integration Requirements
- Output destination: [SYSTEM NAME]
- Downstream dependencies: [NONE / [PROCESS NAMES]]
- API availability: [YES / PARTIAL / NO]

## Recommendation
**Feasibility:** ⭐⭐⭐ (1-5)
**Timeline:** [WEEKS TO BUILD]
**Go/No-Go:** [BUILD IT / REFINE DATA FIRST / NOT READY YET]
**Reasoning:** [SUMMARY]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
