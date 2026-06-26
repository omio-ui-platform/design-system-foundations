# Dotty Typography Foundation Appendix

Snapshot date: 2026-05-26

This appendix supports `Dotty Foundations Guide.md` with deeper typography foundation detail for engineers, designers, and AI agents. It covers the approved typography architecture, Figma variable structure, text styles, responsive behavior, documentation pages, and usage contract.

## Source Links

| Source | Link |
| --- | --- |
| Dotty Foundations Figma file | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=0-1&t=JfhS9ji9Pl7bCqmT-1 |
| Engineering schema reference | https://goeuro.atlassian.net/wiki/spaces/UIP/pages/6381404181/Schema-Driven+Design+System |
| Typography Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=580-2 |
| Typography Docs / 02 Type scale | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=584-2 |
| Typography Docs / 03 Tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=598-2102 |
| Typography Docs / 04 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=623-2702 |
| Typography Docs / 05 Accessibility | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=623-2851 |
| Typography Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=623-3000 |

## Current Scope

Typography is a foundation-level system. It defines font family, font size, line height, weight, letter spacing, responsive Desktop/Mobile behavior, text styles, and documentation guidance.

In scope now:

- Foundation typography primitive variables.
- Responsive semantic typography variables.
- Active text styles for current Dotty usage.
- Typography documentation boards.
- AI guidance for choosing typography in generated designs.

Out of scope now:

- Control/action typography mappings.
- Button, input, link, or component state typography decisions.
- New font sizes, weights, line heights, or letter spacing beyond the current Figma source.
- Non-Roman public styles.

## Canonical Model

```txt
typography primitive variables -> responsive layout drivers -> semantic typography variables -> text styles
```

The current Figma collection model is:

```txt
02 Typography / Primitives -> Responsive layout -> 02 Typography / Semantic -> Figma text styles
```

Primitives hold raw reusable values. `Responsive layout` owns the shared `Desktop` and `Mobile` modes for responsive foundation behavior. Public semantic typography variables keep one `Value` mode and alias to the matching responsive layout drivers. Text styles consume the public semantic variables and approved primitive weight/family values.

## Naming Contract

Canonical public token IDs use dot notation in docs, code syntax, exports, and AI output.

Examples:

- `text.heading.md.bold`
- `text.body.md.regular`
- `text.subheading.sm.medium`
- `typography.heading.md.fontSize`
- `typography.body.sm.lineHeight`

Figma picker names may appear slash-grouped for organization, such as `text/body/md/regular`. Public docs, code, and AI output should use dot IDs.

## Figma Variable Collections

Foundation package state, 2026-05-26:

| Collection | Count | Modes | Purpose |
| --- | ---: | --- | --- |
| `02 Typography / Primitives` | 31 | `Value` | Raw typography values: font family, font sizes, line heights, weights, and letter spacing. |
| `Responsive layout` | 39 | `Desktop`, `Mobile` | Internal responsive drivers for typography only. |
| `02 Typography / Semantic` | 39 | `Value` | Public role-based typography variables. These alias to `Responsive layout` drivers and keep public token IDs/code syntax stable. |

## Primitive Inventory

Font family:

- `typography.fontFamily.default`: GT Walsheim Pro

## Font Assets

GT Walsheim Pro is included in `../assets/fonts/` so engineering and AI-generated local previews can render Dotty typography accurately.

| File | Weight | Style | Use |
| --- | ---: | --- | --- |
| `GT-Walsheim-Pro-Regular.otf` | 400 | normal | Regular body and supporting copy. |
| `GT-Walsheim-Pro-Medium.otf` | 500 | normal | Medium emphasis for body/subheading styles. |
| `GT-Walsheim-Pro-Bold.otf` | 700 | normal | Bold display, heading, subheading, and body styles. |
| `GT-Walsheim-Pro-Regular-Oblique.otf` | 400 | italic | Italic regular fallback when content needs it. |
| `GT-Walsheim-Pro-Medium-Oblique.otf` | 500 | italic | Italic medium fallback when content needs it. |
| `GT-Walsheim-Pro-Bold-Oblique.otf` | 700 | italic | Italic bold fallback when content needs it. |

Implementation must load `GT Walsheim Pro` before visual QA. If the target environment cannot load these font files, document the fallback as a QA caveat.

Font sizes:

- `typography.fontSize.12`
- `typography.fontSize.14`
- `typography.fontSize.16`
- `typography.fontSize.18`
- `typography.fontSize.20`
- `typography.fontSize.22`
- `typography.fontSize.24`
- `typography.fontSize.26`
- `typography.fontSize.30`
- `typography.fontSize.32`
- `typography.fontSize.40`
- `typography.fontSize.56`

Line heights:

- `typography.lineHeight.16`
- `typography.lineHeight.20`
- `typography.lineHeight.24`
- `typography.lineHeight.28`
- `typography.lineHeight.30`
- `typography.lineHeight.32`
- `typography.lineHeight.34`
- `typography.lineHeight.36`
- `typography.lineHeight.38`
- `typography.lineHeight.48`
- `typography.lineHeight.64`

Font weights:

- `typography.fontWeight.regular`
- `typography.fontWeight.medium`
- `typography.fontWeight.bold`

Letter spacing:

- `typography.letterSpacing.0`
- `typography.letterSpacing.1-2`
- `typography.letterSpacing.1-4`
- `typography.letterSpacing.1-6`

Do not add new primitive values unless a foundation decision explicitly approves them.

## Semantic Typography Inventory

Each semantic typography role contains `fontSize`, `lineHeight`, and `letterSpacing` variables. Public semantic variables have one `Value` mode and resolve through `Responsive layout`, which provides `Desktop` and `Mobile` values.

Display:

- `typography.display.xl.{fontSize,lineHeight,letterSpacing}`
- `typography.display.lg.{fontSize,lineHeight,letterSpacing}`

Heading:

- `typography.heading.xl.{fontSize,lineHeight,letterSpacing}`
- `typography.heading.lg.{fontSize,lineHeight,letterSpacing}`
- `typography.heading.md.{fontSize,lineHeight,letterSpacing}`
- `typography.heading.sm.{fontSize,lineHeight,letterSpacing}`
- `typography.heading.xs.{fontSize,lineHeight,letterSpacing}`

Subheading:

- `typography.subheading.md.{fontSize,lineHeight,letterSpacing}`
- `typography.subheading.sm.{fontSize,lineHeight,letterSpacing}`

Body:

- `typography.body.lg.{fontSize,lineHeight,letterSpacing}`
- `typography.body.md.{fontSize,lineHeight,letterSpacing}`
- `typography.body.sm.{fontSize,lineHeight,letterSpacing}`
- `typography.body.xs.{fontSize,lineHeight,letterSpacing}`

Designers should switch the shared `Responsive layout` mode between `Desktop` and `Mobile` on the target frame. They should not maintain separate Desktop and Mobile text style names.

## Active Text Styles

Foundation package state, 2026-05-26: 25 approved public text styles and 0 hidden/archive text styles.

Display:

- `text.display.xl.bold`
- `text.display.lg.bold`

Heading:

- `text.heading.xl.bold`
- `text.heading.lg.bold`
- `text.heading.md.bold`
- `text.heading.sm.bold`
- `text.heading.xs.bold`

Subheading:

- `text.subheading.md.regular`
- `text.subheading.md.medium`
- `text.subheading.md.bold`
- `text.subheading.sm.regular`
- `text.subheading.sm.medium`
- `text.subheading.sm.bold`

Body:

- `text.body.lg.regular`
- `text.body.lg.medium`
- `text.body.lg.bold`
- `text.body.md.regular`
- `text.body.md.medium`
- `text.body.md.bold`
- `text.body.sm.regular`
- `text.body.sm.medium`
- `text.body.sm.bold`
- `text.body.xs.regular`
- `text.body.xs.medium`
- `text.body.xs.bold`

Approved weight scope:

- Display and Heading are bold-only.
- Body and Subheading expose regular, medium, and bold.
- Heading Regular/Medium styles are not part of the approved foundation. Add them only through an explicit foundation change.

## Usage Guidance

Choose typography by content purpose, hierarchy, density, importance, and responsive behavior.

| Role | Best suited for | Weight guidance |
| --- | --- | --- |
| Display | Large brand/editorial moments and major high-impact messaging. | Bold only. |
| Heading | Page titles, section titles, panel titles, and hierarchy anchors. | Bold only. |
| Subheading | 12px caps-style pretitles/overlines, compact labels, metadata labels, dense support text, and structured labels. | Medium is the product UI default for pretitles/overlines; reserve bold for documentation metadata or deliberately high-emphasis labels. Pretitles should normally use neutral/subtle text color, not coral. |
| Body | Main readable content, descriptions, values, dense UI text, and supporting content. | Regular by default; medium or bold only for emphasis. |

General rules:

- Start with the job of the content, not the visual size.
- Use `text.body.md.regular` as the default documentation and general reading text.
- Use larger headings to create hierarchy, not body text with arbitrary custom sizing.
- Use small text for compact metadata, captions, dense labels, or secondary information.
- Use `text.body.xs.*` only for dense metadata, captions, compact secondary labels, or constrained supporting details. Do not use it for main reading text or long-form content.
- Use `text.subheading.sm.medium` for product UI pretitles and overlines by default; do not manually bold them unless a source spec requires stronger emphasis.
- Keep product UI pretitles/overlines short and neutral/subtle by default. Do not use coral pretitles unless the label itself has an approved brand or promotional job.
- Use Display scale mainly for marketing, editorial, or high-impact entry moments. Operational product flows should normally use Heading scale and denser hierarchy.
- Use responsive modes before creating extra styles.
- Do not infer control, action, or input typography from foundation text styles alone; use a documented source spec when those mappings are needed.

## Accessibility And Content Rules

Typography docs currently cover:

- Use heading hierarchy to help people scan and understand the page.
- Keep line lengths readable.
- Avoid truncation unless there is a way to access the full text.
- Check Desktop and Mobile modes.
- Pair typography with appropriate color contrast tokens.
- Preserve semantic structure in code; visual style alone is not enough.
- Do not use all caps for long words or sentences.

## Usage Contract

When Dotty typography is used by designers, engineers, or AI agents:

- Choose from approved Dotty text styles first.
- Do not invent new font sizes, line heights, weights, or letter spacing unless explicitly asked to change the foundation.
- Use content role first: display, heading, subheading, or body.
- Consider hierarchy, density, importance, and responsive behavior.
- Use the approved 12px caps-style treatment for pretitles/overlines instead of normal sentence-case body labels.
- Use `text.subheading.sm.medium` for product UI pretitles/overlines by default; reserve bold for documentation metadata or deliberately high-emphasis labels.
- Explain whether a generated page is marketing/editorial or operational/product before applying large display hierarchy.
- Use Desktop/Mobile semantic behavior instead of inventing separate breakpoint styles.
- Do not infer control, action, or input typography from foundation text styles alone.

Required AI typography output:

- Chosen style.
- Reason.
- Desktop/Mobile behavior.
- Token IDs.
- Caveat or unresolved decision, if any.

Example:

```txt
Chosen style: text.heading.md.bold
Reason: Section title that anchors a compact content group.
Desktop/Mobile behavior: Uses typography.heading.md values in the active mode.
Token IDs: typography.heading.md.fontSize, typography.heading.md.lineHeight, typography.heading.md.letterSpacing, typography.fontWeight.bold
Caveat: Control/action heading rules need a documented source spec.
```

## Online Docs Notes

The online docs should expose:

- Overview of the typography model.
- Type scale and approved styles.
- Token architecture.
- Usage examples and callout templates.
- Accessibility guidance.
- Usage rules.

Keep the online docs product-neutral. The documentation should read as the current Dotty typography foundation.
