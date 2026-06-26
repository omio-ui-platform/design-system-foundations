# 07 Icons

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-8

Icons are compact visual symbols for actions, objects, states, navigation, transport, amenities, and support. They make interfaces easier to scan when they are reused consistently, named clearly, and paired with accessible text where meaning is not obvious.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Icon Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1043-7 | Icon purpose, source priority, and scope. |
| Icon Docs / 02 Anatomy and grid | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1043-131 | 24dp canvas, 20dp live area, trim, stroke, and construction tokens. |
| Icon Docs / 03 Library and sources | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1043-192 | Dotty custom icon reuse, Material adaptation, and custom icon request rules. |
| Icon Docs / 04 Naming and SVG rules | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1043-264 | PascalCase naming and SVG export rules. |
| Icon Docs / 05 Applying icons | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1043-333 | Display sizes, color usage, and accessibility. |
| Icon Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1043-415 | Usage decision order, application/accessibility, required output, and restrictions. |

## Construction Model

- Source canvas: 24dp by 24dp.
- Live area: centered 20dp area.
- Trim: 2dp on each side.
- Default stroke: 2dp.
- Default corner radius: 2dp.
- SVG viewBox: `0 0 24 24`.

## Source Priority

1. Reuse a Dotty custom icon.
2. Adapt a Google Material Icons source candidate only when it fits and can be normalized.
3. Request a custom icon only when reuse or adaptation does not satisfy the need.

## Display Size Tokens

| Token | Icon box | Use |
| --- | --- | --- |
| `icon.size.small` | 16 x 16 | Dense support UI, compact metadata, small inline status, and tight labels. |
| `icon.size.medium` | 20 x 20 | Default inline UI icon beside text, row items, filters, inputs, and compact controls. |
| `icon.size.default` | 24 x 24 | Standalone actions, navigation icons, header/page actions, and larger controls. |
| `icon.size.large` | 32 x 32 | Empty states, guidance, documentation, and expressive support visuals. |

## Core Rules

- Use icons only when they clarify action, object, status, navigation, or supporting meaning.
- Pair icon size tokens with `color.icon.*` tokens.
- The size token controls the displayed icon box; component/container/touch target size is separate.
- Use `currentColor`; do not hardcode internal icon colors.
- Do not create size-specific icon variants.
- Do not use Material icons unchanged; adapt and validate against Dotty rules.
- Important status cannot rely on icon shape or color alone; pair with text or accessible labels.

## AI And Engineering Contract

AI and engineering should output:

- Icon name in PascalCase.
- Source: Dotty custom, adapted Material, or custom request.
- Reason and intended meaning.
- Size token and why it fits.
- Color token such as `color.icon.default` or `color.icon.error`.
- Accessibility treatment.
- SVG checklist: 24 viewBox, centered live area, currentColor, fill-rule, render check.
- Caveat for unresolved library or meaning decisions.
