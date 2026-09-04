# 24. Last-30-days social research

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, LinkedIn, Sheets  
**Trigger:** a Slack message that contains /last30days and a person, company, or handle.  

## Overview

Research the last 30 days of public social activity for a person or brand. Use for personalization, not for sending

## What's Needed From User

- Connectors: `Slack, LinkedIn, Sheets` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message that contains /last30days and a person, company, or handle
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`)

## Procedure

1. Connect Slack, LinkedIn, Sheets. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Last-30-days social research"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Research the last 30 days of public social activity for a person or brand. Use for personalization, not for sending.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Last-30-days social research only after that first output matches the job.
8. Validate the next live fire of `a Slack message that contains /last30days and a person, company, or handle`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Last-30-days social research does this and nothing else — Research the last 30 days of public social activity for a person or brand. Use for personalization, not for sending
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never invent posts or quotes. Never auto-send outbound
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, LinkedIn, Sheets, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never invent posts or quotes. Never auto-send outbound

## Prompt

```text
Create an Opulent automation named "Last-30-days social research".

Trigger: a Slack message that contains /last30days and a person, company, or handle.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Research the last 30 days of public social activity for a person or brand. Use for personalization, not for sending.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Parse the target name or handle. If ambiguous, ask once and stop.
2. Pull public posts from X, LinkedIn, and other connected socials for the last 30 days. Prefer the last30days-style aggregator if that MCP or bot is connected.
3. Summarize themes, launches, hires, opinions, and notable posts. Each bullet needs a URL and date. Skip anything you cannot open.
4. Flag possible buying signals (hiring, new product, funding mention) as hypotheses with links, not as facts beyond the post.
5. Do not scrape private profiles. Do not invent posts.
6. Post the memo in the Slack thread and write it to the account's research tab in the Sheet or CRM note.
7. Do not send outreach from this run. Another template may use the citations after human approval.

CAUTION: Never invent posts or quotes. Never auto-send outbound.
```
