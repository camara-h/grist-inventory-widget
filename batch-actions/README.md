# Grist Batch Inventory Actions v1

Accepts scanner input, Excel paste, or manually typed values.

Resolver searches:
- all scalar Inventory columns
- configured subtype metadata fields from ItemTypes + MetadataFields

It prefers active records and ranks exact ItemID/barcode, catalog/lot, and ItemName matches.
Ambiguous matches require explicit user selection.

Actions:
- Mark Used
- Discard
- Aliquot / Dilute

Aliquot creates child Inventory items, links ParentItemID, copies configured subtype metadata, creates lifecycle Events, and optionally marks the parent Consumed.

Deploy as `batch-actions/index.html` in the existing GitHub Pages repo.
Use a URL like `...?v=1`.
Set Full document access.
