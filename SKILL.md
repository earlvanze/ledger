---
name: real-estate-ledger-csv-analyst
description: Analyze a user-supplied real-estate general-ledger CSV into property-level operating summaries, monthly income statements, NOI, and review-ready exceptions. Use for private CSV analysis and investor reporting; never publish or retain ledger data.
---

# Real-Estate Ledger CSV Analyst

Analyze only a CSV that the operator has supplied for the current task. Treat every transaction row as confidential financial data. Do not upload, publish, commit, or quote raw ledger rows outside the operator's requested output.

## Workflow

1. Confirm the reporting period, properties in scope, and the user's intended categories if the CSV is ambiguous.
2. Inspect the header and validate dates, amounts, category labels, and property identifiers. Report missing or malformed fields rather than silently guessing.
3. Normalize income and expenses separately. Preserve original values and document any category mapping used for summaries.
4. Produce the requested views:
   - property and portfolio income, expense, net-balance, and NOI summary;
   - monthly income statement;
   - filtered transaction detail with running balances;
   - exceptions such as uncategorized entries, duplicates, unusual amounts, or negative income.
5. State that outputs are operating views, not audited financial statements, tax advice, or investment advice. Cap-rate and investment calculations require user-verified inputs and assumptions.

## Guardrails

- Never invent a transaction, property, category, date, balance, or accounting treatment.
- Do not treat a browser summary as the source of truth when the source CSV is available.
- Keep raw data local to the approved workspace. Use redacted excerpts in summaries unless the operator explicitly requests line-level detail.
- Before exporting a report, verify its selected period, property filters, totals, and that it contains no unintended personal or bank information.

## Useful output format

Start with a compact table showing each property’s income, expenses, NOI, and open exceptions. Then provide the category mappings and assumptions, followed by a short exception list and any requested monthly or transaction detail.
