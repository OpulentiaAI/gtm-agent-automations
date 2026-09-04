# 4. LinkedIn engager harvest to Instantly

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Apollo, Instantly, LinkedIn, Sheets  
**Trigger:** a new message in #gtm-outbound that contains a LinkedIn post URL.  

codyschneider: Slack a LinkedIn post; extract engager URLs; Apollo emails; verify; Instantly campaign that references the post.

## Prompt

```text
Create an Opulent automation named "LinkedIn engager harvest to Instantly".

Trigger: a new message in #gtm-outbound that contains a LinkedIn post URL.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A teammate posted a LinkedIn URL. Harvest people who engaged with that post and queue a campaign that references it.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the Slack message and extract the LinkedIn post URL. If there is no URL, ask one focused question and stop.
2. Open the post. Capture the author, the post text, and the list of commenter and reactor profile URLs. Do not invent names that are not on the post.
3. Filter engagers against the ICP (title, seniority, company type). Drop employees of our company, current customers, and anyone already in CRM or Instantly.
4. For each remaining profile, use the Apollo MCP to find a work email. Verify the email with the connected verifier. If Apollo or verify fails, leave email blank and do not guess.
5. Write one email per person that references the specific post (quote a short public snippet or the topic). Keep it short. Do not claim you know why they engaged unless they wrote a comment you can quote.
6. Create a paused Instantly campaign named after the post date and topic. Add only verified emails. Do not start the campaign.
7. If Graphed or Sheets is connected, append a reporting row: post URL, engager count, verified count, campaign link.
8. Post a summary in the Slack thread: post, engager count, verified count, 2 sample drafts, Instantly campaign link. Ask for human approval to start send.
9. After explicit approval, enable only the approved campaign and only within Instantly warmup limits. Never auto-send.
10. Log contacts, campaign, and status in Salesforce or HubSpot and in the Sheet.

CAUTION: Never auto-send outbound. Never invent emails or engagement reasons.
```
