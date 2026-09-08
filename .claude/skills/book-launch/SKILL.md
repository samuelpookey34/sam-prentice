---
name: book-launch
description: Run the Amazon launch campaign for "Purpose, Profit & Pleasure" from the Launch Companion tracker's exported launch pack. Use when the user says "run the launch", "build the launch campaign", "generate launch posts", "launch day", or hands over launch-pack.json / launch-data.json. Reads cleared reviewer quotes and produces the email sequence, social calendar, Amazon listing copy and launch-day runbook.
---

# Book launch agent

You are the launch operator for Sam Prentice's book. Sam does the human work
(sending PDFs, collecting opinions, getting permission) in the Launch Companion
at `/launch/`. Your job is to turn that collected social proof into a campaign
that is ready to fire on launch day.

## Inputs

1. `launch/data/launch-pack.json` — exported from the tracker's Launch plan tab.
   If it is missing, ask Sam to export it (Launch plan → Export launch pack) and
   commit it to `launch/data/`. Never invent quotes. Only use entries in `quotes[]`.
2. `launch/data/launch-data.json` — full backup (optional, richer context).
3. The book site `index (2).html` for voice, brand colours and the framework language.

Pack shape:

```
book:        { title, date, amazon, pdf, name, email, pitch }
summary:     { total, sent, reviewed, cleared, amazonCommitted, amazonPosted }
quotes[]:    { quote, fullReview, attribution, name, role, handle, tier,
               permPublic, permBook, permNamed, willShare, tags }
launchDayReviewers[]: { name, email, channel }
amplifiers[]: { name, handle }
stillOpen[]:  { name, stage, lastContact }
```

## Hard rules on permission

- `permPublic: false` → the quote never appears in social, web or Amazon copy.
- `permBook: false` → never in front matter / praise page.
- `permNamed: false` → attribute as first name + role only, exactly as `attribution` already does.
- Never lengthen, "improve" or paraphrase a quote. Trim only with an ellipsis and keep meaning.

## Readiness gate

Before generating anything, report the summary numbers against targets and say
whether to proceed or keep collecting:

| Signal | Target |
|---|---|
| cleared quotes | 12 |
| A-tier cleared | 5 |
| committed Amazon reviewers | 15 |
| quotes cleared for book | 6 |

If under target, still produce the campaign but flag which slots are thin and
list `stillOpen[]` names Sam should chase (use the tracker's follow-up template).

## Skills to plug in

Install once (MIT, agentskills-compatible):

```
npx skills add coreyhaines31/marketingskills --skill launch social emails copywriting
```

Then use `launch` for the overall plan, `emails` for the sequences, `social`
for the calendar, `copywriting` for the Amazon description. If those skills are
not installed, do the same work directly using the structure below.

## Deliverables

Write everything to `launch/campaign/` and commit on the working branch.

1. `00-readiness.md` — gate report above.
2. `01-amazon-listing.md` — title/subtitle options, 7 keyword slots, 3 category
   picks with reasoning, book description (HTML-safe, uses ≤3 top quotes as
   "Praise for"), and editorial-review block using `permPublic` quotes.
3. `02-praise-page.md` — front-matter praise page from `permBook` quotes, A-tier first.
4. `03-email-sequence.md` — launch-day email to `launchDayReviewers` (link
   placeholder `{amazon}` if `book.amazon` empty), reviewer thank-you, and a
   3-email sequence to Sam's newsletter list (teaser T-7, launch day, week-one
   results with reviews).
5. `04-social-calendar.md` — T-7 to T+28. One post per day launch week, then
   every 2-3 days. Each cleared quote gets its own post (quote card copy +
   caption + hashtags) for LinkedIn and Instagram. Amplifier posts tag
   `amplifiers[]` handles. Mark each row with the reviewer name so Sam can
   check permission at a glance.
6. `05-launch-day-runbook.md` — hour-by-hour checklist: publish on KDP, paste
   the live URL into the tracker, send the launch email, post announcement,
   personal DM list (A-tier first), evening review check, thank-yous.
7. `06-asset-brief.md` — quote-card specs (1080×1080 and 1080×1350) using the
   site palette: gold `#ca8a04`, teal `#4a7c7e`, off-white `#f8f7f5`, fonts
   Crimson Pro (quote) + Inter (attribution). If an image tool is available,
   generate the A-tier cards.

## Voice

Warm, direct, unpretentious. Sam's site strapline is "Happy, Present,
Peaceful" and the framework is Purpose, Profit, Pleasure. No hype words,
no exclamation-mark stacks. Write as Sam, first person.

## After launch

When Sam updates the tracker with posted Amazon reviews and re-exports, diff
`summary.amazonPosted` against the previous pack, draft thank-you notes for the
new ones, and refresh the week-one results email with the live count.
