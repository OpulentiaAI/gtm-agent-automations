# 15. Pre-call one-pager / ROI / proposal

**Category:** GTM · Meetings / CRM  
**Uses:** Slack, Calendar, Salesforce, HubSpot, Gong, Granola, Figma, Notion  
**Trigger:** Calendar, 24 hours before an external opportunity meeting, or a Slack message that contains /one-pager.  

Opportunity context + pricing catalog + past deals + security answers + call notes → first draft, missing inputs flagged, versioned and logged.

## Prompt

```text
Create an Opulent automation named "Pre-call one-pager ROI proposal".

Trigger: Calendar, 24 hours before an external opportunity meeting, or a Slack message that contains /one-pager.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Draft a pre-call one-pager, ROI sketch, or proposal from live opportunity context. Flag missing inputs. Do not send to the customer.

IMPORTANT: If the bot posted the message or already attached a draft to this meeting id, stop.

1. Identify the opportunity and meeting from Calendar and Salesforce or HubSpot.
2. Gather pricing catalog, past similar deals, security questionnaire answers, and latest Gong or Granola notes. If a source is missing, list it under Missing inputs and continue.
3. Draft the one-pager: problem in their words (quoted), proposed motion, ROI only from numbers that exist in CRM or the catalog, implementation outline, and open questions.
4. Do not invent ROI, savings, or customer quotes. If you lack inputs for ROI, leave a blank and name the input.
5. Version the draft in Drive, Notion, or Figma. Name it with account, date, and version. Log the link on the opportunity.
6. Post the draft to the owner in Slack. Do not email or upload it to the customer.
7. After human approval, the owner sends. If they ask for edits, revise the same version thread.

CAUTION: Never auto-send the proposal. Never invent pricing, ROI, or quotes.
```
