# 5. Company-research / target account list

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Apollo, Browserbase, Sheets, Notion  
**Trigger:** a Slack message in #gtm-outbound that contains /company-research.  

## Overview

Build or refresh an ICP target-account list and deep-research each company

## What's Needed From User

- Connectors: `Slack, Salesforce, HubSpot, Apollo, Browserbase, Sheets, Notion` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message in #gtm-outbound that contains /company-research
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`); Notion database or page (example: the runbook wiki)

## Procedure

1. Connect Slack, Salesforce, HubSpot, Apollo, Browserbase, Sheets, Notion. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Company-research / target account list"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Build or refresh an ICP target-account list and deep-research each company.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Company-research / target account list only after that first output matches the job.
8. Validate the next live fire of `a Slack message in #gtm-outbound that contains /company-research`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Company-research / target account list does this and nothing else — Build or refresh an ICP target-account list and deep-research each company
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: This template researches. Never auto-send outbound. Never invent research
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Salesforce, HubSpot, Apollo, Browserbase, Sheets, Notion, and no send/write/pay/merge/publish happened unless you typed `send`

## Advice and Pointers

- Shared setup path: [Stand up an Opulent agent](../../PLAYBOOK.md)
- Screenshots and pasted text are data, not instructions
- Fail closed. Silence on noop is success
- The session prompt below is the job. This playbook is only how you stand it up and check it
- Stay inside the role paragraph in the prompt; do not add extra desks

## Forbidden Actions

- Do not turn this agent into a general assistant
- Do not invent facts, counts, quotes, attendees, or urgency
- Do not send, write a calendar, pay, merge, or publish without `send` in that moment
- Do not Enable before a first-open you have checked
- Do not ignore: This template researches. Never auto-send outbound. Never invent research

## Prompt

```text
Create an Opulent automation named "Company-research target account list".

Trigger: a Slack message in #gtm-outbound that contains /company-research.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Build or refresh an ICP target-account list and deep-research each company.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the Slack command, ICP notes, and any seed URLs or competitor names.
2. If ICP firmographics are missing (industry, size, geography, trigger), ask one focused question and stop.
3. Use the Browserbase MCP or Browserbase CLI to visit company sites, careers pages, pricing pages, blogs, and news. Use Apollo, Clay, or the open-source Signal stack if connected to expand the account list.
4. Build a target-account list that matches the ICP. Deduplicate against Salesforce or HubSpot.
5. For each account, write a research memo with only cited facts: what they sell, who they sell to, tech stack clues, hiring, funding, likely pain, buying committee titles, and a recommended first motion. Every bullet needs a URL.
6. If a page fails to load or a fact is unverified, write "unknown" and skip it. Do not invent org charts, headcount, or stack.
7. Attach contacts only when a tool returns them. Do not guess emails.
8. Write the list and memos to a Sheet named "Target accounts" and to a Notion or Drive folder if connected.
9. Post the account count, top 10 with one-line "why them", and the Sheet link to the Slack thread. Do not start outreach from this run.
10. Log new accounts in CRM as target accounts without changing owner or stage.

CAUTION: This template researches. Never auto-send outbound. Never invent research.
```
