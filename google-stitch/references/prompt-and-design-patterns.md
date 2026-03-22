# Google Stitch — Prompt and Design Patterns

## 1. Prompt Enhancement Pattern

Transform vague ideas into structured Stitch prompts.

### Weak
`make me a dashboard`

### Better
```text
A desktop analytics dashboard for a solo founder, clean minimal style, calm but premium atmosphere.

DESIGN SYSTEM (REQUIRED):
- Theme: light, spacious, quiet confidence
- Background: warm off-white (#f8f7f4)
- Primary accent: deep blue (#264653) for key actions
- KPI cards: softly rounded corners, low shadow, strong number hierarchy
- Charts: simple line and bar visuals, restrained color palette

Page Structure:
1. Header with title, date range, and primary CTA
2. KPI row with 4 cards
3. Main chart section with trend line
4. Secondary insights/cards row
5. Footer/help strip with 1 next-step recommendation
```

## 2. DESIGN.md / Semantic Design System Pattern

Use DESIGN.md as the reusable source of truth for future Stitch generations.

A good DESIGN.md should capture:
- project title / id
- visual atmosphere
- color palette + semantic roles
- typography rules
- component styling rules
- layout principles
- a compact "design system notes for generation" section

## 3. Multi-page Stitch Loop Pattern

For websites/apps with multiple screens, use a repeatable loop:
1. Read current task / page objective
2. Read DESIGN.md
3. Generate or edit screen in Stitch
4. Export HTML/image
5. Integrate into the target project
6. Record the next page / next task

## 4. Variants Pattern

When a screen is close but not right, prefer variants over a full reset.

Useful aspects:
- `LAYOUT`
- `COLOR_SCHEME`
- `TEXT_FONT`
- `TEXT_CONTENT`
- `IMAGES`
