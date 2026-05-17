---
name: review-okrs
description: Detailed coaching review of a product OKR set. No numeric scoring — walks through what is strong, what is weak, why each is the case, and how to fix the issues, with citations to SVPG/Cagan and Wodtke methodology.
mcp:
  server: homeric-skills
  prompt: review_product_okrs
arguments:
  - name: okr_set
    description: The OKR set to review. Paste the Objective plus its Key Results, one per line.
    required: true
  - name: strategy_context
    description: Optional. The strategic priority this OKR ladders up to. Sharpens the coaching on strategic alignment.
    required: false
---

Invoke the `review_product_okrs` MCP prompt with the supplied arguments.
