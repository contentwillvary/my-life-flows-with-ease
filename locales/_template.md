# [Country]

Tax year covered: [e.g. 2027]. Last checked: [date]. Sources: [official links].

## Basics

- Currency: [ISO code, e.g. EUR] · Language tag: [e.g. de-DE] · Time zone: [IANA name, e.g. Europe/Berlin]
- Clock changes: [when, or "none"]. Used to set the right offset on one-off reminders.
- Tax year: [dates]

## Deadlines

The weekly deadline watch checks these. Group them by work type.

- Everyone: [e.g. tax return due date, tax-free allowance resets]
- Employed: [ ]
- Self-employed: [ ]
- Company directors: [ ]

## Accounts and pensions

- Tax-free savings and investment accounts: [names and yearly limits]
- Workplace and personal pensions: [how tax relief works; earliest access age]
- State pension: [full amount per year; age it starts]

## Help

- Free debt advice: [organisations]
- Money guidance: [government-backed service]
- Complaints: [how long a company has to reply; which ombudsman or regulator]

## Visualisation settings

Copy into the `LOCALE` block at the top of the money visualisation:

```js
const LOCALE = { lang:'[e.g. de-DE]', currency:'[e.g. EUR]', taxModel:'manual', taxFreeAccount:'[e.g. a tax-free account]',
  statePension:[per year], statePensionAge:[age], pensionAge:{min:[ ], max:[ ], d:[ ], hint:'[ ]'} };
```

## Doc wording

What to change in the templates. UK term → local term, or "remove".

| UK term in the templates | Here |
| --- | --- |
| ISA / Lifetime ISA | [ ] |
| Workplace pension / SIPP | [ ] |
| Self Assessment (31 Jan) | [ ] |
| National Insurance | [ ] |
| Student loan Plan 1/2/4/5 | [ ] |
| Council tax | [ ] |
| P60, tax code | [ ] |
| StepChange, National Debtline, Citizens Advice, MoneyHelper | [ ] |
| Example figures (£40,000 salary) | [a typical local salary in local currency] |
