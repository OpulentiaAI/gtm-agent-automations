# 26. Slides bot

**Category:** GTM · Account / enablement  
**Uses:** Slack, Calendar, Granola, Figma  
**Trigger:** Calendar at meeting start for accounts with a Figma deck, or a Slack message that contains /heard.  

Owns customer decks in Figma from the brand system and master deck. Copies per customer, translates. Favorite skill: update the "What we've heard" slide live from the Granola transcript.

## Prompt

```text
Create an Opulent automation named "Slides bot".

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
