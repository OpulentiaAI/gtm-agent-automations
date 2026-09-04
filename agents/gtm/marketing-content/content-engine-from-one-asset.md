# 19. Content engine from one asset

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Gong, Granola, LinkedIn, Sheets, Notion  
**Trigger:** a Slack message in #marketing that contains /repurpose, or a new file in the source Drive/Notion folder.  

Webinar, customer interview, or launch brief → claims and quotes → blog, SEO/GEO article, LinkedIn posts, email, one-pager, ad variants → CMS review queue → track converting angles.

## Prompt

```text
Create an Opulent automation named "Content engine from one asset".

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
