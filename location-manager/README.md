# Location Manager v5

Adds:
- position validation against parent Rows × Columns
- occupied-position validation using BOTH child locations and active Inventory items
- relocation position validation
- Edit Selected Location Rows/Columns
- live impact preview
- blocks dimension changes that cannot contain all direct contents
- blocks unsafe dimension changes unless Save + Repack is chosen
- Save + Repack renumbers direct child locations and active Inventory items sequentially
- attempts Events logging when compatible Event columns exist

Rack still uses Rows/Columns and does not auto-create shelves.
