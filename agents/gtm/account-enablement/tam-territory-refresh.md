# 29. TAM / territory refresh

**Category:** GTM · Account / enablement  
**Uses:** Salesforce, HubSpot, Apollo, Browserbase, Sheets  
**Trigger:** a monthly schedule.  

## Overview

Rebuild TAM and propose territory assignments. Do not move accounts without approval

## What's Needed From User

- Connectors: `Salesforce, HubSpot, Apollo, Browserbase, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a monthly schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Salesforce, HubSpot, Apollo, Browserbase, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "TAM / territory refresh"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Rebuild TAM and propose territory assignments. Do not move accounts without approval.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for TAM / territory refresh only after that first output matches the job.
8. Validate the next live fire of `a monthly schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: TAM / territory refresh does this and nothing else — Rebuild TAM and propose territory assignments. Do not move accounts without approval
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never invent TAM numbers. Never auto-reassign accounts. Never auto-send outbound
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Salesforce, HubSpot, Apollo, Browserbase, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never invent TAM numbers. Never auto-reassign accounts. Never auto-send outbound

## Prompt

```text
Create an Opulent automation named "TAM territory refresh".

Trigger: a monthly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Rebuild TAM and propose territory assignments. Do not move accounts without approval.

IMPORTANT: If the bot already posted this month's TAM digest, stop.

1. Rebuild TAM from firmographics and the custom signals listed in the Sheet (industry, size, tech, hiring, funding). Use Apollo, Clay, Crunchbase, and Browserbase as connected.
2. Score accounts with written reasons and source links. Drop rows with no source.
3. Attach contacts only when a provider returns them. Do not guess emails.
4. Compare current Salesforce or HubSpot territories with capacity and win rate. Propose a rebalance. Do not change owner yet.
5. Push prioritized lists with contacts to a Sheet per territory and post the digest to #gtm-revops.
6. After leadership approves, apply owner changes in CRM and log before/after.
7. Do not start outbound from this run.

CAUTION: Never invent TAM numbers. Never auto-reassign accounts. Never auto-send outbound.
```
