---
description: Score a product OKR set against SVPG / Cagan + Wodtke methodology. Returns per-dimension scores, summary, top issues, structural checks, health-metrics layer. Defaults to a human-readable table; pass "as json" for the raw structured output.
---

**CRITICAL — Always invoke the tool, never re-render a cached result.** Even if your context window contains a prior `homeric_assess_product_okrs` result for the same or similar OKRs, you MUST call the tool again for this slash command. The slash command exists precisely so the user can request a fresh server-applied assessment; re-rendering an earlier JSON without re-calling defeats its purpose, skips telemetry (the call doesn't get logged for billing/audit/regression detection), and may serve stale methodology if the rubric was updated between calls. If you find yourself thinking "I already have this answer," that's the signal to invoke the tool anyway.

Assess the following product OKR set using the Homeric Skills `homeric_assess_product_okrs` tool. Pass `$ARGUMENTS` as the `okr_set` argument. If the user mentioned strategic context inline (e.g., "our strategy is..."), pass it as `strategy_context`. If the user mentioned health metrics tracked alongside, pass them as `health_metrics`.

## Rendering the result

The tool returns canonical JSON. By default, present it to the user as a **markdown table** for human readability:

```markdown
## Assessment — Overall: **{overall_score}/100**

### Per-dimension scores

| Dimension | Score | Band |
|---|---:|---|
| Outcome orientation | {scores.outcome_orientation} | {band-label} |
| Measurability | {scores.measurability} | {band-label} |
| Leading indicators | {scores.leading_indicators} | {band-label} |
| Objective quality | {scores.objective_quality} | {band-label} |
| Strategic alignment | {scores.strategic_alignment} | {band-label} |

### Summary

{summary, as a paragraph}

### Top issues

- {top_issues[0]}
- {top_issues[1]}

### Structural checks

| Check | Result |
|---|---|
| Objective count | {structural_checks.objective_count} ({pass-marker if within focus range}) |
| KRs per Objective | {structural_checks.key_results_per_objective.join(", ")} ({pass-marker if within focus range}) |
| Quarterly cadence | {pass-marker} |

### Health metrics

- **Present**: {pass-marker if present}
- **Appropriate**: {pass-marker if appropriate}
- **Notes**: {health_metrics.notes}
```

Use the band labels from the rubric (Excellent 90-100, Good 70-89, Acceptable 50-69, Weak 30-49, Failing 0-29). Use ✓ / ✗ for pass-markers (or "Yes" / "No" if the user prefers plain text). No emojis beyond those check-marks.

## Switching to JSON output

If the user explicitly asks for "raw", "JSON", "structured", "for ingestion", or similar, emit the raw JSON object from the tool result instead — no table, no commentary. The JSON is the canonical machine-readable form (the Stratos UI consumes it directly).

## Input

OKR set to assess:

$ARGUMENTS
