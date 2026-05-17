---
name: assess-okrs
description: Score and brief assessment of a product OKR set against SVPG / Cagan first principles and Christina Wodtke's Radical Focus mechanics. Returns per-dimension scores (0-100), an overall score, a 2-3 sentence summary, the top 1-2 issues, structural checks, and a health-metrics layer assessment.
mcp:
  server: homeric-skills
  prompt: assess_product_okrs
arguments:
  - name: okr_set
    description: The OKR set to assess. Paste the Objective plus its Key Results, one per line. Include baselines, targets, and measurement sources where you have them.
    required: true
  - name: strategy_context
    description: Optional. The strategic priority this OKR ladders up to. Improves the strategic_alignment score.
    required: false
  - name: health_metrics
    description: Optional. Operational metrics the team tracks alongside this OKR (uptime, latency, churn, NPS, etc.).
    required: false
---

Invoke the `assess_product_okrs` MCP prompt with the supplied arguments.
