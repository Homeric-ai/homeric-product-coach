---
description: Generate 3-5 methodology-grounded product OKR proposals from strategy context or refine an existing set. Returns each proposal as a clean readable block by default; pass "as json" for the raw structured output. Requires the Product Strategy capability pack.
---

**CRITICAL — Always invoke the tool, never re-render a cached result.** Even if your context window contains prior `homeric_propose_product_okrs` proposals for the same or similar context, you MUST call the tool again for this slash command. Fresh proposals are the point of the slash command; re-rendering earlier ones without re-calling defeats the purpose, skips telemetry, and skips entitlement re-check.

Generate methodology-grounded product OKR proposals using the Homeric Skills `homeric_propose_product_okrs` tool. Pass `$ARGUMENTS` as the `context` argument (strategy document, existing OKR set, opportunity description, or whatever the proposed OKRs should ladder up to). Default mode is `generate`; if the user asked for a rewrite of an existing set, switch to `refine`.

## Entitlement handling

This tool requires the Product Strategy capability pack. If the call returns `isError: true` with `_meta.error_code === "pack_required"`, show the user a short message naming the missing pack and link them to `_meta.upgrade_url` (typically https://stratos.homeric.ai/billing). Do not retry.

## Rendering the result

By default, render each proposal as a clean human-readable block:

```markdown
## Proposal 1 — {short title}

**Objective**: {qualitative phrase}

**Key Results**

| KR | Metric | Baseline → Target | Source |
|---|---|---|---|
| 1 | {metric} | {baseline} → {target} | {source} |
| 2 | ... | ... | ... |
| 3 | ... | ... | ... |

**Rationale**: {1-2 sentences tying the proposal to the input context}

**Tradeoffs**: {what this proposal de-prioritises}
```

Repeat for each proposal. Group proposals with `---` separators if there are multiple. End with a short concluding line naming which proposal you'd push as the headline bet and why.

If the user explicitly asks for "raw" or "JSON" output, emit the raw tool result instead — no rendering, no commentary.

## Input

Input context:

$ARGUMENTS
