# 1. ICP builder + LinkedIn outbound

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets  
**Trigger:** a Slack message in #gtm-outbound that contains /icp-outbound.  

Gojiberry / Roman: 3 Opulent agents, 97 leads matching the ICP, personalized messages, a demo booked with a 50-person company in less than 24 hours.

## Prompt

```text
Create an Opulent automation named "ICP builder + LinkedIn outbound".

Trigger: a Slack message in #gtm-outbound that contains /icp-outbound.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A teammate asked Opulent to build a specific ICP and run LinkedIn outbound through the GojiberryAI MCP. The full event details are below.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the Slack message, the thread, and any attached ICP notes, product URL, or competitor list.
2. If the product, ICP, or offer is missing, ask one focused question in the thread and stop.
3. Connect to the GojiberryAI MCP. Confirm LinkedIn accounts that the team already linked. Do not connect a new LinkedIn account without a human naming it.
4. Build a super-specific ICP: job titles, company types, employee bands, keywords, competitors, recently funded companies to track, buying signals, and exclusions. Write the ICP into a Sheet tab named "ICP".
5. Create or tune Gojiberry outreach agents against that ICP and the intent signals you identified. Record agent IDs in the Sheet.
6. Find prospects that match the ICP. Cap the first batch at a human-set limit. If none is set, cap at 100.
7. Enrich each prospect with email and phone through Gojiberry. If enrichment fails, leave the field blank. Do not invent contact data.
8. Research every prospect from primary sources only (LinkedIn, company site, funding news, recent posts). Cite the URL for every fact. If you cannot cite it, omit it.
9. Write a personalized LinkedIn connection note and a follow-up message for each prospect. Ground each line in a cited fact. Skip anyone already in CRM, already in a Gojiberry campaign, or already contacted in the last 90 days.
10. Post a review pack in the Slack thread: ICP summary, lead count, 2–3 sample message pairs, and a link to the Sheet. Ask a human to approve sending.
11. Do not send connection requests, emails, or InMails until a human replies with explicit approval. After approval, start sending only the approved batch through Gojiberry.
12. Log every prospect, message, send status, and source URL in Salesforce or HubSpot and in the Sheet. After replies arrive, classify them and alert #gtm-outbound. Do not auto-reply to inbound LinkedIn or email without human approval.

CAUTION: Never auto-send outbound. Never invent research. Roman's run still needed occasional manual intervention; treat send as a gated step.
```
