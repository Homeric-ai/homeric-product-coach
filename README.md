# Homeric Product Coach

A Claude Code plugin that gives product leaders expert-tuned coaching on their OKRs and product strategy. Backed by Homeric's managed methodology service at [mcp.homeric.ai](https://mcp.homeric.ai).

## What you get

Three slash commands the moment you install:

| Command | What it does |
|---|---|
| `/assess-okrs` | Score an OKR set 0-100 across five dimensions. Identify the 1-2 issues most worth fixing. Free. |
| `/review-okrs` | Detailed coaching review — what is strong, what is weak, why, and how to fix. Free. |
| `/propose-okrs` | Draft 3-5 methodology-grounded OKR proposals. Requires the Product Strategy pack. |

The methodology applied behind every command is grounded in:

- **Marty Cagan** (Silicon Valley Product Group) — *INSPIRED*, *EMPOWERED*, *TRANSFORMED*. First principles for product strategy.
- **Christina Wodtke** — *Radical Focus* (2nd edition). Operational mechanics for OKRs.

The Homeric team has distilled and continuously refines these into a structured rubric the plugin's MCP server applies on every call.

## Install

In Claude Code, install from the plugin marketplace:

```bash
claude /plugin install homeric-ai/homeric-product-coach
```

Or add manually in your `~/.claude/settings.json`:

```json
{
  "plugins": ["homeric-ai/homeric-product-coach"]
}
```

The first time you invoke any of the slash commands, Claude Code will open an OAuth consent page. Sign in with your Homeric account (or create one — free). The plugin then has Bearer-token access to the Homeric Skills MCP service.

## Pricing

| Tier | What's included | Price |
|---|---|---|
| **Free** | `/assess-okrs`, `/review-okrs`, full methodology access via MCP | $0 |
| **Product Strategy** | Adds `/propose-okrs` and proposal-generation tools | $199 / user / month |
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

When you invoke `/assess-okrs`, Claude Code calls the `assess_product_okrs` MCP prompt on the Homeric Skills server. The server returns the methodology bundle and the apply-it instructions; the model then applies it to your OKR set and emits a structured assessment.

## Compatibility

| Client | Status |
|---|---|
| Claude Code | ✅ Native plugin install |
| Claude Desktop | ✅ Works via the MCP connector (add `mcp.homeric.ai/mcp` as an MCP server) |
| Cursor, Windsurf, ChatGPT Dev Mode, Atlassian Rovo | ✅ Add the MCP connector URL manually; the plugin's slash commands are Claude Code-only |

## Privacy

- Your OKR text is sent to `mcp.homeric.ai` to be assessed/reviewed/proposed.
- Each call is logged for billing and quality (per-user activity log).
- No third-party LLM provider sees your input — the methodology is applied by your Claude Code session against the rubric the server returns.
- Full policy: [homeric.ai/privacy](https://homeric.ai/privacy)

## Support

- Issues with the plugin install or MCP connector: file an issue here.
- Questions about the methodology or feature requests: hello@homeric.ai.
- Billing or pack-management: [stratos.homeric.ai](https://stratos.homeric.ai).

## License

The plugin wrapper code (this repo) is Apache 2.0. The methodology served at `mcp.homeric.ai` is proprietary to Homeric AI and licensed under the [Homeric Skills License v1.0](https://homeric.ai/skills/license) — free to use as a methodology consumer, no redistribution rights.
