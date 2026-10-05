# Fieldnotes Study Planner

An offline-first study planner for first-year engineering students that turns courses, fixed class times, and deadlines into a realistic weekly study plan.

## Run & Operate

- The `artifacts/study-planner` workflow runs the app preview.
- `pnpm --filter @workspace/study-planner run typecheck` — check the app
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- App: React, TypeScript, Vite
- Persistence: versioned browser localStorage; no app API or database is required
- Offline install support: web app manifest and service worker

## Where things live

- `artifacts/study-planner/src/App.tsx` — screens, local data model, planner, and reminders
- `artifacts/study-planner/src/index.css` — app theme and responsive styling
- `artifacts/study-planner/public/` — install manifest, icons, and service worker

## Architecture decisions

- This MVP intentionally has no accounts, AI, social features, grade tracking, or themes. Defer these until real students want them.
- Student data stays in the browser on the current device; backups are user-managed.
- Study reminders are local notifications and can only fire reliably while the planner is open.

## Product

- Manage courses with difficulty ratings, recurring lectures/labs/tutorials, and weighted test or assignment deadlines.
- Generate a weekly study plan around fixed classes, prioritizing difficult courses with urgent deadlines, with up to two blocks per course per day and a rest buffer.
- Track today's completed blocks, carry missed work forward, and use local browser reminders.

## User preferences

Keep the first release focused on the study-planning MVP. Add later features only when student feedback supports them.

## Gotchas

- Clearing browser storage deletes the planner data; export a backup before changing browsers or clearing site data.
- Browser notifications require permission and browser support; do not promise background delivery while the app is closed.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
