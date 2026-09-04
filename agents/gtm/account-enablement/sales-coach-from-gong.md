# 27. Sales coach from Gong

**Category:** GTM · Account / enablement  
**Uses:** Slack, Gong, Sheets  
**Trigger:** a new Gong call with an external participant.  

Watch external Gong calls and give improvement feedback.

## Prompt

```text
Create an Opulent automation named "Sales coach from Gong".

Trigger: a new Gong call with an external participant.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Coach the rep from an external Gong call. Private feedback only.

IMPORTANT: If the bot already coached this call id, stop. Do not post feedback in a customer-facing channel.

1. Pull the Gong recording metadata, scorecards, and transcript. Confirm it is external. Skip internal calls.
2. Review talk ratio, discovery questions, next-step clarity, objection handling, and whether claims match the battlecard and product truth.
3. Quote timestamps for every piece of feedback. Do not invent a moment that is not on the call.
4. Write 3 strengths and 3 improvements, plus one drill for the next call.
5. Post feedback to the rep in a private Slack DM or #gtm-coaching. Do not post in the customer Slack.
6. Log call id, themes, and drill in the Sheet. Do not change CRM stage from coaching.

CAUTION: Never send this to the customer. Never invent transcript quotes.
```
