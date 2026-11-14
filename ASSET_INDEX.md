# Asset index

This file is the central register of reusable media in EventFlow.

## 1. Asset ID format

Every registered reference or reusable asset receives a permanent ID in this format:

`EFM-000001AA`

The ID consists of three parts:

- `EFM` — EventFlow Media namespace.
- `000001` — product group number. The group belongs to one specific product or template.
- `AA` — material sequence within that product group.

The numeric part has a minimum width of six digits. It may grow beyond six digits when needed; it must never be truncated or reset.

The letter suffix uses uppercase Latin letters and starts at `AA`. It advances in this order: `AA` ... `AZ`, `BA` ... `ZZ`, then `AAA`, `AAB`, and so on. The suffix may grow beyond three letters if ever required.

### Product group assignment

- Assign one unique numeric group number to each independent product or specific template.
- All materials belonging to that product/template use its group number and receive their own letter suffix.
- A separate template receives a separate group number, even when it belongs to the same product direction.
- A product that has no separate templates may use one group number for the product itself.
- Group numbers are assigned centrally and are never reused, including after a product or template is archived or discontinued.
- Do not encode product names, categories, styles, file formats, or storage paths into the ID. Those properties may change and belong in the index metadata.

### Shared materials

The numeric group `000000` is reserved for materials that are genuinely shared across products and do not belong to one specific product/template.

Examples:

- `EFM-000000AA` — first shared material (illustrative only).
- `EFM-000000AB` — next shared material (illustrative only).

Do not put a product-specific material in the shared group merely because it may be useful elsewhere. If a shared item later becomes product-specific, retain its original ID and update its metadata; do not issue a replacement ID.

### Illustrative examples

The following examples explain the pattern only. They do not assign or reserve group numbers for actual products or templates.

| Product/template group | Example IDs |
|---|---|
| Wedding template 1 | `EFM-000001AA`, `EFM-000001AB` |
| Wedding template 2 | `EFM-000002AA`, `EFM-000002AB` |
| Certificate template 1 | `EFM-000003AA`, `EFM-000003AB` |
| Shared library | `EFM-000000AA`, `EFM-000000AB` |

## 2. Registration rules

- Give every registered reference or reusable asset a stable ID that does not depend on its folder path or storage provider.
- One ID identifies one logical material. Revisions and format exports of the same material retain the same ID and are tracked as versions or file variants. A genuinely distinct material receives a new suffix.
- Record the asset ID, title, material type, product/group, category, style/tags, format, version, status, source, rights/usage notes, and storage location.
- Keep original client deliverables and private project files out of this shared library unless reuse rights are explicitly confirmed.
- Prefer one canonical file. If an item belongs to several collections, reference it here with multiple tags instead of duplicating the file.
- Do not rename or reuse an existing asset ID for a different item.
- Moving a file between folders or storage providers does not change its ID. Update its storage location in the index instead.

## 3. Index fields

| Field | Description |
|---|---|
| Asset ID | Permanent unique identifier |
| Title | Human-readable material name |
| Material type | `reference` or `asset` |
| Product/group | Product or template associated with the numeric group; use `shared` for group `000000` |
| Category | Functional category, such as background, typography, layout, transition |
| Style/tags | One or more searchable descriptors |
| Format | File format, such as JPG, PNG, SVG, MP4, HTML |
| Version | Current material version, for example `1.0` |
| Status | `draft`, `approved`, or `archived` |
| Source | Origin of the material or source URL |
| Rights/usage | License, permission, attribution, and restrictions |
| Storage location | Current repository path or external storage reference |

## 4. Statuses

- `draft` — being prepared; not approved for production or general reuse.
- `approved` — reviewed and available for the uses allowed by its rights/usage notes.
- `archived` — retained for history, not recommended for new work.

## 5. Product group registry

Assign each numeric group to one product or template here before registering its first material. Keep assignments permanent.

| Group number | Product/template | State | Notes |
|---|---|---|---|
| `000000` | Shared library | Reserved | Materials not belonging to one specific product/template |

No product/template groups have been assigned yet.

## 6. Index

No materials have been registered yet.
