# 2. Signal-triggered outbound

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Gmail, Salesforce, HubSpot, Gojiberry, Apollo, Instantly, LinkedIn, Sheets  
**Trigger:** a daily schedule.  

Same-day short sequence when a compelling event fires: Head of AI hired, Series B, new tech install, competitor churn, job spike, or product launch.

## Prompt

```text
Create an Opulent automation named "Signal-triggered outbound".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Scan for new buying signals on named accounts and ICP lookalikes, then draft a same-day "why now" sequence.

IMPORTANT: If the bot posted the Slack digest, stop. Do not post a second digest. A second post can start a new run and cause a loop.

1. Load the named-account list and ICP from the Sheet tab "Target accounts" and from Salesforce or HubSpot.
2. For the past 24 hours, pull signals from the connected tools only: LinkedIn jobs / CoreSignal for role spikes and Head of AI (or equivalent) hires; Crunchbase or PitchBook for funding (for example Series B); BuiltWith for new tech installs; news APIs and company blogs for launches; CRM or product data for competitor churn if that source exists.
3. Drop any signal you cannot cite with a URL, job link, or filing. Do not invent a hire, round, or install.
4. Enrich the account and the likely buyer with Clay, Apollo, or Gojiberry. Waterfall-enrich email. Leave blanks when tools miss.
5. Skip contacts that are already in an open opportunity, were contacted in the last 90 days, or are on a suppression / unsubscribe list. Surface any open opp stage, amount, and last activity in the row.
6. For each remaining signal, write a "why now" angle that quotes the cited event in one sentence. Draft a short email and a shorter LinkedIn note off the same hook. Learn voice from 15–30 previously sent emails in Gmail if connected; otherwise use the brand voice doc.
7. Build a same-day 2–3 step sequence in Outreach, Salesloft, Smartlead, Instantly, or Gojiberry as a paused campaign. Do not enable send.
8. Post a digest to #gtm-outbound with account, signal, source link, draft copy, and a request for human approval. Approve 2–3 pairs before any full batch.
9. After explicit approval, enroll only the approved contacts. Respect domain warmup, daily volume caps, and unsubscribe handling. Do not send if warmup or caps are missing.
10. Log signal, copy, campaign, and outcome in CRM and in the Sheet. Reconcile the Sheet after any send.

CAUTION: Never auto-send outbound. Never invent research.
```
