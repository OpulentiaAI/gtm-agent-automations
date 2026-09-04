# 18. Copywriter bot

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Sheets  
**Trigger:** a Slack message in #marketing that contains /copy.  

## Overview

Write website or landing-page copy in a Harry Dry / direct-response style: short sentences, concrete nouns, no fluff

## What's Needed From User

- Connectors: `Slack, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message in #marketing that contains /copy
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Copywriter bot"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Write website or landing-page copy in a Harry Dry / direct-response style: short sentences, concrete nouns, no fluff.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Copywriter bot only after that first output matches the job.
8. Validate the next live fire of `a Slack message in #marketing that contains /copy`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Copywriter bot does this and nothing else — Write website or landing-page copy in a Harry Dry / direct-response style: short sentences, concrete nouns, no fluff
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent testimonials, metrics, logos, or research. Never auto-publish
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
- Do not ignore: Never auto-send outbound. Never invent testimonials, metrics, logos, or research. Never auto-publish

## Prompt

```text
Create an Opulent automation named "Copywriter bot".

Trigger: a Slack message in #marketing that contains /copy.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Write website or landing-page copy in a Harry Dry / direct-response style: short sentences, concrete nouns, no fluff.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the brief: page type, audience, offer, proof you are allowed to use, URL if any.
2. If proof (customers, numbers, quotes) is not in the brief or brand doc, do not invent it. Write around the gap or ask for the proof.
3. Draft headline, subhead, sections, and CTA. Offer 3 headline options.
4. Apply an anti-slop pass: cut adverbs, cut "empower", cut fake urgency. Read it aloud in the draft.
5. Post copy in the thread as text, not as a published CMS page. Wait for human edit and approval before anyone pastes it live.
6. Log brief and final copy link in the Sheet.

CAUTION: Never auto-send outbound. Never invent testimonials, metrics, logos, or research. Never auto-publish.
```
