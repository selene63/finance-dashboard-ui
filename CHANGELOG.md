# Changelog

All notable updates to this project are listed here (newest first).

## [0.1.0] — 2026-04-01

### Added
- Human-style README (trade-offs, limitations, future ideas).
- `CHANGELOG.md` (this file).
- INR formatting (`en-IN`), compact axis labels for charts.
- Simulated app “load” + dashboard skeleton; empty-state messaging.
- `ConfirmDialog` for deletes; inline form validation on transactions.
- Insight blurbs (`insightCopy.js`) + burn-rate warning (~75% of monthly income).
- Mobile floating “+” quick add for admins.
- `filterAndSort` naming; `tableControls` / `visibleTransactions` in context.

### Changed
- Renamed calculation helpers (`incomeTotal`, `expenseTotal`, `netBalance`, `topExpenseCategory`, etc.).
- Summary cards copy and layout tweaks (asymmetric spacing, net balance accent).

### Notes
- No backend; data remains localStorage-only. Role switcher is still UI-only.

---

## Earlier — initial scaffold

- Vite + React + Tailwind + Recharts + React Router.
- Dashboard, transactions table, insights, dark mode, CSV export, mock data seed.
