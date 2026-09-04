# 3. Autonomous outbound SDR

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Calendar, Salesforce, HubSpot, Gojiberry, Apollo, LinkedIn, Sheets  
**Trigger:** a daily schedule at 06:00 America/Chicago.  

## Overview

Run one outbound SDR episode against the live ICP. Keep the episode short. Encode results so the next run can learn

## What's Needed From User

- Connectors: `Slack, Calendar, Salesforce, HubSpot, Gojiberry, Apollo, LinkedIn, Sheets` — least privilege that matches **Mode** (`see CAUTION · fail closed · quiet on noop`)
- Trigger: a daily schedule at 06:00 America/Chicago
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); calendar id and timezone (example: primary, `America/Los_Angeles`); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Calendar, Salesforce, HubSpot, Gojiberry, Apollo, LinkedIn, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Autonomous outbound SDR"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Run one outbound SDR episode against the live ICP. Keep the episode short. Encode results so the next run can learn.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Autonomous outbound SDR only after that first output matches the job.
8. Validate the next live fire of `a daily schedule at 06:00 America/Chicago`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Autonomous outbound SDR does this and nothing else — Run one outbound SDR episode against the live ICP. Keep the episode short. Encode results so the next run can learn
- Mode holds: see CAUTION · fail closed · quiet on noop
- Safety: Do not give send-authority before domain warmup, volume caps, unsubscribe handling, and a review path exist. Hybrid pods (one human SDR overseeing 2–3 agent seats) beat set-and-forget on meeting quality
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Calendar, Salesforce, HubSpot, Gojiberry, Apollo, LinkedIn, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Do not give send-authority before domain warmup, volume caps, unsubscribe handling, and a review path exist. Hybrid pods (one human SDR overseeing 2–3 agent seats) beat set-and-forget on meeting quality

## Prompt

```text
Create an Opulent automation named "Autonomous outbound SDR".

Trigger: a daily schedule at 06:00 America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Run one outbound SDR episode against the live ICP. Keep the episode short. Encode results so the next run can learn.

IMPORTANT: If the bot posted the Slack summary, stop. Do not post a second summary.

1. Load ICP, exclusions, daily volume cap, and suppression lists from the Sheet and from Salesforce or HubSpot.
2. Source new accounts and contacts from Apollo, ZoomInfo, or Clay. Prefer intent sources when connected: 6sense, Common Room, job posts, funding, tech installs, web visits.
3. Waterfall-enrich missing emails and titles. Do not guess an email pattern. If every provider misses, mark "unenriched" and skip send.
4. Score each contact against ICP plus intent. Write the score reasons as cited facts. Drop anyone below the documented threshold.
5. Skip already-touched contacts. Surface open opportunity stage, amount, and last activity when they exist.
6. Draft a persona-specific email sequence and a shorter LinkedIn note off the same hook. Pull style from 15–30 sent emails. Cite research. Never invent research. If a claim has no source, delete it.
7. Load drafts into Outreach, Salesloft, Smartlead, Artisan Ava, 11x Alice, or Gojiberry as paused. Post 2–3 sample pairs to #gtm-outbound and wait for human approval before any send.
8. After approval, send only within warmup and volume caps. Never send without that approval.
9. Classify new replies: meeting, question, objection, not-now, unsubscribe, out-of-office, other. Draft a reply. Do not send the reply.
10. For meeting-intent replies, offer times from Calendar / Calendly / Chili Piper and hand off to the AE in Slack. Do not book over an existing hold without the owner.
11. Log source, score, sequence, reply label, and next action in CRM and in the live Sheet. Reconcile the Sheet after sending.
12. Stop when the daily cap is hit or when the review queue is still waiting on a human.

CAUTION: Do not give send-authority before domain warmup, volume caps, unsubscribe handling, and a review path exist. Hybrid pods (one human SDR overseeing 2–3 agent seats) beat set-and-forget on meeting quality.
```
