# 28. Event / webinar pipeline

**Category:** GTM · Account / enablement  
**Uses:** Apollo, Instantly, Sheets, Airscale  
**Trigger:** a weekly schedule before the event, then a one-shot run after the event ends.  

ICP plus lookalike invite list → personalized invites → post-event enrich attendees vs no-shows → score engagement → route hot, nurture the rest with a session-specific talk track.

## Prompt

```text
Create an Opulent automation named "Event webinar pipeline".

Trigger: a weekly schedule before the event, then a one-shot run after the event ends.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Run event or webinar pipeline work for the event named in the Sheet.

IMPORTANT: If the bot already posted this phase's digest, stop.

1. Read event name, date, session topics, and ICP from the Sheet.
2. Before the event: build an invite list from ICP plus lookalikes in Apollo or Clay. Deduplicate against CRM and recent outreach. Draft personalized invites that cite a real reason they fit the session. Load a paused Instantly, Outreach, or email campaign. Do not send without approval.
3. After the event: import attendees, registrants, and no-shows. Enrich with Apollo or Airscale. Score engagement: attended, asked a question, visited pricing if analytics exist. Cite the source field.
4. Route hot accounts to AEs in #gtm-inbound with a session-specific talk track quoting their question or the session they sat in. Draft follow-ups. Do not send.
5. Put the rest in a nurture campaign as paused. Log every person, score, and route in CRM and the Sheet.
6. Wait for human approval before any invite or follow-up send.

CAUTION: Never auto-send invites or follow-ups. Never invent attendance.
```
