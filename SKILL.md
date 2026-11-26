---
name: lookbook
description: Build one thing in several design styles and show them in a side-by-side gallery where the user rates and comments on each; feedback assembles into copyable JSON for their own AI. Use when the user says "/lookbook", "build this in these styles", "A/B these themes", "show me X as glassmorphism vs swiss vs…", or wants to compare visual styles for the same screen.
license: MIT
compatibility: Claude Code or any agent that can write files. A multiple-choice question tool and a headless browser are optional; the skill falls back without them.
metadata:
  author: Jerry Reinitz
  version: "1.1"
  source: https://github.com/JR91387/lookbook-ai-ux-gallery-skill
---

# /lookbook — same thing, many looks, one gallery

Output: one gallery page. Every style shows the **same content and structure**; only the look changes. The user rates (1–5) and comments on each; the page builds a JSON feedback block with a Copy button.

Files here:
- `styles.md` — the 22-style catalog (definition, feel, example to Google, reference preview), plus a shortlist of 18 more. Read it before the picker.
- `gallery_template.html` — the gallery shell. Copy it; never hand-build the gallery.

## 1. Pin the subject
What is being built (a screen, a landing page, a card, a dashboard)? If the user gave it, use it. If not, ask once. Write a short **content spec**: sections, copy, data, interactions. Every variant uses this spec word for word, so the comparison is fair.

**Use the user's own project material.** Before writing the spec, look for what the project already has and build from it instead of placeholders:
- Visual media: logos, icons, photos, illustrations, screenshots of the current UI, brand or media folders.
- Design sources: theme or token files (CSS variables, Tailwind config, design tokens), style guides, existing pages.
- Documentation: README and docs, project instruction files (`CLAUDE.md`, `AGENTS.md` and similar), and your memory or notes about the user and project, for real product names, copy, audience and data.

Rules: use real copy and real assets where they exist; never invent facts about the product. The same assets and copy go into every variant; the style changes how they're treated, not what they are. Embed images as data: URIs (the gallery must open from disk). Skip anything that looks private or secret (keys, personal data); ask if unsure. List the sources you used in the content spec.

## 2. Pick styles (multi-select question)
Use your environment's question tool (in Claude Code, AskUserQuestion with multiSelect). If there isn't one, give numbered options grouped the same way. Two prompts, grouped as below (tool limit: 4 options per question, 4 questions per prompt).

Round 1
| header | options |
|---|---|
| Soft / 3D | Glassmorphism, Neumorphism, Claymorphism, Ethereal |
| Retro | Y2K Aesthetic, Pixel Art, Synthwave, Cybercore |
| Bold / raw | Neo-Brutalism, Maximalism, Scrapbook, Surrealism |
| Structured | Swiss Design, Minimalism, Bento Grid, Editorial Design |

Round 2
| header | options |
|---|---|
| Ornate | Luxury Typography, Victorian, Bohemian, Wabi-Sabi |
| Wildcards | Cyberpunk, Conceptual Sketch |

- Option `label`: style name. Recommended ones get `⭐ ` in front of the label: 2–4 total across both rounds, picked for this subject and audience. Include one safe pick and one stretch pick.
- Option `description`: one-line definition + feel from `styles.md`. Add the Google example if it fits.
- Question text says ⭐ = recommended for this subject, and that "Other" accepts any style name, including any from the full catalog linked in `styles.md`.
- Fewer than 2 picked: ask again. More than 6: confirm, since every style is a full build.
- A style typed into "Other" that is not in `styles.md`: define it in one line in the gallery card and build it. Do not add it to the catalog without the user's go.
- User wants more choices: offer the 18-style "More styles" shortlist in `styles.md` as a third round (grouped the same way), and say any of the 314 styles at https://chrislemke.github.io/website_designs/ can be typed into "Other".

## 3. Build each variant
- If your environment has an artifact or page-design skill, load it before writing.
- One self-contained HTML fragment per style (its own `<style>`, Google Fonts allowed). It goes into the gallery as a `<template>` and renders in its own iframe, so styles cannot leak into each other.
- Commit to the style fully: the right type, palette, shape, texture and motion. Use the `styles.md` "Build cues" line and, if needed, the reference guide (`designs/<Name>.md` in chrislemke/website_designs) with your web fetch tool.
- Readability holds in every style: body text meets WCAG AA contrast (4.5:1). Neumorphism, Ethereal and Glassmorphism usually fail by default. Fix them inside the style; don't drop the style.
- No external fetch/XHR. Inline images as SVG or data: URIs.

## 4. Assemble the gallery
1. Copy `gallery_template.html` to the output folder as `<subject>_lookbook_v1.html`. Iterations become `_v2`, `_v3`; never overwrite.
2. Fill `LOOKBOOK` in the template's config script (subject, version, content spec summary).
3. For each style add a `<template class="variant" data-style="Name" data-note="one-line definition">…fragment…</template>`.
4. Save the gallery as a standalone HTML file that opens straight from disk (`file://`: no server, relative paths, no ES modules), with `<!doctype html><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">` as the first line. If your environment can publish artifacts or hosted pages, publish it too and give the link.

## 5. Verify before showing
Use a headless browser (e.g. Playwright): open the gallery, screenshot the grid and each variant, and **look at them**. Check that each one reads as its style, that text is readable, and that the rating, comment and Copy controls work. Fix anything wrong, then hand over the link.

## 6. Hand over
Give the link and one line per style (what to notice). Then stop. The user rates in the page and pastes the JSON to whichever AI they use.

## Feedback JSON (built by the page)
```json
{
  "lookbook": "subject", "version": "v1", "date": "YYYY-MM-DD",
  "ranking": ["Style A", "Style B"],
  "styles": [{"style": "Style A", "rating": 5, "comment": "..."}],
  "overall": "...",
  "for_your_ai": "Ratings 1-5, higher is better; unrated = null. Use top-rated styles and comments to direct the next version."
}
```
When the user pastes this JSON back here, build `_v(N+1)` from it: drop low-rated styles, apply the comments, keep ratings visible.
