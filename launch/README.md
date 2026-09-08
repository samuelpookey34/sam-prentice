# Launch Companion

Reviewer and social-proof tracker for the Amazon launch of *Purpose, Profit & Pleasure*.

Live at `/launch/` on the site (same Netlify deploy; `noindex` so it stays out of search).
Open `launch/index.html` locally if you prefer.

## What it does

- Tracks everyone you send the PDF to through a pipeline:
  Identified → Asked → PDF sent → Reading → Review in → Permission asked → Cleared → Posted on Amazon
- Stores each person's review verbatim, a short pull-quote, and exactly what they cleared
  (public / in-book / named attribution) plus whether they will post on Amazon and share.
- Dashboard shows what needs action today (overdue follow-ups, opinions waiting on
  permission, cleared people not yet asked to review on Amazon).
- Seven email templates with placeholders. "Log as sent" stamps dates, sets the next
  follow-up and advances the stage.
- Social proof tab is the quote bank. Launch plan tab has settings, a phased checklist
  and the launch-pack export.

## Data

Everything lives in the browser's localStorage. Back it up:

1. Click **Data → Export everything (JSON backup)** and save it as `launch/data/launch-data.json`.
2. When the quote bank is ready, click **Launch plan → Export launch pack** and save as
   `launch/data/launch-pack.json`.
3. Commit both. Import restores on any other device.

## Hand-off to the launch agent

The `book-launch` skill in `.claude/skills/book-launch/` reads `launch/data/launch-pack.json`
and generates the campaign (Amazon listing copy, praise page, email sequence, social calendar,
launch-day runbook) into `launch/campaign/`. In Claude Code:

```
/book-launch
```

It builds on the open-source marketing skills from
[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)
(`launch`, `social`, `emails`, `copywriting`):

```
npx skills add coreyhaines31/marketingskills --skill launch social emails copywriting
```
