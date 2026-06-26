# Dotty Foundations Guide

Snapshot date: 2026-05-26

Dotty is Omio's AI-ready product design system for all Omio product experiences. This guide is the single starting point for engineers, designers, and AI agents that need to understand or implement the current Dotty Foundations.

AI agents and implementation tools should also follow `AGENTS.md` in this folder. That file is the export-facing guard for using Dotty Foundations correctly and checking output before delivery.

## Source Of Truth

- Current source package: this `Foundations/` folder.
- Temporary visual and variable reference: Dotty Foundations in Figma.
- File key: `WSSIyMUfJz9BsiVx5ocIL9`
- URL: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations
- Live Figma state at export: 19 variable collections, 564 variables, 25 active text styles, 4 effect styles, 60 final docs boards.

This package is the current foundation contract for engineers, designers, and AI agents. Figma is used for visual layout, swatches, diagrams, board anatomy, and variable inspection until the foundation moves to online documentation.

Relevant Figma foundation pages are `01 Color` through `10 Layout`. Ignore `Drafts`, `99 Archive`, active/draft pages, and legacy non-final docs when implementing or reviewing the foundation.

## Scope

This package covers foundations only:

- Color
- Typography
- Spacing
- Radius
- Border
- Elevation
- Icons
- Motion
- Content
- Layout

This package does not include components, component APIs, component variants, component tokens, Code Connect, product templates, or pattern libraries. If implementation needs behavior outside the foundation, state the unresolved source-spec dependency instead of inventing a foundation token.

Foundation-only prototypes may include temporary controls to make a flow inspectable, but those choices must remain simple, neutral, and clearly documented as prototype-only source-spec dependencies. Do not promote prototype controls into Dotty component guidance.

## Token Architecture

Public token IDs use dot notation in docs, code, data files, and AI output. Figma variable names may remain slash-grouped because Figma uses slashes for picker organization.

Color model:

```text
color.palette.* -> theme.* -> product.* -> color.*
```

- Primitives store raw palette values.
- Theme owns Light and Dark appearance mapping.
- Product owns product identity mapping such as B2C and B2B.
- Semantic `color.*` tokens are the current usable foundation layer for page, layout, and product UI.

Size-like model:

```text
dimension.scale.* -> space.*, radius.*, borderWidth.*
```

- Dimension primitives are the internal numeric source scale.
- Product UI should use semantic spacing, radius, and border-width tokens.

Typography model:

```text
typography primitives -> responsive layout drivers -> semantic typography variables -> text styles
```

- Responsive behavior lives in `02 Typography / Responsive layout` with Desktop and Mobile modes.
- Public typography styles stay stable, such as `text.body.md.regular`.

## Foundation Inventory

| Collection | Modes | Count | Use |
| --- | --- | ---: | --- |
| `00 Dimension / Primitives` | Value | 18 | Internal numeric scale. |
| `01 Color / Primitives` | Value | 144 | Raw source colors. |
| `01 Color / Theme` | Light, Dark | 75 | Appearance routing. |
| `01 Color / Product` | B2C, B2B | 75 | Product identity mapping. |
| `01 Color / Semantic` | Value | 38 | Usable color layer for product UI and generated UI. |
| `01 Color / Opacity` | Value | 6 | Approved opacity modifiers. |
| `02 Typography / Primitives` | Value | 31 | Internal typography values. |
| `02 Typography / Semantic` | Value | 39 | Public typography variables. |
| `02 Typography / Responsive layout` | Desktop, Mobile | 39 | Responsive typography drivers. |
| `03 Spacing / Semantic` | Value | 11 | Public spacing roles. |
| `04 Radius / Semantic` | Value | 6 | Public radius roles. |
| `05 Border / Semantic` | Value | 4 | Public border-width roles. |
| `06 Elevation / Primitives` | Value | 12 | Internal shadow values. |
| `06 Elevation / Semantic` | Value | 20 | Public elevation effect tokens. |
| `07 Icons / Primitives` | Value | 9 | Icon construction and sizing. |
| `08 Motion / Primitives` | Value | 9 | Internal motion source values. |
| `08 Motion / Semantic` | Value | 9 | Public duration/easing tokens. |
| `10 Layout / Primitives` | Value | 9 | Layout reference source values. |
| `10 Layout / Semantic` | Value | 10 | Public layout reference tokens. |

There is intentionally no `09 Content` variable collection because Content is guidance, not a token collection.

## Product UI Defaults

- Font family: `GT Walsheim Pro`, loaded from `assets/fonts/`
- Text: `color.text.default`
- Page background: `color.background.default`
- Surface/card background: `color.background.surface`
- Subtle grouped background: `color.background.subtle`
- Default icon: `color.icon.default`
- Quiet border: `color.border.subtle`
- Default readable text style: `text.body.md.regular`
- Normal card/panel radius: `radius.medium`
- Normal border width: `borderWidth.default`
- Elevation: start flat, but use `elevation.surface` for first-level product cards or panels when they need to sit clearly above the page background.

## Foundation Rules

### Color

- Use semantic `color.*` tokens for generated product UI and page/layout styling.
- Use Product, Theme, and Primitive tokens only when explaining source behavior or product/theme resolution.
- Do not use raw hex in product UI when a token exists.
- Dotty does not use pure `#000000`; `color.common.black` is intentionally `#161A24`.
- Use `color.background.surface` for cards, panels, forms, modals, and clean foreground containers.
- Use `color.background.subtle` for nested/grouped surfaces and quieter sections.
- Do not create `color.status.*` tokens. Status meaning is expressed through text, icon, background, and border roles.
- Do not use coral as error. Error uses the red role.
- Branded Omio or Dotty outputs should include a restrained brand anchor when the product context needs identity, but coral is not generic decoration, label, pretitle, status, or selected-state styling.
- Use coral for Omio brand identity, approved primary brand emphasis, promotional emphasis, small active indicators, and one consistent Omio-branded prototype action when final action styling is unresolved.
- When a foundation-only prototype needs an Omio-branded primary action, use the brand role consistently and state final action styling as a source-spec dependency. Do not mix navy and coral as competing primary actions.
- Do not use status backgrounds to invent selected row, card, or option states. Use status color only when the status itself is the meaning.
- Do not add opacity by default. If opacity is requested, use only `opacity.8`, `opacity.12`, `opacity.16`, `opacity.24`, `opacity.40`, or `opacity.80`.

### Typography

- Use approved Dotty text styles and token IDs.
- Use `GT Walsheim Pro` as the Dotty font family; load it from `assets/fonts/` when generating code or local previews.
- Default readable copy uses `text.body.md.regular`.
- Page title uses display scale only for true page-level or high-impact titles.
- Section, panel, and card hierarchy should use heading styles before custom sizes.
- Subheading styles are for overlines, labels, metadata, compact structure, and dense headers.
- Product UI pretitles and overlines use `text.subheading.sm.medium` as the default 12px caps-style treatment; reserve bold for documentation metadata or deliberately high-emphasis labels.
- Product UI pretitles and overlines should normally use neutral/subtle text color. Do not use coral by default, and do not turn long helper labels into all-caps pretitles.
- Use pretitles/overlines to clarify the local section or page role. Do not repeat a generic feature name above every screen, panel, or card.
- Marketing or editorial pages may use Display scale and broader rhythm. Operational product flows should usually use calmer Heading scale, denser spacing, and clear task hierarchy.
- SM and XS are reserved for metadata, captions, compact support text, specs, dense labels, and constrained secondary details.
- Responsive typography uses `02 Typography / Responsive layout` Desktop/Mobile modes. Do not create separate desktop/mobile text style names.

### Spacing

- Foundation spacing is fixed, not responsive by mode.
- Use `space.*` tokens for gaps, padding/insets, and section separation.
- State whether spacing is used as gap, padding, or external layout separation.
- Use hierarchy rhythm: smaller between pretitle/title, medium between title/body, larger between body/examples, largest between major sections.
- Product UI cards and panels should start with `space.lg` padding; compact surfaces can use `space.md`; reserve `space.xl` for larger group separation, not default card padding.
- Operational product UI should be denser than documentation and marketing layouts. Do not apply docs-board padding or repeated display-section gaps to task flows.
- Suggested product hierarchy rhythm: pretitle to title uses a tight token, title to intro/body uses a medium token, body to related controls/examples uses a larger token, and major sections use the largest separation needed for scanability.
- Do not apply documentation board or section padding rules to product cards; product cards follow product surface density.
- Operational screens should avoid over-framing. Prefer one clear first-level panel with grouped content over many nested mini cards when the details are part of the same decision.
- Do not apply one flat repeated gap everywhere.
- Do not use `dimension.scale.*` directly in product UI.

### Radius

- Use `radius.medium` as the normal card, panel, and container radius.
- Use `radius.large` for larger sections or surfaces that need stronger grouping.
- Use `radius.none` only for deliberate square, flush, joined, table/grid, or edge-to-edge media cases.
- Same-level sibling cards, panels, and sections should share the same radius token unless a source spec explains the difference.
- Nested surfaces should not be rounder than their parent. If a child surface is visibly inset inside a padded parent, step down one token where possible: parent `radius.large` -> child `radius.medium`; parent `radius.medium` -> child `radius.small`.
- If a child surface is flush to a parent edge, align with the parent corner logic instead of adding a competing inner rounded corner.
- If the inner content is only related facts, metadata, rows, or comparisons, prefer rows, dividers, spacing, or subtle background before creating nested rounded cards.
- Do not infer action, chip, or pill shape from foundation radius alone; use a documented source spec for those shape decisions.

### Border

- Use borders for separation, structure, selected states, and emphasis.
- Pair border width with border color, usually `borderWidth.default` plus `color.border.subtle`.
- Use `borderWidth.none` when spacing, background, or elevation already separates content.
- Do not make first-level product cards border-only by default. Use borders mainly for nested surfaces, tables, quiet separation, selected structure, or explicit boundaries.
- Small active indicators may use a strong/heavy edge, but that does not define selected card, row, button, or tab component behavior.
- Reserve `borderWidth.strong` and `borderWidth.heavy` for selected, emphasized, or major structural edges.

### Elevation

- Start flat with background, border, radius, and spacing.
- Add elevation only when a surface sits above another layer, scrolls over content, or opens temporarily above the page.
- Use `elevation.surface` for stable raised containers.
- Use `elevation.surface` for first-level product cards or panels when they need foreground separation from the page background; nested and quiet surfaces can stay flat with background and border.
- If a first-level product surface on `color.background.default` needs separation, prefer `elevation.surface` before making it a border-only docs shell.
- Use `elevation.stickyTop` or `elevation.stickyBottom` for sticky surfaces.
- Use `elevation.floating` for temporary layered surfaces such as menus, popovers, dialogs, and overlays.
- Do not elevate every card by default; choose elevation by layer role.

### Icons

- Use icons only when they clarify action, object, status, navigation, or supporting meaning.
- Pair icon size tokens with icon color tokens.
- Default inline icon size is usually `icon.size.medium`.
- Use `icon.size.default` for standalone actions, navigation, and header controls.
- State whether an icon is decorative, labelled, or needs an accessible label.
- Preserve SVG rules: `viewBox="0 0 24 24"`, no fixed width/height, `currentColor`, no hardcoded internal colors, centered content inside the 20dp live area.

### Motion

- Motion is an active foundation tool, not disabled.
- Use motion when it clarifies feedback, state change, loading/progress, reveal/hide, navigation/continuity, or spatial relationship.
- Apply motion consistently: the same intent should use the same duration, easing, direction, and reduced-motion fallback across a flow.
- Component-trigger motion such as hover, press, focus, selected, or CTA animation can be suggested as a prototype assumption, but it must be labelled non-final until component specs define the behavior.
- Use duration tokens: `motion.duration.instant`, `motion.duration.quick`, `motion.duration.standard`, `motion.duration.emphasized`, `motion.duration.expressive`.
- Use easing tokens: `motion.easing.enter`, `motion.easing.exit`, `motion.easing.move`, `motion.easing.continuous`.
- Include reduced-motion behavior.
- Prefer transform and opacity for performance.

### Content

- Use Omio voice: clear, useful, calm, and direct.
- Ask for missing legal, provider, or product facts instead of inventing them.
- Include localization and accessibility notes for generated copy.
- Do not invent promotions, claims, translations, provider rules, or product terminology.
- There is no Content variable collection in foundation v1.

### Layout

- Choose layout by content hierarchy, viewport, content area, grid/alignment, spacing, and component constraints.
- Use approved layout reference tokens for viewport/content/grid behavior.
- Use `space.*` tokens for rhythm, gaps, padding, and external separation.
- Match layout density to the experience type: marketing can be expressive and spacious; operational product flows should be calmer, denser, and scan-first.
- Tables and comparison grids must remain readable. If columns become cramped, switch to stacked cards or rows while preserving the same comparison order.
- Do not invent new breakpoints, grid values, or source-specific layout tokens.
- Do not stretch all content full width by default.

## Implementation Guidance

- Treat public dot token IDs as the implementation contract.
- Generate platform tokens from the public dot IDs.
- Do not expose primitive tokens as normal product UI APIs.
- Do not create component tokens, component APIs, states, or Code Connect mappings from this package.
- Page/layout styling can consume semantic `color.*` tokens.
- If implementation needs behavior outside the foundation, state the unresolved source-spec dependency instead of inventing tokens.
- CSS custom properties can be generated from dot IDs, for example `color.background.surface -> --dotty-color-background-surface`.

Recommended token pipeline:

```text
Figma Variables
  -> foundation token data
  -> Style Dictionary or equivalent transform
  -> platform outputs
  -> product/component consumption
```

Recommended platform outputs:

- CSS custom properties
- TypeScript token constants
- JSON token package for documentation and AI/tooling
- Optional Figma sync output if the implementation pipeline needs round-trip checks

## Usage Contract

When Dotty Foundations are used by designers, engineers, or AI agents:

- Choose existing Dotty tokens before proposing new decisions.
- Explain token choices by role and purpose.
- Use semantic tokens for UI consumption.
- Keep Product, Theme, and Primitive layers internal unless explaining resolution.
- Use Body MD as the default reading size.
- Load `GT Walsheim Pro` before visual QA and report any fallback font as a caveat.
- Use `text.subheading.sm.medium` for product UI pretitles/overlines; do not bold them unless the source spec requires stronger emphasis.
- Keep product UI pretitles neutral/subtle by default; do not use coral or status color unless the pretitle itself carries that approved meaning.
- Use pretitles only when they help scan the local section; avoid repeating one generic flow label across every screen.
- Choose marketing vs operational hierarchy before choosing Display scale. Operational flows should not look like landing pages unless the prompt asks for a marketing surface.
- Use hierarchy-aware spacing instead of one repeated gap everywhere.
- Use `space.lg` as the starting card/panel padding; do not use `space.xl` as default card padding.
- Keep operational product panels readable and grouped; avoid turning every small fact into a separate bordered mini card.
- Use `radius.medium` as the default card/panel radius.
- Keep same-level cards and panels on the same radius token unless the source spec defines a hierarchy difference.
- For nested rounded surfaces, child radius should step down from the parent only when the child is visibly inset; related facts should usually use rows/dividers before nested cards.
- Use first-level product card/panel elevation when foreground separation is needed; do not reduce every product surface to a border-only docs shell.
- Switch cramped tables or comparison grids into stacked content before body text wraps into narrow fragments.
- Include reduced-motion behavior when motion is specified.
- Use approved motion tokens when motion clarifies the experience; label component-trigger motion as non-final until component specs define it.
- Do not use status backgrounds to invent selected states; selected styling is a source-spec dependency unless already documented.
- Keep Omio-branded primary action emphasis on the brand role when a prototype needs that action; do not mix navy and coral as competing primary actions.
- Keep QA summaries and implementation notes outside user-facing UI unless explicitly requested.
- State unresolved source-spec dependencies instead of inventing foundation decisions.

Required output for product UI or implementation work:

1. Product context and assumptions
2. Layout structure
3. Foundation tokens used, grouped by foundation
4. Why each token role was chosen
5. Responsive behavior
6. Accessibility notes
7. Source-spec dependencies or assumptions
8. Things not invented

## Data And Appendices

The `data/` folder contains machine-readable foundation data:

- `foundation-token-manifest.json`: compact foundation manifest for counts, defaults, guardrails, and token groups.
- `foundation-variable-summary.json`: verified live summary of Figma variable collections and style counts.
- `color-variables.figma.json`: current full color per-variable export.
- `font-assets.json`: licensed GT Walsheim Pro font asset manifest.

The `docs-pages/` folder contains curated Markdown mirrors of the final Figma foundation documentation pages:

- `01-color.md`
- `02-typography.md`
- `03-spacing.md`
- `04-radius.md`
- `05-border.md`
- `06-elevation.md`
- `07-icons.md`
- `08-motion.md`
- `09-content.md`
- `10-layout.md`

Use these files for portable AI and engineering reading. Use Figma as the temporary visual and variable reference for layout, examples, swatches, diagrams, and variable inspection.

The `appendices/` folder contains deeper foundation notes that support the main guide:

- `Color Foundation Appendix.md`
- `Typography Foundation Appendix.md`

If engineering needs a full all-foundation per-variable export, build a dedicated Figma export script or REST export job that writes directly to disk instead of returning the payload through chat tooling.
