# GTM

Prompt templates for Opulent automations for marketing and sales. Each file is a complete prompt, including the recommended trigger. No code is required.

## Playbook: Stand up a GTM template

### Overview

Turn one GTM file into a paused automation: the named MCPs, your channel and Sheet names, and a first run that cannot send.

### What's Needed From User

- The template file (example: `outbound/icp-builder-linkedin-outbound.md`)
- MCPs listed in that file (Gojiberry, Slack, Salesforce or HubSpot, Gmail, Calendar, Sheets, Gong or Granola, and so on)
- Destination Slack channel, Sheet tab, and CRM object names
- Send authority only after domain warmup, volume caps, and a human review path exist

### Procedure

1. Open the template and list **Uses** and the Trigger.
2. Connect those MCPs with least privilege. Keep send and ad-spend scopes off until a later approve step.
3. Copy the full prompt. Replace `#gtm-*` channels, Sheet tabs, and timezones with yours.
4. Paste into a new Opulent session. Create the automation Disabled or paused.
5. Run one tick. Confirm the digest or review pack landed once and asked for approval.
6. Validate CRM/Sheet rows against the sources the prompt cited. Enable the schedule only after that pack is clean.

### Specifications

- First run is draft / paused campaign / Slack review pack — never a live send
- Loop guard held: the bot’s own post did not start a second run
- Validation: open the Slack thread and the Sheet. Count of leads or meetings must match rows you can click; missing enrichment is blank, not invented

### Forbidden Actions

- Do not auto-send outbound, InMail, or customer email from the first run
- Do not invent research, emails, or employee counts
- Do not grant admin CRM or unrestricted ad-account write to stand the template up

Shared setup steps: [Stand up an Opulent agent](../PLAYBOOK.md).

## Folders

- [Outbound / prospecting](outbound/README.md)
- [Inbound / conversion](inbound/README.md)
- [Meetings / CRM](meetings-crm/README.md)
- [Marketing / content / creative](marketing-content/README.md)
- [Account / enablement](account-enablement/README.md)

## All templates

- [1. ICP builder + LinkedIn outbound](outbound/icp-builder-linkedin-outbound.md)
- [2. Signal-triggered outbound](outbound/signal-triggered-outbound.md)
- [3. Autonomous outbound SDR](outbound/autonomous-outbound-sdr.md)
- [4. LinkedIn engager harvest to Instantly](outbound/linkedin-engager-harvest-to-instantly.md)
- [5. Company-research / target account list](outbound/company-research-target-account-list.md)
- [6. Signup-to-outbound loop](outbound/signup-to-outbound-loop.md)
- [7. Closed-lost / no-show re-engagement](outbound/closed-lost-no-show-re-engagement.md)
- [8. Inbound speed-to-lead](inbound/inbound-speed-to-lead.md)
- [9. PLG / PQL sales handoff](inbound/plg-pql-sales-handoff.md)
- [10. Daily meeting prep](meetings-crm/daily-meeting-prep.md)
- [11. Inbox scan + drafted replies](meetings-crm/inbox-scan-drafted-replies.md)
- [12. Follow-up drafts from call notes](meetings-crm/follow-up-drafts-from-call-notes.md)
- [13. CRM hygiene + next-best-action](meetings-crm/crm-hygiene-next-best-action.md)
- [14. Forecasting brief](meetings-crm/forecasting-brief.md)
- [15. Pre-call one-pager / ROI / proposal](meetings-crm/pre-call-one-pager-roi-proposal.md)
- [16. Slack marketing team](marketing-content/slack-marketing-team.md)
- [17. Landing-page CRO auditor](marketing-content/landing-page-cro-auditor.md)
- [18. Copywriter bot](marketing-content/copywriter-bot.md)
- [19. Content engine from one asset](marketing-content/content-engine-from-one-asset.md)
- [20. Product demo recorder](marketing-content/product-demo-recorder.md)
- [21. Figma production bot](marketing-content/figma-production-bot.md)
- [22. Competitive intel → battlecards](marketing-content/competitive-intel-battlecards.md)
- [23. Paid campaign optimizer](marketing-content/paid-campaign-optimizer.md)
- [24. Last-30-days social research](marketing-content/last-30-days-social-research.md)
- [25. Per-account customer expert](account-enablement/per-account-customer-expert.md)
- [26. Slides bot](account-enablement/slides-bot.md)
- [27. Sales coach from Gong](account-enablement/sales-coach-from-gong.md)
- [28. Event / webinar pipeline](account-enablement/event-webinar-pipeline.md)
- [29. TAM / territory refresh](account-enablement/tam-territory-refresh.md)
- [30. Projects manager that spawns specialists](account-enablement/projects-manager-that-spawns-specialists.md)
- [31. AEO / GEO mention tracking](account-enablement/aeo-geo-mention-tracking.md)
