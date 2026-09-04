# 20. Product demo recorder

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Sheets  
**Trigger:** a Slack message in #gtm-marketing that contains /demo and a screen list or URL list.  

Krushnasinh: hate recording product demos because the take is never the one you wanted. Tell the bot which screens; it does the rest.

## Prompt

```text
Create an Opulent automation named "Product demo recorder".

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
