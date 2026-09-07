# Grist Batch Actions v2

Adds `REAGENTS / SAMPLES USED TODAY`.

After resolving scanned/pasted identifiers, the widget builds one combined ELN-friendly table containing:
- ItemID
- ItemName
- ItemType
- Status
- Location
- the union of configured subtype metadata fields across the selected items

Fields that do not apply to an item are left blank.

Actions:
- COPY TABLE: tab-separated output for direct paste into ELN or Excel
- DOWNLOAD CSV

This export action is read-only. It does not alter status and does not create Events.

Deploy by replacing your existing batch-actions/index.html and use ?v=2 to force refresh.
