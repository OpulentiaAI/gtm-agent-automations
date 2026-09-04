# 3. Autonomous outbound SDR

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Calendar, Salesforce, HubSpot, Gojiberry, Apollo, LinkedIn, Sheets  
**Trigger:** a daily schedule at 06:00 America/Chicago.  

End-to-end SDR loop: ICP → source → waterfall-enrich → score → persona-specific multichannel sequence → classify replies → book or hand off → log in CRM. Human SDR oversees the agent seat.

## Prompt

```text
Create an Opulent automation named "Autonomous outbound SDR".

Trigger: a daily schedule at 06:00 America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Run one outbound SDR episode against the live ICP. Keep the episode short. Encode results so the next run can learn.

IMPORTANT: If the bot posted the Slack summary, stop. Do not post a second summary.

1. Load ICP, exclusions, daily volume cap, and suppression lists from the Sheet and from Salesforce or HubSpot.
2. Source new accounts and contacts from Apollo, ZoomInfo, or Clay. Prefer intent sources when connected: 6sense, Common Room, job posts, funding, tech installs, web visits.
3. Waterfall-enrich missing emails and titles. Do not guess an email pattern. If every provider misses, mark "unenriched" and skip send.
4. Score each contact against ICP plus intent. Write the score reasons as cited facts. Drop anyone below the documented threshold.
5. Skip already-touched contacts. Surface open opportunity stage, amount, and last activity when they exist.
6. Draft a persona-specific email sequence and a shorter LinkedIn note off the same hook. Pull style from 15–30 sent emails. Cite research. Never invent research. If a claim has no source, delete it.
7. Load drafts into Outreach, Salesloft, Smartlead, Artisan Ava, 11x Alice, or Gojiberry as paused. Post 2–3 sample pairs to #gtm-outbound and wait for human approval before any send.
8. After approval, send only within warmup and volume caps. Never send without that approval.
9. Classify new replies: meeting, question, objection, not-now, unsubscribe, out-of-office, other. Draft a reply. Do not send the reply.
10. For meeting-intent replies, offer times from Calendar / Calendly / Chili Piper and hand off to the AE in Slack. Do not book over an existing hold without the owner.
11. Log source, score, sequence, reply label, and next action in CRM and in the live Sheet. Reconcile the Sheet after sending.
12. Stop when the daily cap is hit or when the review queue is still waiting on a human.

CAUTION: Do not give send-authority before domain warmup, volume caps, unsubscribe handling, and a review path exist. Hybrid pods (one human SDR overseeing 2–3 agent seats) beat set-and-forget on meeting quality.
```
