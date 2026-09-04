# Playbook: Stand up an Opulent agent

## Overview

Take one agent file from this library and turn it into a live Opulent automation: the right connectors, a pasted prompt, a Disabled clock until you Enable, and a first run you can check. This is the human setup path. It does not change the agent’s job once it is running.

## What's Needed From User

- The agent file (example: `agents/work/inbox-manager.md` or `agents/gtm/outbound/icp-builder-linkedin-outbound.md`)
- An Opulent session you can paste into
- MCP / connector access named in that file’s **Uses** line, with the least privilege the prompt asks for (read-only if the agent only reads)
- Names that match your environment: Slack channel, Sheet tab, calendar, CRM object, timezone
- A confirm word you will actually type (`send` unless the prompt names another)

Do not start if you cannot name the connectors or the destination channel.

## Procedure

1. Open the agent file and write down **Uses**, **Trigger**, and **Mode** so you know what to connect and whether send is gated.
2. Connect only those MCPs. Grant read-only when the mode is read-only or draft-then-wait. Skip tools the prompt never names.
3. Copy the full `Create an Opulent automation` prompt, including the Trigger line.
4. Replace example names (channels, Sheet tabs, cron, ICP) with yours. Leave the safety lines and the job intact.
5. Paste the prompt into a new Opulent session and create the automation. Leave clocks **Disabled**.
6. Run one first-open or one manual tick. Confirm the widget or first output appears once, with no loop and no silent write.
7. Enable the clock only after that first output looks right.
8. Validate the next live tick against the agent’s **Specifications** (or the CAUTION block if the file has no playbook section). Pause the clock if auth fails twice.

## Specifications

- One automation exists, named as in the prompt, with the intended trigger
- Connectors match **Uses**; unused admin/send scopes were not granted
- Clocks were Disabled until Enable
- First run produced at most one output; a bot-authored message did not retrigger
- No send, calendar write, pay, merge, or publish happened unless you typed the confirm word
- Validation: open the run log and the destination thread. Confirm a single post (or justified silence), cited sources or `UNVERIFIED`, and no outbound you did not confirm

## Advice and Pointers

- Catalog and GTM files are paste-ready prompts. They do not all repeat this playbook; use this file for setup and the prompt for the job.
- Work agents (`agents/work/`) have full playbook sections because they are a four-agent desk with clocks and a hub.
- Empty search is `UNVERIFIED`, not “zero fires.”
- A late Calendar EA fire (noon or after) belongs on the afternoon pack.

## Forbidden Actions

- Do not Enable a clock before the first-open check
- Do not grant send, write, or admin on a read-only agent
- Do not auto-send outbound, invites, or payments from a first run
- Do not edit the agent’s job into a general assistant while “just setting up”
- Do not reply in a way that retriggers the same automation
