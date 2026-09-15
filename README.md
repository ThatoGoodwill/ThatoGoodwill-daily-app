# PipelinePal

PipelinePal is a lightweight job-application tracker built on the classic Board → Column → Card model. It's for anyone actively job hunting who wants one clear view of where every application actually stands, instead of a scattered spreadsheet or a pile of email threads.

In this domain, a **Board** is your overall job search, a **Column** is a pipeline stage (Applied, Interviewing, Offer, Rejected), and a **Card** is a single job application — holding the company, role, and any notes from the process.

## Purpose

The goal is a fast, no-friction way to glance at your search and immediately know what needs a follow-up next. This repo is being built incrementally, sprint by sprint, as a solo Daily App project — it is not yet feature-complete.

## Setup

No build step, no dependencies, no install required.

1. Clone the repo:
   ```
   git clone https://github.com/ThatoGoodwill/ThatoGoodwill-daily-app.git
   ```
2. Open `index.html` directly in any modern browser (double-click it, or right-click → Open With → your browser).

That's it. There is currently no server, database, or package manager involved — everything runs client-side in one file.

## Usage

1. Open `index.html` in your browser.
2. Click **Create Board**. A board is created with four default columns: Applied, Interviewing, Offer, Rejected.
3. The columns render on the page in that order.

That's the full current functionality. Adding, viewing, and editing individual cards is planned for the remainder of Sprint 1 and is not yet implemented.

## Known Limitations

- **Nothing persists.** Refreshing the page loses the board entirely. There is no localStorage, database, or backend yet.
- **The board name is hardcoded** to `'My Job Search'` — there is no input for the user to name their own board yet.
- **Cards cannot be added yet.** The data model supports cards (see `docs/decisions/`), but the UI for adding one is still To Do.
- **No validation exists anywhere in the current code** — this is a prototype used to verify the data model and board creation, not a production-ready flow.

## Tech Stack

Plain HTML, CSS, and vanilla JavaScript — no framework, no build tools, no dependencies. See `docs/decisions/0001-plain-js-prototype.md` for why this was chosen over the originally-planned React setup.

## Roadmap

See `docs/planning/product-backlog.md` and `docs/planning/sprint-1-backlog.md` for the full backlog and current sprint scope. Sprint 1 is focused entirely on the Board & Cards epic; Auth, Notes & Attachments, Reminders, and Reporting are deferred to later sprints.

## Contribution Guide

This is currently a solo capstone project with no external contributors. If that changes:

- Branch from `main` using the pattern `feature/<short-description>` (e.g. `feature/add-card-form`).
- Commit messages should follow `type: short description` (e.g. `feat: add card creation form`, `docs: update README setup steps`).
- Open a PR into `main` rather than pushing directly, once there's more than one contributor — direct pushes are only acceptable while working solo.