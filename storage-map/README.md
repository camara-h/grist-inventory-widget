# Unified Storage Map v1

Shows Location Inventory and active Inventory items in one map.

Required/recommended schema:
Location Inventory: LocationID, ParentLocationID, Type, Name, Description, Rows, Columns, Position
Inventory: ItemID, ItemName, ItemType, Status, LocationID (Reference -> Location Inventory), ParentItemID, Position

Behavior:
- current location shows child locations + active Inventory items
- both share the same Position slots
- Rows/Columns define a fixed grid
- otherwise 7 columns, auto-growing
- drag to empty = reposition
- drag onto another non-location object = swap
- drag Inventory item onto a child location or breadcrumb = move item into that location at first free position
- location hierarchy relocation remains in Location Manager

Search covers locations plus scalar Inventory fields and highlights ancestor branches.

Deploy as storage-map/index.html with Full document access.
