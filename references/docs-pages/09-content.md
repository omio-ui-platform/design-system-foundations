# 09 Content

Snapshot date: 2026-05-26

Figma page: https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1006-2

Content is part of the product experience. It helps people understand what is happening, decide what to do next, and trust that Omio is guiding them clearly.

## Final Figma Boards

| Board | Figma link | What it covers |
| --- | --- | --- |
| Content Docs / 01 Overview | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1006-3 | Foundation purpose, model, principles, and scope boundaries. |
| Content Docs / 02 Voice and tone | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1006-115 | Voice traits, tone boundaries, tone by context, and examples. |
| Content Docs / 03 Language and grammar | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1006-246 | String rules, date/time, and localization-ready writing. |
| Content Docs / 04 Terminology and glossary | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1006-354 | Core Omio terms and common term decisions. |
| Content Docs / 05 Component content | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1006-478 | Component copy patterns and foundation-level copy rules. |
| Content Docs / 06 Usage | https://www.figma.com/design/WSSIyMUfJz9BsiVx5ocIL9/Dotty-Foundations?node-id=1006-582 | Usage rules, prompt inputs, request shape, required output, and review caveats. |

## Core Model

Use this sequence for product UI, documentation, and AI-generated content:

1. Structure information before writing.
2. Choose voice and tone for the user state and risk.
3. Use approved Omio terminology.
4. Apply string, grammar, localization, and accessibility rules.
5. Review clarity, facts, and context before shipping.

## Voice

Dotty content should be:

- Straightforward.
- Concise.
- Conversational.
- Helpful.
- Positive.

Avoid wording that is jokey, salesy, overly casual, overly formal, robotic, or sycophantic.

## Core Writing Rules

- Use sentence case for UI labels, headings, and messages unless a proper noun or acronym requires otherwise.
- Use numerals for quantities, prices, seats, bags, and time-related values.
- Use the Oxford comma when listing three or more items.
- Use natural contractions when they sound clear and conversational.
- Keep each UI string self-contained; do not split one sentence across multiple elements.
- Avoid idioms, slang, wordplay, and ambiguous variables.
- Use periods for complete sentences.
- Use exclamation marks sparingly.
- Do not use emojis in product UI.
- Do not rely on truncation for essential information.

## Terminology Rules

- Use `trip` for the broader travel plan.
- Use `journey` for one transport booking through Omio.
- Use `leg` for one continuous ride or flight with no vehicle change.
- Use `booking` for all tickets bought together with one payment.
- Use `passenger` for the person travelling.
- Use `bag`, not baggage/luggage, in product UI.
- Use `extras`, not ancillaries.

## AI And Engineering Contract

AI can help write product content, but it must:

- Use Omio voice and glossary terms.
- Apply string rules and localization-safe variables.
- Ask for missing legal, provider, product, or localization context.
- Avoid inventing product terms, provider facts, legal claims, discount claims, translations, or approved terminology.
- Return purpose, suggested copy, tone/context, glossary terms, localization note, accessibility/readability note, and caveats.

There is intentionally no `09 Content` variable collection. Content is guidance, not a token collection.
