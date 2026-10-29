---
name: Monthly payday transfers
schedule: Two days each month at 08:40, set from payday during setup (the second run is a backup). If income varies, no schedule: run it by hand when money lands.
cron: "40 8 {{TRANSFER_DAYS}} * *"
for: Everyone
---

Work out {{NAME}}'s payday transfers so they can do them all in ONE sitting, with no calculating.

About {{NAME}}: {{ABOUT}}
Payday: {{PAYDAY}}.

First, open the **Monthly log** in the Monthly money tab of the money doc ({{MONEY_DOC}}). If this month's "Payday transfers" is already ticked, reply "Transfers done this month ✓" and stop. This task runs twice a month on purpose, so this is normal.

1. Read the Payday plan in the Monthly money tab. Check email for this month's payslip or income, and anything that changes an amount (a bill rise, a one-off cost, a card statement).
2. Reply with a numbered checklist in the order the money moves: **From → To · Amount · Reference**. Exact amounts, no ranges. Say which rows are automatic (standing orders) and only need checking.
3. If pay may not have landed yet (it's before payday, or no payslip has arrived), say "Do these once your pay shows in your account" at the top. Pay often arrives on the Friday before when payday falls on a weekend or bank holiday.
4. If income varies: work out this month's fixed "salary" from the holding account, how much goes to the buffer, and the tax set-aside amount.
5. End with "Reply 'done' and I'll log it." When they reply, tick this month's "Payday transfers" in the Monthly log with today's date, and add a win.

Never make the transfers yourself.
