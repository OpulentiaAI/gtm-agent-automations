# 17. Landing-page CRO auditor

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Browserbase, Sheets  
**Trigger:** a Slack message in #marketing that contains a URL and /cro, or a daily schedule against a watched URL list.  

## Overview

Audit a landing page. Return a scored memo, one priority fix, A/B picks, and an AI-smell check

## What's Needed From User

- Connectors: `Slack, Browserbase, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message in #marketing that contains a URL and /cro, or a daily schedule against a watched URL list
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Browserbase, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Landing-page CRO auditor"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Audit a landing page. Return a scored memo, one priority fix, A/B picks, and an AI-smell check.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Landing-page CRO auditor only after that first output matches the job.
8. Validate the next live fire of `a Slack message in #marketing that contains a URL and /cro, or a daily schedule against a watched URL list`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Landing-page CRO auditor does this and nothing else — Audit a landing page. Return a scored memo, one priority fix, A/B picks, and an AI-smell check
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send outbound. Never invent metrics or research. Never publish page changes
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Browserbase, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send outbound. Never invent metrics or research. Never publish page changes

## Prompt

```text
Create an Opulent automation named "Landing-page CRO auditor".

Trigger: a Slack message in #marketing that contains a URL and /cro, or a daily schedule against a watched URL list.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Audit a landing page. Return a scored memo, one priority fix, A/B picks, and an AI-smell check.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Extract the URL. Open it with Browserbase or the browser. Capture headline, subhead, CTA, social proof, form, and obvious performance issues. Screenshot if possible.
2. If the page 404s or is blocked, report that and stop.
3. Score the page on a short rubric: clarity of offer, CTA, proof, friction, message match to ads/UTM if provided. Use only what is on the page or in linked analytics (GA4) if connected.
4. Name one priority fix. Propose 2–3 A/B picks that change one variable each.
5. Run an AI-smell check: generic claims, stock phrasing, leftover placeholder, mismatched voice. Quote the offending lines.
6. Do not invent conversion rates, lift, or competitor stats. If GA4 is connected, report real numbers with the date range. If not, omit metrics.
7. Post the memo in the Slack thread. Log URL, score, and priority fix in the Sheet. Do not edit the live page.

CAUTION: Never auto-send outbound. Never invent metrics or research. Never publish page changes.
```
