# Batch Actions v3.5

ELN export change:
- Selected records are grouped by ItemType.
- One separate ELN table is rendered per detected ItemType.
- Each table contains:
  - ItemID
  - ItemName
  - ItemType
  - Status
  - LocationID
  - full Location path
  - only the metadata columns present for that ItemType
- Each ItemType table has its own Copy Table button.
- Each ItemType table has its own Download CSV button.
- CSV names are type-specific, e.g.:
  antibodies_used_2026-09-13.csv
  chemicals_used_2026-09-13.csv
  cells_used_2026-09-13.csv

The subtype-link detection improvements from v3.4 are retained.
