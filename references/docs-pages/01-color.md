# 01 Color

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-2

Color creates the shared visual language for Omio products. It defines brand identity, hierarchy, meaning, feedback, and theming through role-based names that designers, engineers, and AI agents can all understand.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Color Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=323-1104 | Foundation purpose and source palette overview. |
| Color Docs / 02 Roles | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=335-1980 | Brand, neutral, information, success, warning, error, inverse, and accent/feature roles. |
| Color Docs / 03 Tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=344-1622 | Token layers, selection order, semantic mapping, surface bridge, naming, boundaries, and opacity modifiers. |
| Color Docs / 04 Applying color tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=386-3506 | How to choose semantic color tokens by property and intent in product UI. |
| Color Docs / 05 Adding a color | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=401-4580 | Workflow for flat accents, gradients, and rare universal color roles. |
| Color Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=736-4996 | Usage guidance for color token selection, hierarchy, mode/product behavior, guardrails, output format, and opacity rules. |

## Token Architecture

```text
01 Color / Primitives
  -> 01 Color / Theme + 01 Color / Product
  -> 01 Color / Semantic
```

Canonical public model:

```text
color.palette.* -> theme.* -> product.* -> color.*
```

- Primitives store raw palette values and common values.
- Theme owns Light and Dark appearance routing.
- Product owns product identity mapping such as B2C and B2B.
- Semantic `color.*` tokens are the current usable layer for product UI, docs, generated UI, and code references.
- Opacity is separate from color and exposes only approved modifiers: `opacity.8`, `opacity.12`, `opacity.16`, `opacity.24`, `opacity.40`, and `opacity.80`.

## Current Collections

| Collection | Modes | Count | Usage |
| --- | --- | ---: | --- |
| `01 Color / Primitives` | Value | 144 | Raw palette, common, and dark-palette values. Do not use directly in product UI. |
| `01 Color / Theme` | Light, Dark | 75 | Appearance mapping between light and dark primitives. |
| `01 Color / Product` | B2C, B2B | 75 | Product identity mapping. |
| `01 Color / Semantic` | Value | 38 | Usable foundation color tokens for UI, docs, and generated designs. |
| `01 Color / Opacity` | Value | 6 | Designer-assigned opacity modifiers for focus/tint/scrim and overlay layers. |

## Core Rules

- Use semantic `color.*` tokens first for product UI.
- Use Product, Theme, and Primitive tokens only when maintaining the system or explaining resolution.
- Do not use raw hex in product UI when a token exists.
- Dotty does not use pure `#000000`; `color.common.black` is intentionally `#161A24`.
- Neutral is intentionally a two-family role: navy blue carries readable content, default icons, hierarchy, and key values; grey carries backgrounds, dividers, disabled states, and quiet structure.
- Use `color.background.surface` for cards, panels, forms, modals, and clean foreground containers.
- Use `color.background.subtle` for nested/grouped surfaces and quieter sections.
- Use `color.background.strong` only for small high-emphasis navy surfaces and pair it with inverse text/icon tokens.
- Do not create `color.status.*` tokens. Status meaning lives in property-first roles such as `color.text.error`, `color.icon.information`, `color.background.success`, and `color.border.warning`.
- Do not use coral as error. Error uses the red role.
- Branded Omio or Dotty outputs should include a restrained brand anchor when the product context needs identity, but coral is not generic decoration, label, pretitle, status, or selected-state styling.
- Use coral for Omio brand identity, approved primary brand emphasis, promotional emphasis, small active indicators, and one consistent Omio-branded prototype action when final action styling is unresolved.
- When a foundation-only prototype needs an Omio-branded primary action, use the brand role consistently and state final action styling as a source-spec dependency. Do not mix navy and coral as competing primary actions.
- Do not use status backgrounds to invent selected row, card, or option states. Use status color only when the status itself is the meaning.
- If a prototype needs a selected row, card, or option before the component source spec exists, keep the cue neutral and structural, then report the selected-state dependency outside the UI.
- Do not tokenize gradients yet. Accent/feature gradients are documented visual references unless explicitly approved as token work.
- Do not add arbitrary opacity. If opacity is needed, apply an approved opacity token as a separate layer.

## Applying Color

Read token names as:

```text
color / property / intent
```

Examples:

- `color.text.default`: primary readable text.
- `color.background.surface`: cards, panels, forms, and clean foreground containers.
- `color.icon.default`: normal supporting icons.
- `color.border.subtle`: quiet structure and low-emphasis dividers.
- `color.background.information`: helpful information surfaces.
- `color.text.error`: failed, invalid, destructive, or serious feedback.
- `color.border.warning`: caution boundaries before a blocking error.

## AI And Engineering Contract

AI and engineering should:

- Choose existing semantic tokens before proposing new values.
- Explain token choice by property and intent.
- State product and theme behavior when relevant.
- Keep Semantic mode-free; Light/Dark belongs in Theme and product differences belong in Product.
- Do not infer hover, focus, selected, loading, disabled, CTA, or other interaction-state styling from color foundations alone; state the unresolved source-spec dependency.
- If a prototype must show a selected item before a component/source spec exists, do not borrow warning, error, or success backgrounds. State the selected-state dependency.
- If a prototype must show selected state, use a simple neutral structural cue and label it as prototype-only in delivery notes.
- Do not use coral as the default selected-row/card wash or as the default pretitle color. Coral only appears when the content has a brand, promotional, active-indicator, or approved primary-action job.
- If a prototype must show an Omio-branded primary action before a source spec exists, use one consistent brand-role emphasis and state the unresolved action styling dependency.
- Ask for approval before adding a new color, ramp, gradient, accent, semantic role, or raw hex.

For deeper color details, read `../appendices/Color Foundation Appendix.md` and `../data/color-variables.figma.json`.
