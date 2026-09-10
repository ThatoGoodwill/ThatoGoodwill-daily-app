# NOTES-yourusername

## Assignment 2.1

### Question 1 — Scrum or Kanban, for two different contexts

**Daily App: Kanban.**
My Daily App is solo, worked in short irregular sessions, with scope that will change as I learn the domain. Scrum's core mechanism is the sprint: a fixed-length box of committed work, planned and reviewed on a cadence, with defined roles (Scrum Master, Product Owner) and ceremonies (standup, retro, sprint planning). None of that machinery earns its cost here — I can't run a "daily standup" with myself, and locking a two-week sprint backlog fights directly against scope that I *expect* to evolve as I build. Kanban's continuous-flow model fits better: I pull the next card when I have capacity (a 45-minute session between classes, not a sprint), I can add/reorder/kill backlog items the moment I learn something new without breaking a sprint commitment, and a WIP limit keeps me from having five half-finished features open at once, which is the real risk in solo work with unpredictable time.

**TrackFlow: Scrum — and yes, the answer differs.**
TrackFlow is a shared, instructor-led build with the whole cohort. The moment more than one person is coordinating dependent work, the ceremonies Scrum bakes in stop being overhead and start being the thing that prevents chaos: a shared sprint goal keeps everyone building toward the same target, standups surface blockers before they become someone else's blocker, and a retro gives the group a structured moment to adjust process rather than everyone privately being annoyed. This lines up with the Principles' emphasis on daily business/developer collaboration and face-to-face communication — those principles matter most exactly when there's more than one "face" involved. Solo work doesn't need the coordination overhead; group work does.

### Question 2 — A real trade-off

**Value:** *Working software over comprehensive documentation.*

**The real decision:** How much planning documentation do I write in `docs/planning/` before I have a single working card moving between columns? I could keep expanding `epics.md` and writing detailed specs for every feature (auth, notifications, collaboration, reporting) before touching code — or I could write the bare minimum needed to start, and let the docs catch up once something actually runs.

**Where I'll lean:** Toward working software. I'll keep `epics.md` to one line per epic — just enough to show the shape of the whole project — and get a single Board → Column → Card slice actually working before I write anything more detailed than that. The Manifesto is explicit that working software is the primary measure of progress, not the completeness of the plan; a thin app that runs teaches me more about what my epics actually need than another hour spent speculatively documenting a notifications feature I haven't built yet. I'll still write things down — a plan with zero documentation is just as risky as over-planning — but the documentation stays a lightweight map, not the destination.

### Question 3 — Critique and redesign

**Problems with the "TaskBoard Pro" Waterfall brief:**

1. **Requirements frozen for two weeks with no changes permitted once design begins.** This directly violates "Welcome changing requirements, even late in development" and the value of "Responding to change over following a plan." Locking the full feature set (labels, permissions, notifications, reporting) before anyone has used the product for even a day guarantees the spec is wrong in places nobody will discover until Phase 3 or later.

2. **No demos until the entire 5-week build phase is complete.** This violates "Deliver working software frequently" and "Working software is the primary measure of progress." Nine weeks pass (Phases 1–3) before a single stakeholder sees anything real. If the team misunderstood a requirement in week 1, that misunderstanding compounds silently for two months before anyone notices.

3. **Full QA testing pass across all features simultaneously, at the very end.** This violates "Continuous attention to technical excellence" and the shift toward continuous testing throughout the lifecycle. Bugs and integration problems discovered in Week 10 are far more expensive to fix than the same bugs caught the week the feature was built — and there's a real risk of finding a fundamental issue too late to fix before the Week 12 deadline.

4. **(Bonus) Launch to all users at once, in Week 12.** A single big-bang release with no earlier feedback loop is the opposite of "early and continuous delivery of valuable software" — there's no way to catch a bad assumption before it hits every user simultaneously.

**Agile redesign — first two iterations, applied to PipelinePal (my Daily App):**

- **Iteration 1 (roughly 1 week):** Build the smallest possible working slice — a single hardcoded "Applications" board with one column and the ability to add a Card (Company name + Role) and see it in a list. No stages, no auth, no styling. Demo it to myself/instructor at the end: does the core object model (Board → Column → Card) even feel right for a job search?
- **Iteration 2 (roughly 1 week):** Add multiple columns representing real pipeline stages (Wishlist → Applied → Interviewing → Offer/Rejected) and the ability to move a Card between columns. Still no auth, no notifications. Demo again: does moving a card between stages match how I actually track applications, or does the model need adjusting before I build anything else on top of it?

Each iteration ships something that runs and gets looked at, so the plan can adjust based on what's actually true rather than what was assumed in Week 1.

## NOTES.md Updates

**1. Naming it made it real.**
Yes — picking "PipelinePal," a job-application tracker, immediately made the abstract Board/Column/Card model concrete in a way "generic board" never did. A "Card" isn't an abstract unit of work anymore; it's a specific job application with a company, a role, a status, and a date I applied. That forced me to think about fields and stages a generic board never would have surfaced (e.g., "Rejected" isn't just "Done," it needs to be distinguishable from "Offer"), which changes what the epics and even the first iteration need to include.

**2. Where the sample brief's problems actually bite.**
The "no demos until build is complete" problem would hurt the most in practice. Frozen requirements and end-of-project testing are both bad, but a nine-week silent build phase means the team could be building confidently on a wrong assumption made in Week 1 and have zero opportunity to catch it until Week 9 — by which point the cost of fixing it (in time, morale, and rework) is at its absolute highest. The other problems compound *within* a phase; this one compounds silently *across* the majority of the project timeline.

## skipping without noticing.

Habit to fix it: before I close my laptop each day, I have to write down the one thing I'm doing next, pulled from the backlog, not from memory. If I can't name it, I didn't actually do the PO part of my job that day, I just coded.

Question 2 — Definition of Ready / Definition of Done (Boards & Cards epic)

Ready means:

it's a real user story, not just a title
there are at least 2 things I can actually test to know it works
anything it depends on already exists (e.g. don't try to build "add a note to a card" before the card itself exists)
I've already made the annoying decisions — like what the default columns are — instead of leaving them for "while I'm coding it"
it's small enough that I could plausibly finish it in one day

Done means:

it's pushed to main and nothing obviously breaks
I actually clicked through it myself, not just "looks right in the code"
it survives a refresh — not just working in whatever's in memory
no red errors in the console
if it turned out different than what I planned, I go back and fix the doc so it's not lying
Question 3 — The artifact most at risk

Sprint Backlog, easily. On a solo project with a daily cadence it's really tempting to just do whatever feels urgent that morning and call it "the sprint" instead of actually pulling specific ready items out of the backlog first. The cost is that grooming and doing blur together — there's no moment where I actually commit to something, so scope just kind of drifts all day. It also means the DoR stuff from Q2 doesn't really get enforced, because nothing is checked against it before I start.

NOTES.md Updates

1. Has the neglected role changed? No, still Product Owner. Writing the DoR/DoD out actually made this more obvious — it's really easy to just skip the "is this ready" check and start typing.

2. What did the DoR actually filter out? Yeah, a few things. Moving cards between columns didn't make Sprint 1 because I hadn't decided drag-and-drop vs buttons yet, and I originally assumed that'd be in. Everything outside Boards & Cards got cut too, since I only wrote a DoR for that one epic — some of those (like basic sign-up) feel simple enough that I expected them in, but by my own rule they're not ready yet.

## Assignment 2.3
Question 1 — Choosing a view

Day to day, Board is going to be my main view. PipelinePal is fundamentally a pipeline (Applied → Interviewing → Offer → Rejected), and honestly the whole point of the app is "what's stuck where" — a Kanban-style board matches that mental model almost exactly, so it's the least friction for checking status at a glance.

List is more useful when I need to actually work, not just look — filtering down to "Sprint 1, not done" or sorting by due date is way easier in list view than scanning a board. I'd reach for it during actual daily work sessions, not for a status check.

Timeline doesn't matter much day to day since this is a solo, daily-cadence project without hard external deadlines, but it'd be useful if I ever need to see how epics overlap or whether Sprint 2 work is going to run into a deadline I've committed to (e.g., if I promise a demo date).

Question 2 — Custom fields, deliberately
Priority (High / Medium / Low) — supports the filter "what should I work on next if I only have an hour," so I'm not just going in due-date order or whatever's on top.
Story Points (1 / 2 / 3 / 5) — supports sizing Sprint 1 realistically instead of eyeballing it, and later lets me check "did I actually finish what I estimated."
Type (Feature / Bug / Chore) — supports separating "am I actually building the product" from "am I just doing repo maintenance," so I can sanity check I'm not spending a whole day on chores.

I'm deliberately not adding more than this — anything I can't name a real filter for isn't going in.

Question 3 — Tag or field?

Tag example: needs-design — something that could apply to a task in any epic (a card UI decision, a reporting chart layout, whatever), and isn't really a property of the task itself so much as a flag I want to filter across the whole project regardless of section.

Custom field example: Priority — it only makes sense within this one project, and every single task should have exactly one value for it, which is what a field is for.

What would go wrong if I swapped them: If Priority were a tag, nothing would stop me from leaving it blank on half the tasks or accidentally tagging something both High and Low, since tags aren't structured or exclusive — the filter "show me everything High priority" gets unreliable. If needs-design were a custom field, I'd be forcing every task in the project to have an opinion on a dropdown that mostly doesn't apply to it, just clutter for the 90% of tasks that have nothing to do with design.

NOTES.md Updates

1. What the QuickNotes exercise revealed Building the sample backlog first made it obvious how fast an Asana project turns into visual noise if you add fields "because you can." I went into my own project already knowing to cut anything from Question 2 that I couldn't name a real filter for.

2. Where Sprint 1 and reality disagreed Moving sprint-1-backlog.md into Asana as actual tasks with subtasks made "edit an existing card's details" look bigger than it did as one line in markdown — it's really at least three separate pieces of work (form, validation, save). I kept it as one Sprint 1 task for now but noted it as the first thing I'd re-size if Sprint 1 runs long.

3. The field vs. tag call I almost got wrong I almost made Type (Feature/Bug/Chore) a tag instead of a field, since it felt similar to needs-design. But every task needs exactly one Type and I do want to filter/report on it directly ("how much of my time is chores"), which is exactly the custom field case, not the tag case.


