# 20. Product demo recorder

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Sheets  
**Trigger:** a Slack message in #gtm-marketing that contains /demo and a screen list or URL list.  

## Overview

Record a product demo from a named list of screens. Do not publish the video

## What's Needed From User

- Connectors: `Slack, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message in #gtm-marketing that contains /demo and a screen list or URL list
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Product demo recorder"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Record a product demo from a named list of screens. Do not publish the video.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Product demo recorder only after that first output matches the job.
8. Validate the next live fire of `a Slack message in #gtm-marketing that contains /demo and a screen list or URL list`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Product demo recorder does this and nothing else — Record a product demo from a named list of screens. Do not publish the video
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never use production customer data. Never invent research or on-screen metrics. Never auto-publish. Never auto-send the video in outbound
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never use production customer data. Never invent research or on-screen metrics. Never auto-publish. Never auto-send the video in outbound

## Prompt

```text
Create an Opulent automation named "Product demo recorder".

Trigger: a Slack message in #gtm-marketing that contains /demo and a screen list or URL list.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Record a product demo from a named list of screens. Do not publish the video.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the requested screens, narrative, audience, and length. If the screen list is missing, ask once and stop.
2. Sign into the product with the demo account only. Never use a real customer workspace. Never copy customer data onto demo screens.
3. Walk the screens in order. Capture the recording with the connected recorder or the bot computer. Follow the script; do not ad-lib fake metrics on screen.
4. If a screen errors, stop that take, note the error, and do not publish a broken demo.
5. Drop the file in Drive or the demo library as draft. Post the link in the Slack thread for human review.
6. Do not upload to YouTube, the marketing site, or outbound sequences until a human approves.
7. Log script, screens, file link, and approval in the Sheet.

CAUTION: Never use production customer data. Never invent research or on-screen metrics. Never auto-publish. Never auto-send the video in outbound.
```
