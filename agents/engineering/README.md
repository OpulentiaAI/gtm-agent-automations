# Engineering

Cloud coding, CI, production, security, migrations, and the paperwork that keeps a team shipping.

## Agents

- [Personal Cloud Coder](personal-cloud-coder.md) — A personal cloud coding agent that codes like you. Learns from your PR reviews, orchestrates a frontier model for the main agent and cheaper open-source models for execution, and ships PRs from an iMessage while your laptop is dead · uses `GitHub, text, Slack`.
- [Architecture Librarian](architecture-librarian.md) — Maps how the codebase fits together, then reads every incoming PR to keep that map current. Pings you in Slack about the PRs you actually need to read, and answers codebase and decision-history questions for new teammates · uses `GitHub, Slack, Notion`.
- [Production Monitor](production-monitor.md) — Watches metrics and logs in Sentry and CloudWatch, and posts in a public Slack channel when something needs attention. The whole team can dig in from the thread · uses `Sentry, AWS, Slack`.
- [CI Babysitter](ci-babysitter.md) — Helps push your PRs to merge by fixing CI errors and addressing review comments · uses `GitHub, Slack`.
- [Bug Investigator](bug-investigator.md) — Does a first-pass investigation the moment #escalated-support gets a ping or someone tags it in a channel, using logs and GitHub, so it is waiting for you · uses `Slack, GitHub, Sentry`.
- [Multiplayer Jarvis](multiplayer-jarvis.md) — A cloud coding agent that lives in Slack. Anyone can ping it in a channel; it puts up a v1 and a draft PR assigned back to them. Bonus: hook feedback or logs and let it put up its own PRs · uses `Slack, GitHub, Vercel`.
- [QA Tester](qa-tester.md) — Walks the production app's critical end-to-end flows every morning in its own browser, with pass, fail, and screenshots in #eng before standup · uses `cloud browser, Slack, Linear`.
- [Security Reviewer](security-reviewer.md) — Runs Vercel's deepsec on every PR and proves each finding is real on its own before posting it · uses `GitHub, Vercel, Slack`.
- [Test Flake Fixer](test-flake-fixer.md) — Quarantines the worst flaky CI tests each week, files the ticket to fix them properly, and puts up the fix when it has one · uses `GitHub, Linear, Slack`.
- [Slow-Drip Codebase Migrator](slow-drip-migrator.md) — Maps out the migration, then walks it one PR at a time overnight, checking logs and metrics before each stage · uses `GitHub, Postgres, Datadog`.
- [Eval Maintainer](eval-maintainer.md) — Runs the eval suite and reads production logs for new cases worth adding · uses `GitHub, Datadog, Google Sheets`.
- [Prototyping Agent](prototyping-agent.md) — Takes an idea and hands back a v1, with screenshots and a live preview link · uses `Vercel, cloud browser, Slack`.
- [Runbook Keeper](runbook-keeper.md) — Rewrites the on-call runbook from what actually happened in the last three incidents · uses `Notion, Slack, Datadog`.
- [Dependency Upgrader](dependency-upgrader.md) — Reads the release notes and breaking changes, then walks 40 services one PR at a time, stopping where the tests do · uses `GitHub, Slack`.
- [Metric Monitor](metric-monitor.md) — Watches one number every day (ours was time to first token), finds the PRs that likely regressed it, and puts up a fix it tested itself · uses `Datadog, GitHub, Slack`.
- [Query Doctor](query-doctor.md) — “Why is this slow?” answered with the plan, not an opinion · uses `Postgres, Slack`.
- [Changelog Writer](changelog-writer.md) — Figures out what is actually live as PRs merge, flags flip, and releases go out, writes it in your voice, then turns it into the marketing copy · uses `GitHub, LaunchDarkly, Notion`.
- [CVE Triager](cve-triager.md) — Escalates only what is actually reachable from your code · uses `GitHub, Sentry, Slack`.
- [Infra Cost Analyzer](infra-cost-analyzer.md) — Does a daily pass and puts up the PR to turn off what nobody uses · uses `AWS, GitHub, Slack`.
- [Rollout Specialist](rollout-specialist.md) — Takes something new through 1%, 10%, then 50% of traffic, and rolls it back on its own when the error rate or another signal moves. Say “ship it” in Slack and it babysits the rest · uses `Vercel, Datadog, Slack`.
- [Customer Bug Reproducer](customer-bug-reproducer.md) — Pulls the production logs and the support ticket, reproduces the bug, and captures enough detail for an engineering agent to pick up · uses `Sentry, Intercom, Linear`.
- [Flag Janitor](flag-janitor.md) — Audits every feature flag older than 90 days, daily, with the deletion PR attached · uses `LaunchDarkly, GitHub, Slack`.
- [Design / Planning Doc Writer](design-planning-doc-writer.md) — Pulls the ideas and open questions out of Slack, writes the first pass, checks it against the code, and chases comments before anyone gets too deep · uses `Slack, Notion, GitHub`.
- [Self Improver](self-improver.md) — Reads its own production logs, finds where it failed, and opens PRs to fix itself · uses `Datadog, GitHub, Slack`.
- [Postmortem Writer](postmortem-writer.md) — Has it done within the hour, with the real timeline pulled from Slack, incident.io, and the deploy log · uses `Slack, GitHub, Notion`.
- [Legacy Service Migrator](legacy-service-migrator.md) — Reads the old service, writes the new one, runs both side by side, and shows you where they disagree · uses `GitHub, Postgres, Datadog`.
- [On-Call Handoff](on-call-handoff.md) — Every morning: what broke overnight, what is still open, and who owns it · uses `Slack, Datadog, Linear`.
- [SDK Release Manager](sdk-release-manager.md) — Cuts the version, writes the migration notes, and publishes when tests are green · uses `GitHub, Mintlify, Slack`.
- [Compliance Specialist](compliance-specialist.md) — Reads your contractual agreements or SOC2 requirements, and monitors PRs so the code matches · uses `GitHub, Google Drive, Slack`.
- [Metric Owner](metric-owner.md) — In charge of an important metric (time to first token, site load speed) that multiple things could regress. Runs benchmarks every day, identifies which PRs caused regressions, and ships the fixes to get it back green · uses `Datadog, GitHub, Slack`.
