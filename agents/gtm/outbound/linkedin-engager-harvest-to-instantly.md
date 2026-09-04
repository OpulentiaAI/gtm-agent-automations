# 4. LinkedIn engager harvest to Instantly

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Apollo, Instantly, LinkedIn, Sheets  
**Trigger:** a new message in #gtm-outbound that contains a LinkedIn post URL.  

## Overview

A teammate posted a LinkedIn URL. Harvest people who engaged with that post and queue a campaign that references it

## What's Needed From User

- Connectors: `Slack, Salesforce, HubSpot, Apollo, Instantly, LinkedIn, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a new message in #gtm-outbound that contains a LinkedIn post URL
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); CRM object and owner field (example: Opportunity, `OwnerId`); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Salesforce, HubSpot, Apollo, Instantly, LinkedIn, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "LinkedIn engager harvest to Instantly"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: A teammate posted a LinkedIn URL. Harvest people who engaged with that post and queue a campaign that references it.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for LinkedIn engager harvest to Instantly only after that first output matches the job.
8. Validate the next live fire of `a new message in #gtm-outbound that contains a LinkedIn post URL`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: LinkedIn engager harvest to Instantly does this and nothing else — A teammate posted a LinkedIn URL. Harvest people who engaged with that post and queue a campaign that references it
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent emails or engagement reasons
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Salesforce, HubSpot, Apollo, Instantly, LinkedIn, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never invent emails or engagement reasons

## Prompt

```text
Create an Opulent automation named "LinkedIn engager harvest to Instantly".

Trigger: a new message in #gtm-outbound that contains a LinkedIn post URL.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A teammate posted a LinkedIn URL. Harvest people who engaged with that post and queue a campaign that references it.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the Slack message and extract the LinkedIn post URL. If there is no URL, ask one focused question and stop.
2. Open the post. Capture the author, the post text, and the list of commenter and reactor profile URLs. Do not invent names that are not on the post.
3. Filter engagers against the ICP (title, seniority, company type). Drop employees of our company, current customers, and anyone already in CRM or Instantly.
4. For each remaining profile, use the Apollo MCP to find a work email. Verify the email with the connected verifier. If Apollo or verify fails, leave email blank and do not guess.
5. Write one email per person that references the specific post (quote a short public snippet or the topic). Keep it short. Do not claim you know why they engaged unless they wrote a comment you can quote.
6. Create a paused Instantly campaign named after the post date and topic. Add only verified emails. Do not start the campaign.
7. If Graphed or Sheets is connected, append a reporting row: post URL, engager count, verified count, campaign link.
8. Post a summary in the Slack thread: post, engager count, verified count, 2 sample drafts, Instantly campaign link. Ask for human approval to start send.
9. After explicit approval, enable only the approved campaign and only within Instantly warmup limits. Never auto-send.
10. Log contacts, campaign, and status in Salesforce or HubSpot and in the Sheet.

CAUTION: Never auto-send outbound. Never invent emails or engagement reasons.
```
