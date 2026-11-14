# Grist Inventory Label Builder v1

Built as a **separate Grist Custom Widget**, informed by `grist_batch_actions_v3_5.zip` and the stable `dev` branch of `camara-h/label_printer_filler`.

Source printer: https://github.com/camara-h/label_printer_filler/tree/dev

## Scope of v1

This widget is the **database integration / label data preparation step**. It does **not** attempt to recreate the tightly calibrated CryoSTUCK Word label sheets inside the browser. You download printer-ready CSV and use the existing stable Streamlit program to build a `.docx` and its ECC200 Data Matrix images.

- Paste/scan many values, one per line, or paste a column from Excel.
- Search core `Inventory` fields and dynamically discovered subtype metadata using `ItemTypes`, `MetadataFields`.
- Exact ID matches outrank catalogue/lot/name matches; partial matches supported.
- Prompts for ambiguous matches, with the matched field displayed.
- When a scanner produces `IT-XXXX|extra text`, retries the ID before `|` if no full match exists.
- Enter number of copies per input, including intentional duplicates.
- Choose label content for circle and rectangle **separately for each ItemType**.
- Save per-type field choices in Grist Custom Widget settings (`setOption`), then apply/save them through Grist's widget options UI.
- `SetID` defaults to `ItemType`. The stable printer uses this to create per-SetID formatting tabs.
- `UniqueID` is the exact Inventory ItemID and is supplied to the Streamlit Data Matrix generator.
- Export UTF-8 CSV with these 10 names, in this order:
  `CircleLine1,CircleLine2MainInfo,CircleLine3,RectangleLine1MainInfo,RectangleLine2,RectangleLine3,RectangleLine4,RectangleLine5,SetID,UniqueID`.
- Read-only: creates no Inventory rows, no Events, no printing audit events.
- No new tables required. Consider a `LabelPrintJobs` table when you need a persistent print queue/history, not merely transient label creation.

## Installation

1. Host **`index.html`** as a static file on your current widget host, for example in a `label-builder/` folder on your GitHub Pages widget repository. The repository source is **not** automatically a hosted custom widget URL; deploy it through the same GitHub Pages workflow you use for other Grist widgets.
2. In Grist, add a new page with a **Custom Widget**, selecting the `Inventory` table for the data source. This widget queries the full document itself.
3. Set Custom URL to the HTTPS address of the hosted `label-builder/index.html`.
4. Grant **Full document access** because Grist requires it for reading across Inventory, ItemTypes, MetadataFields, and subtype tables. Although the widget requests full access, its code performs no Grist table writes. Only its field-mapping widget options can be changed.
5. Paste IDs or text, **Resolve items**, choose any ambiguous matches, adjust per-type fields in the right panel, and **Build label preview**.
6. **Download printer CSV** and upload it to your stable Streamlit label printer. Confirm the mapping and placement in Streamlit, then generate the actual Word document.

## Notes

- The widget works when Grist runs in your Mac's Docker container and is accessed from the institutional PC browser, just like the existing Batch Actions widget.
- The widget does not require any additional Docker ports or services. It still needs the Grist plugin API, loaded from `https://docs.getgrist.com/grist-plugin-api.js`.
- ItemTypes and metadata tables are discovered from Grist rather than hardcoded. A `Conjugations` lookup is supported when present, for human-readable conjugation names.
- No browser-native Data Matrix sheet printing is claimed. Content preview circles and rectangles are only schematic.
- The stable `dev` printer generates Data Matrix data with `UniqueID` first, then possibly other lid text separated by `|`. If you want all printed barcodes to scan to the **exact ItemID only**, that payload behavior needs a small adjustment to the Streamlit printer. This widget's resolver can recognize a leading ItemID in a `|`-separated scan payload.
- Date-like numeric columns are formatted `YYYY-MM-DD` where they resemble Grist Unix timestamps. Check any date fields in preview before printing.
- If a configured subtype reference link is missing or malformed, the widget can still resolve Inventory fields but may omit that type's subtype metadata. Confirm metadata mapping for each new ItemType.
- If you want a one-click `Generate DOCX` directly from Grist, the next stage should reuse the tested Python Word-template renderer through a protected companion service, rather than attempt a newly written browser label renderer with potentially different physical alignment.

## Testing

Tested with a mocked Grist API under a Chromium browser:
- Two Chemical rows sharing a catalogue number, requiring disambiguation.
- An Antibody row with subtype Target and Conjugation reference.
- Exact ItemID and `ItemID|extra` scanner payload.
- Mixed item types, label previews, duplicate rows, and CSV download.

**This is not yet tested against your live Grist document or physical label stock.** Try a small test batch before relying on it for printing.

## v1.1: Today field

The field mapping dropdown includes **Today (date of label generation)**. RectangleLine5 defaults to Today for new label profiles. The date is calculated when **Build label preview** is clicked, using the browser's local date, in MM/DD/YYYY format. Previously saved profiles using the old default Inventory.ItemID in RectangleLine5 are upgraded to Today. Other customized choices are retained.
