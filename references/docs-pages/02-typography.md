# 02 Typography

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-3

Typography creates hierarchy, readable content, and consistent responsive behavior across Dotty product surfaces. Choose text by content purpose first; Desktop and Mobile values resolve through typography variables.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Typography Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=580-2 | Purpose, model, and role map. |
| Typography Docs / 02 Type scale | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=584-2 | Published text styles, visual scale, and weight availability. |
| Typography Docs / 03 Tokens | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=598-2102 | Text style, semantic variable, primitive variable, and mapping boundaries. |
| Typography Docs / 04 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=623-2702 | Applying typography by content role, hierarchy, density, and responsive behavior. |
| Typography Docs / 05 Accessibility | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=623-2851 | Readability, truncation, dynamic content, semantic structure, and QA checks. |
| Typography Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=623-3000 | Usage guidance, selection order, hierarchy roles, output format, and guardrails. |

## Token Architecture

```text
typography primitives -> responsive layout drivers -> semantic typography variables -> text styles
```

- Text styles are the designer-facing entry point.
- Semantic typography variables carry public responsive values.
- `02 Typography / Responsive layout` owns Desktop and Mobile modes.
- Primitive variables hold base font sizes, line heights, weights, family, and letter spacing.
- Font assets live in `../assets/fonts/`; engineering and AI-generated previews must load GT Walsheim Pro before typography visual QA.

## Public Style Roles

| Role | Use for | Weight guidance |
| --- | --- | --- |
| Display | Highest-impact product, brand, or editorial moments. | Bold only. |
| Heading | Page titles, section titles, card titles, and important UI decisions. | Bold only. |
| Subheading | Short labels, compact group headings, metadata labels, and tag-like text. | Regular, Medium, and Bold. |
| Body | Readable content, descriptions, helper text, supporting copy, values, and dense UI text. | Regular by default; Medium or Bold for local emphasis. |

## Core Rules

- Use approved Dotty text styles and token IDs.
- Use GT Walsheim Pro as the Dotty font family.
- Default readable copy uses `text.body.md.regular`.
- Page titles and true high-impact moments can use Display; compact UI should not.
- Section, panel, and card hierarchy should use Heading styles before custom sizes.
- Product UI pretitles and overlines use `text.subheading.sm.medium` as the default 12px caps-style treatment; reserve bold for documentation metadata or deliberately high-emphasis labels.
- Product UI pretitles and overlines should normally use neutral/subtle text color. Do not use coral by default, and do not turn long helper labels into all-caps pretitles.
- Use pretitles and overlines only when they clarify the local page, section, or group role. Do not repeat the same feature name above every screen or card.
- Marketing or editorial pages may use Display scale. Operational product flows should usually use calmer Heading scale so the page reads as a task surface, not a landing page.
- Operational product UI usually needs one strong page title, restrained section/card headings, Body MD reading text, and selective emphasis. Avoid making every value, label, or panel title bold.
- SM and XS are reserved for metadata, captions, compact support text, specs, dense labels, and constrained secondary details.
- Body XS is for short dense metadata and captions, not main reading text.
- Use one public style ID and let Desktop/Mobile values resolve through variables.
- Do not create separate desktop/mobile style names.
- Do not invent font sizes, line heights, weights, or letter spacing.

## AI And Engineering Contract

AI and engineering should return:

- Chosen style ID, such as `text.heading.md.bold`.
- Reason based on content role, hierarchy, importance, density, and responsive behavior.
- Desktop/Mobile behavior through semantic typography variables.
- Implementation tokens such as `typography.body.md.fontSize` and `typography.body.md.lineHeight`.
- Pretitle/overline treatment when the UI uses a section label, including why `text.subheading.sm.medium` with neutral/subtle color is enough or why a stronger approved style is required by a source spec.
- Whether a pretitle is necessary at all; if it repeats a generic flow name or duplicates nearby navigation, omit it.
- Marketing vs operational hierarchy choice when the output includes page titles or large headings.
- Caveats for truncation, accessibility, layout, or unresolved source-spec dependencies.

For deeper typography details, read `../appendices/Typography Foundation Appendix.md`.
