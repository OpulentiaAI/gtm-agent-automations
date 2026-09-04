# 24. Last-30-days social research

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, LinkedIn, Sheets  
**Trigger:** a Slack message that contains /last30days and a person, company, or handle.  

slashlast30days / Matt Van Horn: research a person or brand's last 30 days across socials for top-of-funnel research and personalization.

## Prompt

```text
Create an Opulent automation named "Last-30-days social research".

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
