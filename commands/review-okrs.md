---
description: Detailed coaching review of a product OKR set — what is strong, what is weak, why, and how to fix. No numeric scoring. Cites SVPG / Cagan and Wodtke methodology. Returns clean markdown for human reading.
---

**CRITICAL — Always invoke the tool, never re-render a cached result.** Even if your context window contains a prior `homeric_review_product_okrs` result for the same or similar OKRs, you MUST call the tool again for this slash command. The slash command exists so the user can request a fresh server-applied coaching review; re-rendering an earlier result without re-calling defeats its purpose, skips telemetry, and may serve stale methodology.

Provide a detailed coaching review of the following product OKR set using the Homeric Skills `homeric_review_product_okrs` tool. Pass `$ARGUMENTS` as the `okr_set` argument. If the user mentioned strategic context inline, pass it as `strategy_context`.

## Rendering the result

The coaching tool returns structured Markdown. Render it directly to the user — keep the section headings the methodology emits, trim any preamble that duplicates the user's input.

If the user explicitly asks for "raw" or "JSON" output, emit the raw tool result instead.

## Input

OKR set to review:

$ARGUMENTS
