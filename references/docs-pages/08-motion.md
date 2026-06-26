# 08 Motion

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=10-9

Motion clarifies feedback, continuity, hierarchy, and state change. It should make the product feel responsive and understandable without becoming decorative or slow.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Motion Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1097-53 | Motion model, principles, and scope. |
| Motion Docs / 02 Duration and easing | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1097-159 | Duration roles, easing roles, animated properties, and token reference. |
| Motion Docs / 03 Motion patterns | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1097-219 | Reusable motion patterns and anatomy. |
| Motion Docs / 04 Applying motion | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1097-284 | Choosing motion by intent and documenting product examples. |
| Motion Docs / 05 Accessibility and performance | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1097-347 | Reduced motion, motion-only meaning, and performance constraints. |
| Motion Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1097-426 | Usage rules, output format, prompt guidance, accessibility/performance, and token output. |

## Duration Tokens

| Token | Value | Use |
| --- | ---: | --- |
| `motion.duration.instant` | 0ms | No animation, reduced-motion fallback, immediate critical feedback. |
| `motion.duration.quick` | 75ms | Tiny feedback or small opacity/color changes when explicitly specified. |
| `motion.duration.standard` | 180ms | Menus, small reveals, common transitions, simple state changes. |
| `motion.duration.emphasized` | 280ms | Modals, drawers, larger surfaces, spatial changes. |
| `motion.duration.expressive` | 500ms | Rare onboarding, celebration, empty-state, or brand moments. |

## Easing Tokens

| Token | Behavior | Use |
| --- | --- | --- |
| `motion.easing.enter` | Ease-out | Elements appearing, opening, or becoming visible. |
| `motion.easing.exit` | Ease-in | Elements leaving, dismissing, or hiding. |
| `motion.easing.move` | Ease-in-out | Repositioning, resize, expand/collapse, and two-way changes. |
| `motion.easing.continuous` | Linear | Progress indicators and continuously moving loaders only. |

## Core Rules

- Motion is an active foundation tool, not disabled.
- Use motion for feedback, state change, loading/progress, reveal/hide, navigation continuity, or spatial relationship.
- Apply motion consistently: the same intent should use the same duration, easing, direction, and reduced-motion fallback across a flow.
- Component-trigger motion such as hover, press, focus, selected, or CTA animation can be suggested as a prototype assumption, but it must be labelled non-final until component specs define the behavior.
- Do not use motion as decoration, delay critical feedback, hide latency, or replace visible text/state.
- Prefer transform and opacity.
- Avoid layout-heavy properties unless a documented pattern needs them and engineering can implement safely.
- Reduced-motion behavior is required.

## AI And Engineering Contract

AI and engineering should output:

- Pattern, such as surface enter/exit or expand/collapse.
- Reason motion is needed.
- Duration token and easing token.
- Animated properties.
- Reduced-motion behavior.
- Performance note.
- Caveat for unresolved triggers, interactions, component behavior, or product-specific context.
