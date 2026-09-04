# 12. Follow-up drafts from call notes

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Sheets  
**Trigger:** a daily schedule, and optionally when a Granola or Gong transcript lands.  

## Overview

Draft follow-up emails from new external call notes. Do not send

## What's Needed From User

- Connectors: `Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a daily schedule, and optionally when a Granola or Gong transcript lands
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); mailbox (example: `you@company.com`, read-only unless the mode says send); calendar id and timezone (example: primary, `America/Los_Angeles`); CRM object and owner field (example: Opportunity, `OwnerId`)

## Procedure

1. Connect Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Follow-up drafts from call notes"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Draft follow-up emails from new external call notes. Do not send.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Follow-up drafts from call notes only after that first output matches the job.
8. Validate the next live fire of `a daily schedule, and optionally when a Granola or Gong transcript lands`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Follow-up drafts from call notes does this and nothing else — Draft follow-up emails from new external call notes. Do not send
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send. Never invent research or commitments that are not in the notes
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send. Never invent research or commitments that are not in the notes

## Prompt

```text
Create an Opulent automation named "Follow-up drafts from call notes".

Trigger: a daily schedule, and optionally when a Granola or Gong transcript lands.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Draft follow-up emails from new external call notes. Do not send.

IMPORTANT: If the bot already drafted a follow-up for this meeting id, skip it. Do not email the customer.

1. List external Calendar events that ended since the last successful run.
2. For each event, fetch Granola and/or Gong notes and transcript. If notes are missing, skip and record "no notes".
3. Extract commitments, dates, owners, and objections from the notes. Quote the transcript for anything you claim was said. Do not invent a next step.
4. Draft To, Subject, and body to the customer or prospect. Include concrete next steps that appeared on the call. Match the owner's voice from sent mail.
5. Save as a Gmail draft. Post the draft link in #gtm-followups or Slack DM to the owner, with the meeting title and CRM opportunity.
6. Update Salesforce or HubSpot next step, close date, and stakeholders only when the notes support the change. Write the quote or timestamp in the activity.
7. Log meeting id, draft link, and CRM fields changed in the Sheet.

CAUTION: Never auto-send. Never invent research or commitments that are not in the notes.
```
