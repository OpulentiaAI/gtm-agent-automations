# 8. Inbound speed-to-lead

**Category:** GTM · Inbound / conversion  
**Uses:** Slack, Calendar, Salesforce, HubSpot, Apollo, Sheets  
**Trigger:** a new form submission, chat, or demo request.  

Form, chat, demo, or high-intent page → identify company → enrich → score ICP and urgency → 2–4 qualifying questions → book AE or nurture → CRM in seconds.

## Prompt

```text
Create an Opulent automation named "Inbound speed-to-lead".

Trigger: a new form submission, chat, or demo request.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

An inbound lead just arrived. Qualify and route fast. Do not let the lead go cold.

IMPORTANT: If the bot posted the Slack or CRM note, stop. Do not create a second lead record for the same email in this run.

1. Read the form, chat, or demo payload: name, email, company, page, UTM, comments.
2. Identify the company from domain and Clearbit, Clay, or Apollo. Enrich firmographics and likely role.
3. Score ICP fit and urgency from cited fields only (size, industry, page, message). If data is missing, say so.
4. Create or update the lead in Salesforce or HubSpot within this run. Do not duplicate.
5. If the lead is ICP and high urgency, post a Slack alert in #gtm-inbound tagging the AE on duty, with score, enrichment, and the inbound message.
6. Ask at most 2–4 qualifying questions via the connected chat (Qualified, Drift, HubSpot) or a drafted email. Do not send the email until a human or the documented playbook says inbound auto-reply is allowed for this form type.
7. If the playbook allows booking, offer Calendar / Calendly / Chili Piper slots and book the AE. If it does not, leave a draft booking link for the AE.
8. If not ICP, route to nurture. Do not start cold outbound to extra contacts at the company from this inbound without approval.
9. Log time-to-first-touch, score, route, and meeting in CRM and the Sheet.

CAUTION: Never auto-send outbound sequences from inbound. Never invent company size or title. Default email is draft-only unless the playbook explicitly allows a form auto-reply.
```
