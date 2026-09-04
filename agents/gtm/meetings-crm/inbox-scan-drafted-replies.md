# 11. Inbox scan + drafted replies

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Gong, Granola, Sheets  
**Trigger:** a daily schedule.  

## Overview

Scan Gmail (and Slack DMs if connected) for threads that need the owner. Draft replies. Do not send

## What's Needed From User

- Connectors: `Slack, Gmail, Gong, Granola, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a daily schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); mailbox (example: `you@company.com`, read-only unless the mode says send); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, Gmail, Gong, Granola, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Inbox scan + drafted replies"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Scan Gmail (and Slack DMs if connected) for threads that need the owner. Draft replies. Do not send.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Inbox scan + drafted replies only after that first output matches the job.
8. Validate the next live fire of `a daily schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Inbox scan + drafted replies does this and nothing else — Scan Gmail (and Slack DMs if connected) for threads that need the owner. Draft replies. Do not send
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send. Never invent research. Never reply to a thread the bot itself created
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gmail, Gong, Granola, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send. Never invent research. Never reply to a thread the bot itself created

## Prompt

```text
Create an Opulent automation named "Inbox scan drafted replies".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Scan Gmail (and Slack DMs if connected) for threads that need the owner. Draft replies. Do not send.

IMPORTANT: If the bot posted the digest, stop. Do not post a second digest. Never send email.

1. Use Gmail to list unread or unanswered threads from the lookback window (default 24 hours).
2. Keep only threads that plausibly need a reply: customer, prospect, renewal or pricing, intros, direct questions. Skip newsletters, marketing mail, calendar noise, and automated notifications.
3. For each kept thread, read the full thread. Identify the ask and any deadline.
4. Pull CRM context (account, stage, owner) and recent Gong or Granola notes when they exist.
5. Draft a reply in the owner's voice. Learn voice from Gmail and Slack the way Kristaletz describes: scan sent mail and Slack for how they write. Apply an anti-slop rule: short, specific, no filler.
6. Never auto-send. Put drafts in Gmail drafts or in a digest doc.
7. Post a digest to the owner via Slack DM or #gtm-inbox: thread, why it matters, draft, and CRM link.
8. Log thread id, draft link, and whether the owner sent it (reconcile later from Gmail sent) in the Sheet.

CAUTION: Never auto-send. Never invent research. Never reply to a thread the bot itself created.
```
