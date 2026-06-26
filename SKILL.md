---
name: design-system-foundations
description: Apply Omio Dotty design-system foundation rules, tokens, and AI implementation guardrails. Use when designing, implementing, reviewing, or QAing UI against Dotty foundations, including color, typography, spacing, radius, border, elevation, icons, motion, content, layout, token selection, Figma foundation interpretation, or foundation-only prototypes.
---

# Design System Foundations

Use this skill to apply Dotty Foundations without inventing tokens, component behavior, or raw visual values.

## Start Here

1. Read `references/foundation-agents.md` before generating or reviewing Dotty output.
2. Read `references/dotty-foundations-guide.md` for the current foundation contract.
3. Load only the focused docs page needed for the task:
   - Color: `references/docs-pages/01-color.md`
   - Typography: `references/docs-pages/02-typography.md`
   - Spacing: `references/docs-pages/03-spacing.md`
   - Radius: `references/docs-pages/04-radius.md`
   - Border: `references/docs-pages/05-border.md`
   - Elevation: `references/docs-pages/06-elevation.md`
   - Icons: `references/docs-pages/07-icons.md`
   - Motion: `references/docs-pages/08-motion.md`
   - Content: `references/docs-pages/09-content.md`
   - Layout: `references/docs-pages/10-layout.md`
4. Use JSON data from `references/data/` when exact token IDs, modes, variable summaries, color values, or font asset metadata are needed.

## Scope Boundaries

- Treat Dotty Foundations as foundation-only guidance: color, typography, spacing, radius, border, elevation, icons, motion, content, and layout.
- Do not invent component tokens, component variants, product templates, Code Connect behavior, or pattern-library rules.
- If a UI decision needs component behavior or product-specific patterns, state the missing source-spec dependency instead of promoting a foundation guess.
- Use Figma only as the temporary visual and variable reference when swatches, diagrams, variable inspection, or final board layout matter. The file key is documented in `references/dotty-foundations-guide.md`.

## Implementation Rules

- Use public dot token IDs in explanations, code comments, and generated specs.
- Use semantic `color.*` tokens for product UI. Do not use raw hex values when a token exists.
- Use approved Dotty text styles and `GT Walsheim Pro` for Dotty typography.
- Use `space.*`, `radius.*`, `borderWidth.*`, `elevation.*`, and motion tokens by semantic role.
- Keep product UI denser and calmer than documentation or marketing layouts unless the prompt explicitly asks for editorial/marketing treatment.
- Avoid nested cards and over-framing. Prefer spacing, dividers, subtle backgrounds, or one clear panel when content belongs to the same decision.
- Do not treat foundation radius, border, or color rules as button, chip, tab, or card component APIs.
- Do not use coral as generic decoration, selected state, label color, or error color. Use it only for approved Omio brand emphasis or explicitly unresolved foundation-only prototype actions.

## Typography Assets

The source package references licensed GT Walsheim Pro font files. This public skill does not include those `.otf` binaries.

- Read `references/fonts/font-assets.md` and `references/data/font-assets.json` for expected font names, weights, styles, and source guidance.
- If a target environment cannot load GT Walsheim Pro, report the fallback as a visual QA caveat.
- Do not commit or redistribute `.otf` font files from private Omio sources into public outputs.

## Data References

- Use `references/data/foundation-token-manifest.json` for token inventory and token metadata.
- Use `references/data/foundation-variable-summary.json` for collection/mode summaries.
- Use `references/data/color-variables.figma.json` when exact exported Figma color variable data is required.
- Use `references/data/font-assets.json` for typography asset metadata.

## QA Checklist

Before finalizing Dotty foundation work:

- Verify every visible UI value maps to an existing foundation token or a documented source-spec dependency.
- Verify color uses semantic product UI tokens rather than primitive/theme/product internals.
- Verify typography uses Dotty text styles and records any font fallback caveat.
- Verify spacing, radius, borders, and elevation are purposeful rather than repeated mechanically.
- Verify no component behavior was invented from foundation guidance.
- Verify generated UI text follows Dotty content guidance when user-facing copy is part of the task.
