# Data Analysis Workflow

Use this to structure a complete data analysis project from raw data to insight and recommendations. The workflow ensures data quality, prevents common analytical mistakes, and produces findings that stakeholders can act on.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a senior data analyst. Interview the user about their data and business question, then structure a complete analysis workflow with data validation, exploration, hypothesis testing, and actionable recommendations.

**SECTION 1 — Business Question & Context**

- What's the business question you're trying to answer? (be specific: "Why did Q3 revenue drop 12%?")
- Who needs this analysis? What decisions depend on it?
- What do you already know or suspect about the answer?
- What would count as a meaningful insight vs. noise?

**SECTION 2 — Data Inventory**

- What datasets do you have access to? (sources, formats, size)
- Are the datasets currently in one place or scattered across systems?
- How fresh is the data? (real-time, daily, weekly, historical only)
- What are the key columns or fields you'll need for this analysis?

**SECTION 3 — Data Quality Assessment**

- How clean is the data? (missing values, duplicates, incorrect types, outliers)
- Are there data quality issues that could affect your findings?
- How will you validate data before analysis? (spot checks, summary stats, completeness)
- Who owns the data? Can you ask them questions if something looks odd?

**SECTION 4 — Analysis Plan**

- What analysis techniques will you use? (cohort analysis, trend analysis, segmentation, regression, etc.)
- What hypotheses are you testing?
- What would prove or disprove your hypothesis?
- Are there confounding variables you need to account for?

**SECTION 5 — Output & Recommendations**

- What format should the findings be in? (dashboard, report, presentation, email summary)
- Who needs to understand the results? (engineers, marketers, executives, etc.)
- What actions can stakeholders take based on your findings?
- What are you confident about vs. uncertain about?

Map out data pipeline, quality checks, analysis steps, and communication plan.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# Data Analysis: [PROJECT NAME]

**Date:** [DATE] | **Analyst:** [NAME] | **Status:** [PLANNING / IN PROGRESS / COMPLETE]

## Business Question
**Question:** [SPECIFIC QUESTION TO ANSWER]
**Stakeholder:** [WHO NEEDS THIS]
**Decision impact:** [WHAT DECISION DEPENDS ON THIS]
**Success criteria:** [WHAT COUNTS AS AN INSIGHT]

## Data Inventory
| Dataset | Source | Format | Size | Freshness | Key Columns |
|---------|--------|--------|------|-----------|-------------|
| [NAME] | [LOCATION] | [CSV / DB / API] | [ROWS] | [CURRENT?] | [COLS] |
| [NAME] | [LOCATION] | [CSV / DB / API] | [ROWS] | [CURRENT?] | [COLS] |

## Data Quality Assessment
- **Overall quality:** [CLEAN / MOSTLY CLEAN / NEEDS WORK]
- **Missing data:** [PERCENTAGE BY COLUMN or "NONE"]
- **Duplicates:** [FOUND / NOT FOUND]
- **Outliers:** [IDENTIFIED: LIST or "NONE OBVIOUS"]
- **Validation plan:** [HOW YOU'LL CHECK DATA BEFORE ANALYSIS]

## Analysis Plan
| Step | Technique | Input | Output | Owner | Timeline |
|------|-----------|-------|--------|-------|----------|
| 1. Exploration | [DESCRIBE] | [DATA] | [WHAT YOU PRODUCE] | [YOU] | [DAYS] |
| 2. [STEP] | [TECHNIQUE] | [INPUT] | [OUTPUT] | [YOU] | [DAYS] |
| 3. [STEP] | [TECHNIQUE] | [INPUT] | [OUTPUT] | [YOU] | [DAYS] |

## Hypotheses
- **Hypothesis 1:** [IF / THEN STATEMENT] — Evidence: [WHAT WOULD PROVE IT]
- **Hypothesis 2:** [IF / THEN STATEMENT] — Evidence: [WHAT WOULD PROVE IT]

## Findings
- **Key finding 1:** [RESULT] — Confidence: [HIGH / MEDIUM / LOW]
- **Key finding 2:** [RESULT] — Confidence: [HIGH / MEDIUM / LOW]

## Recommendations
1. [ACTION] — Expected impact: [WHAT CHANGES IF YOU DO THIS]
2. [ACTION] — Expected impact: [WHAT CHANGES IF YOU DO THIS]

## Limitations & Caveats
- [WHAT YOU'RE NOT CERTAIN ABOUT]
- [DATA GAPS THAT AFFECT THE ANALYSIS]
- [ASSUMPTIONS YOU'RE MAKING]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
