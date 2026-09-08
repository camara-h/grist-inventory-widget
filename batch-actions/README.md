# Grist Batch Actions v3.1

Metadata retrieval fix for the current database schema.

Fixes:
- Supports subtype tables whose Inventory reference column is named `ItemID` instead of `Item`.
- Correctly resolves `MetadataFields.ItemType` when it is a Grist Reference.
- Reads every configured metadata field for the resolved ItemType.
- Matches metadata columns despite harmless case/space/underscore differences.
- Keeps the existing batch actions unchanged.

After deploying, use a cache-busting widget URL such as `?v=3.1`.
