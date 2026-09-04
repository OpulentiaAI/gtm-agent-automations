# 10. Daily meeting prep

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Figma, Sheets  
**Trigger:** a daily schedule at 06:30 America/Chicago.  

## Overview

Prepare the owner for today's external meetings. Output must be short and readable on a phone

## What's Needed From User

- Connectors: `Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Figma, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a daily schedule at 06:30 America/Chicago
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); mailbox (example: `you@company.com`, read-only unless the mode says send); calendar id and timezone (example: primary, `America/Los_Angeles`); CRM object and owner field (example: Opportunity, `OwnerId`)

## Procedure

1. Connect Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Figma, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Daily meeting prep"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Prepare the owner for today's external meetings. Output must be short and readable on a phone.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Daily meeting prep only after that first output matches the job.
8. Validate the next live fire of `a daily schedule at 06:30 America/Chicago`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Daily meeting prep does this and nothing else — Prepare the owner for today's external meetings. Output must be short and readable on a phone
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send anything to the customer. Never invent research, numbers, or prior commitments
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Figma, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send anything to the customer. Never invent research, numbers, or prior commitments

## Prompt

```text
Create an Opulent automation named "Daily meeting prep".

Trigger: a daily schedule at 06:30 America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Prepare the owner for today's external meetings. Output must be short and readable on a phone.

IMPORTANT: If the bot already posted today's prep in #gtm-meeting-prep or emailed it, stop. Do not send a second copy.

1. Use Calendar to list external meetings for today. Skip internal 1:1s unless they are tagged customer or prospect.
2. For each meeting, pull Salesforce or HubSpot: account, opportunity stage, amount, close date, last activity, stakeholders.
3. Pull recent Gmail threads with those contacts, Slack mentions, and the latest Granola or Gong notes. If none exist, say "no prior notes".
4. If still thin, do fresh research on the company site, news, hiring, and 10-K or earnings when public. Cite URLs. Do not invent.
5. Write a one-page brief per meeting: who will be there, relationship history, open opp, goal for the call, talk tracks, likely objections, one relevant case study, and risks. Keep it skimmable.
6. If the Slides / Figma bot or a master deck is connected and the meeting is a customer call, attach or update a custom deck copy. Do not invent quotes on a "What we've heard" slide; only use Granola/Gong text.
7. Post the briefs to #gtm-meeting-prep and/or email the owner. Do not email the customer.
8. Log that prep ran (meeting id, time, brief link) in the Sheet.

CAUTION: Never auto-send anything to the customer. Never invent research, numbers, or prior commitments.
```
