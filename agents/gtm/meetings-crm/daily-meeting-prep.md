# 10. Daily meeting prep

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Calendar, Salesforce, HubSpot, Gong, Granola, Figma, Sheets  
**Trigger:** a daily schedule at 06:30 America/Chicago.  

Kristaletz: pull Salesforce, Gmail, Slack, Granola, Gong or fresh research; short skimmable phone-readable brief; optional custom deck for the day's calls.

## Prompt

```text
Create an Opulent automation named "Daily meeting prep".

Trigger: a daily schedule at 06:30 America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Prepare the owner for today's external meetings. Output must be short and readable on a phone.

IMPORTANT: If the bot already posted today's prep in #gtm-meeting-prep or emailed it, stop. Do not send a second copy.

1. Use Calendar to list external meetings for today. Skip internal 1:1s unless they are tagged customer or prospect.
2. For each meeting, pull Salesforce or HubSpot: account, opportunity stage, amount, close date, last activity, stakeholders.
3. Pull recent Gmail threads with those contacts, Slack mentions, and the latest Granola or Gong notes. If none exist, say "no prior notes".
4. If still thin, do fresh research on the company site, news, hiring, and 10-K or earnings when public. Cite URLs. Do not invent.
5. Write a one-page brief per meeting: who will be there, relationship history, open opp, goal for the call, talk tracks, likely objections, one relevant case study, and risks. Keep it skimmable.
6. If the Slides / Figma bot or a master deck is connected and the meeting is a customer call, attach or update a custom deck copy. Do not invent quotes on a "What we've heard" slide; only use Granola/Gong text.
7. Post the briefs to #gtm-meeting-prep and/or email the owner. Do not email the customer.
8. Log that prep ran (meeting id, time, brief link) in the Sheet.

CAUTION: Never auto-send anything to the customer. Never invent research, numbers, or prior commitments.
```
