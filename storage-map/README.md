# Unified Storage Map v2

New:
- Empty slots are clickable.
- Add Existing Item or Add Existing Location into a selected position.
- Search results dropdown for the main map search. Arrow keys + Enter supported.
- Existing-item search includes Inventory fields and detected subtype metadata.
- Existing-location search includes all scalar Location fields.
- Item relocation updates LocationID + Position and writes a Relocated event when compatible Event columns exist.
- Location relocation updates ParentLocationID + Position and writes a Location Relocated event when the Events table has a Location-compatible column.
- Invalid/colliding/out-of-range stored positions are highlighted red.

Expected writable columns:
Location Inventory: ParentLocationID, Position, Rows, Columns
Inventory: LocationID, Position, Status
Events: widget uses whichever of Item, Location, EventType, Notes actually exist.
