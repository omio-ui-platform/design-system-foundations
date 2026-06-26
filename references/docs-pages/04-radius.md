# 04 Radius

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-5

Radius defines how sharp or rounded Dotty surfaces and controls feel. Use radius tokens to create consistent shape, hierarchy, and product polish without choosing raw pixel values.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Radius Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=941-2 | Purpose, model, and at-a-glance roles. |
| Radius Docs / 02 Scale | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=941-102 | Dimension primitives and usable radius tokens. |
| Radius Docs / 03 Tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=941-236 | Token anatomy, resolution, and usage rules. |
| Radius Docs / 04 Applying radius | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=941-288 | Applying radius by shape role. |
| Radius Docs / 05 Usage guidance | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=941-329 | Choosing radius, nested corners, product behavior, and component shape caveats. |
| Radius Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=941-408 | Usage decision rules, surface shape rules, output format, and guardrails. |

## Token Architecture

```text
dimension.scale.* -> radius.*
```

- Dimension primitives store the raw values.
- Semantic radius tokens describe corner intent.
- Product UI and docs should use `radius.*`, not raw dimension values.

## Semantic Scale

| Token | Value | Use |
| --- | ---: | --- |
| `radius.none` | 0px | Square, flush, joined, table/grid, or edge-to-edge cases. |
| `radius.small` | 4px | Compact controls, precise corners, restrained UI. |
| `radius.medium` | 8px | Default cards, panels, and common containers. |
| `radius.large` | 16px | Prominent surfaces and larger panels. |
| `radius.xlarge` | 24px | Expressive large surfaces. |
| `radius.pill` | 9999px | Fully rounded buttons, chips, toggles, and badges. |

## Core Rules

- Use `radius.medium` as the normal default for cards, panels, and containers.
- Use `radius.large` or `radius.xlarge` only when surface scale needs a softer group.
- Use `radius.none` only as a deliberate exception for square, flush, joined, table/grid, or edge-to-edge media cases.
- Use `radius.small` for tight utility surfaces and compact controls.
- Use `radius.pill` only when a source spec explicitly calls for a fully rounded shape.
- Same-level sibling cards, panels, and sections should share the same radius token unless a source spec explains the difference.
- Do not mix top-level and lower-level radius choices just to add visual variety. Radius changes should communicate scale, nesting, or a documented product/component role.
- A first-level product card and its same-level siblings should not switch between rounded and sharper corners because of content type alone. Use hierarchy, nesting, or source spec to justify any radius change.
- Nested surfaces should not be rounder than their parent. If a child surface is visibly inset inside a padded parent, step down one token where possible: parent `radius.large` -> child `radius.medium`; parent `radius.medium` -> child `radius.small`.
- If a child surface is flush to the parent edge, align with the parent corner logic instead of creating a competing rounded corner inside the same edge.
- If the inner content is only related facts, metadata, rows, or comparisons, prefer spacing, rows, dividers, or subtle background before creating multiple nested rounded cards.
- Do not infer action, chip, or pill shape from foundation radius alone; use a documented source spec for those shape decisions.

## AI And Engineering Contract

AI and engineering should output:

- Chosen token, such as `radius.medium`.
- Reason based on surface role and density.
- Same-level consistency check when multiple cards, panels, or sections appear together.
- Hierarchy or source-spec reason for any radius change between sibling product surfaces.
- Parent radius and child radius when a nested surface is used, including whether the child is inset or flush.
- Reason why nested facts need their own rounded surface instead of rows, dividers, or spacing.
- Resolved primitive when useful, such as `dimension.scale.8`.
- Caveat when radius would imply button, chip, selected-card, or component behavior that the foundation does not define.
- Caveat when a source spec maps a product-specific shape to another radius token.
