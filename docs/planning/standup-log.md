# PipelinePal — Standup Log (dry run)

## Day 1

Did: sorted out the Board → Column → Card model and the four default columns. Got the repo scaffolded around it.
Next: build the "create a board" flow so it actually shows up with those columns already there.
Blocker: kept going back and forth on whether columns should be a fixed list or something the user can rename. Going with fixed for now, punting "custom columns" to later.

## Day 2

Did: got board creation working, default columns show up right away. Tested it a couple times to make sure.
Next: add-a-card flow — company, role, date, link.
Blocker: not really blocked, just need to decide if the job link field is required or optional before I lock in the validation.

## Day 3

Did: finished add-a-card including basic validation, started on editing a card (reused most of the same form).
Next: finish editing, then move on to viewing all the cards in a column.
Blocker: officially giving up on drag-and-drop for now — just doing "move to next stage" buttons instead. The drag library decision was eating time it didn't need to. Moving that to Sprint 2.
