# 9. PLG / PQL sales handoff

**Category:** GTM · Inbound / conversion  
**Uses:** Slack, Salesforce, HubSpot, Apollo, Sheets, Stripe, Airscale  
**Trigger:** a daily schedule.  

## Overview

Find product-qualified accounts that crossed a usage threshold and hand them to sales or CS

## What's Needed From User

- Connectors: `Slack, Salesforce, HubSpot, Apollo, Sheets, Stripe, Airscale` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a daily schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Salesforce, HubSpot, Apollo, Sheets, Stripe, Airscale. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "PLG / PQL sales handoff"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Find product-qualified accounts that crossed a usage threshold and hand them to sales or CS.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for PLG / PQL sales handoff only after that first output matches the job.
8. Validate the next live fire of `a daily schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: PLG / PQL sales handoff does this and nothing else — Find product-qualified accounts that crossed a usage threshold and hand them to sales or CS
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent usage numbers. Never include Stripe payment data
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Salesforce, HubSpot, Apollo, Sheets, Stripe, Airscale, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never invent usage numbers. Never include Stripe payment data

## Prompt

```text
Create an Opulent automation named "PLG PQL sales handoff".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Find product-qualified accounts that crossed a usage threshold and hand them to sales or CS.

IMPORTANT: If the bot posted the Slack alert for an account today, skip that account. Do not double-alert.

1. Pull usage from PostHog, Amplitude, Mixpanel, or the warehouse: seats, feature adoption, invites, usage spikes, plan limits. Use Stripe for plan and expansion revenue fields. Do not include payment credentials.
2. Resolve the company from workspace domain or billing email. Enrich decision-makers with Apollo, Clay, or Airscale.
3. Score expansion-assist vs stay-self-serve using the documented PQL rules in the Sheet. Write the rule hits as facts (for example "seats went from N to M on date").
4. Skip accounts with an open sales-assisted opportunity or a CSM task created in the last 7 days. Surface current stage and owner.
5. Post a Slack alert in #gtm-pql with account, usage facts, suggested play (AE outbound vs CSM expansion), and 2–3 decision-maker contacts with sources.
6. Draft an outbound or CSM message that references the product usage, not a cold pitch. Do not send it.
7. After human approval, log the task on the opportunity or account in Salesforce or HubSpot, attach the draft, and only then allow send from the owner or an approved sequence.
8. Update the PQL Sheet: account, threshold, score, owner, approval, outcome.

CAUTION: Never auto-send outbound. Never invent usage numbers. Never include Stripe payment data.
```
