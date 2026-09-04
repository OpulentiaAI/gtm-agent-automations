# 23. Paid campaign optimizer

**Category:** GTM · Marketing / content / creative  
**Uses:** LinkedIn, Figma, Sheets  
**Trigger:** a weekly schedule.  

## Overview

Review paid performance and propose budget and creative changes. Do not spend money without approval

## What's Needed From User

- Connectors: `LinkedIn, Figma, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a weekly schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect LinkedIn, Figma, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Paid campaign optimizer"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Review paid performance and propose budget and creative changes. Do not spend money without approval.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Paid campaign optimizer only after that first output matches the job.
8. Validate the next live fire of `a weekly schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Paid campaign optimizer does this and nothing else — Review paid performance and propose budget and creative changes. Do not spend money without approval
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Do not pause, start, or reallocate spend without human approval. Never invent ROAS, CPA, or research
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in LinkedIn, Figma, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Do not pause, start, or reallocate spend without human approval. Never invent ROAS, CPA, or research

## Prompt

```text
Create an Opulent automation named "Paid campaign optimizer".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Review paid performance and propose budget and creative changes. Do not spend money without approval.

IMPORTANT: If the bot already posted this week's paid digest, stop.

1. Pull Google Ads, Meta Ads, and LinkedIn Ads via their APIs or MCPs, plus GA4 and CRM conversions, for the past 7 days and the prior 7 days.
2. Rank campaigns, ad sets, and creatives by CPA, ROAS, and volume. Use only platform-reported numbers. State the window.
3. Propose pausing creatives or ads that fail the documented threshold in the Sheet. Propose shifting budget to winners. Do not execute pause or budget changes yet.
4. Generate new creative copy and Figma or ad-variant briefs from the top-performing messages. Do not invent proof.
5. Post a "what changed and why" memo to #growth-paid with tables, proposed actions, and new creative drafts.
6. After a human approves named actions, apply only those pause/budget edits. Recheck spend caps.
7. Log proposals, approvals, and live changes in the Sheet and CRM conversion mapping.

CAUTION: Never auto-send outbound. Do not pause, start, or reallocate spend without human approval. Never invent ROAS, CPA, or research.
```
