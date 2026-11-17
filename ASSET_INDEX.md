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
| `000001` | New Year — Fairytale invitation | Active | Product-specific source visual references; first registered group |

## 8. Index

### New Year — Fairytale invitation: source visual references

All entries below are source references uploaded by the owner on 17 November 2026. They are registered as `reference`, version `0.1.0`, status `draft`. They are for visual analysis and direction-setting only, not production-ready assets.

**Source:** [Pinterest board “Новогодние приглашения”](https://pin.it/3lML4kPnE) (the owner also supplied the board URL: https://ru.pinterest.com/pelzarkadiy/%D0%BD%D0%BE%D0%B2%D0%B3%D0%BE%D0%B4%D0%BD%D1%96%D0%B5-%D0%BF%D1%80%D0%B8%D0%B3%D0%BB%D0%B0%D1%88%D0%B5%D0%BD%D0%B8%D1%8F/). Individual Pinterest pin URLs and original creators have not been mapped to the uploaded files.

**Rights/usage for every entry:** Pinterest source; original creator, license, and reuse permission are not verified. Use as inspiration/reference for analysis only. Do not copy, publish, redistribute, or use the source image in production without identifying the original source and confirming permission or a suitable license. A draft reference registration is not a rights clearance.

| Asset ID | Title / visual content | Category and tags | Version / status | File |
|---|---|---|---|---|
| `EFM-000001AA` | Lit pine boughs framing a cool teal bokeh field | forest detail, foreground frame, warm lights, depth | 0.1.0 / draft | [0d8bc155ac08c20c74a3c0b3fea8947d.jpg](references/products/new-year/fairytale/0d8bc155ac08c20c74a3c0b3fea8947d.jpg) |
| `EFM-000001AB` | Glowing crystalline snowflake on dark blue snow | magic detail, snowflake, particles, blue night | 0.1.0 / draft | [17478bf22418b836cea183c469d9ab7a.jpg](references/products/new-year/fairytale/17478bf22418b836cea183c469d9ab7a.jpg) |
| `EFM-000001AC` | Ornamental fir-and-bauble border with open center | decorative frame, turquoise ornaments, gold, negative space | 0.1.0 / draft | [21737725ed98c2767d8248e982bd04fd.jpg](references/products/new-year/fairytale/21737725ed98c2767d8248e982bd04fd.jpg) |
| `EFM-000001AD` | Wide snowy fir canopy with warm lights and open depth | forest canopy, wide composition, snow, bokeh | 0.1.0 / draft | [3dde6022de3a714166b6e9ee3dbbcf75.jpg](references/products/new-year/fairytale/3dde6022de3a714166b6e9ee3dbbcf75.jpg) |
| `EFM-000001AE` | Close fir branch with warm amber bokeh | forest detail, shallow depth, warm highlights | 0.1.0 / draft | [538722df5f1dd57dc37199f4b8244687.jpg](references/products/new-year/fairytale/538722df5f1dd57dc37199f4b8244687.jpg) |
| `EFM-000001AF` | Dark teal negative space framed by a lit pine branch | forest foreground, dark teal, composition space | 0.1.0 / draft | [5f85eecbd989d2c58787123d72a5dbae.jpg](references/products/new-year/fairytale/5f85eecbd989d2c58787123d72a5dbae.jpg) |
| `EFM-000001AG` | Snowy branches framing a softly lit winter background | snowy forest, framing, warm bokeh, atmosphere | 0.1.0 / draft | [6615845dcacbe133d9a83d064b76c268.jpg](references/products/new-year/fairytale/6615845dcacbe133d9a83d064b76c268.jpg) |
| `EFM-000001AH` | Snowy forest path with warm lights receding into depth | forest path, perspective, snow, depth, light | 0.1.0 / draft | [6ec52a42a80678c3ee1838a56a700034.jpg](references/products/new-year/fairytale/6ec52a42a80678c3ee1838a56a700034.jpg) |
| `EFM-000001AI` | Vertical snowy path with glowing trees and soft focus | forest path, perspective, warm light, snow | 0.1.0 / draft | [77b9df82132a35652896c6fa33b8cc28.jpg](references/products/new-year/fairytale/77b9df82132a35652896c6fa33b8cc28.jpg) |
| `EFM-000001AJ` | Pale icy clearing framed by snow and delicate branches | clearing mood, negative space, snowflakes, soft light | 0.1.0 / draft | [a23459f295876986cf98c195d8d06b89.jpg](references/products/new-year/fairytale/a23459f295876986cf98c195d8d06b89.jpg) |
| `EFM-000001AK` | Deep navy snowflake field with golden light and snowy ground | magical night, snowflakes, gold, depth | 0.1.0 / draft | [b41fe77d774778bbf28a501a72d9ec9a.jpg](references/products/new-year/fairytale/b41fe77d774778bbf28a501a72d9ec9a.jpg) |
| `EFM-000001AL` | Teal-lit fir branches and pinecones against vivid cyan | fir detail, pinecones, warm sparks, teal | 0.1.0 / draft | [c0d2572c622de5fdcb023e811887c563.jpg](references/products/new-year/fairytale/c0d2572c622de5fdcb023e811887c563.jpg) |
| `EFM-000001AM` | Snowy park lane with lanterns and glowing trees | winter path, lanterns, perspective, snow | 0.1.0 / draft | [d14258739c1fb4b51570b291596987aa.jpg](references/products/new-year/fairytale/d14258739c1fb4b51570b291596987aa.jpg) |
| `EFM-000001AN` | Dense dark fir texture with scattered golden lights | forest texture, dense branches, warm lights | 0.1.0 / draft | [e7f8bf9b7cd60a539fb6df3dbadaeab2.jpg](references/products/new-year/fairytale/e7f8bf9b7cd60a539fb6df3dbadaeab2.jpg) |
| `EFM-000001AO` | Hanging gold stars over a deep blue glowing ground | magical decor, stars, gold, night, reflective ground | 0.1.0 / draft | [f726f284fefce4a977a3804c553247d2.jpg](references/products/new-year/fairytale/f726f284fefce4a977a3804c553247d2.jpg) |
| `EFM-000001AP` | Snow-covered fir branches, red berries, and lanterns | enchanted forest, berries, lanterns, snow, depth | 0.1.0 / draft | [fdd58d29d119c34c9e337d60b3bbcc46.jpg](references/products/new-year/fairytale/fdd58d29d119c34c9e337d60b3bbcc46.jpg) |

The agreed story scenario at `references/products/new-year/fairytale/NEW_YEAR_STORY_SCENARIO.md` remains a product-direction document, not a media asset.
