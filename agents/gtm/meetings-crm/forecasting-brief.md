# 14. Forecasting brief

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Salesforce, HubSpot, Gong, Granola, Sheets  
**Trigger:** a daily schedule in the evening America/Chicago.  

Nightly pipeline movement, forecast vs commit, stalled opps, inbound quality, call themes. Short brief on what is slipping and which accounts need exec attention. Cloudflare-style: draft, fact-check, then tone.

## Prompt

```text
Create an Opulent automation named "Forecasting brief".

Trigger: a daily schedule in the evening America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Compile a leadership forecast brief. Fact-check every number against CRM.

IMPORTANT: If the bot already posted tonight's brief, stop.

1. Pull pipeline from Salesforce or HubSpot: movement since yesterday, commit vs forecast vs pipeline, stalled opps, new inbound, win/loss.
2. Pull Granola, Gong, Slack, and email for call themes and risk language on the largest deals. Quote timestamps. Do not invent risk.
3. Auto-update opportunity notes in the owner's Salesforce format only when the note is a factual digest of a new call. Do not change amount or close date here.
4. Draft the brief: what moved, what is slipping, inbound quality, call themes, and up to 10 accounts that need exec attention, each with a cited reason.
5. Fact-check pass: every dollar, date, and stage must match CRM. Delete anything that does not.
6. Tone pass: short, no hype, no invented quotes.
7. Post to #gtm-forecast and optionally email leadership. Do not email customers.
8. Log the brief link and the 10 accounts in the Sheet.

CAUTION: Never invent forecast numbers. Never auto-send outbound. Do not change commit categories without a human.
```
