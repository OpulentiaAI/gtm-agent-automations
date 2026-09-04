# 7. Closed-lost / no-show re-engagement

**Category:** GTM · Outbound / prospecting  
**Uses:** Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Gojiberry, Instantly, LinkedIn, Sheets  
**Trigger:** a weekly schedule.  

## Overview

Find closed-lost and no-show accounts whose timing may have changed, and queue re-engagement

## What's Needed From User

- Connectors: `Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Gojiberry, Instantly, LinkedIn, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a weekly schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: mailbox (example: `you@company.com`, read-only unless the mode says send); calendar id and timezone (example: primary, `America/Los_Angeles`); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Gojiberry, Instantly, LinkedIn, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Closed-lost / no-show re-engagement"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Find closed-lost and no-show accounts whose timing may have changed, and queue re-engagement.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Closed-lost / no-show re-engagement only after that first output matches the job.
8. Validate the next live fire of `a weekly schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Closed-lost / no-show re-engagement does this and nothing else — Find closed-lost and no-show accounts whose timing may have changed, and queue re-engagement
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent research or a past conversation
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Gojiberry, Instantly, LinkedIn, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never invent research or a past conversation

## Prompt

```text
Create an Opulent automation named "Closed-lost no-show re-engagement".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Find closed-lost and no-show accounts whose timing may have changed, and queue re-engagement.

IMPORTANT: If the bot posted the weekly digest, stop. Do not post a second digest.

1. Pull opportunities in Salesforce or HubSpot with stage closed-lost, and meetings with no-show in Calendar or the meeting tool, from the lookback window in the Sheet (default 18 months for lost, 90 days for no-shows).
2. For each account, read the original close reason, last call notes from Gong or Granola, and last email thread in Gmail. Quote the original context. Do not invent a reason.
3. Scan for new triggers since the loss or no-show: funding, exec hire, product launch, job spike, tech change, new inbound, usage return. Cite each trigger. If none exists, skip the account.
4. Skip anyone who asked not to be contacted, who is in an open opportunity, or who was emailed about re-engagement in the last 60 days.
5. Draft a short "timing changed" email and LinkedIn note that references the original conversation and the new cited trigger. Do not pretend a meeting happened that did not.
6. Load drafts into a paused sequence in Gojiberry, Instantly, or Outreach. Post the list to #gtm-outbound with account, original reason, new trigger link, and draft.
7. Wait for the owner to approve. Never auto-send. After approval, enroll only approved people and log the re-open motion in CRM.
8. Update the Sheet: account, loss date, trigger, approval, send status, outcome.

CAUTION: Never auto-send outbound. Never invent research or a past conversation.
```
