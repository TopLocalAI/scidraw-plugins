# SciDraw AI plugins

[中文说明](#中文说明)

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

## 中文说明

本仓库是 SciDraw AI 的官方插件包（含远程 MCP 服务与 4 个技能），支持在 Codex 和 Claude Code 中调用；SciDraw AI 的官方网站是 [sci-draw.com](https://sci-draw.com)。

**能做什么**

- 用文字描述生成科研插图
- 绘制机制图、通路图与技术路线图
- 生成图形摘要 / TOC 与神经网络结构图
- 导出 SVG / PPTX 再编辑

**怎么用**

让助手自动安装——粘贴到 Codex：

```
/goal Read https://sci-draw.com/mcp/install.md to install SciDraw AI for Codex and run its first-time setup.
```

或发送到 Claude：

```
Connect the SciDraw AI MCP server at https://sci-draw.com/api/mcp
```

手动安装到 Codex：

```sh
codex plugin marketplace add TopLocalAI/scidraw-plugins --ref main
codex plugin add scidraw-ai@scidraw-marketplace
```

手动安装到 Claude Code：

```
/plugin marketplace add TopLocalAI/scidraw-plugins
/plugin install scidraw-ai@scidraw-plugins
```

在 Claude Code 运行 `/mcp`（或按 Codex 提示登录），在浏览器授权 SciDraw AI 账号即可，无需 API Key。其他 MCP 客户端可将 `https://sci-draw.com/api/mcp` 设为自定义连接器。

**价格**：注册送免费积分；付费 $10/月起（年付），月付 $20；支持支付宝。

**相关链接**：[SciDraw AI 中文页](https://sci-draw.com/zh) · [中文教程与示例](https://sci-draw.cn) · [MCP 指南](https://sci-draw.com/mcp) · [文档](https://sci-draw.com/docs)

## License

MIT
