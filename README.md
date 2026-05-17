# Homeric Product Coach

A Claude Code plugin that gives product leaders expert-tuned coaching on their OKRs and product strategy. Backed by Homeric's managed methodology service at [mcp.homeric.ai](https://mcp.homeric.ai).

## What you get

When this plugin is installed, three slash commands plus a connected MCP server:

| Slash command | What it does |
|---|---|
| `/homeric-product-coach:assess-okrs <okr-set>` | Score an OKR set 0-100 across five dimensions; identify the 1-2 issues most worth fixing. Free. |
| `/homeric-product-coach:review-okrs <okr-set>` | Detailed coaching review — what is strong, weak, why, and how to fix. Free. |
| `/homeric-product-coach:propose-okrs <context>` | Generate 3-5 methodology-grounded OKR proposals. Requires the Product Strategy pack. |

The plugin also registers an MCP server (`homeric-skills`) which exposes the underlying tools (`homeric_assess_product_okrs`, `homeric_review_product_okrs`, `homeric_propose_product_okrs`) and prompts directly. The model can invoke them autonomously when context matches — the slash commands are convenience shortcuts.

The methodology applied behind every call is grounded in:

- **Marty Cagan** (Silicon Valley Product Group) — *INSPIRED*, *EMPOWERED*, *TRANSFORMED*. First principles for product strategy.
- **Christina Wodtke** — *Radical Focus* (2nd edition). Operational mechanics for OKRs.

The Homeric team has distilled and continuously refines these into a structured rubric the MCP server applies on every call.

## Install (local, for testing)

Clone this repo, then point Claude Code at it directly:

```bash
git clone https://github.com/Homeric-ai/homeric-product-coach.git
claude --plugin-dir ./homeric-product-coach
```

The first time you invoke a slash command or the MCP server starts a tool call, Claude Code will open an OAuth consent page. Sign in with your Homeric account (or create one — free).

Once Claude Code is running, type `/help` to see the plugin's commands listed under the `homeric-product-coach:` namespace.

If you make changes to the plugin while Claude Code is running, run `/reload-plugins` to pick them up without restarting.

## Install (from marketplace)

*Coming soon* — the plugin will be available in the official Claude Code marketplace.

## Pricing

| Tier | What's included | Price |
|---|---|---|
| **Free** | `/homeric-product-coach:assess-okrs`, `/homeric-product-coach:review-okrs`, full MCP methodology access | $0 |
| **Product Strategy** | Adds `/homeric-product-coach:propose-okrs` and proposal-generation tools | $199 / user / month |
| **Product Discovery** | (forthcoming) Opportunity prioritization, evidence synthesis, experiment design | $299 / user / month |
| **Product Engineering** | (forthcoming) Spec coaching, telemetry framing, delivery diagnostics | $599 / user / month |

Manage seats at [stratos.homeric.ai/billing](https://stratos.homeric.ai/billing).

## What this plugin is not

This plugin is a thin Claude Code distribution wrapper. It contains no methodology content. Everything the model applies — the rubric, signals, anti-patterns, output schemas — lives in Homeric's managed service and is delivered over MCP at invocation time.

## Architecture

```
Claude Code (this plugin) ──MCP──> mcp.homeric.ai
                                         │
                                         ▼
                                  managed methodology
                                  + entitlements + telemetry
```

When you invoke `/homeric-product-coach:assess-okrs`, Claude Code substitutes `$ARGUMENTS` into the command body and invokes the `homeric_assess_product_okrs` MCP tool. The server returns the methodology bundle and apply-it instructions; the model then applies it to your OKR set and emits a structured assessment.

## Compatibility

| Client | Status |
|---|---|
| Claude Code | ✅ Native plugin install (`--plugin-dir` or marketplace) |
| Claude Desktop | ✅ Works via the raw MCP connector — add `https://mcp.homeric.ai/mcp` as an MCP server in your Claude Desktop config (the slash commands here are Claude Code-only, but the underlying tools are available everywhere) |
| Cursor, Windsurf, ChatGPT Dev Mode, Atlassian Rovo | ✅ Add `https://mcp.homeric.ai/mcp` as an MCP server; tools auto-discover |

## Privacy

- Your OKR text is sent to `mcp.homeric.ai` for the methodology to be applied.
- Each call is logged for billing and quality (per-user activity log).
- The methodology body and your input are processed by your own Claude Code session against the rubric the server returns; no third-party LLM provider intermediates.
- Full policy: [homeric.ai/privacy](https://homeric.ai/privacy)

## Support

- Issues with the plugin install or MCP connector: file an issue here.
- Questions about the methodology or feature requests: hello@homeric.ai.
- Billing or pack-management: [stratos.homeric.ai](https://stratos.homeric.ai).

## License

The plugin wrapper code (this repo) is Apache 2.0. The methodology served at `mcp.homeric.ai` is proprietary to Homeric AI and licensed under the [Homeric Skills License v1.0](https://homeric.ai/skills/license) — free for use as a methodology consumer, no redistribution rights. See [LICENSE](./LICENSE).
