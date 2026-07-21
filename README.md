<div align="center">

# Design PPT

**An agent skill for presentations that look designed—not assembled.**

[English](README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

</div>

![Design PPT — editorial presentation system](assets/readme/hero.png)

Design PPT gives an AI agent a reusable system for turning source material into polished presentations. It combines narrative planning, visual direction, semantic slide layouts, production rules, and render-based QA in a portable `SKILL.md` package.

It does **not** require Open Design, an MCP server, a daemon, or a separate design application.

## What it adds

- **Story before slides** — define the audience, thesis, evidence, and decision before laying out pages.
- **Message titles** — make every slide state a conclusion instead of naming a topic.
- **One design system** — control typography, color, spacing, imagery, charts, and shape language consistently.
- **Purpose-driven layouts** — select statement, evidence, comparison, process, system, portfolio, quote, or table compositions by communication need.
- **Visual guardrails** — reject card grids, tiny text, decorative gradients, pill spam, weak contrast, and other common AI-slide patterns.
- **Render-based QA** — inspect actual slide pixels for clipping, overflow, rhythm, hierarchy, contrast, and consistency.
- **Honest delivery modes** — prefer editable PPTX; flatten slides only when fidelity matters more than editability; use HTML only as a declared fallback.

## Example output

These slides were created in a forward test using only the skill's built-in HTML fallback—no external fonts, images, or presentation service.

| Cover | Comparison | Process |
|:---:|:---:|:---:|
| ![Editorial cover slide](assets/readme/example-cover.png) | ![Comparison slide](assets/readme/example-comparison.png) | ![Process slide](assets/readme/example-process.png) |

## Install

### Ask your agent to install it

This is the recommended path. In Codex, use:

```text
Use $skill-installer to install the skill from
https://github.com/zuomian726/design-ppt
and validate the installation.
```

For another Agent Skills-compatible agent:

```text
Install https://github.com/zuomian726/design-ppt as an Agent Skill.
Place the repository root in your configured skills directory and verify SKILL.md.
```

### Install manually in Codex

```bash
git clone https://github.com/zuomian726/design-ppt.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/design-ppt"
```

Restart Codex or begin a new task so the skill catalog is refreshed.

### Update

```bash
git -C "${CODEX_HOME:-$HOME/.codex}/skills/design-ppt" pull --ff-only
```

## Use

Invoke it explicitly when you want strict design behavior:

```text
Use $design-ppt to turn the attached strategy document into a
12-slide editable executive PPTX. Audience: leadership team.
Visual direction: restrained editorial, high contrast, data-led.
```

```text
Use $design-ppt to redesign this existing deck without changing
the facts. Keep it editable and return the PPTX plus a PDF preview.
```

```text
Use $design-ppt to create a Chinese/English bilingual investor deck.
Use message titles, real charts, and a strong visual rhythm.
```

The skill can also trigger implicitly for requests involving PPT/PPTX creation, deck redesign, pitch decks, executive presentations, keynote-style talks, or HTML decks.

## How it works

```text
Source material
      ↓
Audience + thesis + evidence
      ↓
Slide map with one conclusion per page
      ↓
Typography + color + grid + image system
      ↓
Native PPTX or fixed-canvas HTML production
      ↓
Render → inspect → fix → deliver
```

The agent always reads the core visual rules. It loads story/layout guidance when planning or restructuring a deck, and production/QA guidance before authoring or export. This progressive loading keeps the default context compact.

## Output modes

| Mode | Best for | Editability | Fidelity |
|---|---|---:|---:|
| Native PPTX | Business reviews, collaboration, recurring reports | High | High, viewer-dependent |
| Image-backed PPTX | Keynotes, launch decks, visual handoff | Low | Very high |
| Self-contained HTML | Browser delivery or no PPTX tool available | Source-editable | Very high in browser |

The skill never claims that HTML, PDF, or slide images are an editable PPTX.

## Requirements and compatibility

- An agent that supports Agent Skills / `SKILL.md` directories.
- Optional native presentation tooling for editable PPTX creation.
- Optional browser or presentation renderer for visual QA.
- No required API key, MCP server, daemon, or desktop design application.

The skill is validated and forward-tested with Codex. Other compatible agents can consume the same files, but their presentation and rendering capabilities determine the final output format.

## Repository structure

```text
design-ppt/
├── SKILL.md                         # Trigger and operating workflow
├── agents/openai.yaml              # Codex UI metadata
├── references/
│   ├── design-rules.md             # Visual quality floor
│   ├── story-and-layouts.md         # Narrative and semantic layouts
│   └── production-and-qa.md        # Authoring, rendering, export checks
└── assets/
    ├── html-deck/index.html        # Dependency-free HTML fallback
    └── readme/                     # Repository artwork and examples
```

## Design principles

1. One conclusion and one focal point per slide.
2. Composition and whitespace before containers and decoration.
3. Real evidence before stock icons or visual filler.
4. Consistency across the deck, rhythm across the sequence.
5. Inspect rendered pixels before delivery.
6. Be explicit about editability and export tradeoffs.

## License

[MIT](LICENSE)
