---
name: scidraw-charts
description: Use when the user wants a chart, plot or graph made from data (CSV, spreadsheet rows, a table in the chat) with SciDraw AI, for a paper, thesis or slides.
---

# Charts from data with SciDraw AI

Call `generate_chart` with the data and a prompt. Pass either `data` (CSV text with a header row) or `rows` (JSON objects), never both.

## Before calling

- Use the user's real data only. Never invent, round or fill in values. If the data is in a file you can read, convert it to CSV yourself; keep column names as they are.
- Check that each column has one meaning and one unit, that group/category columns are text and value columns are numbers, and that there are no summary rows mixed into the data.
- If the user hasn't said, ask (once) what to compare and which chart type they expect.

## Options

- `prompt` — what to show: axes, grouping, error bars, titles, label language.
- `chart_types` — leave empty to let SciDraw AI choose, or set the types the user asked for.
- `journal_style` — match the target journal family if the user names one.
- `figure_width` — single or double journal column.
- `color_palette` — colour-blind-safe palettes; pick one if the user mentions accessibility or a journal palette.

## After the call

Poll `get_job` with `wait_seconds` if the job isn't finished; never re-send `generate_chart` while it runs. Show the file link and remind the user to check axis labels, units and values against their data before publishing. To export the chart as SVG, PPTX or a high-DPI TIFF, use the `scidraw-export` skill.
