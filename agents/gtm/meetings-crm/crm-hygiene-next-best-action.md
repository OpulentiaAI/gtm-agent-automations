# 13. CRM hygiene + next-best-action

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Salesforce, HubSpot, Gong, Granola, Sheets  
**Trigger:** a daily schedule.  

## Overview

Keep Salesforce or HubSpot honest and recommend the next action. Short episode. Human approval for forecast-moving edits

## What's Needed From User

- Connectors: `Slack, Gmail, Salesforce, HubSpot, Gong, Granola, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a daily schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); mailbox (example: `you@company.com`, read-only unless the mode says send); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Gmail, Salesforce, HubSpot, Gong, Granola, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "CRM hygiene + next-best-action"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Keep Salesforce or HubSpot honest and recommend the next action. Short episode. Human approval for forecast-moving edits.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for CRM hygiene + next-best-action only after that first output matches the job.
8. Validate the next live fire of `a daily schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: CRM hygiene + next-best-action does this and nothing else — Keep Salesforce or HubSpot honest and recommend the next action. Short episode. Human approval for forecast-moving edits
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Do not mass-close or mass-stage-change. Never invent activity or research. Playbooks orchestrate; the bot does not override the owner
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gmail, Salesforce, HubSpot, Gong, Granola, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Do not mass-close or mass-stage-change. Never invent activity or research. Playbooks orchestrate; the bot does not override the owner

## Prompt

```text
Create an Opulent automation named "CRM hygiene next-best-action".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Keep Salesforce or HubSpot honest and recommend the next action. Short episode. Human approval for forecast-moving edits.

IMPORTANT: If the bot already posted today's hygiene digest, stop.

1. Pull open opportunities owned by the team, plus contacts with missing title, email, or account match.
2. For each open opp, read Gmail, Gong or Granola, and Slack for new activity since last close date or last activity field.
3. Propose updates: contacts, stage, next step, close date, stakeholders, amount. Each proposal must cite an email, call, or meeting. If you cannot cite it, do not propose it.
4. Apply low-risk writes automatically only if the Sheet says so: add missing contact, log activity, fill blank next step copied from a call note. Do not change stage, amount, or close date without human approval.
5. Flag stale deals (no human activity longer than the SLA in the Sheet, default 14 days) with a recommended next action from the playbook.
6. Post a digest to #gtm-revops: proposed field changes, stale deals, next-best-actions, and a one-click approval list.
7. After the owner approves, apply the remaining CRM writes. Log before/after in the Sheet.

CAUTION: Never auto-send outbound. Do not mass-close or mass-stage-change. Never invent activity or research. Playbooks orchestrate; the bot does not override the owner.
```
