---
name: design-ppt
description: Design, create, revise, and visually validate polished presentations, pitch decks, proposals, reports, keynote-style talks, and slide-based narratives. Use for PPT/PPTX creation or redesign, presentation outlines that must become slides, visual storytelling, slide templates, HTML decks, executive decks, Chinese or bilingual presentations, and any request to make slides look professional, branded, editorial, cinematic, or design-led.
---

# Design PPT

Create presentations as designed visual narratives, not documents broken into rectangles. Use the agent's installed presentation, document, browser, image, and filesystem tools; require no Open Design application, daemon, MCP server, or external design runtime.

## Load the right references

- Always read [references/design-rules.md](references/design-rules.md).
- Read [references/story-and-layouts.md](references/story-and-layouts.md) when planning a new deck or substantially restructuring one.
- Read [references/production-and-qa.md](references/production-and-qa.md) before authoring or exporting files.
- When no native presentation authoring capability exists, copy and adapt [assets/html-deck/index.html](assets/html-deck/index.html). Do not read or copy this asset when native PPTX authoring is available unless an HTML preview was requested.

## Operating contract

1. Inspect all supplied material before proposing slides. Preserve facts, numbers, names, citations, and required sections.
2. Infer audience, objective, viewing context, language, and editability from the request. Ask only when a missing answer would materially change the deck.
3. Produce the requested deliverable, not merely advice or an outline. If the user requests a PPTX, finish and verify a PPTX whenever the environment supports it.
4. Prefer an editable native PPTX for business review and collaboration. Prefer a rendered or image-backed deck only when visual fidelity is explicitly more important than editability. State the tradeoff.
5. Never claim an HTML file, PDF, or folder of images is an editable PPTX.
6. Keep temporary renders and diagnostic files out of the final deliverable directory.

## Workflow

### 1. Distill the brief

Write a compact internal brief containing:

- audience and decision/action sought;
- one-sentence thesis;
- 3–5 supporting arguments;
- required evidence and assets;
- expected slide count or presentation duration;
- chosen visual direction in 3–5 adjectives.

Do not expose this as a long planning document unless requested.

### 2. Build the story spine

Draft a slide map before layout. Give every slide:

- a message title that states the conclusion;
- one job in the narrative;
- one dominant visual form;
- the evidence required to support it.

Remove slides that repeat a point. Split slides that contain two independent conclusions. Follow [references/story-and-layouts.md](references/story-and-layouts.md).

### 3. Lock one design system

Choose and consistently apply:

- one background strategy;
- one display typeface and one body typeface, or a disciplined single-family system;
- one primary text color, one muted text color, and one accent color;
- a spacing unit and page margins;
- image treatment, chart treatment, and shape language.

If the user provides a brand guide, template, website, screenshot, or prior deck, derive actual colors, typography, spacing, and imagery from it. Do not imitate a named brand from memory.

### 4. Author with semantic layouts

Select layouts by communication purpose rather than visual novelty. Use composition, scale, alignment, and whitespace to create hierarchy. Avoid turning every idea into a card.

For each slide:

1. Place the dominant message and visual anchor.
2. Add only the supporting information required to understand it.
3. Align all elements to an intentional grid.
4. Remove decoration that does not clarify hierarchy, sequence, contrast, or meaning.

### 5. Use assets deliberately

- Prefer real product screenshots, supplied photography, diagrams, and defensible charts over generic decoration.
- Generate or source images only when they support the message; preserve provenance when citations matter.
- Never stretch images. Crop intentionally and preserve faces, products, and focal points.
- Represent quantitative claims with proportionally accurate charts. Do not eyeball bar lengths or fabricate data.

### 6. Render and inspect

Render every slide to images or inspect it in a browser/presentation renderer. Check the actual pixels, not only source code or object coordinates.

Perform at least one full-deck pass for:

- overflow, clipping, collisions, and unsafe margins;
- unreadable type and weak contrast;
- inconsistent spacing, colors, strokes, or radii;
- repetitive layouts and monotonous rhythm;
- unsupported claims, missing sources, and broken image links;
- speaker-view versus projected-view legibility.

Fix issues and render again. Follow [references/production-and-qa.md](references/production-and-qa.md).

### 7. Deliver cleanly

Return the final presentation file and, when useful, a PDF preview. Briefly state:

- the file path or link;
- slide count;
- whether the PPTX is editable or image-backed;
- any font, media, or citation caveats.

Do not narrate routine implementation details.

## Non-negotiable visual constraints

- One clear focal point per slide.
- One conclusion per slide; use message titles, not topic labels.
- Use 2–4 meaningful content regions, not a dashboard grid by default.
- Maintain generous outer margins and consistent alignment anchors.
- Use at most one accent color per slide unless data semantics require more.
- Avoid default gradients, glassmorphism, glow, pill-shaped labels, excessive rounded cards, and decorative icons.
- Avoid tiny body text, long centered paragraphs, and full-width dense tables.
- Vary the rhythm across the deck: statement, evidence, comparison, process, image, synthesis.
- Never place content merely to fill empty space. Whitespace is part of the composition.

## Tool and format selection

- If a presentation-specific skill or tool is installed, use it for native PPTX creation and its required render/verification workflow.
- If only office libraries are available, generate native slides with editable text, shapes, charts, and images; render them for QA.
- If no PPTX authoring path exists, produce a self-contained HTML deck from the bundled asset and clearly report the limitation.
- For pixel-perfect export, an image-backed PPTX may be used only with the user's explicit preference or when editability is clearly irrelevant.
