# ADR 0001: Build the Sprint 1 prototype in plain HTML/CSS/JS instead of React

**Status:** Accepted

**Context:**

PipelinePal's original plan was to build the Daily App in React. Going into Assignment 2.4's Task 5 ("move cards for real — do a small amount of real planning/setup work so there's something honest to move"), the repo had only planning documents in it (`docs/planning/`) and zero actual code. Setting up a React project first (tooling, build step, component structure) would have taken real time away from the actual goal of that task: producing genuine, verifiable progress on two Sprint 1 stories within a single session.

**Decision:**

Build the initial data model and board-creation flow in one plain `index.html` file with inline vanilla JavaScript — no framework, no build tools, no dependencies. This lets the app be opened directly in a browser and tested immediately, with zero setup.

**Consequences:**

- Positive: verifiable progress was possible within minutes — the data model could be tested in the browser console, and the "create board" button could be clicked and visually confirmed, satisfying Sprint 1's Definition of Done for those two stories the same day.
- Positive: zero environment setup means anyone (including a grader) can clone the repo and see it work with no install step at all.
- Negative: this is not the architecture the project is meant to end on. As more stories are built (adding cards, editing, multiple boards), inline JavaScript in one file will become hard to extend and will need real restructuring — likely into React, as originally planned, or an equivalent component-based structure.
- Negative: there is currently no separation between structure, styling, and logic, which is an accepted short-term trade, not a long-term pattern.

This decision is scoped to the prototype phase. It should be revisited once Sprint 2 (Auth) begins, since login/logout state and per-user data will be significantly harder to manage cleanly in a single inline script.
