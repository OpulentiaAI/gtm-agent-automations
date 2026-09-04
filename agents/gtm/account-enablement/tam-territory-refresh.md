# 29. TAM / territory refresh

**Category:** GTM · Account / enablement  
**Uses:** Salesforce, HubSpot, Apollo, Browserbase, Sheets  
**Trigger:** a monthly schedule.  

Continuously rebuild TAM from firmographics plus custom signals. Score. Rebalance territories by capacity and win rate. Push prioritized lists with contacts attached.

## Prompt

```text
Create an Opulent automation named "TAM territory refresh".

Trigger: a monthly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Rebuild TAM and propose territory assignments. Do not move accounts without approval.

IMPORTANT: If the bot already posted this month's TAM digest, stop.

1. Rebuild TAM from firmographics and the custom signals listed in the Sheet (industry, size, tech, hiring, funding). Use Apollo, Clay, Crunchbase, and Browserbase as connected.
2. Score accounts with written reasons and source links. Drop rows with no source.
3. Attach contacts only when a provider returns them. Do not guess emails.
4. Compare current Salesforce or HubSpot territories with capacity and win rate. Propose a rebalance. Do not change owner yet.
5. Push prioritized lists with contacts to a Sheet per territory and post the digest to #gtm-revops.
6. After leadership approves, apply owner changes in CRM and log before/after.
7. Do not start outbound from this run.

CAUTION: Never invent TAM numbers. Never auto-reassign accounts. Never auto-send outbound.
```
