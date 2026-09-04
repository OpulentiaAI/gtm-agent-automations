# 31. AEO / GEO mention tracking

**Category:** GTM · Account / enablement  
**Uses:** Sheets, Notion  
**Trigger:** a weekly schedule.  

Dan Kulkov / Dawood Khan: Opulent as Chief of AI Visibility. CrowdReply MCP. Track and improve brand mentions inside ChatGPT, Grok, Google AI, and Perplexity answers.

## Prompt

```text
Create an Opulent automation named "AEO GEO mention tracking".

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
