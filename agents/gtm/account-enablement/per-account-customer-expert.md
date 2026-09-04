# 25. Per-account customer expert

**Category:** GTM · Account / enablement  
**Uses:** Slack, Gmail, Salesforce, HubSpot, Gong, Granola, LinkedIn, Sheets, Notion  
**Trigger:** a weekly schedule, once per strategic account in the Sheet.  

## Overview

Act as the customer expert for one named strategic account. Update the state file. Do not spam the customer

## What's Needed From User

- Connectors: `Slack, Gmail, Salesforce, HubSpot, Gong, Granola, LinkedIn, Sheets, Notion` — least privilege that matches **Mode** (`see CAUTION · fail closed · quiet on noop`)
- Trigger: a weekly schedule, once per strategic account in the Sheet
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); mailbox (example: `you@company.com`, read-only unless the mode says send); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Gmail, Salesforce, HubSpot, Gong, Granola, LinkedIn, Sheets, Notion. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Per-account customer expert"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Act as the customer expert for one named strategic account. Update the state file. Do not spam the customer.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Per-account customer expert only after that first output matches the job.
8. Validate the next live fire of `a weekly schedule, once per strategic account in the Sheet`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Per-account customer expert does this and nothing else — Act as the customer expert for one named strategic account. Update the state file. Do not spam the customer
- Mode holds: see CAUTION · fail closed · quiet on noop
- Safety: Never email or Slack the customer automatically. Never invent quotes or tickets. Use the state file to avoid repeats
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gmail, Salesforce, HubSpot, Gong, Granola, LinkedIn, Sheets, Notion, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never email or Slack the customer automatically. Never invent quotes or tickets. Use the state file to avoid repeats

## Prompt

```text
Create an Opulent automation named "Per-account customer expert".

Trigger: a weekly schedule, once per strategic account in the Sheet.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Act as the customer expert for one named strategic account. Update the state file. Do not spam the customer.

IMPORTANT: If the bot already posted this week's rundown for this account, stop.

1. Read the account name from the trigger and the prior state file in Drive or Notion so you do not repeat last week's items.
2. Watch the account Slack channels, Gmail, Gong or Granola, and support tickets. Digest new threads and calls with quotes and timestamps.
3. Run a weekly media rundown: exec posts on X and LinkedIn, webinars, podcasts, blogs, competitor mentions. Include sentiment and quotes with timestamps or URLs.
4. Flag buying signals, feature requests, open tickets, and product features we shipped that match their requests. Cite each.
5. Write the new state file. Post a short rundown to the account team Slack channel, not to the customer.
6. Draft any customer-facing note for the owner. Do not send it.
7. Log signals, tickets, and feature matches on the Salesforce or HubSpot account.

CAUTION: Never email or Slack the customer automatically. Never invent quotes or tickets. Use the state file to avoid repeats.
```
