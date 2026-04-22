---
name: excel-wizard
description: Builds complex spreadsheets with functional formulas and data modeling. Use this skill whenever the user wants to create, design, or improve a spreadsheet — including financial models, trackers, dashboards, data tables, or any Excel/Google Sheets file. Trigger on phrases like "build a spreadsheet", "make a tracker", "create a formula", "model this in Excel", "set up a sheet for", or "help me with Excel". Also trigger when the user shares data and wants it organized, calculated, or visualized in a spreadsheet format. Always use this skill before generating any spreadsheet output to ensure formulas, structure, and formatting are handled correctly.
---

# Excel Wizard

A skill for building well-structured, formula-driven spreadsheets and financial models.

## Core Principles

1. **Formula First** — Before outputting data, specify the Excel/Sheets formulas to be used (e.g., `SUMIFS`, `XLOOKUP`, `IF`, `INDEX/MATCH`). Prefer modern functions (`XLOOKUP` over `VLOOKUP`) unless compatibility with older Excel versions is required.

2. **Variables Section** — For any financial model or configurable tracker, always create a dedicated **Variables / Inputs** section at the top of the sheet. Users should be able to change key inputs in one place and have everything else update automatically.

3. **Formatting Suggestions** — Always suggest specific cell ranges for formatting:
   - Bolding for headers and totals (e.g., `A1:Z1`, row 1)
   - Borders to separate sections
   - Conditional formatting rules (e.g., "Set C2:C100 to green fill if value > 0, red if < 0")
   - Number formats (currency, percentage, date)

4. **Named Ranges** — For frequently referenced cells or ranges, suggest named ranges (e.g., `TaxRate`, `StartDate`) for readability and maintainability.

---

## Output Structure

When building a spreadsheet, always output in this order:

### 1. Sheet Layout Overview
List the sheets/tabs and their purpose (e.g., `Dashboard`, `Data`, `Variables`, `Summary`).

### 2. Variables / Inputs Section
List adjustable inputs with:
- Cell reference
- Label
- Default value
- Notes/constraints

### 3. Formula Specifications
For each calculated column or cell, specify:
- Cell reference
- Formula (exact syntax)
- Plain-language explanation

### 4. Formatting Guide
List formatting rules with:
- Range
- Rule/format to apply
- Reason

### 5. File Output
If using the `xlsx` skill to generate the actual file, read `/mnt/skills/public/xlsx/SKILL.md` for implementation details.

---

## Common Formula Patterns

| Use Case | Recommended Formula |
|---|---|
| Conditional sum | `=SUMIFS(sum_range, criteria_range, criteria)` |
| Flexible lookup | `=XLOOKUP(lookup_value, lookup_array, return_array, "Not found")` |
| Dynamic row count | `=COUNTA(A:A)-1` |
| Running total | `=SUM($B$2:B2)` |
| % of total | `=B2/SUM($B$2:$B$100)` |
| YoY growth | `=(B2-A2)/A2` |
| Nested condition | `=IFS(A2>90,"A",A2>75,"B",A2>60,"C",TRUE,"F")` |
| Error handling | `=IFERROR(formula, "—")` |
| Date difference | `=DATEDIF(start,end,"D")` |
| Dynamic average | `=AVERAGEIFS(...)` |

---

## Financial Model Template

When building a financial model from scratch, use this default structure:

**Sheet 1 — Variables**
- Time horizon (months/years)
- Revenue assumptions
- Cost assumptions
- Tax rate, discount rate, growth rate

**Sheet 2 — P&L / Projections**
- Revenue, COGS, Gross Profit, OPEX, EBITDA, Net Income
- All cells reference Variables sheet

**Sheet 3 — Dashboard**
- Key metrics: Revenue, Net Margin, Burn Rate
- Charts: Line (trend), Bar (comparison), Pie (composition)

---

## Conditional Formatting Rules (Quick Reference)

| Scenario | Rule |
|---|---|
| Positive values | Green fill if value > 0 |
| Negative values | Red fill if value < 0 |
| Above target | Green if ≥ target cell |
| Overdue dates | Red if date < TODAY() |
| Top 10% | Use Top/Bottom rule |
| Duplicates | Highlight duplicates in orange |

---

## Notes

- If the user is building a **Google Sheets** file, flag any Excel-only functions (e.g., `XLOOKUP` requires Google Sheets 2022+).
- If the user needs an actual `.xlsx` file generated, load `/mnt/skills/public/xlsx/SKILL.md` for the correct implementation approach.
- Always ask clarifying questions if the data structure, row count, or use case is unclear before specifying formulas.
