# Grist Batch Actions v3.2

Fixes the current Grist schema and adds partial search.

## Metadata retrieval fix

In the current Chemicals table:

- `ItemName` is the actual Reference -> Inventory column.
- `ItemID` is a formula (`$ItemName.ItemID`).

Previous widget versions were looking for the relationship in `Item` or `ItemID`.

v3.2 detects common Inventory-reference columns including:
- Item
- ItemName
- InventoryItem
- Inventory
- ItemID

It only accepts a candidate when its values resolve to Grist row references.

This allows Chemical metadata such as Catalogue, Lot, Storage, ExpirationDate,
Vendor, URL, Concentration, and Solvent to be associated with the correct Inventory item.

## Search improvement

Resolver now supports:
- exact ItemID / barcode matching
- exact catalogue and lot matching
- exact ItemName matching
- partial text matching

Examples:
- `IT-HC000277` -> exact item
- `M22425` -> catalogue match
- `2591163` -> lot match
- `mito` -> MitoTracker records
- `green` -> MitoTracker Green FM

Exact machine identifiers rank much higher than partial text results.
When several partial matches exist, the user must choose the intended physical item.

## Deployment

Replace the current batch-actions/index.html and use a cache-busting URL such as:

`?v=3.2`

Do not convert the Grist Reference columns to text.
