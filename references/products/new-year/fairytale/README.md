# New Year — Fairytale

References for fairytale and storybook-inspired New Year products.

## Agreed product direction

The New Year product uses an interactive fairytale sequence, not a generic winter invitation. See [NEW_YEAR_STORY_SCENARIO.md](./NEW_YEAR_STORY_SCENARIO.md) for the restored, previously agreed scene sequence, states, RSVP behavior, and architecture boundaries.

Use this folder for source visual references for the fairytale forest, clearing, ribboned envelope, magical invitation sheet, transitions, and lighting/effects. Keep source URLs and usage restrictions with each registered reference.

Do not treat the scenario brief itself as an approved production asset. Register actual visual reference files and reusable assets in the central `ASSET_INDEX.md`.

## Approved storyboard

The approved visual storyboard for the first New Year fairytale template is documented in [NEW_YEAR_FAIRYTALE_STORYBOARD.md](./NEW_YEAR_FAIRYTALE_STORYBOARD.md). It supersedes earlier visual details where the owner approved later changes. Responsive design is mandatory for every generated media item; see the storyboard's adaptation requirements.

## Visual decomposition

The production breakdown of scenes into reusable backgrounds, layers, objects, effects, interface elements, and responsive variants is documented in [NEW_YEAR_FAIRYTALE_DECOMPOSITION.md](./NEW_YEAR_FAIRYTALE_DECOMPOSITION.md). This is a technical production plan, not approval of generated assets.

## Free SVG/CSS prototype

The first original responsive forest prototype is in [prototypes/forest-test.html](./prototypes/forest-test.html). It now composes four independently animated SVG planes (far forest, middle forest, clearing, foreground framing), with separate desktop and mobile variants in [prototypes/layers/](./prototypes/layers/). Earlier single-canvas drafts are retained for comparison. It is a draft technical proof of concept, not approved final artwork.

## Envelope motion prototype

A standalone local-browser test for the generated transparent envelope is available at [prototypes/envelope-motion-test.html](./prototypes/envelope-motion-test.html). It loads the forest background and envelope through local file pickers, then previews CSS-based levitation without AI video generation or external animation libraries. This is an experimental interaction prototype, not production integration.
