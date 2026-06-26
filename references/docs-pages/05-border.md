# 05 Border

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-6

Border width controls visible stroke weight across the system. It helps separate surfaces, define boundaries, and create stronger emphasis when color alone is not enough.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Border Width Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=966-2 | Purpose, architecture, and relationship to color/radius. |
| Border Width Docs / 02 Scale | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=966-50 | Primitive values and semantic border-width tokens. |
| Border Width Docs / 03 Tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=966-131 | Resolution model and naming guidance. |
| Border Width Docs / 04 Applying border width | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=966-196 | Applying width with border color and radius. |
| Border Width Docs / 05 Usage guidance | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=966-252 | Choosing the lightest effective boundary. |
| Border Width Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=966-317 | Usage rules, separation rules, examples, and response shape. |

## Token Architecture

```text
dimension.scale.* -> borderWidth.*
```

- Dimension primitives store raw numeric values.
- Semantic border-width tokens expose the usable stroke weights.
- A visible border should normally pair width with `color.border.*` and often `radius.*`.

## Semantic Scale

| Token | Value | Use |
| --- | ---: | --- |
| `borderWidth.none` | 0px | No visible stroke or boundary removal. |
| `borderWidth.default` | 1px | Default outline, divider, separator, field, or card boundary. |
| `borderWidth.strong` | 2px | Clearer boundary, selected structure, or emphasis. |
| `borderWidth.heavy` | 4px | Heavy rail, status strip, navigation indicator, or strong visual anchor. |

## Core Rules

- Start with `borderWidth.default` for most outlines and dividers.
- Use `borderWidth.none` when spacing, background, or elevation already separates content.
- Use `borderWidth.strong` only when the boundary needs stronger priority.
- Use `borderWidth.heavy` sparingly for rails, active indicators, or strong anchors.
- Do not make first-level product cards border-only by default. Use borders mainly for nested surfaces, tables, quiet separation, selected structure, or explicit boundaries.
- Do not use borders to turn every small fact into its own card. Related facts can live in one surface with rows, dividers, or spacing.
- A small active indicator can use a strong/heavy edge, but that pattern does not define selected card, row, button, or tab component behavior.
- Do not rely on stroke width alone to communicate status or importance.
- Pair visible borders with `color.border.*`; include `radius.*` when the border wraps a rounded surface.

## AI And Engineering Contract

AI and engineering should output:

- Chosen border-width token.
- Reason: structure, emphasis, selected structure, or visual anchor.
- Paired tokens such as `color.border.subtle` and `radius.medium`.
- Whether the border is supporting a nested/quiet surface or whether elevation should carry first-level surface hierarchy instead.
- Whether the border is clarifying structure or creating unnecessary docs-like boxes inside product UI.
- Whether any active/selected cue is a documented source spec or only a prototype dependency.
- Caveat if using a heavy stroke too broadly or relying on width alone for meaning.
