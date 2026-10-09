---
name: scidraw-figures
description: Use when the user asks SciDraw AI to draw, generate, create or edit a scientific figure, illustration, graphical abstract, mechanism, pathway, schematic or diagram, or to change an existing SciDraw AI image.
---

# Scientific figures with SciDraw AI

## Before calling a tool

Every successful call spends credits, so get the brief right first. If the request is vague, ask at most one round of questions, covering only what is missing:

- **Content** — the entities, steps or relationships to show, and what goes at the visual centre.
- **Labels** — which labels, and in which language (default: the language of the user's paper or request).
- **Style** — flat, line art, 3D, hand-drawn; colour constraints (journal palette, colour-blind safe).
- **Format** — aspect ratio (1:1 default, 16:9 or 4:3 for slides, wide for graphical abstracts), 2K or 4K (4K costs more; 2K is enough for screens and most submissions), and how many variants (1–4; each one is charged).

If the user pasted an abstract, methods or results, turn them into a clear visual brief yourself and confirm it in one or two sentences before generating.

## Writing the prompt

Describe the figure like a brief to an illustrator: layout (left to right, panels), each element and its label text, arrows and what they mean, background, palette. Put exact label text in quotes. Avoid asking for long paragraphs of text inside the image.

## Generating

1. Call `generate_figure` with `prompt`, `size`, `aspect_ratio` and `count`.
2. The call waits up to about 50 seconds. If it returns a `job_id` with a non-final status, call `get_job` with `wait_seconds` up to 50 until it is `succeeded` or `failed`.
3. **Never call `generate_figure` or `edit_figure` again to "retry" a job that is still running** — that starts a second paid job. Poll `get_job` instead.
4. On success, show the file links (and the preview image if your host displays it). Tell the user to check labels, structures and values for scientific accuracy before publishing.
5. On failure, report the error text. Failed jobs are refunded automatically. Ask before trying again with a changed prompt.

## Editing

To change a figure, call `edit_figure` with the figure's image URL (from a previous result or a public link the user gives you) and a prompt that states only the change ("make the arrows thicker and label them 'secretion'", "switch to a green-purple palette"). Keep each edit to one or two changes; several small edits work better than one large one.

## Costs

The credit cost of each tool is stated in its description. If the user is low on credits, `get_credit_balance` returns a `buy_credits_url`. Don't quote prices from memory.

Users can also continue in the web app: https://sci-draw.com/ai-drawing
