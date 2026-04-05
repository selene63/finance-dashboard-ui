# Finance dashboard (student / portfolio piece)

**Current version:** `0.1.0` · **See:** [CHANGELOG.md](./CHANGELOG.md) for what changed.

A small **React + Vite + Tailwind** UI for tracking money in and out. It’s **frontend-only**: data lives in **localStorage**, roles are **fake** (viewer vs admin), and nothing hits a server. That’s intentional — the goal was to practice layout, state, and UX without pretending to be a bank.

## Why it’s built this way

- **Context API** for global state — enough for one screen tree, no need for Redux here. Trade-off: everything re-renders when transactions change; at this scale that’s fine.
- **Plain functions** in `utils/` for math (totals, trends). Easier to read than clever abstractions, and you can reason about bugs in the console.
- **INR** via `Intl` so formatting looks right in India without hand-rolling commas.
- **Simulated “loading”** (~400ms on first paint) so the dashboard doesn’t flash empty charts. It’s a cheap UX trick, not real async.

## What works

- Overview with summary cards, balance line chart, category donut (expenses).
- Transaction table: search, filter, sort, CSV export, **inline validation** on the form, **confirm dialog** instead of `window.confirm` for deletes.
- Insights with **short explanations** (rule-based copy, not ML) — e.g. many small expenses vs one big one.
- **Burn-rate warning** when this month’s spending crosses ~75% of logged income — rough signal, not financial advice.
- **Floating “+” on small screens** for quick adds (admin) — thumb reach, not a second product.
- Dark mode + role switcher persisted in localStorage.

## What we deliberately kept simple

- **No backend / auth** — “admin” is a dropdown, not security.
- **Calendar months only** — comparisons don’t follow “pay cycles” or custom budgets.
- **No undo**, no multi-currency, no attachments — scope creep is the enemy of a student project.
- Insights are **heuristics** (counts + amounts). They can be wrong in edge cases; that’s noted in the UI copy.

## Known limitations (left on purpose)

1. **Deleting or clearing storage** is the only way to “reset” — there’s no “restore demo data” button (we could add one; didn’t).
2. **Very large numbers** rely on the browser’s `Intl` implementation — good enough for demo; not audited for accounting.

## Future ideas (if this grew up)

- Real API + auth, or at least export/import JSON backup.
- Proper pay-period budgets instead of calendar months.
- Virtualized table if transactions hit thousands.

## Run it

```bash
cd dashboard
npm install
npm run dev
```

Node 18+ is fine. Build: `npm run build`, preview: `npm run preview`.

## Folder map (short)

- `src/context/` — provider + `useFinance` hook  
- `src/utils/` — calculations, filters, CSV, formatting, insight blurbs  
- `src/components/` — layout, charts, table, modals  
- `src/` — pages and `App.jsx`

---

MIT — use freely for learning and portfolios.
