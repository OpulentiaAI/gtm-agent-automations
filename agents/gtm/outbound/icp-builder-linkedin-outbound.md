# 1. ICP builder + LinkedIn outbound

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets  
**Trigger:** a Slack message in #gtm-outbound that contains /icp-outbound.  

## Overview

A teammate asked Opulent to build a specific ICP and run LinkedIn outbound through the GojiberryAI MCP. The full event details are below

## What's Needed From User

- Connectors: `Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message in #gtm-outbound that contains /icp-outbound
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "ICP builder + LinkedIn outbound"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: A teammate asked Opulent to build a specific ICP and run LinkedIn outbound through the GojiberryAI MCP. The full event details are below.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for ICP builder + LinkedIn outbound only after that first output matches the job.
8. Validate the next live fire of `a Slack message in #gtm-outbound that contains /icp-outbound`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: ICP builder + LinkedIn outbound does this and nothing else — A teammate asked Opulent to build a specific ICP and run LinkedIn outbound through the GojiberryAI MCP. The full event details are below
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent research. Roman's run still needed occasional manual intervention; treat send as a gated step
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never invent research. Roman's run still needed occasional manual intervention; treat send as a gated step

## Prompt

```text
Create an Opulent automation named "ICP builder + LinkedIn outbound".

Trigger: a Slack message in #gtm-outbound that contains /icp-outbound.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A teammate asked Opulent to build a specific ICP and run LinkedIn outbound through the GojiberryAI MCP. The full event details are below.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the Slack message, the thread, and any attached ICP notes, product URL, or competitor list.
2. If the product, ICP, or offer is missing, ask one focused question in the thread and stop.
3. Connect to the GojiberryAI MCP. Confirm LinkedIn accounts that the team already linked. Do not connect a new LinkedIn account without a human naming it.
4. Build a super-specific ICP: job titles, company types, employee bands, keywords, competitors, recently funded companies to track, buying signals, and exclusions. Write the ICP into a Sheet tab named "ICP".
5. Create or tune Gojiberry outreach agents against that ICP and the intent signals you identified. Record agent IDs in the Sheet.
6. Find prospects that match the ICP. Cap the first batch at a human-set limit. If none is set, cap at 100.
7. Enrich each prospect with email and phone through Gojiberry. If enrichment fails, leave the field blank. Do not invent contact data.
8. Research every prospect from primary sources only (LinkedIn, company site, funding news, recent posts). Cite the URL for every fact. If you cannot cite it, omit it.
9. Write a personalized LinkedIn connection note and a follow-up message for each prospect. Ground each line in a cited fact. Skip anyone already in CRM, already in a Gojiberry campaign, or already contacted in the last 90 days.
10. Post a review pack in the Slack thread: ICP summary, lead count, 2–3 sample message pairs, and a link to the Sheet. Ask a human to approve sending.
11. Do not send connection requests, emails, or InMails until a human replies with explicit approval. After approval, start sending only the approved batch through Gojiberry.
12. Log every prospect, message, send status, and source URL in Salesforce or HubSpot and in the Sheet. After replies arrive, classify them and alert #gtm-outbound. Do not auto-reply to inbound LinkedIn or email without human approval.

CAUTION: Never auto-send outbound. Never invent research. Roman's run still needed occasional manual intervention; treat send as a gated step.
```
