# Function Documentation: `createBoard`

**File:** `index.html`
**Type:** Function (no API exists yet in this project — documenting the core function instead, per Task 8's fallback option)

## Description

Creates a new board object with a given name and a fixed set of default columns (Applied, Interviewing, Offer, Rejected), each initialized as an empty array ready to hold cards.

## Signature

```js
function createBoard(name)
```

## Inputs

| Parameter | Type | Required | Description |
|---|---|---|---|
| `name` | string | Yes | The display name for the board. Currently always called with the hardcoded value `'My Job Search'` from the click handler — see Known Limitations in the README. |

## Output

Returns a plain object:

```js
{
  name: "My Job Search",
  columns: {
    "Applied": [],
    "Interviewing": [],
    "Offer": [],
    "Rejected": []
  }
}
```

- `name` — echoes back the input string exactly, unmodified.
- `columns` — an object keyed by each entry in `DEFAULT_COLUMNS`, with every value initialized as an empty array. The key order matches `DEFAULT_COLUMNS`'s order, which is meaningful (see the comment above that constant) — it reflects real pipeline progression, not an arbitrary list.

## Error Cases

**None currently handled.** This is a known gap, not an oversight being hidden:

- Calling `createBoard()` with no argument returns a board with `name: undefined` — there is no validation or default value.
- Calling `createBoard(123)` (a non-string) is accepted silently; `name` will simply hold `123`.

This function is a prototype-stage building block, not a validated public API. Adding input validation is expected before this becomes part of a real "create board" story with its own acceptance criteria.
