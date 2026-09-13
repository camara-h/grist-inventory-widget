# Unified Storage Map v5

Behavior change requested:
- Item -> Location tile now SWAPS their Position values.
- Location -> Location tile also swaps positions.
- Item -> Item continues to swap positions.
- Dragging to an empty slot continues to move within the current parent.
- Dragging onto breadcrumbs no longer relocates anything. Breadcrumbs are navigation-only.
- Drag-and-drop never moves an item inside another location.

To move an item into a child/other location:
1. Navigate into the destination location.
2. Click an empty slot.
3. Use Add Existing Item.

This makes cross-location relocation explicit and harder to do accidentally.
