# 6. Signup-to-outbound loop

**Category:** GTM · Outbound / prospecting  
**Uses:** Slack, Salesforce, HubSpot, Gojiberry, LinkedIn, Sheets, Stripe, Airscale  
**Trigger:** a new Stripe customer or signup event.  

Roman: Stripe signup → companies with 20+ employees → Airscale LinkedIn + mobile → Slack alert for the best accounts → every signup into Gojiberry for intent, research, and outreach.

## Prompt

```text
Create an Opulent automation named "Signup-to-outbound loop".

Trigger: a new Stripe customer or signup event.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A new person signed up for the product. Recover high-value signups that would otherwise sit in a generic email sequence.

The stack: Opulent is the brain, Stripe is signup data, Airscale is enrichment, GojiberryAI is intent plus outreach, Slack is the sales alert.

IMPORTANT: If the bot posted the Slack alert, stop. Do not post a second alert for the same Stripe customer id.

1. Use the Stripe MCP to read the new customer: email, name, company fields, plan, timestamp. Do not include payment method, card, or bank data in any note.
2. Identify the company from the email domain and Stripe metadata. Look up employee count from Airscale or the connected firmographic tool.
3. If the company has 20 or more employees, use Airscale to find LinkedIn and mobile number. Leave fields blank on miss. Do not invent a phone number.
4. Score whether this is a self-serve user or a potential account (company size, role if known, plan). Write the reasons.
5. For accounts that meet the 20+ employee bar, post one Slack alert in #gtm-signups with name, company, employee band, LinkedIn, role if known, and a suggested outbound angle grounded in the signup context. Tag the sales owner.
6. For every signup, not only the large ones, create or update the contact in Salesforce or HubSpot and push the record into GojiberryAI (list + context: signup, plan, company).
7. Ask Gojiberry to analyze signup plus intent, research the prospect, and draft a personalized LinkedIn and email message based on their context. Keep the Gojiberry campaign paused.
8. Do not let Gojiberry send LinkedIn or email until a human approves the Slack alert or an owner has pre-approved a paused-to-live rule in writing in the Sheet. Default is paused.
9. Never send a generic "you signed up" blast from this bot. The point of the loop is research → intent → personalized outreach, not a default email sequence.
10. Log Stripe customer id, company size, enrichment status, Slack permalink, Gojiberry campaign id, and send-approval status in the Sheet and CRM.

CAUTION: Never auto-send outbound. Never include Stripe payment data. Never invent employee count or phone.
```
