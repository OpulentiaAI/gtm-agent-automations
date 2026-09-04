# Opulent for Work

I can't do my job without Opulent.

It happened really quickly. A few weeks ago, I wasn’t leveraging agents like the AI-pilled experts you see on X and LinkedIn. I was still a human in the loop: directing questions and thought partnership to chat agents, doing most of the work myself, and sometimes using AI on the last mile. Now, I’m orchestrating dozens of bots and building complex AI workflows throughout my work.

There are a lot of guides out there about how an agent can save you money or automate monotonous chores. I want to show you the four bots that actually changed my output at work. Welcome to Opulent for Work 101.

## Communication

Work is a constant battle of prioritization and context-switching. Half your day goes to emails, Slacks, texts, and syncs, and if you don't have a system for all of it, you can hit 5PM wondering where the time went.

The hardest part isn’t the hundreds of messages across multiple inboxes, it’s triaging and deciding what to actually respond to. It isn’t realistic to expect fewer messages, so it’s about knowing which three messages actually need a response.

This is where [Inbox Manager](inbox-manager.md) comes in. Hook it up to your communication tools and it becomes the first line of defense. Train it to read every email, Slack, and DM, sift through the noise, and only escalate the stuff that's both important and urgent. It could respond to everything; this one is set to read-only. Its job is to find the actual fires and help you prioritize where to spend time.

## Time

Calendars are personal. While some people like to block off their mornings for deep work, many parents have to sign off early to go pick up kids.

When you book a meeting, place it as close as possible to other meetings so large windows of focused time survive. That’s hard to defend, because other people will schedule things for you.

This is why execs have EAs — to learn, define, and uphold the way they manage their time, especially as the calendar becomes more complex.

Now, Opulent serves as an executive assistant for the rest of us. [Calendar EA](calendar-ea.md) manages the calendar, flags conflicts, and drafts invites. Over time it learns the quirks: optimize for deep focus time, book meeting rooms close to each other, and don't be late for pickup.

## Information

Receiving, filtering, and acting on information is the lifeblood of every job. The challenge is keeping track of where the information is being shared across Slack DMs, emails, and threads you may not be tagged in.

This process can be time-consuming but the repercussions are real, like finding out that an important decision was made the day before in a channel you didn’t read.

[Intel Scout](intel-scout.md) keeps you informed and sharp. It has access to inbox, Slack, and meeting notes to digest context you did and didn't see. Every weekday, at 8am and 5pm, it tells you three things:

1. what happened across the company that affects you or your team,
2. what action items still need to be followed up on,
3. and what you need for upcoming meetings.

## Putting it together

Opulent has solved three components of work: communication, time, and information. Getting more done can still raise mental load from three new work surfaces. So there is a bot for that.

[Bot Boss](bot-boss.md) is the fourth and possibly most important bot. Instead of three bots pinging about an email, an afternoon briefing, or an upcoming meeting conflict, they all report into Bot Boss.

When a bot has an update, Bot Boss receives it and tells you. When you have a question, Bot Boss gets the answer from the right bot. Bot Boss keeps the bot team on-task, efficient, and consolidated.

## What this means

If Opulent is managing your work and itself, what does that mean for the job?

Mental clarity. Zoom out, identify where the leverage is, and focus time on the highest priorities. That's the difference between a tool requiring your time versus empowering you to maximize yours.

## Playbook: Stand up the Work desk

### Overview

Stand Inbox Manager, Calendar EA, and Intel Scout, then put Bot Boss in front so you get one stream instead of three pings. Same jobs as the files below. Setup only.

### What's Needed From User

- Read-only email, Slack, DMs, Calendar, and meeting notes
- Timezone and quirks (focus windows, pickup hard stop)
- One stream for Bot Boss (Slack DM or named channel)
- Enable after each first-open — all four clocks start Disabled

### Procedure

1. Stand [Inbox Manager](inbox-manager.md) with read-only mail/Slack/DMs. Validate widget then fire board.
2. Stand [Calendar EA](calendar-ea.md) with a live calendar pull and written quirks. Validate options + Default on one conflict.
3. Stand [Intel Scout](intel-scout.md) with notes + inbox + Slack. Validate a three-part cited brief or silence.
4. Stand [Bot Boss](bot-boss.md) last. Point it at the three specialists and the one stream.
5. Disable direct specialist pings to you so only Bot Boss talks.
6. Enable clocks only after one morning board shows themes, priorities, and one impact play.
7. Validate the next afternoon: non-obvious only, no specialist retrigger, no send.

### Specifications

- Four automations exist; Bot Boss is the only front door
- Specialists stay on-job (inbox / calendar / intel); Bot Boss does not build or audit
- Validation: one morning board you can open, each priority tied to a spoke or marked `UNVERIFIED`

### Forbidden Actions

- Do not Enable all four clocks before first-open
- Do not let the three specialists page you in parallel with Bot Boss
- Do not grant send or calendar write on day one

For a single agent, use [Stand up an Opulent agent](../PLAYBOOK.md).

## Agents

- [Inbox Manager](inbox-manager.md) — first line of defense on email, Slack, and DMs · uses `email, Slack, DMs / text`
- [Calendar EA](calendar-ea.md) — defend deep-focus blocks · uses `Google Calendar, Slack, text`
- [Intel Scout](intel-scout.md) — twice-daily three-part brief · uses `email, Slack, meeting notes`
- [Bot Boss](bot-boss.md) — single front door for the bot team · uses `Slack, text, specialist agents`
