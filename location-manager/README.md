# Location Manager v6

Changes from v5:
- Supports Location Inventory `Active` toggle.
- New locations and auto-created shelves are created with `Active = true`.
- Relocation parent picker only shows active locations.
- Cannot create children under, relocate, or edit dimensions of an inactive location.
- Adds `INACTIVATE LOCATION`.
- Inactivation writes a `Location Inactivated` event when compatible Events columns exist.
- Safety guard: a location cannot be inactivated while any active child location or active Inventory item exists anywhere in its descendant hierarchy.
- Position occupancy checks use active child locations plus active Inventory items.

This keeps inactive locations as historical records while preventing active inventory from becoming hidden inside them.
