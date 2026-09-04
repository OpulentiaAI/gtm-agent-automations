# 23. Paid campaign optimizer

**Category:** GTM · Marketing / content / creative  
**Uses:** LinkedIn, Figma, Sheets  
**Trigger:** a weekly schedule.  

Ingest CPA, ROAS, audience, creative, and landing-page performance. Pause losers, shift budget to winners, generate new creative from top messages, weekly "what changed and why".

## Prompt

```text
Create an Opulent automation named "Paid campaign optimizer".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Review paid performance and propose budget and creative changes. Do not spend money without approval.

IMPORTANT: If the bot already posted this week's paid digest, stop.

1. Pull Google Ads, Meta Ads, and LinkedIn Ads via their APIs or MCPs, plus GA4 and CRM conversions, for the past 7 days and the prior 7 days.
2. Rank campaigns, ad sets, and creatives by CPA, ROAS, and volume. Use only platform-reported numbers. State the window.
3. Propose pausing creatives or ads that fail the documented threshold in the Sheet. Propose shifting budget to winners. Do not execute pause or budget changes yet.
4. Generate new creative copy and Figma or ad-variant briefs from the top-performing messages. Do not invent proof.
5. Post a "what changed and why" memo to #growth-paid with tables, proposed actions, and new creative drafts.
6. After a human approves named actions, apply only those pause/budget edits. Recheck spend caps.
7. Log proposals, approvals, and live changes in the Sheet and CRM conversion mapping.

CAUTION: Never auto-send outbound. Do not pause, start, or reallocate spend without human approval. Never invent ROAS, CPA, or research.
```
