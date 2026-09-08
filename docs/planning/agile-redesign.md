# Agile Redesign of "TaskBoard Pro" — Applied to PipelinePal

## Problems with the original Waterfall-style brief

1. **Frozen requirements after Phase 1, no changes permitted once design begins** — violates "Welcome changing requirements, even late in development" and "Responding to change over following a plan." Locks in a full feature set before anyone has used the product.
2. **No demos until the entire build phase (Phases 1–3, ~9 weeks) is complete** — violates "Deliver working software frequently" and "Working software is the primary measure of progress." A wrong assumption from Week 1 could go undetected for two months.
3. **Full QA pass across all features simultaneously, at the very end** — violates continuous attention to technical excellence and testing throughout the lifecycle rather than as a single terminal phase.
4. **Launch to all users at once** — the opposite of early, continuous, incremental delivery; no chance to catch a bad assumption before it reaches everyone.

## Iterative redesign — first two iterations for PipelinePal

**Iteration 1 (~1 week):**
Build the smallest working slice: one hardcoded board, a single column, and the ability to add a Card with just a company name and role, and see it listed. No auth, no stages, no styling. Demo at the end of the iteration — the question being answered is whether the core Board/Column/Card object model even fits a job search before anything else gets built on top of it.

**Iteration 2 (~1 week):**
Add the real pipeline stages as columns (Wishlist → Applied → Interviewing → Offer/Rejected) and let a Card move between them. Still no auth or notifications. Demo again — the question being answered is whether moving a card between stages matches how applications actually get tracked day to day, catching any needed model changes early rather than after Auth, Reminders, and Reporting are already built on top of an assumption that turned out wrong.

Each iteration produces something that runs and gets looked at, so the plan adjusts based on what's true rather than what was guessed in Week 1 — the direct opposite of the original brief's 9-week silent build.
