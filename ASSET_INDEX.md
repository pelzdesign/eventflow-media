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
- Record the asset ID, title, material type, product/group, category, style/tags, source, rights/usage notes, and storage location.
- Keep original client deliverables and private project files out of this shared library unless reuse rights are explicitly confirmed.
- Prefer one canonical file. If an item belongs to several collections, reference it here with multiple tags instead of duplicating the file.
- Do not rename or reuse an existing asset ID for a different item.
- Moving a file between folders or storage providers does not change its ID or version. Update its storage location in the index instead.

## 3. Versioning rules

### Version format

Each logical asset uses a three-part version number:

`MAJOR.MINOR.PATCH`, for example `1.0.0`.

- A new material in preparation may start at `0.1.0` with status `draft`.
- The first approved release is normally `1.0.0`.
- Increase only the part that describes the scale of the change; reset the parts to its right to zero.

### When to increase a version

| Version part | Use when | Examples |
|---|---|---|
| MAJOR | The material's identity, composition, purpose, behavior, or compatibility changes substantially | Full redesign; changed template structure; animation rebuilt with a different sequence or meaning |
| MINOR | A meaningful improvement or addition is made without changing the material's core purpose | Additional editable elements; improved layout; new optional scene or content block |
| PATCH | A correction or technical refinement does not intentionally change the design or behavior | Typo fix; export correction; corrected color profile; fixed technical defect |

Use judgment: if a change makes the material meaningfully different for someone reusing it, prefer a new Asset ID rather than forcing it into a new version.

### Versions and approval

- Never overwrite an already registered version. Keep its files and change history.
- Every version has its own status: `draft`, `approved`, or `archived`.
- A new draft version does not automatically invalidate an earlier approved version. The earlier version remains approved until it is deliberately archived.
- Only approved versions may be selected for production or general reuse, and only within the rights/usage restrictions recorded for the asset.
- Archive a version when it should no longer be selected for new work, but retain its history and files where retention is permitted.
- A rejected or abandoned draft is retained as `archived` with a short explanation; its version number is not reused.
- A version change never changes the Asset ID.

## 4. File variants and derived materials

### File variants — same Asset ID and version

A file variant is another representation or export of the same approved design/content. It does not receive a separate Asset ID when the underlying material remains the same.

Examples:

- PNG, JPG, SVG, PDF, MP4 exports of the same source material.
- Different resolutions or compression levels.
- Print and web exports with no meaningful design change.
- Responsive sizes or aspect-ratio adaptations that preserve the same concept and remain variants of one reusable item.
- Source/editable file plus preview image.

Record each variant's label, format, dimensions or technical properties when relevant, and exact storage path. Do not encode the format or dimensions into the Asset ID.

### Derived materials — new Asset ID

Create a new Asset ID when an adaptation becomes a distinct reusable material in its own right, with a materially changed composition, purpose, content, or behavior.

- Register the new material under the appropriate product group.
- Add a `Derived from` reference to the source Asset ID.
- Keep the source asset and its history unchanged.
- Do not treat a derivative as a new version of the source if both materials may continue to be used independently.

### Example

Illustrative only:

- `EFM-000001AA`, version `1.0.0`: one approved invitation template.
- `EFM-000001AA`, version `1.0.0`, variants: editable source, web preview PNG, print PDF.
- `EFM-000001AA`, version `1.1.0`: refined typography and spacing, same template identity.
- `EFM-000001AB`: a separately designed invitation derived from the first template; its record points to `EFM-000001AA`.

## 5. Index structure and fields

Keep one asset record per Asset ID. Under that record, maintain a version history; each version may contain several file variants.

### Asset-level fields

| Field | Description |
|---|---|
| Asset ID | Permanent unique identifier |
| Title | Human-readable material name |
| Material type | `reference` or `asset` |
| Product/group | Product or template associated with the numeric group; use `shared` for group `000000` |
| Category | Functional category, such as background, typography, layout, transition |
| Style/tags | One or more searchable descriptors |
| Derived from | Source Asset ID, when this is a derivative |
| Source | Origin of the material or source URL |
| Rights/usage | License, permission, attribution, and restrictions |

### Version-level fields

| Field | Description |
|---|---|
| Version | `MAJOR.MINOR.PATCH` |
| Date | Date this version was registered |
| Status | `draft`, `approved`, or `archived` |
| Change summary | What changed from the previous version |
| File variants | Variant label, format, technical properties and exact storage path |

The index must make it clear which version is approved for reuse. Do not rely on folder names or file timestamps as a substitute for the index.

## 6. Statuses

Statuses apply to a specific version, not to the Asset ID as a whole.

- `draft` — being prepared; not approved for production or general reuse.
- `approved` — reviewed and available for the uses allowed by its rights/usage notes.
- `archived` — retained for history, not recommended for new work.

## 7. Product group registry

Assign each numeric group to one product or template here before registering its first material. Keep assignments permanent.

| Group number | Product/template | State | Notes |
|---|---|---|---|
| `000000` | Shared library | Reserved | Materials not belonging to one specific product/template |

No product/template groups have been assigned yet.

## 8. Index

No materials have been registered yet.
