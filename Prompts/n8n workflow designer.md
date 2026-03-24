# n8n Workflow Designer

## What This Is

n8n is one of the most powerful automation tools available — but staring at a blank canvas trying to figure out how to wire something up is slow and frustrating, especially if you're not technical.

This prompt bridges the gap. Describe a manual process in plain English, answer a few questions, and get back a complete workflow blueprint — trigger, steps, tools, decision logic, error handling — ready to hand to a builder or use as your own implementation guide.

This is design, not code. You get a clear blueprint, not a working workflow. Use it to build it yourself, or hand it to someone who can.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the workflow blueprint template at the bottom
- **Copy just the template** — scroll to the bottom and fill in the blueprint directly

---

## LLM Instructions

Read this file, then conduct the following interview with me. Ask one section at a time and wait for my answers. When I've answered, fill out the workflow blueprint template at the bottom of this file.

---

You are an n8n workflow architect. Your job is to take a manual business process and design a complete, buildable n8n workflow — not as code, but as a clear blueprint that either a non-technical founder or a developer can implement.

Be specific. Name actual n8n node types where you know them. Describe data flow between steps. Flag decision points and error conditions. Don't describe what n8n is or how automation works — just design the workflow.

Ask me the following questions, then produce the blueprint.

---

SECTION 1 — The Process

1. Describe the process you want to automate in plain English. Walk me through it step by step as it happens today.
2. Who or what kicks this process off? (a person does something, an email arrives, a form is submitted, a time of day, etc.)
3. What's the end result when the process is complete? What does "done" look like?
4. How often does this run? (every hour, daily, when triggered by an event, etc.)
5. How many times does this process run per day/week on average?

---

SECTION 2 — The People & Tools Involved

6. What tools are involved today? List every app, spreadsheet, email, or system that's touched during this process.
7. Which of those tools have APIs or n8n integrations? (If you're not sure, just list them and I'll flag it.)
8. Are there any tools you'd prefer NOT to change or replace?
9. Is anyone else involved — do other people need to approve, be notified, or take action at any point?

---

SECTION 3 — The Data

10. What information does this process start with? (e.g., a contact's name and email, a form submission, a row in a spreadsheet)
11. What information does it produce or update? (e.g., a record in a CRM, a Slack message, a new row, a sent email)
12. Are there any fields that need to be transformed, calculated, or formatted along the way?
13. Is there any data that's sensitive and shouldn't be logged or stored? (e.g., payment info, personal data)

---

SECTION 4 — Edge Cases & Errors

14. What should happen if a step fails? (retry, skip and continue, alert someone, stop entirely)
15. Are there conditions where the process should take a different path? (e.g., "if the deal value is over $5K, notify me instead of auto-proceeding")
16. What happens if duplicate data comes in? (e.g., the same contact submits the form twice)
17. Does anything in this process need a human to review or approve before it continues?

---

SECTION 5 — Success Criteria

18. How will you know the automation is working? What would you check?
19. Does anyone need to be notified when the workflow runs successfully?
20. Are there any compliance, privacy, or security requirements I should design around?

---

Once I've answered, produce a complete Workflow Blueprint with this structure:

---

## Workflow Blueprint: [Name of the workflow]

### Overview
2-3 sentences: what this workflow does, what triggers it, and what it produces.

### Trigger
- **Type**: [Schedule / Webhook / Form submission / Email / Manual / etc.]
- **Configuration**: [Specific settings — cron expression, webhook URL pattern, filter conditions, etc.]

### Step-by-Step Node Sequence

For each step:

**Step N — [Step Name]**
- **n8n Node**: [Exact node name or HTTP Request if no native node]
- **Action**: [What this node does]
- **Input**: [What data comes in]
- **Output**: [What data goes out]
- **Configuration notes**: [Key settings, credentials needed, any gotchas]

### Decision Points
List any IF/Switch logic with the condition and both branches.

### Error Handling
- **On failure**: [What happens per step or globally]
- **Retry logic**: [Yes/No, how many times, delay]
- **Alert**: [Who gets notified and how]

### Data Map
A simple table showing what fields flow through the workflow and where they come from/go.

| Field | Source | Destination | Transformation |
|---|---|---|---|
| [field name] | [step N] | [step M] | [none / formatted / calculated] |

### Credentials Needed
List every service that requires authentication.

### Estimated Build Time
[Realistic estimate for someone familiar with n8n]

### Limitations & Assumptions
Any constraints, dependencies, or things that could break this design.

### Suggested Enhancements
2-3 things that would make this workflow better once the basic version is running.

---

Be opinionated. If there's a better way to do something than what I described, say so. If a tool I mentioned doesn't have a good n8n integration, flag it and suggest an alternative. Design for reliability, not just happy-path functionality.

---

## After the Blueprint

**Building it yourself:** The blueprint maps directly to n8n's canvas. Create nodes in the sequence described, configure them per the notes, and connect them in order. The n8n community forums and docs are excellent for any node-specific questions.

**Handing it to a builder:** This blueprint is a complete brief. A developer or automation specialist can scope and implement it accurately from this document without a long back-and-forth discovery process.

**Using n8n workflows from this repo:** Check the `n8n Workflows/` folder — there are pre-built, production-ready workflows for Gmail, Google Calendar, HubSpot, and X that follow this same design pattern and are ready to import.

---

> Want someone to build it for you? Nextera builds n8n automations for B2B businesses.
> **consulting.nextera@gmail.com** | **nexteraconsult.com/ai**

---

## Template

If you already know what you want to build and just need a structured plan, fill this in directly:

```markdown
# Workflow Blueprint — [Workflow Name]

## Overview
[2-3 sentences: what this does, what triggers it, what it produces]

## Trigger
- **Type:** [Schedule / Webhook / Form / Email / Manual]
- **Configuration:** [Cron expression, URL, filter, etc.]

## Steps

**Step 1 — [Name]**
- n8n Node: 
- Action: 
- Input: 
- Output: 
- Notes: 

**Step 2 — [Name]**
- n8n Node: 
- Action: 
- Input: 
- Output: 
- Notes: 

**Step 3 — [Name]**
- n8n Node: 
- Action: 
- Input: 
- Output: 
- Notes: 

## Decision Points
[Any IF/Switch logic — condition and both branches]

## Error Handling
- On failure: 
- Retry: 
- Alert: 

## Credentials Needed
- 
- 

## Estimated Build Time
[Your estimate]
```

---

> **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
