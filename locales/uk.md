# United Kingdom

Tax year covered: 2026/27 (6 April 2026 to 5 April 2027). England, Wales and Northern Ireland; Scotland's income tax bands differ. Sources: GOV.UK.

## Basics

- Currency: GBP · Language tag: en-GB · Time zone: Europe/London
- Clock changes: forward at 01:00 on the last Sunday in March, back at 02:00 on the last Sunday in October. Offset `+01:00` in between, `+00:00` otherwise.
- Tax year: 6 April to 5 April

## Deadlines

- Everyone: 5 April tax year ends (use any ISA allowance first); 6 April new allowances and check your tax code.
- Employed: P60 by 31 May; P11D (benefits) by 6 July.
- Self Assessment: register by 5 October after your first year; online return and balance due 31 January; second payment on account 31 July.
- Company directors: confirmation statement within 14 days of its review date each year; accounts to Companies House 9 months after year-end; corporation tax payment 9 months and 1 day after year-end; CT600 return 12 months after year-end; payroll (RTI) on or before each payday if running a salary; VAT returns 1 month and 7 days after each quarter if registered.

## Accounts and pensions

- ISAs: £20,000 a year across all ISAs. Lifetime ISA: up to £4,000 of that, 25% bonus, open aged 18–39, for a first home or from 60.
- Pensions: tax relief at your highest rate. Workplace pension with employer contributions, often by salary sacrifice; personal pension (SIPP) gets basic-rate relief added. Earliest access age 55, rising to 57 from 6 April 2028.
- State Pension: full new State Pension £12,548 a year (£241.30 a week), from age 67 for most people now under 60.

## Help

- Free debt advice: StepChange, National Debtline, Citizens Advice
- Money guidance: MoneyHelper
- Complaints: a company has 8 weeks to give a final response; then the Financial Ombudsman Service (money) or the relevant ombudsman.

## Visualisation settings

The money visualisation ships with these, and its built-in tax maths is for the UK:

```js
const LOCALE = { lang:'en-GB', currency:'GBP', taxModel:'uk', taxFreeAccount:'an ISA',
  statePension:12548, statePensionAge:67, pensionAge:{min:55, max:60, d:57, hint:'57 from April 2028'} };
```

## Doc wording

The templates are written for the UK, so nothing needs changing.
