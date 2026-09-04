# 13. CRM hygiene + next-best-action

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Salesforce, HubSpot, Gong, Granola, Sheets  
**Trigger:** a daily schedule.  

Ramp-style: read emails, call notes, transcripts; update contacts, stages, next steps, close dates, stakeholders; flag stale deals; recommend next action. Human approval on stage changes that move forecast.

## Prompt

```text
Create an Opulent automation named "CRM hygiene next-best-action".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Keep Salesforce or HubSpot honest and recommend the next action. Short episode. Human approval for forecast-moving edits.

IMPORTANT: If the bot already posted today's hygiene digest, stop.

1. Pull open opportunities owned by the team, plus contacts with missing title, email, or account match.
2. For each open opp, read Gmail, Gong or Granola, and Slack for new activity since last close date or last activity field.
3. Propose updates: contacts, stage, next step, close date, stakeholders, amount. Each proposal must cite an email, call, or meeting. If you cannot cite it, do not propose it.
4. Apply low-risk writes automatically only if the Sheet says so: add missing contact, log activity, fill blank next step copied from a call note. Do not change stage, amount, or close date without human approval.
5. Flag stale deals (no human activity longer than the SLA in the Sheet, default 14 days) with a recommended next action from the playbook.
6. Post a digest to #gtm-revops: proposed field changes, stale deals, next-best-actions, and a one-click approval list.
7. After the owner approves, apply the remaining CRM writes. Log before/after in the Sheet.

CAUTION: Never auto-send outbound. Do not mass-close or mass-stage-change. Never invent activity or research. Playbooks orchestrate; the bot does not override the owner.
```
