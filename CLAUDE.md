# My life flows with ease: instructions for Claude

This folder sets someone up with two living docs, a money visualisation and a set of scheduled routines that keep life admin and money ticking over with very little effort. The kit is named after its home page, the **My life flows with ease** doc; **Money uplifts me** and the **Money visualisation** are linked from the top of it. Your job is to set it up for the person in front of you, then help them keep it up. When you hand over at the end of setup, give them the My life flows with ease link first and call it their home page.

When they say anything like "set me up", "get started" or "what is this", run **Setup** below. Go one step at a time, keep messages short, and never ask more than three questions at once.

## Files

| Path | What it is |
| --- | --- |
| `templates/my-life-flows-with-ease/` | Life admin doc, one file per tab. `README.md` is the main view: TL;DR, the **Everything at a glance** table (Theme · Item · Status · Next step · When) and This Week. Each theme has its own tab, linked from the Theme cell, so detail stays out of the way. Then Wins. |
| `templates/money-uplifts-me/` | Money doc, one file per tab (12). `README.md` is the main view: key takeaway, wins, links to every other tab, and next actions. Figures and charts live in `key-figures.md`. |
| `visualisation/money-visualisation.html` | The interactive money visualisation (take-home pay, debts, and when savings could cover retirement, a lower income, or everything), all in one file. Numbers stay in the viewer's browser. The `LOCALE` block at the top of its script holds everything country-specific. |
| `locales/` | One file per country: deadlines, accounts, help organisations, visualisation settings and wording swaps. See `locales/README.md`. |
| `screenshots/` | Images for the README. Not used during setup. |
| `routines/*.md` | One scheduled routine per file: frontmatter (name, schedule, cron, who it's for) then the prompt, with `{{PLACEHOLDERS}}`. |
| `routines/_ground-rules.md` | Appended to the end of every routine prompt. |
| `my-setup.md` | The person's own details. Created during setup. Git-ignored: never commit it. |
| `my-docs/` | Local copies of their docs, only if Claude Docs aren't available. Git-ignored. |

## Setup

### 1. Get to know them (saves to `my-setup.md`)

Ask, a few at a time:

- First name, and the pronouns to use in routine prompts.
- Which country they live in, so you know which rules apply and can set their time zone (e.g. Europe/London). Read the computer's time zone too and check the two agree. Then open `locales/<country>.md`. If there isn't one, make it now: copy `locales/_template.md`, fill it from official government sources, list each source with today's date, and ask them to look it over. Everything country-specific below comes from this file.
- Work type: employed / self-employed / company director / mixed / not working right now.
- Payday: a fixed day of the month (which?), the last working day, or "varies".
- Company year-end and accountant name, and bookkeeping app (directors and self-employed only).
- Which admin themes apply (Travel, Health, Documents and ID, Home and errands, Complaints and correspondence, Family and care, plus their own).
- In their own words: why they want this, and anything that makes admin hard for them (it shapes the tone of the routines).

Write `my-setup.md` with these answers plus an **About** paragraph (3–5 sentences) that every routine will include as `{{ABOUT}}`. Keep sensitive detail out of it: no account numbers, no passwords, no balances.

### 2. Make their docs

Each template is a folder, and **each file in it is one tab**, in the order given in the comment at the top of its `README.md`. `README.md` is always the first tab, the main view. A link to another file in the folder (e.g. `[Travel](travel.md)`) becomes a link to that tab.

- **If a Claude Docs connector is available:** create "My life flows with ease" and "Money uplifts me" as two docs, one tab per file. Turn every file link into a link to the matching tab. Keep headings, tables and wording; keep `[square bracket]` placeholders. For admin themes they don't need, delete both the tab and its table row. For a theme of their own, add a tab and a row.
- **Otherwise:** copy both folders into `my-docs/` and use those paths as the doc links everywhere below. The file links work as they are.
- **Outside the UK:** apply the *Doc wording* table from their country file as you create the docs. Swap example figures into local currency and a typical local salary.

### 3. Publish the money visualisation

The money visualisation is one self-contained HTML file. Each person publishes their own copy, so their numbers are never shared.

1. Copy `visualisation/money-visualisation.html` to `my-docs/` (create the folder if needed). Replace the `LOCALE` block at the top of its script with the *Visualisation settings* from their country file. For the UK it's already right, so leave it as it is.
2. If you can publish artifacts, publish that copy as a private artifact. Otherwise tell them to open the file in their browser.
3. Fill the **Links** line at the top of both docs so the two docs and the money visualisation point to each other, and save all three links in `my-setup.md`.

**Charts in the money doc.** The Key figures tab has two "Chart goes here" lines. Once that tab has real numbers (step 7), draw them with the doc's own chart feature:
- **How your security builds up:** yearly totals of savings and pension, against the "lower income covered" line. Work out the series with the same model as the money visualisation (the `project()` function in its HTML), using their numbers.
- **Where your money goes:** the buckets from the "Where it goes" table in Monthly money.

If the docs can't draw charts, suggest a screenshot of the money visualisation's chart instead. Until there are real numbers, leave the "Chart goes here" lines as they are.

### 4. Connect email

Most routines read email to stay up to date. Check whether an email connector (Gmail, Outlook) is connected; if not, explain in one line why it helps and how to connect it. The routines only read email; they never send or delete.

### 5. Choose routines

Show this table and ask which they want. Suggest the starred ones to begin with; they can add more later.

| Routine | When | For |
| --- | --- | --- |
| ★ Daily admin nudge | Daily 12:00 | Everyone |
| ★ Weekly admin update | Sun 19:50 | Everyone |
| ★ Weekly money refresh | Sun 19:30 | Everyone |
| Weekly deadline watch | Mon 11:45 | Most useful if self-employed or a director |
| ★ Monthly balances & check-in | Around payday, twice (second run is a backup) | Everyone |
| ★ Monthly payday transfers | Around payday, twice (second run is a backup) | Everyone |
| Quarterly bookkeeping session | 10 Jan/Apr/Jul/Oct | Self-employed or directors |
| Quarterly strategy review | 20 Jan/Apr/Jul/Oct | Everyone |
| Renewal reminder | One-off, about 5 weeks before each renewal | One per insurance, fix or deal end |

Offer to move any time, but never to between 01:00 and 02:59: the clocks change then, so a run can be skipped or doubled.

**Payday days.** Never do date maths in cron (no "payday − 1"): it breaks on the 1st and in short months. Only use days 1–28, which exist in every month. Look the days up here:

| Payday | `CHECKIN_DAYS` | `TRANSFER_DAYS` |
| --- | --- | --- |
| 1st | `2,4` | `1,3` |
| 2nd–26th (call it D) | D−1 and D+1 | D and D+2 |
| 27th–31st, or last working day | `25,27` | `26,28` |
| Varies | `1,3` | No schedule: create it as an on-demand task they run by hand when money lands |

For example, payday on the 15th gives `CHECKIN_DAYS` = `14,16` and `TRANSFER_DAYS` = `15,17`. The routines tick a Monthly log in the money doc, so the second run of each pair stops at once if the first one worked. The transfers routine tells them to wait for their pay to land if it runs early.

### 6. Create the routines

For each routine they choose:

1. Take the prompt (everything after the frontmatter) and append `routines/_ground-rules.md`.
2. Replace every `{{PLACEHOLDER}}` from `my-setup.md` and their country file: `NAME`, `ABOUT`, `COUNTRY`, `TIMEZONE`, `DEADLINES` (the country file's Deadlines list, keeping only the lines for their work type), `ADMIN_DOC`, `MONEY_DOC`, `VISUALISATION`, `PAYDAY`, `WORK_TYPE`, `YEAR_END`, `ACCOUNTANT`, `BOOKKEEPING_APP`, and `CHECKIN_DAYS` / `TRANSFER_DAYS` in the cron (from the payday table). For a renewal reminder, also `WHAT`, `PROVIDER` and `DATE`. If something doesn't apply, replace it with "none" rather than leaving a placeholder. Check that no `{{` is left in the prompt or the cron.
3. Create it as a scheduled task with whatever scheduler you have (Claude Code's scheduled tasks, Cowork's Scheduled tab, or Claude's own scheduled tasks). Before creating the first one, find out three things about that scheduler:
   - **Time zone:** does it take times in their local time zone? If it only takes UTC, convert, and warn that runs will shift by an hour when the clocks change.
   - **Day-of-month, quarterly and one-off dates:** some schedulers only offer hourly, daily, weekly or weekdays. If yours can't do a routine's exact days, schedule it daily at the same time and put a date gate at the very top of its prompt: "First, check today's date in {{TIMEZONE}}. Unless it is day 14 or 16 of the month, reply only 'Not today' and stop." Use the routine's own days; for quarterly ones, add the months too. For one-offs, gate on the exact date, and tell them to delete the task after it has run.
   - **Where it runs:** schedulers that run in the cloud keep going when the computer is off, but can only reach the docs through connectors, not local files. If their docs are local copies in `my-docs/`, the tasks must run on their computer.
4. **One-off tasks** (renewal reminders), where the scheduler supports them, take a timestamp with an offset, not a cron. Use the offset in force *on that date*, not today's: their country file gives the clock-change rule. In the UK, for example, 11:00 on 15 Sep 2027 is `2027-09-15T11:00:00+01:00` (summer time) even if you create it in November. The date must be in the future.
5. List the tasks back with the scheduler's own next-run times. Check each one is on the day and at the hour you meant, and fix any that aren't before moving on.
6. Tell them two things:
   - Whether their tasks need the computer on. Some run only while the Claude app is open, and run late when it next opens; others run in the cloud. Say which applies to the scheduler you used. The routines check the date, so a late run is fine.
   - Each run starts fresh: everything a routine needs is in its prompt and the docs.

### 7. Fill the docs in

Offer to fill the docs now by chatting: they tell you what's going on in their own words, and you put it in the right place. With email connected, offer to search for appointments, bookings, renewals and payslips first and draft the glance table from those. Once Key figures has real numbers, draw the two charts (step 3).

## Keeping it up

- **Admin doc:** every item is one row in the glance table. Status follows the rules under the table. Detail goes in that theme's tab, newest first. Finished items move to Wins.
- **Money doc:** keep the main view short: takeaway, wins, links, next actions. Everything else goes in its tab. Never guess a figure; leave the placeholder until there's a real number. Wins go in the Wins log, newest first, never deleted.
- **Changing a routine:** edit its file here if the change is for everyone, or just update the scheduled task if it's only for them.
- **Country rules change every year.** When the tax year in their country file has ended, offer to refresh it.
- Money content is a planning aid, not financial advice.
