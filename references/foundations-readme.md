# Dotty Foundations

Snapshot date: 2026-05-26

This folder is the clean sendable source-of-truth package for Dotty Foundations. It is for engineers, designers, and AI agents that need to understand or implement the foundation.

Figma is the temporary visual and variable reference while the foundation is still being moved toward online documentation:
https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations

Use this `Foundations/` package as the current foundation contract. Use Figma links when visual layout, swatches, diagrams, or variable inspection matter.

## Read Order

1. `README.md`
2. `AGENTS.md`
3. `Dotty Foundations Guide.md`
4. `docs-pages/README.md`
5. `docs-pages/01-color.md` through `docs-pages/10-layout.md`
6. `data/foundation-token-manifest.json`
7. `data/foundation-variable-summary.json`
8. `data/font-assets.json`

`AGENTS.md` is the export-facing AI and implementation guard. The `docs-pages/` folder contains curated Markdown mirrors of the final Figma docs pages. The `appendices/` folder contains deeper notes for foundations that need more detail than the main guide. The `data/` folder contains machine-readable JSON. The `assets/fonts/` folder contains the licensed GT Walsheim Pro files needed for accurate Dotty typography rendering.

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

## Folder Contents

```text
Dotty Design System/
  Foundations/
    AGENTS.md
    README.md
    Dotty Foundations Guide.md
    docs-pages/
      README.md
      01-color.md
      02-typography.md
      03-spacing.md
      04-radius.md
      05-border.md
      06-elevation.md
      07-icons.md
      08-motion.md
      09-content.md
      10-layout.md
    data/
      foundation-token-manifest.json
      foundation-variable-summary.json
      color-variables.figma.json
      font-assets.json
    assets/
      fonts/
        README.md
        GT-Walsheim-Pro-Regular.otf
        GT-Walsheim-Pro-Medium.otf
        GT-Walsheim-Pro-Bold.otf
        GT-Walsheim-Pro-Regular-Oblique.otf
        GT-Walsheim-Pro-Medium-Oblique.otf
        GT-Walsheim-Pro-Bold-Oblique.otf
    appendices/
      Color Foundation Appendix.md
      Typography Foundation Appendix.md
```

## Important

- AI agents and implementation tools should follow `AGENTS.md` before generating or reviewing output.
- Use public dot token IDs in docs, code references, and AI output.
- Figma slash names are for picker organization only.
- Do not use primitive tokens directly in product UI.
- Do not invent raw values when a Dotty token exists.
- Do not add component tokens during foundation implementation.
- Keep implementation notes and QA summaries outside user-facing UI unless the prompt explicitly asks to render them.
- Load `GT Walsheim Pro` from `assets/fonts/` before typography visual QA.
