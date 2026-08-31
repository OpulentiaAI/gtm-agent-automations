# Cloud Agent Workflows

Prompt templates for Grok Bot automations for marketing and sales (GTM).

Layout copied from [dabit3/cloud-agent-automations](https://github.com/dabit3/cloud-agent-automations). Each template is a complete prompt you paste into a new Grok Bot session.

Each template is a complete prompt that tells Grok Bot to create an automation, including the recommended trigger. No code is required.

To use a template, paste its full prompt into a new Grok Bot session. Grok Bot then creates the automation for you.

Grok Bot starts the automation when a schedule, Slack message, email, Stripe event, calendar event, GitHub event, or form submission matches the trigger. Most templates also require an MCP connection.

## How to use the templates

1. Choose a template below.
2. Copy the full prompt, including the "Create a Grok Bot automation" line and the trigger.
3. If the example names, channels, or schedule do not match your environment, change them in the prompt.
4. Paste the prompt into a new Grok Bot session. Grok Bot creates the automation and asks about any missing details, such as the exact Slack channel, CRM object, or calendar.
5. If the template uses an MCP, connect that MCP before the first run.
6. Give each MCP connection the least access that the template needs. If a template only reads data, connect read-only credentials.

The prompts contain safety rules, for example "Never auto-send outbound" and "If the bot posted the message, stop". These rules guide Grok Bot, but they are not a security boundary. The credentials that you connect set the real limit on what Grok Bot can do.

Connect the named MCPs first: Gojiberry, Stripe, Airscale, Slack, Salesforce or HubSpot, Gmail, Calendar, Gong or Granola, Apollo, Instantly, LinkedIn, Browserbase, Figma, Sheets, Notion, and any ads or product-analytics tools the template lists. Do not grant send, write, or admin access unless the template needs it.

## Outbound / prospecting

### 1. ICP builder + LinkedIn outbound

Gojiberry / Roman: 3 Grok bots, 97 leads matching the ICP, personalized messages, a demo booked with a 50-person company in less than 24 hours.

```text
Create a Grok Bot automation named "ICP builder + LinkedIn outbound".

Trigger: a Slack message in #gtm-outbound that contains /icp-outbound.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A teammate asked Grok Bot to build a specific ICP and run LinkedIn outbound through the GojiberryAI MCP. The full event details are below.

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

### 2. Signal-triggered outbound

Same-day short sequence when a compelling event fires: Head of AI hired, Series B, new tech install, competitor churn, job spike, or product launch.

```text
Create a Grok Bot automation named "Signal-triggered outbound".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Scan for new buying signals on named accounts and ICP lookalikes, then draft a same-day "why now" sequence.

IMPORTANT: If the bot posted the Slack digest, stop. Do not post a second digest. A second post can start a new run and cause a loop.

1. Load the named-account list and ICP from the Sheet tab "Target accounts" and from Salesforce or HubSpot.
2. For the past 24 hours, pull signals from the connected tools only: LinkedIn jobs / CoreSignal for role spikes and Head of AI (or equivalent) hires; Crunchbase or PitchBook for funding (for example Series B); BuiltWith for new tech installs; news APIs and company blogs for launches; CRM or product data for competitor churn if that source exists.
3. Drop any signal you cannot cite with a URL, job link, or filing. Do not invent a hire, round, or install.
4. Enrich the account and the likely buyer with Clay, Apollo, or Gojiberry. Waterfall-enrich email. Leave blanks when tools miss.
5. Skip contacts that are already in an open opportunity, were contacted in the last 90 days, or are on a suppression / unsubscribe list. Surface any open opp stage, amount, and last activity in the row.
6. For each remaining signal, write a "why now" angle that quotes the cited event in one sentence. Draft a short email and a shorter LinkedIn note off the same hook. Learn voice from 15–30 previously sent emails in Gmail if connected; otherwise use the brand voice doc.
7. Build a same-day 2–3 step sequence in Outreach, Salesloft, Smartlead, Instantly, or Gojiberry as a paused campaign. Do not enable send.
8. Post a digest to #gtm-outbound with account, signal, source link, draft copy, and a request for human approval. Approve 2–3 pairs before any full batch.
9. After explicit approval, enroll only the approved contacts. Respect domain warmup, daily volume caps, and unsubscribe handling. Do not send if warmup or caps are missing.
10. Log signal, copy, campaign, and outcome in CRM and in the Sheet. Reconcile the Sheet after any send.

CAUTION: Never auto-send outbound. Never invent research.
```

### 3. Autonomous outbound SDR

End-to-end SDR loop: ICP → source → waterfall-enrich → score → persona-specific multichannel sequence → classify replies → book or hand off → log in CRM. Human SDR oversees the agent seat.

```text
Create a Grok Bot automation named "Autonomous outbound SDR".

Trigger: a daily schedule at 06:00 America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Run one outbound SDR episode against the live ICP. Keep the episode short. Encode results so the next run can learn.

IMPORTANT: If the bot posted the Slack summary, stop. Do not post a second summary.

1. Load ICP, exclusions, daily volume cap, and suppression lists from the Sheet and from Salesforce or HubSpot.
2. Source new accounts and contacts from Apollo, ZoomInfo, or Clay. Prefer intent sources when connected: 6sense, Common Room, job posts, funding, tech installs, web visits.
3. Waterfall-enrich missing emails and titles. Do not guess an email pattern. If every provider misses, mark "unenriched" and skip send.
4. Score each contact against ICP plus intent. Write the score reasons as cited facts. Drop anyone below the documented threshold.
5. Skip already-touched contacts. Surface open opportunity stage, amount, and last activity when they exist.
6. Draft a persona-specific email sequence and a shorter LinkedIn note off the same hook. Pull style from 15–30 sent emails. Cite research. Never invent research. If a claim has no source, delete it.
7. Load drafts into Outreach, Salesloft, Smartlead, Artisan Ava, 11x Alice, or Gojiberry as paused. Post 2–3 sample pairs to #gtm-outbound and wait for human approval before any send.
8. After approval, send only within warmup and volume caps. Never send without that approval.
9. Classify new replies: meeting, question, objection, not-now, unsubscribe, out-of-office, other. Draft a reply. Do not send the reply.
10. For meeting-intent replies, offer times from Calendar / Calendly / Chili Piper and hand off to the AE in Slack. Do not book over an existing hold without the owner.
11. Log source, score, sequence, reply label, and next action in CRM and in the live Sheet. Reconcile the Sheet after sending.
12. Stop when the daily cap is hit or when the review queue is still waiting on a human.

CAUTION: Do not give send-authority before domain warmup, volume caps, unsubscribe handling, and a review path exist. Hybrid pods (one human SDR overseeing 2–3 agent seats) beat set-and-forget on meeting quality.
```

### 4. LinkedIn engager harvest to Instantly

codyschneider: Slack a LinkedIn post; extract engager URLs; Apollo emails; verify; Instantly campaign that references the post.

```text
Create a Grok Bot automation named "LinkedIn engager harvest to Instantly".

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

### 5. Company-research / target account list

Jay Sahnan /company-research: agent builds an ICP target-account list and deep-researches each company (Browserbase).

```text
Create a Grok Bot automation named "Company-research target account list".

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

### 6. Signup-to-outbound loop

Roman: Stripe signup → companies with 20+ employees → Airscale LinkedIn + mobile → Slack alert for the best accounts → every signup into Gojiberry for intent, research, and outreach.

```text
Create a Grok Bot automation named "Signup-to-outbound loop".

Trigger: a new Stripe customer or signup event.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A new person signed up for the product. Recover high-value signups that would otherwise sit in a generic email sequence.

The stack: Grok Bot is the brain, Stripe is signup data, Airscale is enrichment, GojiberryAI is intent plus outreach, Slack is the sales alert.

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

### 7. Closed-lost / no-show re-engagement

Monitor lost and no-show accounts for a new trigger, then a "timing changed" message that reuses original context. Cheapest pipeline.

```text
Create a Grok Bot automation named "Closed-lost no-show re-engagement".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Find closed-lost and no-show accounts whose timing may have changed, and queue re-engagement.

IMPORTANT: If the bot posted the weekly digest, stop. Do not post a second digest.

1. Pull opportunities in Salesforce or HubSpot with stage closed-lost, and meetings with no-show in Calendar or the meeting tool, from the lookback window in the Sheet (default 18 months for lost, 90 days for no-shows).
2. For each account, read the original close reason, last call notes from Gong or Granola, and last email thread in Gmail. Quote the original context. Do not invent a reason.
3. Scan for new triggers since the loss or no-show: funding, exec hire, product launch, job spike, tech change, new inbound, usage return. Cite each trigger. If none exists, skip the account.
4. Skip anyone who asked not to be contacted, who is in an open opportunity, or who was emailed about re-engagement in the last 60 days.
5. Draft a short "timing changed" email and LinkedIn note that references the original conversation and the new cited trigger. Do not pretend a meeting happened that did not.
6. Load drafts into a paused sequence in Gojiberry, Instantly, or Outreach. Post the list to #gtm-outbound with account, original reason, new trigger link, and draft.
7. Wait for the owner to approve. Never auto-send. After approval, enroll only approved people and log the re-open motion in CRM.
8. Update the Sheet: account, loss date, trigger, approval, send status, outcome.

CAUTION: Never auto-send outbound. Never invent research or a past conversation.
```

## Inbound / conversion

### 8. Inbound speed-to-lead

Form, chat, demo, or high-intent page → identify company → enrich → score ICP and urgency → 2–4 qualifying questions → book AE or nurture → CRM in seconds.

```text
Create a Grok Bot automation named "Inbound speed-to-lead".

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

### 9. PLG / PQL sales handoff

Usage thresholds (seats, feature adoption, invites, spikes) → company → decision-makers → expansion vs self-serve → Slack plus outbound or CSM play.

```text
Create a Grok Bot automation named "PLG PQL sales handoff".

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

## Meetings / CRM

### 10. Daily meeting prep

Kristaletz: pull Salesforce, Gmail, Slack, Granola, Gong or fresh research; short skimmable phone-readable brief; optional custom deck for the day's calls.

```text
Create a Grok Bot automation named "Daily meeting prep".

Trigger: a daily schedule at 06:30 America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Prepare the owner for today's external meetings. Output must be short and readable on a phone.

IMPORTANT: If the bot already posted today's prep in #gtm-meeting-prep or emailed it, stop. Do not send a second copy.

1. Use Calendar to list external meetings for today. Skip internal 1:1s unless they are tagged customer or prospect.
2. For each meeting, pull Salesforce or HubSpot: account, opportunity stage, amount, close date, last activity, stakeholders.
3. Pull recent Gmail threads with those contacts, Slack mentions, and the latest Granola or Gong notes. If none exist, say "no prior notes".
4. If still thin, do fresh research on the company site, news, hiring, and 10-K or earnings when public. Cite URLs. Do not invent.
5. Write a one-page brief per meeting: who will be there, relationship history, open opp, goal for the call, talk tracks, likely objections, one relevant case study, and risks. Keep it skimmable.
6. If the Slides / Figma bot or a master deck is connected and the meeting is a customer call, attach or update a custom deck copy. Do not invent quotes on a "What we've heard" slide; only use Granola/Gong text.
7. Post the briefs to #gtm-meeting-prep and/or email the owner. Do not email the customer.
8. Log that prep ran (meeting id, time, brief link) in the Sheet.

CAUTION: Never auto-send anything to the customer. Never invent research, numbers, or prior commitments.
```

### 11. Inbox scan + drafted replies

Only threads that plausibly need a reply. Digest plus a proposed reply in the owner's voice. Never auto-send.

```text
Create a Grok Bot automation named "Inbox scan drafted replies".

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

### 12. Follow-up drafts from call notes

Detect external calls since last run. Draft To / Subject / body grounded in what was discussed, with concrete next steps.

```text
Create a Grok Bot automation named "Follow-up drafts from call notes".

Trigger: a daily schedule, and optionally when a Granola or Gong transcript lands.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Draft follow-up emails from new external call notes. Do not send.

IMPORTANT: If the bot already drafted a follow-up for this meeting id, skip it. Do not email the customer.

1. List external Calendar events that ended since the last successful run.
2. For each event, fetch Granola and/or Gong notes and transcript. If notes are missing, skip and record "no notes".
3. Extract commitments, dates, owners, and objections from the notes. Quote the transcript for anything you claim was said. Do not invent a next step.
4. Draft To, Subject, and body to the customer or prospect. Include concrete next steps that appeared on the call. Match the owner's voice from sent mail.
5. Save as a Gmail draft. Post the draft link in #gtm-followups or Slack DM to the owner, with the meeting title and CRM opportunity.
6. Update Salesforce or HubSpot next step, close date, and stakeholders only when the notes support the change. Write the quote or timestamp in the activity.
7. Log meeting id, draft link, and CRM fields changed in the Sheet.

CAUTION: Never auto-send. Never invent research or commitments that are not in the notes.
```

### 13. CRM hygiene + next-best-action

Ramp-style: read emails, call notes, transcripts; update contacts, stages, next steps, close dates, stakeholders; flag stale deals; recommend next action. Human approval on stage changes that move forecast.

```text
Create a Grok Bot automation named "CRM hygiene next-best-action".

Trigger: a daily schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Keep Salesforce or HubSpot honest and recommend the next action. Short episode. Human approval for forecast-moving edits.

IMPORTANT: If the bot already posted today's hygiene digest, stop.

1. Pull open opportunities owned by the team, plus contacts with missing title, email, or account match.
2. For each open opp, read Gmail, Gong or Granola, and Slack for new activity since last close date or last activity field.
3. Propose updates: contacts, stage, next step, close date, stakeholders, amount. Each proposal must cite an email, call, or meeting. If you cannot cite it, do not propose it.
4. Apply low-risk writes automatically only if the Sheet says so: add missing contact, log activity, fill blank next step copied from a call note. Do not change stage, amount, or close date without human approval.
5. Flag stale deals (no human activity longer than the SLA in the Sheet, default 14 days) with a recommended next action from the playbook.
6. Post a digest to #gtm-revops: proposed field changes, stale deals, next-best-actions, and a one-click approval list.
7. After the owner approves, apply the remaining CRM writes. Log before/after in the Sheet.

CAUTION: Never auto-send outbound. Do not mass-close or mass-stage-change. Never invent activity or research. Playbooks orchestrate; the bot does not override the owner.
```

### 14. Forecasting brief

Nightly pipeline movement, forecast vs commit, stalled opps, inbound quality, call themes. Short brief on what is slipping and which accounts need exec attention. Cloudflare-style: draft, fact-check, then tone.

```text
Create a Grok Bot automation named "Forecasting brief".

Trigger: a daily schedule in the evening America/Chicago.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Compile a leadership forecast brief. Fact-check every number against CRM.

IMPORTANT: If the bot already posted tonight's brief, stop.

1. Pull pipeline from Salesforce or HubSpot: movement since yesterday, commit vs forecast vs pipeline, stalled opps, new inbound, win/loss.
2. Pull Granola, Gong, Slack, and email for call themes and risk language on the largest deals. Quote timestamps. Do not invent risk.
3. Auto-update opportunity notes in the owner's Salesforce format only when the note is a factual digest of a new call. Do not change amount or close date here.
4. Draft the brief: what moved, what is slipping, inbound quality, call themes, and up to 10 accounts that need exec attention, each with a cited reason.
5. Fact-check pass: every dollar, date, and stage must match CRM. Delete anything that does not.
6. Tone pass: short, no hype, no invented quotes.
7. Post to #gtm-forecast and optionally email leadership. Do not email customers.
8. Log the brief link and the 10 accounts in the Sheet.

CAUTION: Never invent forecast numbers. Never auto-send outbound. Do not change commit categories without a human.
```

### 15. Pre-call one-pager / ROI / proposal

Opportunity context + pricing catalog + past deals + security answers + call notes → first draft, missing inputs flagged, versioned and logged.

```text
Create a Grok Bot automation named "Pre-call one-pager ROI proposal".

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

## Marketing / content / creative

### 16. Slack marketing team

Eve: a team lead in Slack briefs five specialists — content, social, SEO, email, product marketing.

```text
Create a Grok Bot automation named "Slack marketing team".

Trigger: a new message in #marketing that contains /brief or @marketing-lead.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

A human briefed the marketing team lead in Slack. Route work to specialists. Do not publish.

IMPORTANT: If the bot posted the message, stop. Do not post a reply that retriggers /brief. A reply can start a new run and cause a loop.

1. Read the Slack brief and thread. Restate the requested asset, channel, deadline, and audience. If the brief is ambiguous, ask one focused question and stop.
2. Act as team lead. Spawn or call five specialists as separate bot sessions or skills: content, social, SEO, email, product marketing. Only call the specialists the brief needs.
3. Content: outline or draft the core narrative from brand docs. Social: channel-native posts. SEO: title, slug, internal links, search intent. Email: subject plus body in brand voice. PMM: positioning, audience, competitive note.
4. Each specialist must cite source briefs, product docs, or URLs. No invented customer quotes, metrics, or launch dates.
5. Collect drafts in one Slack thread with clearly labeled sections. Put publish-ready copy in a Notion or CMS review queue (Webflow, WordPress) as draft, not published.
6. Do not post to LinkedIn, X, email platforms, or ad accounts from this run.
7. Log the brief, specialist outputs, and review-queue links in the Sheet.

CAUTION: Never auto-send email or auto-publish. Humans ship.
```

### 17. Landing-page CRO auditor

Blunt (Tal Siach): paste a URL, get a scored memo with the priority fix, A/B picks, and an AI-smell check.

```text
Create a Grok Bot automation named "Landing-page CRO auditor".

Trigger: a Slack message in #marketing that contains a URL and /cro, or a daily schedule against a watched URL list.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Audit a landing page. Return a scored memo, one priority fix, A/B picks, and an AI-smell check.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Extract the URL. Open it with Browserbase or the browser. Capture headline, subhead, CTA, social proof, form, and obvious performance issues. Screenshot if possible.
2. If the page 404s or is blocked, report that and stop.
3. Score the page on a short rubric: clarity of offer, CTA, proof, friction, message match to ads/UTM if provided. Use only what is on the page or in linked analytics (GA4) if connected.
4. Name one priority fix. Propose 2–3 A/B picks that change one variable each.
5. Run an AI-smell check: generic claims, stock phrasing, leftover placeholder, mismatched voice. Quote the offending lines.
6. Do not invent conversion rates, lift, or competitor stats. If GA4 is connected, report real numbers with the date range. If not, omit metrics.
7. Post the memo in the Slack thread. Log URL, score, and priority fix in the Sheet. Do not edit the live page.

CAUTION: Never auto-send outbound. Never invent metrics or research. Never publish page changes.
```

### 18. Copywriter bot

Harry Dry style: banger copy for websites and landing pages. Short, specific, not corporate.

```text
Create a Grok Bot automation named "Copywriter bot".

Trigger: a Slack message in #marketing that contains /copy.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Write website or landing-page copy in a Harry Dry / direct-response style: short sentences, concrete nouns, no fluff.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the brief: page type, audience, offer, proof you are allowed to use, URL if any.
2. If proof (customers, numbers, quotes) is not in the brief or brand doc, do not invent it. Write around the gap or ask for the proof.
3. Draft headline, subhead, sections, and CTA. Offer 3 headline options.
4. Apply an anti-slop pass: cut adverbs, cut "empower", cut fake urgency. Read it aloud in the draft.
5. Post copy in the thread as text, not as a published CMS page. Wait for human edit and approval before anyone pastes it live.
6. Log brief and final copy link in the Sheet.

CAUTION: Never auto-send outbound. Never invent testimonials, metrics, logos, or research. Never auto-publish.
```

### 19. Content engine from one asset

Webinar, customer interview, or launch brief → claims and quotes → blog, SEO/GEO article, LinkedIn posts, email, one-pager, ad variants → CMS review queue → track converting angles.

```text
Create a Grok Bot automation named "Content engine from one asset".

Trigger: a Slack message in #marketing that contains /repurpose, or a new file in the source Drive/Notion folder.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Turn one source asset into a content set. Queue for review. Do not publish.

IMPORTANT: If the bot posted the message, stop. Do not start a second repurpose on the same asset id.

1. Load the source: webinar or interview transcript (Fireflies, Descript, Granola, Gong) or launch brief. Identify claims and quotes. Every quote needs a speaker and timestamp or doc location.
2. Drop any claim that is not in the asset or the brand fact sheet.
3. Produce drafts: blog / SEO / GEO article, LinkedIn posts, email, one-pager, and ad variants from the same claims. Vary format, not facts.
4. Put drafts in Webflow, WordPress, or Notion as unpublished review-queue items. Use Semrush or GSC only to suggest real queries; do not fake keyword volume.
5. Post a pack in Slack with links and which claim each asset uses. Ask for human approval to schedule.
6. After publish (by a human), track which angles convert if analytics are connected. Log in the Sheet. Do not auto-send the email or auto-post social.

CAUTION: Never invent quotes. Never auto-send or auto-publish.
```

### 20. Product demo recorder

Krushnasinh: hate recording product demos because the take is never the one you wanted. Tell the bot which screens; it does the rest.

```text
Create a Grok Bot automation named "Product demo recorder".

Trigger: a Slack message in #gtm-marketing that contains /demo and a screen list or URL list.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Record a product demo from a named list of screens. Do not publish the video.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the requested screens, narrative, audience, and length. If the screen list is missing, ask once and stop.
2. Sign into the product with the demo account only. Never use a real customer workspace. Never copy customer data onto demo screens.
3. Walk the screens in order. Capture the recording with the connected recorder or the bot computer. Follow the script; do not ad-lib fake metrics on screen.
4. If a screen errors, stop that take, note the error, and do not publish a broken demo.
5. Drop the file in Drive or the demo library as draft. Post the link in the Slack thread for human review.
6. Do not upload to YouTube, the marketing site, or outbound sequences until a human approves.
7. Log script, screens, file link, and approval in the Sheet.

CAUTION: Never use production customer data. Never invent research or on-screen metrics. Never auto-publish. Never auto-send the video in outbound.
```

### 21. Figma production bot

John Bai's figma bro: repetitive design and production tasks against the brand system.

```text
Create a Grok Bot automation named "Figma production bot".

Trigger: a Slack message in #design that contains /figma, or a new row in the creative request Sheet.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Do repetitive Figma production work from the brand system. Do not invent a new visual language.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Read the request: asset type, size, copy source, target file. Open the brand master in Figma MCP.
2. Duplicate from existing components. Do not restyle tokens unless the request says to.
3. Place only copy that was provided or that a human already approved. Do not write new claims or metrics on the canvas.
4. Name layers cleanly. Put the output on a clearly labeled page. Share the Figma link in Slack.
5. If the request is ambiguous (wrong size, missing logo lockup), ask one question and stop.
6. Do not export to ads or CMS without human approval.
7. Log request, file link, and status in the Sheet.

CAUTION: Never auto-send outbound. Never invent copy, metrics, or research on the canvas. Never overwrite the master deck or brand library.
```

### 22. Competitive intel → battlecards

Monitor competitor sites, changelogs, pricing, ads, earnings, G2, and call mentions. Refresh battlecards and objection scripts. Alert PMM.

```text
Create a Grok Bot automation named "Competitive intel battlecards".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Refresh competitive enablement from primary sources and call mentions.

IMPORTANT: If the bot already posted this week's intel digest, stop.

1. Load the competitor list from the Sheet. Visit each site, changelog, pricing page, and G2 with Browserbase. Pull ads if an ads library MCP is connected. Pull earnings if they are public companies.
2. Search Gong or Granola for competitor mentions since last run. Quote with timestamps. Do not paraphrase a mention you did not find.
3. Diff against last week's battlecard. List only confirmed positioning, pricing, or product shifts, each with a URL or call timestamp.
4. Update battlecards and objection scripts in Notion, Highspot, Seismic, or Drive as a new version. Do not delete the prior version.
5. Push short snippets to CRM / sales rooms only as "unverified until PMM approves" if you post before approval. Default: post the digest to #pmm and wait.
6. Alert PMM in Slack with what changed, evidence links, and recommended talk-track edits.
7. Log competitor, change, evidence, and battlecard version in the Sheet.

CAUTION: Never invent a competitor feature or price. Never auto-send outbound that names a competitor without PMM approval.
```

### 23. Paid campaign optimizer

Ingest CPA, ROAS, audience, creative, and landing-page performance. Pause losers, shift budget to winners, generate new creative from top messages, weekly "what changed and why".

```text
Create a Grok Bot automation named "Paid campaign optimizer".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Review paid performance and propose budget and creative changes. Do not spend money without approval.

IMPORTANT: If the bot already posted this week's paid digest, stop.

1. Pull Google Ads, Meta Ads, and LinkedIn Ads via their APIs or MCPs, plus GA4 and CRM conversions, for the past 7 days and the prior 7 days.
2. Rank campaigns, ad sets, and creatives by CPA, ROAS, and volume. Use only platform-reported numbers. State the window.
3. Propose pausing creatives or ads that fail the documented threshold in the Sheet. Propose shifting budget to winners. Do not execute pause or budget changes yet.
4. Generate new creative copy and Figma or ad-variant briefs from the top-performing messages. Do not invent proof.
5. Post a "what changed and why" memo to #growth-paid with tables, proposed actions, and new creative drafts.
6. After a human approves named actions, apply only those pause/budget edits. Recheck spend caps.
7. Log proposals, approvals, and live changes in the Sheet and CRM conversion mapping.

CAUTION: Never auto-send outbound. Do not pause, start, or reallocate spend without human approval. Never invent ROAS, CPA, or research.
```

### 24. Last-30-days social research

slashlast30days / Matt Van Horn: research a person or brand's last 30 days across socials for top-of-funnel research and personalization.

```text
Create a Grok Bot automation named "Last-30-days social research".

Trigger: a Slack message that contains /last30days and a person, company, or handle.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Research the last 30 days of public social activity for a person or brand. Use for personalization, not for sending.

IMPORTANT: If the bot posted the message, stop. Do not post a reply. A reply can start a new run and cause a loop.

1. Parse the target name or handle. If ambiguous, ask once and stop.
2. Pull public posts from X, LinkedIn, and other connected socials for the last 30 days. Prefer the last30days-style aggregator if that MCP or bot is connected.
3. Summarize themes, launches, hires, opinions, and notable posts. Each bullet needs a URL and date. Skip anything you cannot open.
4. Flag possible buying signals (hiring, new product, funding mention) as hypotheses with links, not as facts beyond the post.
5. Do not scrape private profiles. Do not invent posts.
6. Post the memo in the Slack thread and write it to the account's research tab in the Sheet or CRM note.
7. Do not send outreach from this run. Another template may use the citations after human approval.

CAUTION: Never invent posts or quotes. Never auto-send outbound.
```

## Account / enablement

### 25. Per-account customer expert

One agent per strategic account: Slack, calls, email, weekly media rundown, buying signals, feature requests, tickets, new features. State file so it does not repeat itself.

```text
Create a Grok Bot automation named "Per-account customer expert".

Trigger: a weekly schedule, once per strategic account in the Sheet.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Act as the customer expert for one named strategic account. Update the state file. Do not spam the customer.

IMPORTANT: If the bot already posted this week's rundown for this account, stop.

1. Read the account name from the trigger and the prior state file in Drive or Notion so you do not repeat last week's items.
2. Watch the account Slack channels, Gmail, Gong or Granola, and support tickets. Digest new threads and calls with quotes and timestamps.
3. Run a weekly media rundown: exec posts on X and LinkedIn, webinars, podcasts, blogs, competitor mentions. Include sentiment and quotes with timestamps or URLs.
4. Flag buying signals, feature requests, open tickets, and product features we shipped that match their requests. Cite each.
5. Write the new state file. Post a short rundown to the account team Slack channel, not to the customer.
6. Draft any customer-facing note for the owner. Do not send it.
7. Log signals, tickets, and feature matches on the Salesforce or HubSpot account.

CAUTION: Never email or Slack the customer automatically. Never invent quotes or tickets. Use the state file to avoid repeats.
```

### 26. Slides bot

Owns customer decks in Figma from the brand system and master deck. Copies per customer, translates. Favorite skill: update the "What we've heard" slide live from the Granola transcript.

```text
Create a Grok Bot automation named "Slides bot".

Trigger: Calendar at meeting start for accounts with a Figma deck, or a Slack message that contains /heard.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Maintain the customer deck. Update the "What we've heard" slide from live notes.

IMPORTANT: If the bot posted the message, stop. Do not fork a second deck for the same meeting id.

1. Identify the account and the Figma customer copy of the master deck. If no copy exists, duplicate the master and name it for the account. Do not edit the master.
2. Before the call, refresh title, attendees, and agenda from Calendar and CRM. Do not invent case-study metrics.
3. During or immediately after the call, read the Granola transcript. Update only the "What we've heard" slide with short bullets that quote the customer. Each bullet needs a timestamp.
4. If Granola has not landed yet, wait and retry once. Do not fill the slide from memory.
5. If translation was requested, duplicate the deck and translate while keeping layout. Flag untranslated screenshots.
6. Post the Figma link to the owner in Slack. Do not present or send the deck to the customer.
7. Log deck URL and "What we've heard" version on the opportunity.

CAUTION: Never invent customer quotes. Never overwrite the brand master. Never auto-send the deck.
```

### 27. Sales coach from Gong

Watch external Gong calls and give improvement feedback.

```text
Create a Grok Bot automation named "Sales coach from Gong".

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

### 28. Event / webinar pipeline

ICP plus lookalike invite list → personalized invites → post-event enrich attendees vs no-shows → score engagement → route hot, nurture the rest with a session-specific talk track.

```text
Create a Grok Bot automation named "Event webinar pipeline".

Trigger: a weekly schedule before the event, then a one-shot run after the event ends.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Run event or webinar pipeline work for the event named in the Sheet.

IMPORTANT: If the bot already posted this phase's digest, stop.

1. Read event name, date, session topics, and ICP from the Sheet.
2. Before the event: build an invite list from ICP plus lookalikes in Apollo or Clay. Deduplicate against CRM and recent outreach. Draft personalized invites that cite a real reason they fit the session. Load a paused Instantly, Outreach, or email campaign. Do not send without approval.
3. After the event: import attendees, registrants, and no-shows. Enrich with Apollo or Airscale. Score engagement: attended, asked a question, visited pricing if analytics exist. Cite the source field.
4. Route hot accounts to AEs in #gtm-inbound with a session-specific talk track quoting their question or the session they sat in. Draft follow-ups. Do not send.
5. Put the rest in a nurture campaign as paused. Log every person, score, and route in CRM and the Sheet.
6. Wait for human approval before any invite or follow-up send.

CAUTION: Never auto-send invites or follow-ups. Never invent attendance.
```

### 29. TAM / territory refresh

Continuously rebuild TAM from firmographics plus custom signals. Score. Rebalance territories by capacity and win rate. Push prioritized lists with contacts attached.

```text
Create a Grok Bot automation named "TAM territory refresh".

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

### 30. Projects manager that spawns specialists

Eric Zakariasson: a projects manager bot that creates specialists (coder, designer, researcher, writer) and runs projects as a team.

```text
Create a Grok Bot automation named "Projects manager".

Trigger: a Slack message in #gtm-ops that contains /project, or a new project row in the Sheet.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

You are the projects manager. Spawn specialist Grok bots and coordinate one project. You do not do all the work yourself.

IMPORTANT: If the bot posted the message, stop. Do not create a second project for the same Slack ts. A reply can start a new run and cause a loop.

1. Read the project brief. Restate goal, deadline, constraints, and what "done" means. If the brief is vague, ask one focused question and stop.
2. Create or call specialists the work needs. Default set: researcher, writer, designer, coder. For GTM briefs, add SDR or PMM only if the brief needs them. Give each specialist a one-paragraph job and the tools they may use.
3. Create the project record in the Sheet or Notion: owner, specialists, status, links.
4. Assign first tasks. Researcher gathers cited facts only. Writer drafts from those facts. Designer works in Figma from the brand system. Coder only touches repos the human named.
5. Collect specialist output. Do not publish, send email, tweet, or merge code. Gate all outbound and all production deploys on the human project owner.
6. Post a status in the Slack thread: who did what, links, blockers, and the next human decision.
7. On later /project status commands, update the same record. Do not spawn duplicate specialists with the same role unless one failed.

CAUTION: Never auto-send outbound. Never invent research. Specialists do not get send or prod credentials unless the owner names them.
```

### 31. AEO / GEO mention tracking

Dan Kulkov / Dawood Khan: Grok Bot as Chief of AI Visibility. CrowdReply MCP. Track and improve brand mentions inside ChatGPT, Grok, Google AI, and Perplexity answers.

```text
Create a Grok Bot automation named "AEO GEO mention tracking".

Trigger: a weekly schedule.

When the automation runs, start a session with the prompt below. Everything after this line is the session prompt.

Act as Chief of AI Visibility. Measure whether the brand is cited in AI answers. Draft work to improve citations. Do not publish pages or send outreach without approval.

IMPORTANT: If the bot already posted this week's visibility digest, stop.

1. Load the brand, product names, competitors, and target questions from the Sheet (the prompts from the AEO article the team stored).
2. Connect the CrowdReply MCP if available. For each target question, record whether ChatGPT, Grok, Google AI Overviews, and Perplexity mention the brand, a competitor, or neither. Quote the answer and date. Do not fabricate a mention.
3. Diff against last week. List gained, lost, and unchanged questions.
4. For gaps, recommend cited actions only: which existing article, page, or third-party source already supports an answer, and what is missing. Do not invent backlinks or rankings.
5. Draft on-site or content briefs into the Notion review queue. Do not publish.
6. Post the digest to #pmm or #aeo with tables, quotes, and recommended briefs. Log results in the Sheet.
7. Do not pitch journalists or send outbound from this run without a separate approved template.

CAUTION: Never invent AI-answer quotes. Never auto-publish. Never auto-send.
```

## Sources

Research compiled 2026-08-31 from public posts and a private Grok panel answer. Metrics and quotes below are from those posts only.

### Gojiberry / Roman (ICP outbound, signup loop)

- [I let 3 Grok bots take over one of my employees' LinkedIn accounts](https://x.com/romanbuildsaas/status/2093621993262223407) — @romanbuildsaas, Aug 29, 2026. ICP, GojiberryAI MCP, 97 leads, personalized messages, connection requests.
- [GrokBot booked a demo with a 50-person company in less than 24 hours](https://x.com/romanbuildsaas/status/2093962339233964323) — @romanbuildsaas, Aug 30, 2026. 97 contacted, 33 accepted, 15+ replied, 1 demo.
- [Signup → Stripe → Airscale → Slack → Gojiberry](https://x.com/romanbuildsaas/status/2094312818992468097) — @romanbuildsaas, Aug 31, 2026. 20+ employees, Airscale LinkedIn + mobile, every signup into Gojiberry.
- [Grok Bot booked a demo for us (almost) in autopilot](https://x.com/romanbuildsaas/status/2094326465303097748) — quote of @pierreeliottlal.
- [GojiberryAI is now available inside Grok Bot](https://x.com/gojiberryai/status/2094024289825558816) — @gojiberryai, Aug 30, 2026. MCP: find in-market leads, tune ICP and signals, rewrite copy, reply, enrich, score intent.

### Kristaletz (Grok Bot for GTM)

- [Grok Bot for GTM](https://x.com/kristaletz/status/2089103618121314689) — @kristaletz, Aug 16, 2026. Meeting prep, inbox drafts (never auto-send), Granola/Gong follow-ups, prospecting guardrails, per-account customer expert, forecasting, slides bot ("What we've heard"), Gong sales coach. Salesforce, Gmail, Calendar, Sheets, Drive, Slack, Notion, Granola, Figma, X, LinkedIn.
- [Repost](https://x.com/kristaletz/status/2092658608035250403) — Aug 26, 2026.
- [Grok Bot for GTM: From Prospecting to Customer Calls](https://x.com/kristaletz/status/2091573453409472513) — live walkthrough, Aug 23, 2026.

### Eric thread (bot templates)

- [what are the best grok @bots you've used so far?](https://x.com/ericzakariasson/status/2094448760281796952) — @ericzakariasson, Aug 31, 2026.
- Projects manager that spawns specialists — @ericzakariasson, [share post](https://x.ai/bot/FU-Ev6_Ju4lFGWwWRD0GD) referenced in that thread.
- [last30days](https://x.com/ericzakariasson/status/2094448760281796952) — @mvanhorn / @slashlast30days, social research across the last 30 days.
- Harry Dry copywriter — @joseamijares in the same thread.
- Blunt landing-page reviews — @Talsiach in the same thread. Scored memo, priority fix, A/B picks, AI-smell check.
- Demo Video — @KdJadeja911 in the same thread. Tell it which screens.
- figma bro — @johnbai in the same thread. Repetitive Figma production.

### Bookmarks and other GTM posts

- [Ramp Revenue / GTM coworker](https://x.com/ParthGujare_/status/2080716441041465427) — @ParthGujare_, Jul 24, 2026. CRM updates, inbox, prospecting, post-call follow-ups, playbooks, human approval.
- [Full AI GTM operator loop](https://x.com/chrispisarski/status/2081846875217399998) — @chrispisarski, Jul 27, 2026. ICP/TAM, signals, outbound, inbound, AEO, closed-lost, PQL, call analysis, pre-call briefs, one-pager/ROI/proposal, CRM.
- [Deploy a marketing team in Slack](https://x.com/evedev_/status/2084284424233828532) — @evedev_, Aug 3, 2026. [vercel-labs/marketing-team-eve-template](https://github.com/vercel-labs/marketing-team-eve-template). Content, social, SEO, email, product marketing.
- [/company-research](https://x.com/JaySahnan/status/2047730585313980499) — @JaySahnan, Apr 24, 2026. ICP target-account list, Browserbase. Also [Signal outbound stack](https://x.com/JaySahnan/status/2048457832387764398).
- [LinkedIn engager → Apollo → Instantly](https://x.com/codyschneider/status/2023834888596545773) — @codyschneider, Feb 17, 2026.
- [grok bot is literally Jarvis for AEO](https://x.com/DanKulkov) — @DanKulkov, Aug 31, 2026, quoting @dawoodkhan254 on ranking brands inside ChatGPT, Grok, Google AI, and Perplexity (CrowdReply MCP).
- [Introducing Grok Bot](https://x.com/bot/status/2087224798078517251) — @bot, Aug 11, 2026.

### Format

Skeleton copied from [dabit3/cloud-agent-automations](https://github.com/dabit3/cloud-agent-automations) (Cloud Agent Workflows README): Create line, Trigger, session prompt after the divider, numbered steps, loop guards, least-privilege MCP note. Create line uses Grok Bot, not Devin.
