---
name: google-stitch
description: Google Stitch — AI UI design tool (stitch.withgoogle.com). Generate, edit, variant-test, and export UI screens via the Stitch MCP API/SDK. Use for UI screen generation, prompt enhancement, DESIGN.md-based design-system reuse, multi-page Stitch workflows, and HTML/CSS handoff.
---

# Google Stitch Skill

Stitch is Google's AI-native UI design canvas.

Prompt -> high-fidelity UI -> HTML/CSS export.

This public version combines:
- Stitch MCP / SDK usage patterns
- prompt-enhancement ideas
- DESIGN.md design-system reuse
- multi-page workflow patterns

## Core Use Cases

Use Stitch when you want to:
- generate a UI screen from a text prompt
- improve a weak prompt before generation
- iterate on an existing screen with edits or variants
- extract a reusable semantic design system into `DESIGN.md`
- run a multi-page website/app flow screen by screen
- export HTML/CSS for implementation handoff

## Authentication

Use OAuth2 or an API key depending on your environment and access model.
Do not hardcode private credentials into a shared skill.

## MCP Endpoint

`https://stitch.googleapis.com/mcp`

## Core Tools

- `list_projects`
- `get_project`
- `create_project`
- `list_screens`
- `get_screen`
- `generate_screen_from_text`
- `edit_screens`
- `generate_variants`

## Recommended Workflow

### 1. Start with a good prompt

Before generating, improve the prompt.

Specify:
- device type (`MOBILE`, `DESKTOP`, `TABLET`, `AGNOSTIC`)
- page purpose
- atmosphere / visual style
- information hierarchy
- important components
- design-system constraints if they already exist

Read `references/prompt-and-design-patterns.md` for the prompt-enhancement pattern.

### 2. Build or reuse a semantic design system

For multi-screen work, treat `DESIGN.md` as the reusable source of truth.

A good `DESIGN.md` captures:
- visual atmosphere
- color palette with semantic roles
- typography rules
- component styling rules
- layout principles
- a compact generation-oriented design block

Read:
- `references/prompt-and-design-patterns.md`
- `references/design-md-template.md`

### 3. Generate, edit, and variant-test deliberately

Use this sequence:
1. generate one promising screen
2. inspect result
3. use `edit` for targeted changes
4. use `variants` when direction is close but not right
5. export only after direction is stable

### 4. Use a Stitch loop for multi-page builds

For websites/apps with several pages, use an iterative loop:
1. define current page objective
2. load design context (`DESIGN.md`)
3. generate or edit the screen
4. export HTML/image
5. integrate into the site/app
6. decide the next page

If the project benefits from explicit file structure, use the templates in:
- `references/stitch-loop-files.md`

### 5. Hand off to implementation

Typical flow:
1. generate screen via Stitch
2. retrieve HTML export URL
3. download/export HTML
4. hand off HTML to the implementation workflow

## SDK / Agent Usage

If you want SDK-driven flows instead of raw MCP calls, read `references/sdk-and-tooling.md`.

## References

- `references/prompt-and-design-patterns.md`
- `references/design-md-template.md`
- `references/stitch-loop-files.md`
- `references/sdk-and-tooling.md`
