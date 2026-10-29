# Countries

Everything that depends on where someone lives is kept in one file per country, so the rest of the kit stays the same everywhere.

| File | Status |
| --- | --- |
| [uk.md](uk.md) | Complete: England, Wales and Northern Ireland, 2026/27. Scotland: same, except income tax bands. |
| [_template.md](_template.md) | Blank. Copy it to add a country. |

## How it's used

During setup Claude asks where you live and opens that country's file. It uses it to:

1. **Adapt the docs.** The templates are written in UK terms (ISA, Self Assessment, council tax). Claude swaps each UK term for the local one using the file's *Doc wording* table, and removes what has no equivalent.
2. **Set up the money visualisation.** It copies the file's *Visualisation settings* into the `LOCALE` block at the top of `visualisation/money-visualisation.html` before publishing. Outside the UK the money visualisation switches to "enter my take-home myself", since its built-in tax maths is UK-only.
3. **Fill the routines.** The *Deadlines* list goes into the weekly deadline watch, and the time zone and clock-change rule decide when routines run.

## Adding a country

If there's no file for your country, Claude makes one during setup. It copies `_template.md`, fills it from official government sources, and lists each source with the date it checked. Read it through before relying on it. If it looks right, it's worth sharing back so the next person gets it ready-made.

Tax rules change every year. Each file says which tax year it covers; refresh it when that year ends.
