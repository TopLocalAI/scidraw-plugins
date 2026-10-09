---
name: scidraw-export
description: Use when the user wants a SciDraw AI figure as SVG, PowerPoint/PPTX, PDF, TIFF or high-DPI PNG, wants an editable version, or asks which file format a journal or slide deck needs.
---

# Exporting figures with SciDraw AI

Call `convert_figure` with the image URL and a `format`. Each conversion is charged (see the tool description), so pick the right one first:

| The user wants… | Use |
|---|---|
| To edit text and labels in Illustrator, Inkscape or Figma | `svg` with editable text (text becomes real text, the artwork stays an image) |
| Every shape editable — recolour, move, delete parts | `svg` with full vector mode (costs more; very detailed artwork can produce large files) |
| To edit in PowerPoint or Keynote, or present it | `pptx` |
| A journal submission file | `tiff` at 600 DPI is a safe default; 300 for photos/halftones, 1000 for line art if the journal asks |
| A document or preprint | `pdf` |
| A sharper PNG for slides or web | `png` at 300 or 600 |

Notes:

- The DPI choice sets the pixel size of the output (higher DPI = more pixels); check the journal's required width in inches or millimetres if the user mentions one.
- Conversion runs as a job like generation: poll `get_job` with `wait_seconds` if it isn't finished; never re-send `convert_figure` while it runs.
- Give the user the file link and say what they can now edit.
