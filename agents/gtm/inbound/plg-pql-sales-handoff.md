# 9. PLG / PQL sales handoff

**Category:** GTM · Inbound / conversion  
**Uses:** Slack, Salesforce, HubSpot, Apollo, Sheets, Stripe, Airscale  
**Trigger:** a daily schedule.  

Usage thresholds (seats, feature adoption, invites, spikes) → company → decision-makers → expansion vs self-serve → Slack plus outbound or CSM play.

## Prompt

```text
Create an Opulent automation named "PLG PQL sales handoff".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Find product-qualified accounts that crossed a usage threshold and hand them to sales or CS.

IMPORTANT: If the bot posted the Slack alert for an account today, skip that account. Do not double-alert.

1. Pull usage from PostHog, Amplitude, Mixpanel, or the warehouse: seats, feature adoption, invites, usage spikes, plan limits. Use Stripe for plan and expansion revenue fields. Do not include payment credentials.
2. Resolve the company from workspace domain or billing email. Enrich decision-makers with Apollo, Clay, or Airscale.
3. Score expansion-assist vs stay-self-serve using the documented PQL rules in the Sheet. Write the rule hits as facts (for example "seats went from N to M on date").
4. Skip accounts with an open sales-assisted opportunity or a CSM task created in the last 7 days. Surface current stage and owner.
5. Post a Slack alert in #gtm-pql with account, usage facts, suggested play (AE outbound vs CSM expansion), and 2–3 decision-maker contacts with sources.
6. Draft an outbound or CSM message that references the product usage, not a cold pitch. Do not send it.
7. After human approval, log the task on the opportunity or account in Salesforce or HubSpot, attach the draft, and only then allow send from the owner or an approved sequence.
8. Update the PQL Sheet: account, threshold, score, owner, approval, outcome.

CAUTION: Never auto-send outbound. Never invent usage numbers. Never include Stripe payment data.
```
