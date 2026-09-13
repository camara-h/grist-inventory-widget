# Unified Storage Map v3

Changes from v2:
- If Location Inventory has an `Active` toggle, only Active locations are displayed.
- Main location search only returns Active locations.
- Add Existing Location only returns Active locations.
- Inventory remains limited to `Status = Active`.
- Item/location relocation refuses inactive destination locations.
- Search suggestions navigate only when clicked or selected with Enter.
- Clicking outside the search dropdown closes only the dropdown. Search text and map highlighting remain active.
- Focusing the search box again reopens the suggestions while the query remains.
- If the currently displayed location becomes inactive, the map falls back to an active ancestor or Root.

`Active` is treated as active for boolean true / 1 / "true" / "yes".
If there is no Active column, locations remain backward-compatible and are all considered active.
