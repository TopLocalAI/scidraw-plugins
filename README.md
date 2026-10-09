# SciDraw AI plugins

Use [SciDraw AI](https://sci-draw.com) — publication-ready scientific illustrations, charts and editable figure exports — from your AI assistant. One plugin works in **Codex** (CLI and ChatGPT desktop app) and **Claude Code**.

It bundles:

- the remote MCP server `https://sci-draw.com/api/mcp` (sign in with your SciDraw AI account in the browser — no API key needed), and
- four skills that teach the assistant how to brief, generate, edit, export and chart figures without wasting credits.

Usage spends the credits on your SciDraw AI account at the same prices as the website. Failed jobs are refunded. Plans: https://sci-draw.com/pricing

## Install

**Let your assistant do it** — paste this into Codex:

```
/goal Read https://sci-draw.com/mcp/install.md to install SciDraw AI for Codex and run its first-time setup.
```

or into Claude:

```
Connect the SciDraw AI MCP server at https://sci-draw.com/api/mcp
```

**Codex, by hand**

```sh
codex plugin marketplace add TopLocalAI/scidraw-plugins --ref main
codex plugin add scidraw-ai@scidraw-marketplace
```

**Claude Code, by hand**

```
/plugin marketplace add TopLocalAI/scidraw-plugins
/plugin install scidraw-ai@scidraw-plugins
```

Then run `/mcp` in Claude Code (or follow the sign-in prompt in Codex) and allow SciDraw AI in the browser.

**ChatGPT, Claude.ai, Cursor and other MCP clients** — add the server URL `https://sci-draw.com/api/mcp` as a custom connector. Step-by-step guide: https://sci-draw.com/mcp

## Tools

| Tool | What it does |
|---|---|
| `generate_figure` | Scientific illustration from a description (2K/4K, 1–4 images) |
| `edit_figure` | Change an existing figure from its image URL |
| `convert_figure` | SVG (editable text or full vector), PPTX, PNG, PDF, TIFF |
| `generate_chart` | Journal-style chart from CSV or table rows |
| `get_job` | Status and files of a running job |
| `get_credit_balance` | Your credit balance (free) |

## Layout

```
.agents/plugins/marketplace.json      Codex marketplace
.claude-plugin/marketplace.json       Claude Code marketplace
plugins/scidraw-ai/
  .codex-plugin/plugin.json           Codex manifest
  .claude-plugin/plugin.json          Claude Code manifest
  .mcp.json                           Remote MCP server
  skills/                             Skills shared by both hosts
  assets/icon.png
```

## Support

https://sci-draw.com/contact · Docs: https://sci-draw.com/docs

## License

MIT
