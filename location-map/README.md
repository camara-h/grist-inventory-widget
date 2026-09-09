# Location Map v3

Requires `Location Inventory.Position` as a numeric/integer data column.

Uses parent's existing `Rows` and `Columns` when present. Otherwise uses 7 columns and grows rows automatically.

Drag child to:
- empty slot = move
- occupied slot = swap

IMPORTANT page linking:
- Map must be the linking source.
- Set Location Inventory table -> Select By -> Location Map.
- Set Location Manager -> Select By -> Location Map.
- Do NOT set Location Map -> Select By -> Location Inventory.

Deploy with ?v=3.
