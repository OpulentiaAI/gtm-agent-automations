# 19. Content engine from one asset

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Gong, Granola, LinkedIn, Sheets, Notion  
**Trigger:** a Slack message in #marketing that contains /repurpose, or a new file in the source Drive/Notion folder.  

## Overview

Turn one source asset into a content set. Queue for review. Do not publish

## What's Needed From User

- Connectors: `Slack, Gong, Granola, LinkedIn, Sheets, Notion` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a Slack message in #marketing that contains /repurpose, or a new file in the source Drive/Notion folder
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`); Notion database or page (example: the runbook wiki)

## Procedure

1. Connect Slack, Gong, Granola, LinkedIn, Sheets, Notion. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Content engine from one asset"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: Turn one source asset into a content set. Queue for review. Do not publish.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Content engine from one asset only after that first output matches the job.
8. Validate the next live fire of `a Slack message in #marketing that contains /repurpose, or a new file in the source Drive/Notion folder`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Content engine from one asset does this and nothing else — Turn one source asset into a content set. Queue for review. Do not publish
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never invent quotes. Never auto-send or auto-publish
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, Gong, Granola, LinkedIn, Sheets, Notion, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never invent quotes. Never auto-send or auto-publish

## Prompt

```text
Create an Opulent automation named "Content engine from one asset".

Trigger: a Slack message in #marketing that contains /repurpose, or a new file in the source Drive/Notion folder.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Turn one source asset into a content set. Queue for review. Do not publish.

IMPORTANT: If the bot posted the message, stop. Do not start a second repurpose on the same asset id.

1. Load the source: webinar or interview transcript (Fireflies, Descript, Granola, Gong) or launch brief. Identify claims and quotes. Every quote needs a speaker and timestamp or doc location.
2. Drop any claim that is not in the asset or the brand fact sheet.
3. Produce drafts: blog / SEO / GEO article, LinkedIn posts, email, one-pager, and ad variants from the same claims. Vary format, not facts.
4. Put drafts in Webflow, WordPress, or Notion as unpublished review-queue items. Use Semrush or GSC only to suggest real queries; do not fake keyword volume.
5. Post a pack in Slack with links and which claim each asset uses. Ask for human approval to schedule.
6. After publish (by a human), track which angles convert if analytics are connected. Log in the Sheet. Do not auto-send the email or auto-post social.

CAUTION: Never invent quotes. Never auto-send or auto-publish.
```
