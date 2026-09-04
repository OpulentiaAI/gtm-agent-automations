# 28. Event / webinar pipeline

**Category:** GTM · Account / enablement  
**Uses:** Apollo, Instantly, Sheets, Airscale  
**Trigger:** a weekly schedule before the event, then a one-shot run after the event ends.  

## Overview

Run event or webinar pipeline work for the event named in the Sheet

## What's Needed From User

- Connectors: `Apollo, Instantly, Sheets, Airscale` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a weekly schedule before the event, then a one-shot run after the event ends
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Apollo, Instantly, Sheets, Airscale. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Event / webinar pipeline"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Run event or webinar pipeline work for the event named in the Sheet.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Event / webinar pipeline only after that first output matches the job.
8. Validate the next live fire of `a weekly schedule before the event, then a one-shot run after the event ends`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Event / webinar pipeline does this and nothing else — Run event or webinar pipeline work for the event named in the Sheet
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send invites or follow-ups. Never invent attendance
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Apollo, Instantly, Sheets, Airscale, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send invites or follow-ups. Never invent attendance

## Prompt

```text
Create an Opulent automation named "Event webinar pipeline".

Trigger: a weekly schedule before the event, then a one-shot run after the event ends.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Run event or webinar pipeline work for the event named in the Sheet.

IMPORTANT: If the bot already posted this phase's digest, stop.

1. Read event name, date, session topics, and ICP from the Sheet.
2. Before the event: build an invite list from ICP plus lookalikes in Apollo or Clay. Deduplicate against CRM and recent outreach. Draft personalized invites that cite a real reason they fit the session. Load a paused Instantly, Outreach, or email campaign. Do not send without approval.
3. After the event: import attendees, registrants, and no-shows. Enrich with Apollo or Airscale. Score engagement: attended, asked a question, visited pricing if analytics exist. Cite the source field.
4. Route hot accounts to AEs in #gtm-inbound with a session-specific talk track quoting their question or the session they sat in. Draft follow-ups. Do not send.
5. Put the rest in a nurture campaign as paused. Log every person, score, and route in CRM and the Sheet.
6. Wait for human approval before any invite or follow-up send.

CAUTION: Never auto-send invites or follow-ups. Never invent attendance.
```
