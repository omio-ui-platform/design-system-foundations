# Design System Foundations

Codex and Claude Code skill and reference package for applying Omio Dotty design-system foundations.

This repository helps AI agents, engineers, and designers use the same foundation contract when working with color, typography, spacing, radius, border, elevation, icons, motion, content, and layout.

**Outline**

- [What This Is](#what-this-is)
- [Install For Codex](#install-for-codex)
- [Install For Claude Code](#install-for-claude-code)
- [Lovable Integration](#lovable-integration)
- [Use The References Directly](#use-the-references-directly)
- [Figma Integration](#figma-integration)
- [Photoshop Integration](#photoshop-integration)
- [Illustrator Integration](#illustrator-integration)
- [Other Common Designer Tools](#other-common-designer-tools)
- [Updating The Skill](#updating-the-skill)
- [Public Repo Safety](#public-repo-safety)

## What This Is

This repo is a Codex and Claude Code skill. It is not a Figma plugin, Adobe plugin, component library, or token pipeline by itself.

It contains:

- `SKILL.md` - the runtime skill instructions Codex and Claude Code load. Shared by both agents; keep its frontmatter to `name` and `description` only.
- `agents/openai.yaml` - Codex UI metadata for the skill.
- `agents/claude.yaml` - Claude Code UI metadata for the skill (parity record; Claude Code reads `SKILL.md` frontmatter at runtime).
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

## Install For Claude Code

Claude Code discovers skills from a `skills/` directory. Clone this repo as a skill.

Personal (available in every session, just you). `~/.claude/skills` is not inside another repo, so a plain clone is fine:

```sh
mkdir -p "$HOME/.claude/skills"
git clone git@github.com:omio-ui-platform/design-system-foundations.git \
  "$HOME/.claude/skills/design-system-foundations"
```

Project (committed to a repo so the whole team gets it). Do **not** `git clone` straight into `.claude/skills/` and commit it — a nested `.git` becomes an embedded gitlink with no `.gitmodules`, so a normal clone of the parent repo gives teammates an empty directory. Use one of:

- **Submodule** — stays linked to this repo for updates:

  ```sh
  git submodule add git@github.com:omio-ui-platform/design-system-foundations.git \
    .claude/skills/design-system-foundations
  git commit -m "chore: add design-system-foundations skill (submodule)"
  ```

  Teammates then fetch the files with:

  ```sh
  git submodule update --init --recursive
  ```

  Update to the latest skill version later with `git submodule update --remote .claude/skills/design-system-foundations`.

- **Vendor / copy** — simplest for consumers (a normal clone just works); re-sync manually when the skill changes:

  ```sh
  git clone --depth 1 git@github.com:omio-ui-platform/design-system-foundations.git /tmp/dsf
  mkdir -p .claude/skills/design-system-foundations
  rsync -a --exclude '.git' /tmp/dsf/ .claude/skills/design-system-foundations/
  git add .claude/skills/design-system-foundations
  git commit -m "chore: vendor design-system-foundations skill"
  ```

Claude Code loads `SKILL.md` automatically from its `name`/`description` frontmatter. Invoke it with the slash command, or just describe the task and let it auto-activate:

```text
/design-system-foundations review this checkout screen against Dotty foundations.
```

```text
Use the design-system-foundations skill to map this UI spec to Dotty color, typography, spacing, radius, border, and elevation tokens.
```

```text
Use the design-system-foundations skill to QA this Figma frame for foundation-token mistakes and source-spec gaps.
```

```text
Use the design-system-foundations skill to generate CSS variables from the Dotty foundation token manifest.
```

`SKILL.md` and the `references/` package are shared verbatim with the Codex skill — there is no Claude-specific fork of the foundation contract.

Verify the install by checking the skill file exists:

```sh
test -f "$HOME/.claude/skills/design-system-foundations/SKILL.md"
```

Then start a new Claude Code session and run one of the prompts above. For project installs, use the same check against `.claude/skills/design-system-foundations/SKILL.md` from the project root.

## Lovable Integration

Lovable can use this repository in three practical ways:

1. Import it as a workspace skill for on-demand Dotty foundation work.
2. Add a short Dotty summary to workspace or project knowledge for always-on guardrails.
3. Reference the token data when building a Lovable Enterprise design system project.

Relevant Lovable docs:

- [Skills](https://docs.lovable.dev/features/skills)
- [Knowledge](https://docs.lovable.dev/features/knowledge)
- [Design systems](https://docs.lovable.dev/features/design-systems)
- [GitHub integration](https://docs.lovable.dev/integrations/github)

### Import as a Lovable Skill

Use this when Lovable should apply Dotty foundations only for design-system tasks.

1. In Lovable, open `Settings` -> `Skills`.
2. Choose `Add` -> `Import from GitHub`.
3. Paste this repository URL:

   ```text
   https://github.com/omio-ui-platform/design-system-foundations
   ```

4. Confirm the imported skill name is `design-system-foundations`.
5. Keep automatic use enabled if every Dotty-related request in the workspace should trigger it. Disable automatic use if teams should invoke it manually.

Manual invocation examples:

```text
/design-system-foundations Review this dashboard for Dotty token, spacing, typography, and color mistakes.
```

```text
/design-system-foundations Rework this Lovable page to use Dotty foundations without inventing component behavior.
```

```text
/design-system-foundations Create a QA checklist for this generated page before I publish it.
```

### Add Always-On Lovable Knowledge

Use knowledge for rules that should apply to every Lovable prompt, even when the full skill is not loaded.

Recommended workspace or project knowledge snippet:

```text
Follow Omio Dotty Foundations for UI styling. Use semantic color.*, typography, space.*, radius.*, borderWidth.*, elevation.*, icon, motion, content, and layout tokens. Do not use raw hex values, primitive tokens, invented component tokens, or component behavior unless an owning component spec exists. For detailed Dotty foundation work, use the design-system-foundations skill from https://github.com/omio-ui-platform/design-system-foundations.
```

Keep knowledge short. Put detailed rules in this skill so Lovable loads the larger reference package only when the task needs it.

### Use with Lovable Design Systems

Use Lovable design systems when you have a React component library, installation instructions, and machine-readable schema that should flow into connected Lovable projects. This repository is foundation guidance and token data, not a complete React component library.

Recommended path:

1. Use `references/data/foundation-token-manifest.json` as source material for token schema.
2. Use `references/docs-pages/*.md` as rendered rules for colors, typography, spacing, radius, border, elevation, icons, motion, content, and layout.
3. Keep component catalog, props, variants, examples, installation, and package setup in the separate Lovable design system project.
4. Reference this repo from that design system project's documentation or setup notes.

Do not connect this repo as a full Lovable design system unless a component library and `.lovable` design-system schema are added intentionally.

### Lovable Prompting Pattern

Use Plan mode first for broad UI refactors:

```text
/design-system-foundations In Plan mode, audit this app for Dotty foundation violations. Group findings by color, typography, spacing, layout, and component-spec gaps. Do not edit yet.
```

Then implement small batches:

```text
/design-system-foundations Fix only the color and typography violations on /checkout. Preserve behavior and do not introduce new component variants.
```

Ask Lovable to verify:

```text
/design-system-foundations Verify the updated /checkout page against Dotty foundations and list any remaining token or source-spec gaps.
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

- `SKILL.md` has only `name` and `description` in YAML frontmatter (both Codex and Claude Code accept this; extra frontmatter breaks the Codex loader).
- `name` is `design-system-foundations`.
- `agents/openai.yaml` still points to `$design-system-foundations`.
- `agents/claude.yaml` still references the `design-system-foundations` skill.
- No `.otf`, `.ttf`, `.woff`, or `.woff2` files are included.

## Public Repo Safety

This repo is public. Do not commit:

- licensed font binaries
- private Figma access tokens
- private file-storage or drive links
- product-roadmap details
- unreleased component specs unless explicitly approved for public distribution
