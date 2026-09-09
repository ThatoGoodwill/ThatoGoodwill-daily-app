# PipelinePal — Product Backlog

Rough list, not estimated yet, broken down from the epics.

## Boards & Cards

1. Figure out the actual Board → Column → Card data model, including what the default columns are (Applied, Interviewing, Offer, Rejected probably)
2. Creating a board should auto-populate it with those default columns
3. Add a card to a column — needs company, role, date applied, link to the posting
4. See all the cards in a column at once
5. Edit a card after it's created
6. Move a card from one column to another (still not sure if drag-and-drop or just buttons)
7. Delete or archive a card — haven't decided which

## Auth

8. Sign up with email/password
9. Login/logout
10. Make sure boards are actually scoped to the logged-in user, not global

## Reminders

11. Set some kind of "days in this stage" threshold per column
12. Flag a card somehow when it's been sitting past that threshold (not sure yet if that's just a badge in the UI or an actual email)

## Notes & Attachments

13. Free text notes on a card — interview prep, contact names, whatever
14. Attach a link to a card (resume version, job post)
15. Attach an actual file to a card (still need to figure out storage for this)

## Reporting

16. Total applications sent
17. Response rate — % of cards that moved past Applied
18. Average time spent in each stage
