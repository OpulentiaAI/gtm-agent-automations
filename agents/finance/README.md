# Finance

Invoices, burn, runway, rev rec, and the pack the board actually gets.

## Agents

- [Invoice Reconciler](invoice-reconciler.md) — A team invoice reconciler with access to several teammates’ inboxes, working out whether an invoice should be approved · uses `email, QuickBooks, Slack`.
- [Spend Reconciler](spend-reconciler.md) — Weekly across AWS, your model providers, and SaaS, with what moved explained · uses `AWS, QuickBooks, Google Sheets`.
- [Modeler](modeler.md) — Rebuilds with a new hiring plan and shows runway under three growth cases · uses `Google Sheets, Postgres, Slack`.
- [Expense Filer](expense-filer.md) — Works from a photo dump of receipts, coded to the right category · uses `cloud browser, QuickBooks, text`.
- [Collections Agent](collections-agent.md) — Chases every overdue invoice with a polite email and a real escalation path · uses `Stripe, email, Slack`.
- [Bookkeeper](bookkeeper.md) — 90% of transactions categorized before a human opens the books · uses `QuickBooks, Stripe`.
- [Margin Watcher](margin-watcher.md) — Tells you the day gross margin moves more than a point, and why · uses `Postgres, Google Sheets, Slack`.
- [Board Reporter](board-reporter.md) — Builds the financials from the source systems · uses `QuickBooks, Google Drive, Postgres`.
- [Subscription Auditor](subscription-auditor.md) — Finds the duplicate three teams are all paying for · uses `QuickBooks, email, Google Sheets`.
- [Cash Forecaster](cash-forecaster.md) — Weekly, with the week it gets tight named early · uses `QuickBooks, Google Sheets, Slack`.
- [Audit Prepper](audit-prepper.md) — The pack ready, with the auditor’s first 40 questions already answered · uses `Google Drive, QuickBooks, email`.
- [Rev Rec Runner](rev-rec-runner.md) — Monthly, with the contracts that break the template flagged · uses `Stripe, Google Sheets, Google Drive`.
- [Deal Pricer](deal-pricer.md) — Checks a custom enterprise deal against your real cost to serve · uses `Postgres, Google Sheets, Slack`.
