# Grist Inventory Widget v2

Changes from the first MVP:

- Fixes Events.Item by resolving the selected Inventory record to its raw Grist row ID before creating the event.
- Adds a Relocate workflow.
- Relocate:
  - loads existing locations from the Grist location table,
  - lets the user search the full location label/path,
  - updates Inventory.LocationID,
  - creates a Relocated event,
  - records FromLocation and ToLocation.

## Expected table IDs

- Inventory
- Events
- Location_Inventory

The widget also tries LocationInventory and Locations as fallback table IDs.

## Required columns

Inventory:
- ItemID or AutoItemID
- ItemName
- ItemType
- Status
- LocationID (Reference -> location table)

Events:
- Item (Reference -> Inventory)
- EventType
- FromLocation (Reference -> location table)
- ToLocation (Reference -> location table)
- Notes

Location_Inventory:
- LocationID
- Description
- Name (optional)
- Type (optional)

## Update your GitHub Pages widget

Replace the existing index.html in your GitHub repository with this version and commit it.

GitHub Pages should redeploy automatically. Refresh/reload the custom widget in Grist after deployment.

Keep the widget Access Level set to Full document access.
