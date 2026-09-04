# Data

Answers with the query attached, plus the monitors that catch a silent zero.

## Agents

- [Analyst](analyst.md) — Lives in #data. Answers with the query it ran, so anyone can check the work · uses `Postgres, Amplitude, PostHog, Slack`.
- [Churn Explainer](churn-explainer.md) — Pulls the cohorts, tests the obvious causes, and shows what held up · uses `Postgres, Amplitude, Slack`.
- [Metrics Email](metrics-email.md) — Stopped sending the numbers nobody opens · uses `Postgres, email, Slack`.
- [Dashboard Monitor](dashboard-monitor.md) — Finds the broken one before an exec does · uses `Postgres, Slack, Amplitude`.
- [Metrics Librarian](metrics-librarian.md) — One place they are defined, and every query that disagrees gets flagged · uses `Notion, Postgres, Slack`.
- [Tracking Auditor](tracking-auditor.md) — Lists every event firing wrong · uses `Amplitude, GitHub, Slack`.
- [Pricing Analyst](pricing-analyst.md) — Works from real usage and names the unprofitable customers · uses `Postgres, Google Sheets, Slack`.
- [Chart Builder](chart-builder.md) — The animated one for the board deck, straight from the warehouse · uses `Postgres, Figma, Google Drive`.
- [Pipeline Watcher](pipeline-watcher.md) — Catches the one that silently started returning zero rows · uses `Postgres, Slack, Datadog`.
- [Reconciler](reconciler.md) — Checks the finance numbers against the product numbers and finds the gap · uses `Postgres, QuickBooks, Google Sheets`.
- [Signal Spotter](signal-spotter.md) — Finds the customer whose usage says they’re building something you should know about · uses `Postgres, Slack, HubSpot`.
- [Anomaly Sweep](anomaly-sweep.md) — Weekly across your top 30 metrics, reporting only what moved · uses `Postgres, Slack, Amplitude`.
