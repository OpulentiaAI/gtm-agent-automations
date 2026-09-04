# 21. Figma production bot

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Figma, Sheets  
**Trigger:** a Slack message in #design that contains /figma, or a new row in the creative request Sheet.  

## Overview

Do repetitive Figma production work from the brand system. Do not invent a new visual language

## What's Needed From User

- Connectors: `Slack, Figma, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message in #design that contains /figma, or a new row in the creative request Sheet
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Figma, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Figma production bot"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Do repetitive Figma production work from the brand system. Do not invent a new visual language.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Figma production bot only after that first output matches the job.
8. Validate the next live fire of `a Slack message in #design that contains /figma, or a new row in the creative request Sheet`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Figma production bot does this and nothing else — Do repetitive Figma production work from the brand system. Do not invent a new visual language
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent copy, metrics, or research on the canvas. Never overwrite the master deck or brand library
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Figma, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never invent copy, metrics, or research on the canvas. Never overwrite the master deck or brand library

## Prompt

```text
Create an Opulent automation named "Figma production bot".

Trigger: a Slack message in #design that contains /figma, or a new row in the creative request Sheet.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Do repetitive Figma production work from the brand system. Do not invent a new visual language.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the request: asset type, size, copy source, target file. Open the brand master in Figma MCP.
2. Duplicate from existing components. Do not restyle tokens unless the request says to.
3. Place only copy that was provided or that a human already approved. Do not write new claims or metrics on the canvas.
4. Name layers cleanly. Put the output on a clearly labeled page. Share the Figma link in Slack.
5. If the request is ambiguous (wrong size, missing logo lockup), ask one question and stop.
6. Do not export to ads or CMS without human approval.
7. Log request, file link, and status in the Sheet.

CAUTION: Never auto-send outbound. Never invent copy, metrics, or research on the canvas. Never overwrite the master deck or brand library.
```
