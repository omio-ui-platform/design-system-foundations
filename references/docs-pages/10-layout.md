# 10 Layout

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1129-2

Layout defines how content sits on the screen: page structure, responsive frames, columns, gutters, and broad composition. Spacing still handles relationships inside and between elements.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Layout Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1129-3 | Layout purpose, mental model, source grid, and scope. |
| Layout Docs / 02 Responsive frames | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1129-100 | Mobile/desktop references and responsive layout checks. |
| Layout Docs / 03 Grid and columns | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1129-195 | Grid specs, column examples, and when to use grid vs auto layout. |
| Layout Docs / 04 Page spacing | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1129-286 | Relationship between layout and spacing. |
| Layout Docs / 05 Applying layout | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1129-353 | Applying layout from primary task, pattern, and spacing. |
| Layout Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1129-411 | Usage contract, hierarchy/padding/gap rules, output format, and prompt template. |

## Mental Model

```text
Viewport -> Content area -> Grid/alignment -> Spacing -> Component
```

- Layout decides where things live.
- Spacing decides how close related things are.
- Documented source specs define repeated behavior inside the layout.

## Reference Tokens

| Context | Reference | Columns | Margin | Gutter |
| --- | ---: | ---: | ---: | ---: |
| Mobile | `layout.viewport.mobile` = 375px | 4 | 16px | 16px |
| Desktop | `layout.viewport.desktop` = 1440px | 12 | 146px | 16px |

These are documentation references, not the complete product breakpoint system.

## Core Rules

- Start with content hierarchy: primary task, supporting information, and secondary actions.
- Choose viewport, content width, grid, and columns before stretching content full width.
- Use grid for page regions, forms next to summaries, repeated card lists, and broad desktop alignment.
- Use auto layout for component internals, small stacks, rows, inline metadata, and content-driven groups.
- Use `space.*` tokens for gaps, insets, and section rhythm.
- Do not invent arbitrary margins, offsets, widths, or page nudges.
- Do not apply one repeated gap/padding to every layer when relationships differ.
- Visual layer order should match reading hierarchy. Sticky or fixed bars can use sticky elevation, but they should not overpower the primary content unless they are actively overlaying it.
- Decide whether the layout is marketing/editorial or operational/product before choosing scale and density. Marketing can be broader and more expressive; operational flows should be calmer, denser, and scan-first.
- Operational product layouts should keep the primary task close to supporting information, avoid oversized hero spacing, and avoid turning every content block into a large docs-style section.
- Tables and comparison grids must stay readable. If columns become cramped, convert the same content into stacked cards or rows before body text wraps into narrow fragments.
- Side summaries should support the primary task without forcing the main content into narrow columns. If the main table or comparison needs width, stack or move the side summary.
- Behavior outside the layout foundation needs a documented source spec.

## AI And Engineering Contract

AI and engineering should output:

- Pattern: single column, split view, side panel, card grid, dashboard, form flow, or another named structure.
- Reason based on user task and content hierarchy.
- Responsive behavior: stack, columns, content order, or density changes.
- Grid and spacing choices: reference frame, content width, columns, margin/gutter, and spacing tokens.
- Layering choices for sticky, side-panel, first-level, and nested regions.
- Experience type: marketing/editorial or operational/product, with the hierarchy and density choice explained.
- Table or comparison behavior: keep as table, stack into cards/rows, or reorder content for mobile readability.
- Constraints and caveats for source specs, real content, localization, accessibility, or engineering rules.
