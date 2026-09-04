# 22. Competitive intel → battlecards

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Gong, Granola, Browserbase, Sheets, Notion  
**Trigger:** a weekly schedule.  

Monitor competitor sites, changelogs, pricing, ads, earnings, G2, and call mentions. Refresh battlecards and objection scripts. Alert PMM.

## Prompt

```text
Create an Opulent automation named "Competitive intel battlecards".

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
