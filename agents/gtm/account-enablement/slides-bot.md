# 26. Slides bot

**Category:** GTM · Account / enablement  
**Uses:** Slack, Calendar, Granola, Figma  
**Trigger:** Calendar at meeting start for accounts with a Figma deck, or a Slack message that contains /heard.  

## Overview

Maintain the customer deck. Update the "What we've heard" slide from live notes

## What's Needed From User

- Connectors: `Slack, Calendar, Granola, Figma` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: Calendar at meeting start for accounts with a Figma deck, or a Slack message that contains /heard
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); calendar id and timezone (example: primary, `America/Los_Angeles`)

## Procedure

1. Connect Slack, Calendar, Granola, Figma. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Slides bot"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Maintain the customer deck. Update the "What we've heard" slide from live notes.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Slides bot only after that first output matches the job.
8. Validate the next live fire of `Calendar at meeting start for accounts with a Figma deck, or a Slack message that contains /heard`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Slides bot does this and nothing else — Maintain the customer deck. Update the "What we've heard" slide from live notes
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never invent customer quotes. Never overwrite the brand master. Never auto-send the deck
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Calendar, Granola, Figma, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never invent customer quotes. Never overwrite the brand master. Never auto-send the deck

## Prompt

```text
Create an Opulent automation named "Slides bot".

Trigger: Calendar at meeting start for accounts with a Figma deck, or a Slack message that contains /heard.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Maintain the customer deck. Update the "What we've heard" slide from live notes.

IMPORTANT: If the bot posted the message, stop. Do not fork a second deck for the same meeting id.

1. Identify the account and the Figma customer copy of the master deck. If no copy exists, duplicate the master and name it for the account. Do not edit the master.
2. Before the call, refresh title, attendees, and agenda from Calendar and CRM. Do not invent case-study metrics.
3. During or immediately after the call, read the Granola transcript. Update only the "What we've heard" slide with short bullets that quote the customer. Each bullet needs a timestamp.
4. If Granola has not landed yet, wait and retry once. Do not fill the slide from memory.
5. If translation was requested, duplicate the deck and translate while keeping layout. Flag untranslated screenshots.
6. Post the Figma link to the owner in Slack. Do not present or send the deck to the customer.
7. Log deck URL and "What we've heard" version on the opportunity.

CAUTION: Never invent customer quotes. Never overwrite the brand master. Never auto-send the deck.
```
