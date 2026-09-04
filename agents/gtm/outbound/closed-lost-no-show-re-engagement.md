# 7. Closed-lost / no-show re-engagement

**Category:** GTM · Outbound / prospecting  
**Uses:** Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Gojiberry, Instantly, LinkedIn, Sheets  
**Trigger:** a weekly schedule.  

Monitor lost and no-show accounts for a new trigger, then a "timing changed" message that reuses original context. Cheapest pipeline.

## Prompt

```text
Create an Opulent automation named "Closed-lost no-show re-engagement".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Find closed-lost and no-show accounts whose timing may have changed, and queue re-engagement.

IMPORTANT: If the bot posted the weekly digest, stop. Do not post a second digest.

1. Pull opportunities in Salesforce or HubSpot with stage closed-lost, and meetings with no-show in Calendar or the meeting tool, from the lookback window in the Sheet (default 18 months for lost, 90 days for no-shows).
2. For each account, read the original close reason, last call notes from Gong or Granola, and last email thread in Gmail. Quote the original context. Do not invent a reason.
3. Scan for new triggers since the loss or no-show: funding, exec hire, product launch, job spike, tech change, new inbound, usage return. Cite each trigger. If none exists, skip the account.
4. Skip anyone who asked not to be contacted, who is in an open opportunity, or who was emailed about re-engagement in the last 60 days.
5. Draft a short "timing changed" email and LinkedIn note that references the original conversation and the new cited trigger. Do not pretend a meeting happened that did not.
6. Load drafts into a paused sequence in Gojiberry, Instantly, or Outreach. Post the list to #gtm-outbound with account, original reason, new trigger link, and draft.
7. Wait for the owner to approve. Never auto-send. After approval, enroll only approved people and log the re-open motion in CRM.
8. Update the Sheet: account, loss date, trigger, approval, send status, outcome.

CAUTION: Never auto-send outbound. Never invent research or a past conversation.
```
