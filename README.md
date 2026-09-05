# Grist Inventory Actions MVP

This widget is linked to the Inventory table.

It displays the selected item and provides one action:
MARK USED

On click it:
1. Updates Inventory.Status to Used.
2. Adds a Used event to Events.

Required Grist table IDs:
- Inventory
- Events

Required columns:
Inventory: ItemID or AutoItemID, ItemName, ItemType, Status, LocationID
Events: Item (Reference -> Inventory), EventType, Notes

## GitHub Pages
1. Create a public repository, e.g. grist-inventory-widget
2. Upload index.html to the repository root
3. Settings -> Pages
4. Deploy from a branch
5. Select main and /(root)
6. Save
7. Copy the published URL into the Grist Custom URL field
8. Set Access Level to Full document access
9. Link the widget to Inventory using Select By

Test on a copy of the Grist document first.
