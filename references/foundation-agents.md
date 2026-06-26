# Dotty Foundations Agent Contract

Snapshot date: 2026-05-26

This file is the AI and implementation guard for Dotty Foundations. It is export-facing and safe to send with the foundation package. It is not a local continuity note.

Use this contract whenever an AI agent, engineer, designer, or implementation tool consumes the Dotty Foundations package to create UI, generate code, review output, or prepare platform tokens.

## Foundation Guard Role

This file acts as the Dotty Foundation Guard for designers, engineers, AI agents, and implementation tools.

Use it to protect foundation decisions whenever Dotty Foundations are read, implemented, translated into code, used in prototypes, or used to review output.

The guard does not generate new design rules. It verifies that the existing foundation is being applied correctly, that missing component or product decisions are reported as gaps, and that no unofficial tokens, values, states, components, or patterns are invented from foundation documentation alone.

## Required Read Order

1. `README.md`
2. `AGENTS.md`
3. `Dotty Foundations Guide.md`
4. `docs-pages/README.md`
5. `docs-pages/01-color.md` through `docs-pages/10-layout.md`
6. `data/foundation-token-manifest.json`
7. `data/foundation-variable-summary.json`
8. `data/font-assets.json`
9. Appendices only when deeper detail is needed.

The `Foundations/` package is the current source-of-truth contract for AI and implementation. Figma is the temporary visual and variable reference while the foundation is still being moved toward online documentation:
https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations

## Scope Guard

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

Do not create, infer, or document components, component APIs, component states, component tokens, Code Connect mappings, templates, or product patterns from this package. If a task needs behavior outside the foundation, state the unresolved source-spec dependency instead of inventing a foundation decision.

When a prototype must include component-like controls before component specs exist, keep the choice simple, neutral, and local to the prototype. Document it in delivery notes as a source-spec dependency; do not present it as a Dotty component rule.

## Token Contract

- Use public dot token IDs in output, code references, documentation, and generated UI specs.
- Treat Figma slash names as picker organization only.
- Do not use primitive tokens directly in product UI.
- Do not invent raw values when a Dotty token exists.
- Do not invent new tokens, modes, breakpoints, ramps, shadows, radii, or text styles unless the user explicitly asks to extend the foundation.
- If a needed token does not exist, report the gap instead of creating an unofficial substitute.

## Foundation Rules

### Color

- Product UI should use semantic `color.*` tokens.
- Product and Theme collections explain resolution; they are not the default authoring surface for generated UI.
- Do not use raw hex values for UI when a token exists.
- Dotty does not use pure `#000000`; `color.common.black` is intentionally `#161A24`.
- Do not create `color.status.*` tokens.
- Status meaning uses property-first roles, such as `color.text.error`, `color.icon.information`, `color.background.success`, and `color.border.warning`.
- Do not use coral for error.
- Branded Omio or Dotty outputs should include a restrained brand anchor when the product context needs identity, but coral is not generic decoration, label, pretitle, status, or selected-state styling.
- Coral is appropriate for Omio brand identity, approved primary brand emphasis, promotional emphasis, small active indicators, and one consistent Omio-branded prototype action when final action styling is unresolved.
- When a foundation-only prototype needs an Omio-branded primary action, use the brand role consistently and state final action styling as a source-spec dependency. Do not mix navy and coral as competing primary actions.
- Do not use status backgrounds to invent selected row, card, or option states. Use status color only when the status itself is the meaning.
- Do not add opacity by default. If opacity is required, use only approved opacity tokens.

### Typography

- Load `GT Walsheim Pro` from `assets/fonts/` before visual QA.
- Default readable copy uses `text.body.md.regular`.
- Product UI pretitles and overlines use `text.subheading.sm.medium` as the default 12px caps-style treatment; reserve bold for documentation metadata or deliberately high-emphasis labels.
- Product UI pretitles and overlines should normally use neutral/subtle text color. Do not make them coral by default, and do not use long all-caps phrases.
- Use pretitles only when they clarify the local section or page role. Do not repeat the same feature label above every screen or card just to add decoration.
- Marketing pages may use larger display hierarchy; operational product flows should use calmer page/section hierarchy and avoid hero-scale headings unless the source spec calls for a hero.
- Use SM and XS only for metadata, captions, specs, dense labels, code-like examples, and constrained secondary details.
- Do not manually resize text to approximate a missing style.
- Use responsive typography modes through the approved typography foundation; do not create separate desktop/mobile style names.

### Spacing

- Use `space.*` tokens for gaps, padding, and layout separation.
- Apply hierarchy rhythm: tighter pretitle/title, medium title/body, larger body/examples, largest major section separation.
- Operational product UI should be denser than documentation or marketing layouts. Do not apply docs-board spacing to product flows.
- Product UI cards and panels should start with `space.lg` padding; compact surfaces can use `space.md`; reserve `space.xl` for larger group separation, not default card padding.
- Keep operational product hierarchy scan-first: one strong page title, restrained panel/card headings, readable body copy, and fewer boxed facts. Do not turn every field or detail into a separate mini card unless the product source spec requires that structure.
- Do not apply one flat gap everywhere.
- Do not use `dimension.scale.*` directly in product UI.

### Radius

- Use `radius.medium` as the normal card, panel, and container radius.
- Use `radius.large` for larger grouped sections.
- Use `radius.none` only for deliberate square, joined, table/grid, flush, or edge-to-edge cases.
- Same-level sibling cards, panels, and sections should share the same radius token unless a source spec explains the difference.
- Nested surfaces should not be rounder than their parent. If a child surface is visibly inset inside a padded parent, step down one token where possible: parent `radius.large` -> child `radius.medium`; parent `radius.medium` -> child `radius.small`.
- If a child surface is flush to a parent edge, align with the parent corner logic instead of adding a competing inner rounded corner.
- If the inner content is only related facts, metadata, rows, or comparisons, prefer rows, dividers, spacing, or subtle background before creating nested rounded cards.
- Do not infer action, chip, or pill shape from foundation radius alone; use a documented source spec for those shape decisions.

### Border

- Pair border width and border color, usually `borderWidth.default` with `color.border.subtle`.
- Use borders for structure, separation, selected states, and emphasis.
- Do not make first-level product cards border-only by default. Use borders mainly for nested surfaces, tables, quiet separation, selected structure, or explicit boundaries.
- A small active indicator can use a strong/heavy edge, but that pattern does not define selected card, row, button, or tab component behavior.
- Do not use heavy borders for normal cards or quiet content.

### Elevation

- Start flat.
- Add elevation only when layer behavior requires it, such as sticky, floating, overlay, or temporary surfaces.
- First-level product cards or panels should use `color.background.surface` and can use `elevation.surface` when they need to sit above the page background; nested and quiet surfaces can stay flat with background and border.
- Do not elevate every card by default; choose elevation by layer role.
- If a first-level card sits on `color.background.default` and visually blends into the page, prefer `elevation.surface` before adding more borders or nested outlines.

### Icons

- Use icons only when they clarify action, object, status, navigation, or supporting meaning.
- Pair icon size tokens with icon color tokens.
- Ensure icons are either decorative or have accessible labels.
- SVGs should use `viewBox="0 0 24 24"`, `currentColor`, no hardcoded internal colors, and no fixed width/height.

### Motion

- Motion is an active foundation tool, not disabled.
- Use motion when it clarifies feedback, state change, loading/progress, reveal/hide, navigation continuity, or spatial relationship.
- Apply motion consistently: the same intent should use the same duration, easing, direction, and reduced-motion fallback across a flow.
- Component-trigger motion such as hover, press, focus, selected, or CTA animation can be suggested as a prototype assumption, but it must be labelled non-final until component specs define the behavior.
- Use approved duration and easing tokens.
- Include reduced-motion behavior.
- Prefer transform and opacity for performance.

### Content

- Use Omio voice: clear, useful, calm, and direct.
- Do not invent legal, provider, price, route, promotion, localization, or product facts.
- Ask for missing required facts or mark assumptions clearly.

### Layout

- Choose layout by hierarchy, viewport, content area, grid/alignment, spacing, and component constraints.
- Separate marketing/editorial hierarchy from operational product hierarchy. Marketing can be broader and more expressive; task flows should be calmer, denser, and easier to scan.
- Do not invent new breakpoints, grids, or source-specific layout tokens.
- Do not stretch all content full width by default.
- Tables must stay readable. If columns become cramped or body text wraps into narrow fragments, switch to stacked comparison cards or rows using the same table content order.

## AI Output Contract

When generating a UI, website, product flow, or code from Dotty Foundations, include:

- The foundation files used.
- The product context and assumptions.
- The Dotty tokens applied for color, typography, spacing, radius, border, elevation, icon, motion, content, and layout.
- Any unresolved source-spec dependencies.
- A QA summary using the checks below.

Keep those notes outside the user-facing UI unless the prompt explicitly asks to render them.

## QA Gate

Before finalizing any output that claims to follow Dotty Foundations, verify:

- No raw hex, pixel, font-size, radius, shadow, or motion value is used where a Dotty token exists.
- GT Walsheim Pro is loaded from `assets/fonts/`; any fallback font is reported as a QA caveat.
- No primitive token is consumed directly in product UI.
- No unofficial token names are introduced.
- Normal readable copy uses `text.body.md.regular` unless there is a valid compact/metadata reason.
- SM/XS typography is limited to approved compact use cases.
- Cards, panels, tables, and docs-like surfaces use approved surface, border, radius, padding, and gap rules.
- First-level product cards and panels are not treated like documentation table/card shells unless that role is intentional.
- Operational product UI does not use coral pretitles, hero-scale headings, or large documentation spacing by default.
- Tables follow the canonical table anatomy from the foundation docs.
- Tables or comparison grids collapse to readable stacked content before text becomes cramped.
- Color uses semantic roles correctly and does not use coral as error.
- Primary action brand emphasis is consistent or called out as an unresolved source-spec dependency.
- Selected rows, cards, or options do not borrow status colors unless the status itself is the meaning.
- Pure black `#000000` is not used.
- Opacity is absent unless intentionally required and uses an approved opacity token.
- Icons use approved sizes, colors, and accessibility treatment.
- Motion has a purpose, approved duration/easing tokens, and reduced-motion behavior.
- Content does not invent unsupported facts.
- Layout uses approved spacing, hierarchy, and responsive guidance.

If any check fails, fix the output before presenting it. If the fix requires a missing token or source spec, report that dependency instead of inventing one.

## Source Protection

- Do not modify foundation docs, token data, variable exports, or Figma references unless explicitly asked.
- Do not add demos, temporary test artifacts, chat logs, local continuity notes, or generated prompts to this package.
- Keep this package final-facing and exportable.
- If the foundation changes, update the relevant guide, docs-page mirror, data export, and appendix together so the package stays consistent.
