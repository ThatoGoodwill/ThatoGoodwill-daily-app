# NOTES-ThatoGoodwill


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


## Assignment 2.4

## Question 1 — Rewrite Sprint 1 as real user stories

 1. Define the Board → Column → Card data model As Thato, building this thing solo, I want to lock in what a board/column/card actually looks like before I build anything on top of it, so I'm not rebuilding half of Sprint 1 later because I forgot a field.
 2. Create a new board with default columns As someone just starting to use PipelinePal, I want a new board to already have Applied, Interviewing, Offer, and Rejected columns set up, so I can start logging applications right away instead of configuring stuff first.
 3. Add a new card to a column As me right after I've submitted an application, I want to quickly log the company, role, date, and the job link, so I don't forget what I applied to or have to go dig up the posting again later.
 4. View all cards in a column As me checking in on my job search, I want to see everything sitting in a column at a glance, so I know how many things are actually at each stage without clicking into every single card.
 5. Edit an existing card's details As me, when something about an application changes, I want to go update that card, so the board actually reflects reality instead of going stale the second something changes.

 ## Question 2 — Acceptance criteria

 1. Data model — board/column/card schema is written down somewhere real (not just in my head); default columns (Applied, Interviewing, Offer, Rejected) are baked into the model; someone else could read it and understand the shape without asking me anything.
 2. Create board with defaults — new board shows up with exactly those 4 columns, right names, right order, zero cards in them, no extra setup step needed.
 3. Add a card — company + role required, date and link optional; card shows up in the right column instantly, no refresh needed; still there after I actually refresh the page.
 4. View cards in a column — every card in a column shows up with at least company + role visible; empty column shows an empty state, not a blank confusing screen.
 5. Edit a card — opening a card shows its current values already filled in; saving a change updates just that card and survives a refresh; hitting cancel doesn't touch the original data.

 ## Question 3 — INVEST check

  Picked #3, "Add a new card to a column," since basically everything else leans on it.

 . Independent — kind of fails, it needs #1 (data model) and #2 (a board that exists) first. Not a hidden    problem though, it's already an actual dependency in Asana.

 . Negotiable — passes, the form itself isn't locked in, just what it needs to do.

 . Valuable — obviously passes, this is the whole point of the app.

 . Estimable — passes, I know what this involves.

 . Small — passes, one day of work, not several things stapled together.

 . Testable — passes, the acceptance criteria above are actually checkable.

Fails Independent, but that's a real dependency not bad scoping — I'm not changing the story, just making sure I build it in order.

 ## Question 4 — Estimating alone, again

Reference story: "Create a new board with default columns" = 2, since I get it completely.

Define the data model — 3 (more deciding than typing)
Create board with defaults — 2 (the reference)
Add a new card — 3 (more fields/validation than the title makes it sound)
View cards in a column — 1 (it's just a list, genuinely small)
Edit a card — 3 (basically the same form as adding one, plus pre-filling and saving logic)

The one that surprised me was editing a card. Back in Assignment 2.2 it felt like a tiny tweak on top of "add a card." Writing it out as a full story made me realize it needs its own pre-fill and update logic — it's basically the same size as adding a card, not smaller.

NOTES.md Updates

1. What changed between backlog phrase and real story "Add a new card" looked like plain CRUD when it was just a phrase. Writing the "so that" made me actually picture the moment — right after I've applied, trying not to lose the posting link — and that's literally why the link field matters, not just an extra nice-to-have.

2. The retro, from the inside [Filling this in after the actual TrackFlow retro happens in class — can't write this one honestly beforehand.]

3. Estimating with real stories vs. rough backlog items Less confident on "edit a card" once I wrote the real story out — the vague phrase hid how much overlap it has with adding a card in the first place. Writing acceptance criteria is what actually exposed that, not the estimating step itself.

## ## Assignment 3.1

### Question 1 — Suggesting mode vs. comments vs. direct edits

**Direct edits** — for things that are objectively wrong and not worth a conversation. If I spot a typo in my own `product-backlog.md` when I port it into the Project Doc, or a column name written as "Interviewing" in one place and "Interview" in another, I just fix it. Nobody needs to weigh in on a spelling fix.

**Suggesting mode** — for changes to someone else's wording where they should get the final say. Example: if a teammate wrote PipelinePal's Scope section as "track job applications" and I think it should say "track job applications through defined pipeline stages," that's a real change in meaning. Suggesting mode lets them accept or reject it instead of me quietly overwriting their intent.

**Comments** — for raising a question or concern without touching the text at all. Example: on the Timeline section, leaving a comment like "is 4 weeks realistic if Auth isn't started yet?" — I'm not proposing specific replacement wording, I'm flagging something that needs a decision from whoever owns that section.

The rough rule I'm using: if it's objectively wrong, edit it. If I know what it should say but it's not my call, suggest it. If I don't know what it should say but something's off, comment.

### Question 2 — Permissions, deliberately

**Editor** — just me. I'm the only person actually building PipelinePal, so I'm the only one who needs to create, rename, move, or delete files. Handing Editor out more widely wouldn't help anyone and would mean someone could restructure the folder by accident.

**Commenter** — my instructor, and any trainee I'm pairing with for standups. They need to be able to leave real feedback on the Project Doc and flag problems in the tracker, but they have no reason to change the documents themselves. Commenter gets them everything they actually need without the risk.

**Viewer** — other cohorts or anyone who just wants to see what I'm building. They can read the structure and learn from it, but they can't alter or annotate anything.

The reason I'm not defaulting everyone to Editor: Editor includes the ability to delete files and change sharing settings. That's a genuinely destructive level of access to hand out just because it's convenient, and nobody on this list actually needs it.

### Question 3 — Sync or async?

**Belongs in a live Meet call:**
- **Goal-setting** — this is where disagreement surfaces and needs resolving in real time. A vague goal written async tends to stay vague because nobody wants to be the one to challenge it in a comment thread.
- **Blocking questions** — if something is genuinely blocking work, waiting for an async reply costs more than the meeting does. That's the whole justification for interrupting someone.

**Belongs in async Docs/Sheets/Calendar:**
- **Task assignment** — once the goal is agreed, who-does-what is better written down than spoken. A Sheet with an Owner column is unambiguous and still readable next week; a verbal assignment in a call isn't.
- **Status updates** — these are almost never worth a meeting. Updating a Status field or writing a line in a doc gives everyone the same information without spending anyone's time in sync.

The split I'm using: **sync for anything that needs disagreement resolved or a decision made; async for anything that just needs recording.** Status updates and task lists are information transfer, and meetings are a terrible way to transfer information — but they're a good way to surface the thing nobody wanted to write down.

## NOTES.md Updates

**1. What the "TidyUp" practice revealed**
Building the sample first made it clear how much faster the whole package goes if the Drive folder structure exists before anything else — I created the Doc first on TidyUp and then had to move it, which was avoidable. On the real PipelinePal folder I built the structure first, then created each file directly inside the right subfolder.

**2. The permission I almost got wrong**
When sharing the real Project Doc for feedback, my first instinct was to grant Editor, since that's the default that appears and it's one less thing to think about. Caught it and set Commenter instead — feedback doesn't require the ability to rewrite or delete the document, and Editor would also have let them change who else has access.

**3. Sync vs. async, in practice**
Mostly held up. The one thing I'd move from async to sync: I'd planned to just write the Scope section and let comments handle any disagreement, but the actual back-and-forth about what's in and out of scope for a 4-week build is exactly the kind of thing that takes three comment rounds and could have been two minutes of conversation.

## Links to real (non-sample) artifacts

- Drive folder: https://drive.google.com/drive/folders/16wvRDcxo5XhWGnQXNBZGdmsWo3SUgKU1?usp=drive_link
- Project Doc:https://docs.google.com/document/d/1Iy7-xcg6C5roBDxp5Yn6waYFeWYc3FBu0cKrQ9aiL0o/edit?usp=sharing
- Tracker Sheet: https://docs.google.com/spreadsheets/d/1AKK2GXhUNACXC6ZU-e180b4GNfWyY7h3tmrICV7fi88/edit?usp=sharing
- Kickoff Deck:https://docs.google.com/presentation/d/1BBNUO7uk9lRiA_41CF2vPyrKgba3XxrlhZECxGaWJ0I/edit?usp=sharing
- Calendar event: https://calendar.app.google/9cEVTqjVdCNDanicA

## ## Assignment 3.2

### Question 1 — Beyond the core four

My capstone repo needs a **Known Limitations** section, beyond Purpose/Setup/Usage/Contribution.

Right now `index.html` looks complete to someone skimming it — there's a button, it renders columns, it looks like a working app. What isn't obvious from reading the code is what it *doesn't* do yet: board state is not persisted anywhere (refreshing the page loses everything), the board name is hardcoded to `'My Job Search'` instead of being user-provided, and there's no way to add a card yet at all despite the file being called a "job application tracker." Leaving this section out would hurt someone by letting them believe the prototype is further along than it is — they'd try to refresh the page mid-demo, lose their board, and reasonably think something is broken when it's actually working exactly as far as it's been built.

### Question 2 — Comment audit

Being honest about what I actually found: **there are currently zero comments anywhere in `index.html`.** So there's no existing bad comment to quote and remove — the file simply hasn't been commented yet, since it was built fast to get real Sprint 1 verification (see Assignment 2.4).

Since the letter of the question assumes an existing bad comment, here's how I handled that gap honestly: I deliberately wrote one intentionally-bad, restating comment, then immediately corrected it, to demonstrate I can actually tell the difference — rather than fabricate a fake "audit history" that didn't happen.

**Bad comment (written, then removed), `index.html`, above the click handler:**
```js
// Create a board when the button is clicked
document.getElementById('createBoardBtn').addEventListener('click', function() {...
```
This restates exactly what the next line already says in plain code — the event name, the handler, and the function called are all already legible. It earns nothing.

**Missing "why" comment (added for real), `index.html`, above `const DEFAULT_COLUMNS`:**
```js
// Order matters here: columns render left-to-right in this exact sequence,
// matching the real progression of a job application (not alphabetical
// or arbitrary) — reordering this array changes the board's visual flow.
const DEFAULT_COLUMNS = ['Applied', 'Interviewing', 'Offer', 'Rejected'];
```
This one earns its place — nothing in the array literal itself tells a reader that the order is meaningful rather than incidental.

### Question 3 — What makes a decision ADR-worthy

The real decision: **building Sprint 1 as a single plain HTML file with inline vanilla JavaScript, instead of the React setup originally planned for PipelinePal.**

What made this ADR-worthy rather than a routine detail: it was a genuine fork with real consequences either way, not an obvious default. React was the original plan; switching to plain JS mid-sprint was a deliberate trade of long-term structure for immediate, verifiable progress on Task 5 of Assignment 2.4, when the repo had no code in it yet at all. A future contributor (or future me) opening this repo and seeing plain inline JavaScript when the README says "React" would be confused without an explanation — that confusion is exactly what an ADR prevents. A routine detail, like naming a variable `board` instead of `currentBoard`, has no real alternative worth weighing and wouldn't confuse anyone regardless of which way it went — that's the line.

## NOTES.md Updates

**1. What the sample exercise revealed**
Documenting the throwaway signup function first made the "why, not what" rule concrete before I had to apply it to my own code — the bcrypt-rounds comment and the verified-before-login comment in the sample are the exact pattern I reused on my own `DEFAULT_COLUMNS` comment.

**2. The comment I was wrong about**
Not applicable in the usual sense — there was no existing comment to be wrong about, since the file had none. The real surprise was realizing a completely uncommented file is its own finding, not a non-answer.

**3. The line between decision and detail**
After actually writing the ADR, I'd document *fewer* decisions than I originally assumed, not more. Writing it out made clear how much work a real ADR takes to do honestly (weighing a real alternative, naming real consequences) — that effort is only worth spending on choices that could plausibly have gone the other way and would confuse someone later if unexplained, which is a smaller set than I first thought.

## Links to real artifacts

- README: https://github.com/ThatoGoodwill/ThatoGoodwill-daily-app/blob/main/README.md
- ADR: https://github.com/ThatoGoodwill/ThatoGoodwill-daily-app/blob/main/docs/decisions/0001-plain-js-prototype.md
- Documented function:https://github.com/ThatoGoodwill/ThatoGoodwill-daily-app/blob/main/docs/createBoard-function-doc.md