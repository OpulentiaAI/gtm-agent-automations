# 6. Signup-to-outbound loop

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets, Stripe, Airscale  
**Trigger:** a new Stripe customer or signup event.  

## Overview

A new person signed up for the product. Recover high-value signups that would otherwise sit in a generic email sequence

## What's Needed From User

- Connectors: `Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets, Stripe, Airscale` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a new Stripe customer or signup event
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets, Stripe, Airscale. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Signup-to-outbound loop"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: A new person signed up for the product. Recover high-value signups that would otherwise sit in a generic email sequence.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Signup-to-outbound loop only after that first output matches the job.
8. Validate the next live fire of `a new Stripe customer or signup event`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Signup-to-outbound loop does this and nothing else — A new person signed up for the product. Recover high-value signups that would otherwise sit in a generic email sequence
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never include Stripe payment data. Never invent employee count or phone
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets, Stripe, Airscale, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never include Stripe payment data. Never invent employee count or phone

## Prompt

```text
Create an Opulent automation named "Signup-to-outbound loop".

Trigger: a new Stripe customer or signup event.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A new person signed up for the product. Recover high-value signups that would otherwise sit in a generic email sequence.

The stack: Opulent is the brain, Stripe is signup data, Airscale is enrichment, GojiberryAI is intent plus outreach, Slack is the sales alert.

IMPORTANT: If the bot posted the Slack alert, stop. Do not post a second alert for the same Stripe customer id.

1. Use the Stripe MCP to read the new customer: email, name, company fields, plan, timestamp. Do not include payment method, card, or bank data in any note.
2. Identify the company from the email domain and Stripe metadata. Look up employee count from Airscale or the connected firmographic tool.
3. If the company has 20 or more employees, use Airscale to find LinkedIn and mobile number. Leave fields blank on miss. Do not invent a phone number.
4. Score whether this is a self-serve user or a potential account (company size, role if known, plan). Write the reasons.
5. For accounts that meet the 20+ employee bar, post one Slack alert in #gtm-signups with name, company, employee band, LinkedIn, role if known, and a suggested outbound angle grounded in the signup context. Tag the sales owner.
6. For every signup, not only the large ones, create or update the contact in Salesforce or HubSpot and push the record into GojiberryAI (list + context: signup, plan, company).
7. Ask Gojiberry to analyze signup plus intent, research the prospect, and draft a personalized LinkedIn and email message based on their context. Keep the Gojiberry campaign paused.
8. Do not let Gojiberry send LinkedIn or email until a human approves the Slack alert or an owner has pre-approved a paused-to-live rule in writing in the Sheet. Default is paused.
9. Never send a generic "you signed up" blast from this bot. The point of the loop is research → intent → personalized outreach, not a default email sequence.
10. Log Stripe customer id, company size, enrichment status, Slack permalink, Gojiberry campaign id, and send-approval status in the Sheet and CRM.

CAUTION: Never auto-send outbound. Never include Stripe payment data. Never invent employee count or phone.
```
