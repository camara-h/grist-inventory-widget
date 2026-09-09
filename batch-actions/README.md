# Grist Batch Actions v3.3

Adds reference-aware Location export.

Inventory.LocationID is a Reference -> Location Inventory, so Grist stores a numeric row id underneath.

v3.3 exports:
- LocationID = the human-facing location ID, e.g. BX000164
- Location = the full Description/path

It also lets the resolver search the human-visible location ID and path.

All v3.2 behavior remains unchanged.

Deploy over the current batch-actions widget and use `?v=3.3`.
