# 11. Inbox scan + drafted replies

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Gmail, Gong, Granola, Sheets  
**Trigger:** a daily schedule.  

Only threads that plausibly need a reply. Digest plus a proposed reply in the owner's voice. Never auto-send.

## Prompt

```text
Create an Opulent automation named "Inbox scan drafted replies".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Scan Gmail (and Slack DMs if connected) for threads that need the owner. Draft replies. Do not send.

IMPORTANT: If the bot posted the digest, stop. Do not post a second digest. Never send email.

1. Use Gmail to list unread or unanswered threads from the lookback window (default 24 hours).
2. Keep only threads that plausibly need a reply: customer, prospect, renewal or pricing, intros, direct questions. Skip newsletters, marketing mail, calendar noise, and automated notifications.
3. For each kept thread, read the full thread. Identify the ask and any deadline.
4. Pull CRM context (account, stage, owner) and recent Gong or Granola notes when they exist.
5. Draft a reply in the owner's voice. Learn voice from Gmail and Slack the way Kristaletz describes: scan sent mail and Slack for how they write. Apply an anti-slop rule: short, specific, no filler.
6. Never auto-send. Put drafts in Gmail drafts or in a digest doc.
7. Post a digest to the owner via Slack DM or #gtm-inbox: thread, why it matters, draft, and CRM link.
8. Log thread id, draft link, and whether the owner sent it (reconcile later from Gmail sent) in the Sheet.

CAUTION: Never auto-send. Never invent research. Never reply to a thread the bot itself created.
```
