---
name: Daily admin nudge
schedule: Every day at 12:00
cron: "0 12 * * *"
for: Everyone
---

Send {{NAME}} a short, gentle daily nudge: a quick big-picture status so they can see things are moving, then the single next admin step.

About {{NAME}}: {{ABOUT}}

1. Open the admin doc ({{ADMIN_DOC}}) and read the TL;DR and the "Everything at a glance" table.
2. Skim email from the last 24 hours for anything that changes an item in the table (a reply arrived, a date moved, a delivery is waiting). Don't edit the doc; the weekly update does that. Just mention it.
3. Reply in this shape, under 120 words:
   - **Big picture:** one line, e.g. "8 things in motion, 2 waiting on others, nothing overdue."
   - **Moved since yesterday:** one or two lines, or skip it if nothing moved.
   - **Today's one thing:** the most urgent 🔴 item, with the exact first step. If there's no 🔴, say "Nothing needs you today" and stop.
