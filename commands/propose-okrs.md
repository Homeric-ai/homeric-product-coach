---
name: propose-okrs
description: Generate methodology-grounded product OKR proposals from strategy context, an existing goal, or an opportunity description. Supports refine (rewrite an existing set) and generate (from scratch) modes. Returns 3-5 proposed OKRs with rationale tied to the input and notes on tradeoffs. Requires the Product Strategy capability pack.
mcp:
  server: homeric-skills
  prompt: propose_product_okrs
arguments:
  - name: context
    description: Strategy document, existing OKR set, opportunity description, or any context the proposed OKRs should ladder up to.
    required: true
  - name: mode
    description: Either `refine` (rewrite an existing OKR set) or `generate` (draft from scratch). Defaults to `generate`.
    required: false
---

Invoke the `propose_product_okrs` MCP prompt with the supplied arguments.
