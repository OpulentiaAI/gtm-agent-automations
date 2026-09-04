# 27. Sales coach from Gong

**Category:** GTM · Account / enablement  
**Uses:** Slack, Gong, Sheets  
**Trigger:** a new Gong call with an external participant.  

## Overview

Coach the rep from an external Gong call. Private feedback only

## What's Needed From User

- Connectors: `Slack, Gong, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a new Gong call with an external participant
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Gong, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Sales coach from Gong"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Coach the rep from an external Gong call. Private feedback only.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Sales coach from Gong only after that first output matches the job.
8. Validate the next live fire of `a new Gong call with an external participant`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Sales coach from Gong does this and nothing else — Coach the rep from an external Gong call. Private feedback only
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never send this to the customer. Never invent transcript quotes
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gong, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never send this to the customer. Never invent transcript quotes

## Prompt

```text
Create an Opulent automation named "Sales coach from Gong".

Trigger: a new Gong call with an external participant.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Coach the rep from an external Gong call. Private feedback only.

IMPORTANT: If the bot already coached this call id, stop. Do not post feedback in a customer-facing channel.

1. Pull the Gong recording metadata, scorecards, and transcript. Confirm it is external. Skip internal calls.
2. Review talk ratio, discovery questions, next-step clarity, objection handling, and whether claims match the battlecard and product truth.
3. Quote timestamps for every piece of feedback. Do not invent a moment that is not on the call.
4. Write 3 strengths and 3 improvements, plus one drill for the next call.
5. Post feedback to the rep in a private Slack DM or #gtm-coaching. Do not post in the customer Slack.
6. Log call id, themes, and drill in the Sheet. Do not change CRM stage from coaching.

CAUTION: Never send this to the customer. Never invent transcript quotes.
```
