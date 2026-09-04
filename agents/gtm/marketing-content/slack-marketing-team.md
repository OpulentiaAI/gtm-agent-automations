# 16. Slack marketing team

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, LinkedIn, Sheets, Notion  
**Trigger:** a new message in #marketing that contains /brief or @marketing-lead.  

## Overview

A human briefed the marketing team lead in Slack. Route work to specialists. Do not publish

## What's Needed From User

- Connectors: `Slack, LinkedIn, Sheets, Notion` — least privilege that matches **Mode** (`draft / paused · human approval before send · fail closed`)
- Trigger: a new message in #marketing that contains /brief or @marketing-lead
- Your names for channels, calendars, repos, Sheet tabs, and timezone
- Confirm word `send` (or the word the prompt names) for any write
- Enable after first-open — clocks stay Disabled until you hit Enable
- Example inputs: Slack channel or DM (example: `#eng` or a private DM); Sheet tab name (example: `ICP` or `Target accounts`); Notion database or page (example: the runbook wiki)

## Procedure

1. Connect Slack, LinkedIn, Sheets, Notion. Grant read-only when the mode is read-only or draft-then-wait.
2. Copy the `Create an Opulent automation named "Slack marketing team"` prompt, including Trigger.
3. Replace example names with yours. Do not change the job, the loop guard, or the CAUTION.
4. Leave the automation Disabled. Run one manual first-open or one tick.
5. Check the output against the job: A human briefed the marketing team lead in Slack. Route work to specialists. Do not publish.
6. Open every cited source (thread, PR, invoice, event). Mark the run failed if a fact is uncited.
7. Enable the clock for Slack marketing team only after that first output matches the job.
8. Validate the next live fire of `a new message in #marketing that contains /brief or @marketing-lead`. Pause if auth fails twice or if a write happened without `send`.

## Specifications

- Postcondition: Slack marketing team does this and nothing else — A human briefed the marketing team lead in Slack. Route work to specialists. Do not publish
- Mode holds: draft / paused · human approval before send · fail closed
- Safety: Never auto-send email or auto-publish. Humans ship
- Empty or failed search is `UNVERIFIED`, never an invented zero, quote, or count
- Validation: on the next real trigger, confirm a single output or justified silence, every kept item opens in Slack, LinkedIn, Sheets, Notion, and no send/write/pay/merge/publish happened unless you typed `send`

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
- Do not ignore: Never auto-send email or auto-publish. Humans ship

## Prompt

```text
Create an Opulent automation named "Slack marketing team".

Trigger: a new message in #marketing that contains /brief or @marketing-lead.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A human briefed the marketing team lead in Slack. Route work to specialists. Do not publish.

IMPORTANT: If the bot posted the message, stop. Do not post a reply that retriggers /brief. A reply can start a new run and cause a loop.

1. Read the Slack brief and thread. Restate the requested asset, channel, deadline, and audience. If the brief is ambiguous, ask one focused question and stop.
2. Act as team lead. Spawn or call five specialists as separate bot sessions or skills: content, social, SEO, email, product marketing. Only call the specialists the brief needs.
3. Content: outline or draft the core narrative from brand docs. Social: channel-native posts. SEO: title, slug, internal links, search intent. Email: subject plus body in brand voice. PMM: positioning, audience, competitive note.
4. Each specialist must cite source briefs, product docs, or URLs. No invented customer quotes, metrics, or launch dates.
5. Collect drafts in one Slack thread with clearly labeled sections. Put publish-ready copy in a Notion or CMS review queue (Webflow, WordPress) as draft, not published.
6. Do not post to LinkedIn, X, email platforms, or ad accounts from this run.
7. Log the brief, specialist outputs, and review-queue links in the Sheet.

CAUTION: Never auto-send email or auto-publish. Humans ship.
```
