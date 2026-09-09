# Grist Location Visual Mapper v2

Adds two-way synchronization.

Previously:
- Location Inventory cursor -> map

Now:
- Location Inventory cursor -> map
- map tile click -> Grist cursor
- breadcrumb location click -> Grist cursor
- Up One Level -> Grist cursor when destination is a real location

Root is only a navigation state, not a real Location record, so it cannot become the Grist cursor. At Root, click a real location before using Location Manager actions.

Deploy over the current location-map widget and use `?v=2`.
