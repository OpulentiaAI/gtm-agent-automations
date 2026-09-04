# 2. Signal-triggered outbound

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Gmail, Salesforce, HubSpot, Gojiberry, Apollo, Instantly, LinkedIn, Sheets  
**Trigger:** a daily schedule.  

## Overview

Scan for new buying signals on named accounts and ICP lookalikes, then draft a same-day "why now" sequence

## What's Needed From User

- Connectors: `Slack, Gmail, Salesforce, HubSpot, Gojiberry, Apollo, Instantly, LinkedIn, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a daily schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); mailbox (example: `you@company.com`, read-only unless the mode says send); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Gmail, Salesforce, HubSpot, Gojiberry, Apollo, Instantly, LinkedIn, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Signal-triggered outbound"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Scan for new buying signals on named accounts and ICP lookalikes, then draft a same-day "why now" sequence.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Signal-triggered outbound only after that first output matches the job.
8. Validate the next live fire of `a daily schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Signal-triggered outbound does this and nothing else — Scan for new buying signals on named accounts and ICP lookalikes, then draft a same-day "why now" sequence
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent research
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gmail, Salesforce, HubSpot, Gojiberry, Apollo, Instantly, LinkedIn, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never invent research

## Prompt

```text
Create an Opulent automation named "Signal-triggered outbound".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Scan for new buying signals on named accounts and ICP lookalikes, then draft a same-day "why now" sequence.

IMPORTANT: If the bot posted the Slack digest, stop. Do not post a second digest. A second post can start a new run and cause a loop.

1. Load the named-account list and ICP from the Sheet tab "Target accounts" and from Salesforce or HubSpot.
2. For the past 24 hours, pull signals from the connected tools only: LinkedIn jobs / CoreSignal for role spikes and Head of AI (or equivalent) hires; Crunchbase or PitchBook for funding (for example Series B); BuiltWith for new tech installs; news APIs and company blogs for launches; CRM or product data for competitor churn if that source exists.
3. Drop any signal you cannot cite with a URL, job link, or filing. Do not invent a hire, round, or install.
4. Enrich the account and the likely buyer with Clay, Apollo, or Gojiberry. Waterfall-enrich email. Leave blanks when tools miss.
5. Skip contacts that are already in an open opportunity, were contacted in the last 90 days, or are on a suppression / unsubscribe list. Surface any open opp stage, amount, and last activity in the row.
6. For each remaining signal, write a "why now" angle that quotes the cited event in one sentence. Draft a short email and a shorter LinkedIn note off the same hook. Learn voice from 15–30 previously sent emails in Gmail if connected; otherwise use the brand voice doc.
7. Build a same-day 2–3 step sequence in Outreach, Salesloft, Smartlead, Instantly, or Gojiberry as a paused campaign. Do not enable send.
8. Post a digest to #gtm-outbound with account, signal, source link, draft copy, and a request for human approval. Approve 2–3 pairs before any full batch.
9. After explicit approval, enroll only the approved contacts. Respect domain warmup, daily volume caps, and unsubscribe handling. Do not send if warmup or caps are missing.
10. Log signal, copy, campaign, and outcome in CRM and in the Sheet. Reconcile the Sheet after any send.

CAUTION: Never auto-send outbound. Never invent research.
```
