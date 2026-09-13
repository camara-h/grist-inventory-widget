# Batch Actions v3.4

Fix for mixed ItemType metadata export ("Reagents / Samples Used Today").

Changes:
- Subtype -> Inventory link detection now scans every subtype-table column and
  chooses the column whose values actually resolve to Inventory row IDs.
  It no longer relies only on Item / ItemName / ItemID naming.
- Supports mixed selections across Cell, Chemical, Antibody, Primer,
  Biological Sample, and other configured ItemTypes.
- MetadataFields configuration is still preferred for labels.
- If subtype columns exist but are missing from MetadataFields, they are
  included as a fallback instead of silently dropping the entire ItemType.
- Export still builds the union of metadata columns across all selected items.
  Rows only populate fields relevant to their own ItemType.
- Export status now reports how many selected items had subtype metadata found.

Example behavior:
Chemical rows can populate Catalogue/Lot/Storage/Vendor while Antibody rows
populate Clone/Host/Conjugation/etc. in the same exported table, with blanks
where a field does not apply.
