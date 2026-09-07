# Grist Location Visual Mapper v1

A read-only visual navigator for the Location Inventory hierarchy.

## What it does
- Starts at root locations such as Rooms.
- Displays direct child locations as a responsive grid of clickable cards.
- Clicking a card navigates down one level.
- Breadcrumbs let you jump back to any ancestor.
- Root and Up One Level buttons are included.
- If the widget is linked to a Location Inventory widget using Select By, selecting a location in Grist opens that location in the mapper.
- If a `Position` column exists, children are ordered by numeric Position. Otherwise they are ordered by Type, Name, then LocationID.

## Expected Location table
Required:
- LocationID
- ParentLocationID (Reference -> Location table)
- Type

Recommended:
- Name
- Description

Optional:
- Position

## Grist setup

Add a Custom Widget to your Location Browser page.
Use the URL for this widget.
It only needs read-table access, but Grist may offer broader access choices.

Optionally set `Select By` to your Location Inventory table/card widget. That makes the map jump to whatever location you select in Grist.

## Deployment

Place:
`location-map/index.html`

in your existing GitHub Pages repository.

Then use something like:
`https://YOURNAME.github.io/YOUR-REPO/location-map/?v=1`

## Future extension

A later version can render true fixed-position matrices for freezers/racks if you add fields such as:
- Position
- Rows
- Columns

It can then support empty slots and eventually drag-and-drop placement/swap behavior.
