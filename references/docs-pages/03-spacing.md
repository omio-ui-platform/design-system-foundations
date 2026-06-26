# 03 Spacing

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-4

Spacing creates rhythm, hierarchy, and relationships across Dotty interfaces. Use spacing tokens to describe the job of the space, not a one-off pixel value.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Spacing Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=888-794 | Purpose, architecture, and core gap/padding/margin model. |
| Spacing Docs / 02 Scale | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=888-1051 | Dimension primitives, semantic spacing scale, and visual rhythm. |
| Spacing Docs / 03 Tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=888-1121 | Token layers, naming, and engineering notes. |
| Spacing Docs / 04 Applying spacing | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=888-1175 | Applying spacing by relationship and example usage. |
| Spacing Docs / 05 Usage guidance | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=888-1267 | Padding, gap, margin, and responsive notes. |
| Spacing Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=888-1365 | Usage selection order, rules, hierarchy rhythm, and required output. |

## Token Architecture

```text
dimension.scale.* -> space.*
```

- Dimension primitives store raw numeric values.
- Semantic spacing exposes the usable `space.*` scale.
- There are no product, theme, dark-mode, or responsive spacing modes in the foundation.

## Semantic Scale

| Token | Value | Typical use |
| --- | ---: | --- |
| `space.none` | 0px | No space or reset. |
| `space.xs` | 4px | Tiny icon/text or nested detail separation. |
| `space.sm` | 8px | Compact relationship between closely related elements. |
| `space.smPlus` | 12px | Intermediate rhythm between 8px and 16px. |
| `space.md` | 16px | Default compact spacing for grouped content. |
| `space.lg` | 24px | Comfortable container padding or clear internal separation. |
| `space.xl` | 32px | Large separation between content groups. |
| `space.2xl` | 48px | Section spacing inside larger surfaces or documentation examples. |
| `space.3xl` | 64px | Large section separation. |
| `space.4xl` | 80px | Page-level spacing for broad layouts. |
| `space.5xl` | 96px | Largest foundation spacing for major layout separation. |

## Core Rules

- Use `space.*` tokens for gaps, padding/insets, and documented external separation.
- State whether spacing is acting as gap, padding, or margin-like layout separation.
- Use the smallest token that clearly communicates the relationship.
- Use larger spacing only when the content group or page section changes.
- Product UI cards and panels should start with `space.lg` padding; compact surfaces can use `space.md`; reserve `space.xl` for larger group separation, not default card padding.
- Do not apply documentation board or section padding rules to product cards. Product surfaces use product density; documentation shells use larger docs spacing.
- Operational product UI should be denser than documentation and marketing layouts. It should feel scan-first and task-focused, not like a docs board or landing-page section.
- Suggested product hierarchy rhythm: pretitle to title uses a tight token, title to intro/body uses a medium token, body to related controls/examples uses a larger token, and major sections use the largest separation needed for scanability.
- Do not over-frame operational detail. When facts belong to one decision, group them inside one surface with clear rows, dividers, or local stacks instead of turning every fact into a separate card.
- Do not use one repeated gap for every child in a section when relationships differ.
- Do not use `dimension.scale.*` directly in product UI.
- Spacing tokens are fixed; responsive layouts choose different fixed tokens when needed.

## Product Hierarchy Rhythm

| Relationship | Typical rhythm | Guidance |
| --- | --- | --- |
| Pretitle to title | Tight | Keep the label close to the title it describes. |
| Title to intro/body | Medium | Give readable copy enough air without creating a hero. |
| Body to controls/examples | Larger | Separate explanation from action or scannable content. |
| Related fields in one decision | Compact to medium | Prefer rows, dividers, or local stacks over many mini cards. |
| Major product sections | Largest needed | Separate real task changes, not every small block. |

## AI And Engineering Contract

AI and engineering should output:

- Chosen token, such as `space.lg`.
- Property: gap, padding, or external layout separation.
- Reason based on relationship and hierarchy.
- Whether the spacing is product surface spacing or documentation/page-section spacing.
- Whether the hierarchy is marketing/editorial or operational/product, because those layouts use different density even when they use the same token scale.
- Whether related facts should be grouped inside one surface instead of split into repeated bordered mini cards.
- Responsive caveat if a compact layout should choose another fixed token.
- Source-spec caveat when exact named anatomy is not defined by the foundation.
