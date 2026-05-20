# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install       # install dependencies (required before first run)
npm run dev       # start dev server at http://localhost:5173
npm run build     # production build
npm run lint      # run ESLint
npm run preview   # preview production build
```

## Architecture

This is a single-component React app (Vite + React 19). All logic lives in `src/App.jsx` — there are no sub-components, routing, or external state management libraries.

**Known intentional issues (part of a course exercise):**
- `amount` is stored as a string in state, causing `totalIncome` and `totalExpenses` to concatenate instead of add — the summary totals are wrong.
- Transaction #4 ("Freelance Work") is typed as `"expense"` but categorized as `"salary"` — inconsistent seed data.
- The UI is intentionally minimal and unstyled beyond basics.
- A `.delete-btn` CSS class exists in `App.css` but no delete functionality is wired up yet.

**Data shape** — each transaction object:
```js
{ id, description, amount, type: "income"|"expense", category, date }
```

Categories are a fixed array: `["food", "housing", "utilities", "transport", "entertainment", "salary", "other"]`.

State is entirely in-memory (no persistence); refreshing the page resets to the hardcoded seed transactions.
