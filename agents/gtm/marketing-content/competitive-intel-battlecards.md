# 22. Competitive intel → battlecards

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Gong, Granola, Browserbase, Sheets, Notion  
**Trigger:** a weekly schedule.  

## Overview

Refresh competitive enablement from primary sources and call mentions

## What's Needed From User

- Connectors: `Slack, Gong, Granola, Browserbase, Sheets, Notion` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a weekly schedule
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`); Notion database or page (example: the runbook wiki)

## Procedure

1. Connect Slack, Gong, Granola, Browserbase, Sheets, Notion. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Competitive intel → battlecards"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Refresh competitive enablement from primary sources and call mentions.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Competitive intel → battlecards only after that first output matches the job.
8. Validate the next live fire of `a weekly schedule`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Competitive intel → battlecards does this and nothing else — Refresh competitive enablement from primary sources and call mentions
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never invent a competitor feature or price. Never auto-send outbound that names a competitor without PMM approval
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gong, Granola, Browserbase, Sheets, Notion, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never invent a competitor feature or price. Never auto-send outbound that names a competitor without PMM approval

## Prompt

```text
Create an Opulent automation named "Competitive intel battlecards".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Refresh competitive enablement from primary sources and call mentions.

IMPORTANT: If the bot already posted this week's intel digest, stop.

1. Load the competitor list from the Sheet. Visit each site, changelog, pricing page, and G2 with Browserbase. Pull ads if an ads library MCP is connected. Pull earnings if they are public companies.
2. Search Gong or Granola for competitor mentions since last run. Quote with timestamps. Do not paraphrase a mention you did not find.
3. Diff against last week's battlecard. List only confirmed positioning, pricing, or product shifts, each with a URL or call timestamp.
4. Update battlecards and objection scripts in Notion, Highspot, Seismic, or Drive as a new version. Do not delete the prior version.
5. Push short snippets to CRM / sales rooms only as "unverified until PMM approves" if you post before approval. Default: post the digest to #pmm and wait.
6. Alert PMM in Slack with what changed, evidence links, and recommended talk-track edits.
7. Log competitor, change, evidence, and battlecard version in the Sheet.

CAUTION: Never invent a competitor feature or price. Never auto-send outbound that names a competitor without PMM approval.
```
