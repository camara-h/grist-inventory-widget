# Location Visual Mapper v4

Adds hierarchy-aware search highlighting.

## Search
Searches partial text across:
- LocationID
- Name
- Description
- Type

Examples:
- `BX0164`
- `Nawaz`
- `Liq.N2`
- `Shelf 4`

## Highlighting
- exact matching location = green highlight
- ancestor/branch leading to one or more matches = yellow highlight
- multiple matches can highlight multiple branches simultaneously
- each highlighted branch shows how many matches exist below it

At Root, if matches exist under Room 1, Room 1 is highlighted.
After entering Room 1, matching Freezer(s) are highlighted.
Continue clicking down until the exact location is highlighted.

Press Enter in search to jump directly to the first match.

All v3 functionality remains:
- map as linking source
- positional grid
- Rows/Columns support
- default 7-column layout
- drag to empty = move
- drag to occupied = swap

Deploy over location-map and use `?v=4`.
