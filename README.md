# Design System Foundations

Codex skill and reference package for applying Omio Dotty design-system foundations.

This repository helps AI agents, engineers, and designers use the same foundation contract when working with color, typography, spacing, radius, border, elevation, icons, motion, content, and layout.

## What This Is

This repo is a Codex skill. It is not a Figma plugin, Adobe plugin, component library, or token pipeline by itself.

It contains:

- `SKILL.md` - the runtime skill instructions Codex loads.
- `agents/openai.yaml` - UI metadata for the skill.
- `references/` - Dotty foundation docs, token JSON, Figma export data, and font metadata.

It intentionally does not include licensed GT Walsheim Pro font binaries. Use your private Omio font source when accurate typography rendering is required.

## Install For Codex

Clone this repo into your Codex skills directory:

```sh
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone git@github.com:omio-ui-platform/design-system-foundations.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/design-system-foundations"
```

Then invoke it explicitly:

```text
Use $design-system-foundations to review this checkout screen against Dotty foundations.
```

Useful prompts:

```text
Use $design-system-foundations to map this UI spec to Dotty color, typography, spacing, radius, border, and elevation tokens.
```

```text
Use $design-system-foundations to QA this Figma frame for foundation-token mistakes and source-spec gaps.
```

```text
Use $design-system-foundations to generate CSS variables from the Dotty foundation token manifest.
```

## Use The References Directly

Start with:

- `references/foundation-agents.md`
- `references/dotty-foundations-guide.md`
- `references/data/foundation-token-manifest.json`
- `references/data/foundation-variable-summary.json`

Focused foundation docs live in `references/docs-pages/`:

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

## Figma Integration

Use Figma as the primary designer-facing place to inspect and apply Dotty foundations.

Recommended workflow:

1. Open the Dotty Foundations Figma file documented in `references/dotty-foundations-guide.md`.
2. Use `references/data/color-variables.figma.json` as the exported variable reference when checking color variable names and values.
3. Use `references/data/foundation-token-manifest.json` as the token contract when mapping UI decisions to public dot-token IDs.
4. Publish or consume the relevant Figma library in the design workspace so designers use shared variables and text styles instead of local duplicates.
5. When reviewing frames, compare local variables, styles, fills, effects, radii, and spacing decisions against the matching `references/docs-pages/*.md` page.

For automation:

- Build a small internal Figma plugin or script that reads `foundation-token-manifest.json` and creates or audits variables/styles.
- Keep public dot-token IDs in descriptions or annotations so handoff stays traceable.
- Treat Figma slash names as picker organization; use dot-token IDs in specs, code, and AI output.

Do not create component behavior from this repo. If a Figma decision needs component variants, component tokens, or product patterns, link to the owning component or product source spec.

## Photoshop Integration

Photoshop is useful for campaign imagery, raster design, and visual exploration, but it should consume Dotty foundations rather than redefine them.

Recommended workflow:

1. Install GT Walsheim Pro from Omio's private licensed font source before visual QA.
2. Create or import swatches from semantic color tokens, not primitive palette values.
3. Name swatches with public dot-token IDs, for example `color.text.default`.
4. Create text styles that match Dotty public text styles, for example `text.body.md.regular`.
5. Keep layer names and notes token-based when files are handed off to engineers.

For automation:

- Use `foundation-token-manifest.json` as the source for generated swatch/style setup.
- Use Photoshop scripting or UXP tooling only as a bridge; keep this repo as the token source of truth.
- Record any fallback font usage as a QA caveat.

## Illustrator Integration

Illustrator is useful for icons, vector artwork, diagrams, and brand assets.

Recommended workflow:

1. Use Dotty semantic color tokens for fills, strokes, and text colors.
2. Create swatches named by public dot-token ID.
3. Use `references/docs-pages/07-icons.md` before drawing or reviewing icon work.
4. Keep stroke widths, radii, and spacing aligned with foundation tokens when artwork is intended to match product UI.
5. Avoid inventing icon component behavior; document unresolved component dependencies separately.

For automation:

- Generate ASE/swatches or Illustrator scripts from `foundation-token-manifest.json` when a repeated workflow is needed.
- Use Creative Cloud Libraries for shared swatches and text styles across Photoshop and Illustrator.

## Other Common Designer Tools

| Tool | Best Integration Path |
| --- | --- |
| Sketch | Import or recreate color variables/text styles from `foundation-token-manifest.json`; keep token IDs in style names. |
| Penpot | Use token JSON as the source for design tokens; map colors, typography, spacing, and radii to shared assets/styles. |
| InDesign | Use Dotty typography and color tokens for docs and presentation layouts; install GT Walsheim Pro privately. |
| After Effects / Premiere Pro | Use semantic colors and typography metadata for motion/title templates; use `08-motion.md` for duration/easing guidance. |
| Tokens Studio | Use this repo's JSON as source material for a Tokens Studio-compatible transform, then sync to Figma variables. |
| Web / code handoff | Use public dot-token IDs from `foundation-token-manifest.json`; do not hand off raw values when a token exists. |

## Updating The Skill

Keep `SKILL.md` concise. Put durable foundation detail in `references/`.

Before publishing updates:

```sh
jq empty references/data/*.json
python3 /path/to/skill-creator/scripts/quick_validate.py .
```

If `quick_validate.py` cannot run because `PyYAML` is unavailable, validate manually that:

- `SKILL.md` has only `name` and `description` in YAML frontmatter.
- `name` is `design-system-foundations`.
- `agents/openai.yaml` still points to `$design-system-foundations`.
- No `.otf`, `.ttf`, `.woff`, or `.woff2` files are included.

## Public Repo Safety

This repo is public. Do not commit:

- licensed font binaries
- private Figma access tokens
- private file-storage or drive links
- product-roadmap details
- unreleased component specs unless explicitly approved for public distribution
