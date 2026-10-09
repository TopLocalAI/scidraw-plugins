---
name: scidraw-onboarding
description: Use when the user has just installed or connected SciDraw AI, asks what SciDraw AI can do, or asks to check that the SciDraw AI connection works. Verifies the connection without spending credits and introduces the tools.
---

# SciDraw AI onboarding

Goal: confirm the connection works and show the user what they can ask for. Never generate an image during onboarding — generation spends the user's credits.

## 1. Check the connection

1. Confirm the `scidraw-ai` MCP tools are loaded: `generate_figure`, `edit_figure`, `convert_figure`, `generate_chart`, `get_job`, `get_credit_balance`. If your host defers tools, search for them before concluding they are missing.
2. Call `get_credit_balance`. It is free. A balance proves sign-in and tool discovery both work.
3. If the server answers 401 or asks for authorization, let the host start its sign-in flow and ask the user to sign in to SciDraw AI in the browser and click **Allow**. Never ask the user to paste a password, token or API key into the chat.
4. If it answers 403, the account cannot use the API yet (unverified email or restricted account). Point the user to https://sci-draw.com/settings and support at the address on https://sci-draw.com/contact.

Report only what you observed. Do not say "connected" unless `get_credit_balance` returned a balance.

## 2. Introduce SciDraw AI (in the user's language)

Keep it short:

- **Scientific illustrations** — graphical abstracts, mechanisms, pathways, labelled diagrams, from a description (2K or 4K, 1–4 images).
- **Edits** — change an existing figure from its image link: colours, labels, layout, style.
- **Charts from data** — CSV or table rows to a journal-style chart.
- **Editable exports** — SVG with editable text or full vectors, PowerPoint, and PNG/PDF/TIFF at 300/600/1000 DPI.

Mention: it uses the same account and credits as the website; the cost of each tool is in its description; failed jobs are refunded; the balance is shown by `get_credit_balance`; plans are at https://sci-draw.com/pricing.

Then offer two or three concrete starting requests that fit what you know about the user's work, for example "Draw a graphical abstract for this abstract" or "Plot this CSV as a grouped bar chart in Nature style".
