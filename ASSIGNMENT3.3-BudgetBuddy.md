# Assignment 3.3 — Part 2: Sample "BudgetBuddy" Scenario

## Task 1 — Channel rewrite

**Original bad message:**
 "hey so the budget sync feature is kind of broken and also can we talk about whether we're doing the export feature this sprint, no rush but let me know"

This actually bundles two unrelated things with two different urgencies — that's the core problem, not the wording.

**Slack message (the broken feature — needs quick visibility, not a decision):**
 Budget sync is broken — categories aren't updating after a sync. Looking into it now, will post what I find. Flagging in case anyone else touches that code today.

**Email (the export feature scope question — needs a real decision, not urgent):**
Subject: Export feature — in or out of this sprint?

 Quick scope check: are we still planning to ship CSV export this sprint, or pushing it to next? No urgency on my end, but I want to plan the rest of my week around the answer either way. Let me know when you get a chance — end of day tomorrow is totally fine.

**Why split them:** the bug is time-sensitive and needs eyes fast — that's what Slack is for. The scope question is a real decision that deserves a considered answer, not a reflexive one squeezed between other Slack messages — email (or an async doc comment) gives the other person room to actually think before replying, and it doesn't get buried in a channel's scrollback the way a Slack message does.

## Task 2 — Question rewrite

**Original bad question:**
 "the totals aren't adding up right, anyone know why?"

**Rebuilt using context / what I tried / exact behavior / specific ask:**

 **Context:** Working on `updateBudget()` — after syncing, the "Groceries" category total should reflect all transactions tagged Groceries this month.

**What I tried:** Added a `console.log` right before the total is written to the DB, and manually summed the transactions in that category by hand.

 **Exact behavior:** My manual sum comes to $342.10. The value being written to the DB is $284.50 — consistently $57.60 short, which happens to match exactly one transaction I can see in the list.

 **Specific ask:** Does `updateBudget()` skip transactions marked `pending`? That $57.60 transaction is still pending — if that's intentional, is there a reason totals include some pending transactions but not others, or is this a bug in the filter?

This gives the other person everything they need to actually answer without a back-and-forth just to understand the problem.

## Task 3 — PR feedback on `updateBudget()`

**The issue:** validates input, recalculates every category total, and writes to the DB — all in one 40-line block, no comments.

**Feedback comment:**

 This works, but right now `updateBudget()` is doing three genuinely separate jobs in one function: validating input, recalculating totals, and persisting to the DB. That makes it hard to test any one piece in isolation, and if the DB write ever needs to change (say, batching writes later), we'd have to touch validation and calculation logic to get there.

 Suggested direction: split into `validateBudgetInput()`, `recalculateCategoryTotals()`, and keep `updateBudget()` as a thin orchestrator that calls both and then writes. That'd also make it possible to unit test the recalculation logic without hitting the DB at all.

 Not blocking — happy to pair on the split if useful, but wanted to flag it before it grows another responsibility.

This is specific (names the actual three responsibilities), about the work (not "this is messy"), and gives a real direction, not just a complaint.

## Task 4 — Receiving the Task 3 feedback well

If I were the one who wrote `updateBudget()` and got that comment:

Yeah, that's fair — I mashed it all together to get sync working fast and didn't come back to split it out. Quick question before I refactor: should `recalculateCategoryTotals()` take the full transaction list and filter internally, or should the caller (`updateBudget()`) already have filtered by category before calling it? Want to make sure I'm not just moving the same tangle one function over.

 Thanks for catching this before it grew — I'll split it out today.

This models the actual pattern: listen first (acknowledge the point, don't get defensive), ask a real clarifying question instead of pretending it's fully clear, then say thanks — genuinely, not as a formality tacked on.