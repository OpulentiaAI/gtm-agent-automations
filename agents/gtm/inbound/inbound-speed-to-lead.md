# 8. Inbound speed-to-lead

**Category:** GTM · Inbound / conversion  
**Uses:** Slack, Calendar, Salesforce, HubSpot, Apollo, Sheets  
**Trigger:** a new form submission, chat, or demo request.  

## Overview

An inbound lead just arrived. Qualify and route fast. Do not let the lead go cold

## What's Needed From User

- Connectors: `Slack, Calendar, Salesforce, HubSpot, Apollo, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a new form submission, chat, or demo request
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); calendar id and timezone (example: primary, `America/Los_Angeles`); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Calendar, Salesforce, HubSpot, Apollo, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Inbound speed-to-lead"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: An inbound lead just arrived. Qualify and route fast. Do not let the lead go cold.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Inbound speed-to-lead only after that first output matches the job.
8. Validate the next live fire of `a new form submission, chat, or demo request`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Inbound speed-to-lead does this and nothing else — An inbound lead just arrived. Qualify and route fast. Do not let the lead go cold
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound sequences from inbound. Never invent company size or title. Default email is draft-only unless the playbook explicitly allows a form auto-reply
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Calendar, Salesforce, HubSpot, Apollo, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound sequences from inbound. Never invent company size or title. Default email is draft-only unless the playbook explicitly allows a form auto-reply

## Prompt

```text
Create an Opulent automation named "Inbound speed-to-lead".

Trigger: a new form submission, chat, or demo request.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

An inbound lead just arrived. Qualify and route fast. Do not let the lead go cold.

IMPORTANT: If the bot posted the Slack or CRM note, stop. Do not create a second lead record for the same email in this run.

1. Read the form, chat, or demo payload: name, email, company, page, UTM, comments.
2. Identify the company from domain and Clearbit, Clay, or Apollo. Enrich firmographics and likely role.
3. Score ICP fit and urgency from cited fields only (size, industry, page, message). If data is missing, say so.
4. Create or update the lead in Salesforce or HubSpot within this run. Do not duplicate.
5. If the lead is ICP and high urgency, post a Slack alert in #gtm-inbound tagging the AE on duty, with score, enrichment, and the inbound message.
6. Ask at most 2–4 qualifying questions via the connected chat (Qualified, Drift, HubSpot) or a drafted email. Do not send the email until a human or the documented playbook says inbound auto-reply is allowed for this form type.
7. If the playbook allows booking, offer Calendar / Calendly / Chili Piper slots and book the AE. If it does not, leave a draft booking link for the AE.
8. If not ICP, route to nurture. Do not start cold outbound to extra contacts at the company from this inbound without approval.
9. Log time-to-first-touch, score, route, and meeting in CRM and the Sheet.

CAUTION: Never auto-send outbound sequences from inbound. Never invent company size or title. Default email is draft-only unless the playbook explicitly allows a form auto-reply.
```
