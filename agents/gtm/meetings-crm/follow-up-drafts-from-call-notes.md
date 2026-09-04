# 12. Follow-up drafts from call notes

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Sheets  
**Trigger:** a daily schedule, and optionally when a Granola or Gong transcript lands.  

Detect external calls since last run. Draft To / Subject / body grounded in what was discussed, with concrete next steps.

## Prompt

```text
Create an Opulent automation named "Follow-up drafts from call notes".

Trigger: a daily schedule, and optionally when a Granola or Gong transcript lands.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Draft follow-up emails from new external call notes. Do not send.

IMPORTANT: If the bot already drafted a follow-up for this meeting id, skip it. Do not email the customer.

1. List external Calendar events that ended since the last successful run.
2. For each event, fetch Granola and/or Gong notes and transcript. If notes are missing, skip and record "no notes".
3. Extract commitments, dates, owners, and objections from the notes. Quote the transcript for anything you claim was said. Do not invent a next step.
4. Draft To, Subject, and body to the customer or prospect. Include concrete next steps that appeared on the call. Match the owner's voice from sent mail.
5. Save as a Gmail draft. Post the draft link in #gtm-followups or Slack DM to the owner, with the meeting title and CRM opportunity.
6. Update Salesforce or HubSpot next step, close date, and stakeholders only when the notes support the change. Write the quote or timestamp in the activity.
7. Log meeting id, draft link, and CRM fields changed in the Sheet.

CAUTION: Never auto-send. Never invent research or commitments that are not in the notes.
```
