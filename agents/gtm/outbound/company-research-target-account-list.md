# 5. Company-research / target account list

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Apollo, Browserbase, Sheets, Notion  
**Trigger:** a Slack message in #gtm-outbound that contains /company-research.  

Jay Sahnan /company-research: agent builds an ICP target-account list and deep-researches each company (Browserbase).

## Prompt

```text
Create an Opulent automation named "Company-research target account list".

Trigger: a Slack message in #gtm-outbound that contains /company-research.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Build or refresh an ICP target-account list and deep-research each company.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the Slack command, ICP notes, and any seed URLs or competitor names.
2. If ICP firmographics are missing (industry, size, geography, trigger), ask one focused question and stop.
3. Use the Browserbase MCP or Browserbase CLI to visit company sites, careers pages, pricing pages, blogs, and news. Use Apollo, Clay, or the open-source Signal stack if connected to expand the account list.
4. Build a target-account list that matches the ICP. Deduplicate against Salesforce or HubSpot.
5. For each account, write a research memo with only cited facts: what they sell, who they sell to, tech stack clues, hiring, funding, likely pain, buying committee titles, and a recommended first motion. Every bullet needs a URL.
6. If a page fails to load or a fact is unverified, write "unknown" and skip it. Do not invent org charts, headcount, or stack.
7. Attach contacts only when a tool returns them. Do not guess emails.
8. Write the list and memos to a Sheet named "Target accounts" and to a Notion or Drive folder if connected.
9. Post the account count, top 10 with one-line "why them", and the Sheet link to the Slack thread. Do not start outreach from this run.
10. Log new accounts in CRM as target accounts without changing owner or stage.

CAUTION: This template researches. Never auto-send outbound. Never invent research.
```
