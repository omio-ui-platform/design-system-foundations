# 06 Elevation

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-7

Elevation helps people understand which surfaces sit above other surfaces. Dotty elevation is intentionally simple: use surface color for the plane, an elevation style for the shadow, and layout rules for stacking order.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Elevation Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1033-2 | Purpose, model, and practical levels. |
| Elevation Docs / 02 Levels | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1033-43 | Flat, surface, sticky, and floating levels. |
| Elevation Docs / 03 Tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1033-111 | Primitive ingredients, semantic elevation tokens, and effect styles. |
| Elevation Docs / 04 Applying elevation | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1033-194 | Choosing elevation by surface relationship. |
| Elevation Docs / 05 Layering guidance | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1033-231 | Surface color, dark mode, and layer order. |
| Elevation Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1033-293 | Usage selection rules, flat-vs-layered guidance, and output format. |

## Token Architecture

```text
elevation primitives -> elevation semantic tokens -> Figma effect styles
```

- Primitives store reusable shadow ingredients.
- Semantic elevation tokens describe the layer job.
- Effect styles package semantic values into designer-applied styles.

## Current Styles

| Style | Use |
| --- | --- |
| No elevation | Default page sections and in-flow surfaces separated by spacing, background, or border. |
| `elevation.surface` | Stable raised cards, panels, and containers. |
| `elevation.stickyTop` | Top bars fixed above scrolling content. |
| `elevation.stickyBottom` | Bottom bars or persistent actions fixed to the bottom edge. |
| `elevation.floating` | Menus, popovers, dialogs, overlays, and temporary layered surfaces. |

## Core Rules

- Start flat with background, border, radius, and spacing.
- Add elevation only when a surface sits above another layer, scrolls over content, or opens temporarily above the page.
- Use `elevation.surface` for stable raised containers.
- Use `elevation.surface` for first-level product cards or panels when they need foreground separation from the page background; nested and quiet surfaces can stay flat with background and border.
- Use sticky elevation only for edge-fixed surfaces.
- Use `elevation.floating` for temporary layered surfaces.
- Do not elevate every card by default; choose elevation by layer role.
- Do not replace first-level product surface hierarchy with border-only outlines when `elevation.surface` is the clearer layer cue.
- Product UI first-level surfaces should not look like documentation table/card shells. Use `color.background.surface`, radius, spacing, and elevation together when the surface needs to sit forward.
- Nested facts inside a first-level product card should usually stay flat. Use spacing, rows, or subtle dividers before adding nested shadows or many nested borders.
- Do not invent stronger dark-mode shadows; validate the full surface with color, border, shadow visibility, and contrast.

## Product Surface Decision

| Surface role | Preferred treatment | Avoid |
| --- | --- | --- |
| First-level card or panel on page background | `color.background.surface`, `radius.medium`, product padding, and `elevation.surface` when separation is needed. | Border-only docs shells when the card should sit forward. |
| Nested facts or rows inside a card | Flat surface, spacing, rows, or subtle dividers. | Every fact becoming a mini card with its own outline. |
| Tables and dense comparison areas | Flat table anatomy with borders/dividers. | Elevating each row or cell. |
| Sticky or floating layers | Sticky or floating elevation by layer behavior. | Applying sticky/floating shadows to normal in-flow cards. |

## AI And Engineering Contract

AI and engineering should output:

- Chosen style, such as `elevation.surface`.
- Reason based on layer relationship.
- Paired surface color, usually `color.background.surface`.
- Layer behavior: stable, sticky, or floating.
- Whether the surface is first-level, nested, sticky, or temporary.
- Whether border or elevation is carrying the hierarchy, especially for first-level product panels.
- Whether nested facts are grouped simply instead of over-framed.
- Caveat for dark mode, scroll behavior, or stacking order.
