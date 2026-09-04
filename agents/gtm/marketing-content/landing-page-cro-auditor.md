# 17. Landing-page CRO auditor

**Category:** GTM · Marketing / content / creative  
**Uses:** Slack, Browserbase, Sheets  
**Trigger:** a Slack message in #marketing that contains a URL and /cro, or a daily schedule against a watched URL list.  

Blunt (Tal Siach): paste a URL, get a scored memo with the priority fix, A/B picks, and an AI-smell check.

## Prompt

```text
Create an Opulent automation named "Landing-page CRO auditor".

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
