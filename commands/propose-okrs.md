---
description: Generate 3-5 methodology-grounded product OKR proposals from strategy context or refine an existing set. Requires the Product Strategy capability pack.
---

Generate methodology-grounded product OKR proposals using the Homeric Skills `homeric_propose_product_okrs` tool. Pass `$ARGUMENTS` as the `context` argument (strategy document, existing OKR set, opportunity description, or whatever the proposed OKRs should ladder up to). Default mode is `generate`; if the user asked for a rewrite, switch to `refine`.

This command requires the Product Strategy capability pack. If the call returns `isError: true` with `pack_required`, show the user the upgrade URL from `_meta.upgrade_url` and stop.

Input context:

$ARGUMENTS
