# Targets & Rewards Portal

A wholesaler performance portal: monthly targets, progress dashboards, partial rewards and loyalty tiers, all driven by CSV uploads.

> **Status: in development.** This repo is the plan and the write-up; the interactive demo is being built next.
> **Demo preview:** https://julynard.github.io/targets-rewards-portal/ (becomes the live demo when it ships).

Part of [Julynard Tago-on's portfolio](https://julynardtago-on.netlify.app/#projects). Based on the wholesaler performance portal at CoreProc, my first major project, where I became the #2 contributor.
Client code is private, so this is a clean-room demo with fictional data. No client names or real data.

## What the demo will show

- [ ] **Admin**: upload a monthly targets CSV; re-uploading the same month overwrites it (as-of-date), history stays
- [ ] **Wholesaler dashboard**: volume and purchase-frequency progress bars, focus-brand goals, tier badge
- [ ] **Partial rewards** when a target is only partly reached
- [ ] Perpetual vs monthly benefits

Every key action will have an **"In production"** note explaining how the real system does it.

## How the production system works

The real system runs on Laravel. The demo simulates these behaviours in the browser so it can stay fast and always on.

- Laravel with an Inertia/Vue 3 front end for wholesalers and Laravel Nova for staff
- Invoice and receivables data ingested from the client's ERP feed, idempotent on business keys + as-of-date
- MySQL views as the reporting layer for the performance dashboards
- Sargable date ranges instead of `whereDate()`/`whereMonth()` so the invoice indexes are used
- Feature tests for policies, filters and widgets that caught authorization regressions found in UAT

## Planned stack

- Vue 3 + TypeScript + Vite
- Tailwind CSS v4
- Pinia (state saved in the browser, with a **Reset demo** button)
- Vitest for the domain logic, ESLint + Prettier + `vue-tsc` in CI
- GitHub Actions → GitHub Pages (free, always on)

## Roadmap

1. Project scaffold, CI (lint, type-check, test, build) and GitHub Pages deploy
2. Domain logic with Vitest tests
3. UI with seeded data, guided steps and "In production" notes
4. Screenshot/GIF in this README and the live demo link

## Author

**Julynard Tago-on**, Laravel / PHP full-stack engineer · [Portfolio](https://julynardtago-on.netlify.app) · [GitHub](https://github.com/Julynard) · [LinkedIn](https://www.linkedin.com/in/julynard-tago-on/)

## License

[MIT](LICENSE)
