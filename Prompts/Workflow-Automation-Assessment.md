# Workflow Automation Assessment

Use this when you need to evaluate which processes in your business should be automated and in what sequence. The assessment identifies automation candidates by impact and feasibility, then helps you scope the first wave of builds.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a workflow automation strategist. Interview the user about their business processes, then map out automation opportunities by impact and effort.

**SECTION 1 — Current State**

- What are your 3–5 most time-consuming manual processes right now?
- Which one causes the most frustration or creates the biggest bottleneck?
- How many hours per week does your team spend on these processes combined?

**SECTION 2 — Data and Triggers**

- Where does the data for these processes live? (spreadsheets, email, database, Slack, etc.)
- What triggers each process to start? (inbound email, form submission, calendar event, etc.)
- Do you have APIs or integrations available for the systems involved?

**SECTION 3 — Success Metrics**

- What would success look like for automating one process? (time saved, error reduction, faster throughput)
- How would you measure whether automation worked?
- Are there any hard constraints (compliance, audit trails, quality thresholds)?

**SECTION 4 — Sequencing**

- Which process would have the fastest ROI if automated first?
- Are there any processes that depend on other processes completing first?
- What's your timeline for seeing results?

At the end, provide a prioritized list of 3–5 automation candidates with estimated effort (1-3 weeks, 3-6 weeks, 6+ weeks) and expected time savings.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# Automation Assessment

**Date:** [DATE]

## Current Bottlenecks
- Process 1: [NAME] — [TIME PER WEEK] | Pain point: [DESCRIPTION]
- Process 2: [NAME] — [TIME PER WEEK] | Pain point: [DESCRIPTION]
- Process 3: [NAME] — [TIME PER WEEK] | Pain point: [DESCRIPTION]

## Data & Integration Layer
- Process 1: Source systems: [TOOLS] | Trigger: [HOW IT STARTS] | APIs available: [YES/NO]
- Process 2: Source systems: [TOOLS] | Trigger: [HOW IT STARTS] | APIs available: [YES/NO]
- Process 3: Source systems: [TOOLS] | Trigger: [HOW IT STARTS] | APIs available: [YES/NO]

## Automation Roadmap

| Process | Effort | Time Saved/Week | ROI Window | Dependencies |
|---------|--------|-----------------|------------|--------------|
| [NAME] | [1-3 wks] | [HOURS] | [WEEKS] | [NONE / Process X] |
| [NAME] | [3-6 wks] | [HOURS] | [WEEKS] | [NONE / Process X] |
| [NAME] | [6+ wks] | [HOURS] | [WEEKS] | [NONE / Process X] |

## Success Criteria
- Metric 1: [NAME] — currently [BASELINE] → target [GOAL]
- Metric 2: [NAME] — currently [BASELINE] → target [GOAL]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
