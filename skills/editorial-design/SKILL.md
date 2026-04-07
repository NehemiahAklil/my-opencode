---
name: editorial-design
description: Enforce editorial-quality UI standards through prescriptive constraints. Use alongside frontend-design to apply specific anti-patterns, typography rules, and layout disciplines that elevate interfaces beyond generic AI outputs.
license: Complete terms in LICENSE.txt
---

This skill enforces **Digital Editorialism** principles: typography-first design, structural integrity, and intentional aesthetics over decorative crutches.

Use this skill in conjunction with `frontend-design` (for creative direction) to apply specific quality constraints and avoid common AI-generated interface patterns.

## Core Principles

Digital Editorialism prioritizes:
- **Typography over decoration** - Let font weight, size, and spacing create visual hierarchy
- **Structure over styling** - Use alignment and whitespace instead of backgrounds and borders
- **Restraint over excess** - Every element must earn its place

---

## Icon & Card Discipline

### Forbidden Patterns

**No Decorative Icons:** Never use icons as bullet points, list markers, or decorative accents unless they serve a unique functional purpose that text cannot convey.

```html
<!-- BAD: Icon as decoration -->
<div class="feature">
  <i class="icon-check"></i>
  <span>Fast performance</span>
</div>

<!-- GOOD: Typography creates emphasis -->
<div class="feature">
  <span class="feature-text">Fast performance</span>
</div>

<style>
.feature-text {
  font-weight: 600;
  letter-spacing: 0.02em;
}
</style>
```

**Ban "Sticker" UI:** Never place icons inside small, light-colored rounded rectangles. This pattern reads as artificial and derivative.

**Structural Separation:** Replace light-shaded background cards with:
- Whitespace and margin
- 1px borders
- Grid alignment
- Typographic weight shifts

If an element needs visual distinction, use the text itself (weight, size, letter-spacing) rather than a container background.

---

## Punctuation vs. Layout

### The Rule

**Never use punctuation marks (em dashes, en dashes, colons, pipes) as structural separators.**

Punctuation is for sentences, not layouts. Use CSS layout techniques instead.

### Pattern: Label-Value Pairs

```html
<!-- BAD: Dash as separator -->
<div class="row">
  <span>Item One — $10</span>
</div>

<!-- GOOD: Layout creates separation -->
<div class="row">
  <span class="label">Item One</span>
  <span class="value">$10</span>
</div>

<style>
.row {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid #eee;
  padding: 12px 0;
}
.label {
  font-weight: 600;
  letter-spacing: 0.01em;
}
.value {
  font-variant-numeric: tabular-nums;
  color: #666;
}
</style>
```

### Pattern: Key-Value Metadata

```html
<!-- BAD: Colon separator -->
<div class="meta">Status: Active</div>

<!-- GOOD: Layout separation -->
<div class="meta-row">
  <span class="meta-key">Status</span>
  <span class="meta-value">Active</span>
</div>

<style>
.meta-row {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 8px;
}
.meta-key {
  font-size: 0.875em;
  color: #888;
}
.meta-value {
  font-weight: 500;
}
</style>
```

---

## Typography Hierarchy

### Font Pairing Principle

Pair distinctive fonts at opposing visual weights to create tension:

```css
/* Example: Editorial hierarchy */
h1 {
  font-family: 'Playfair Display', serif;
  font-weight: 700;
  font-size: 3.5rem;
  line-height: 1.1;
  letter-spacing: -0.02em;
}

.meta-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
```

### Weight Contrast

Use dramatic weight differences (not incremental):

```css
/* BAD: Similar weights */
.title { font-weight: 500; }
.subtitle { font-weight: 400; }

/* GOOD: Dramatic contrast */
.title { font-weight: 700; }
.subtitle { font-weight: 300; }
```

---

## Color Discipline

### Single Accent Rule

Commit to one dominant accent color. Use it sparingly and intentionally.

```css
:root {
  --bg: #fafafa;
  --fg: #111;
  --muted: #888;
  --accent: #1a1a1a; /* Single accent, used for emphasis only */
}
```

Avoid the "AI Purple" default. If you reach for purple, consider black or a contextually-relevant color instead.

---

## Anti-Patterns Checklist

Before finalizing any interface, verify these patterns are absent:

- [ ] Icons used as bullet points or decorative markers
- [ ] Icons inside pastel/light-shaded rounded containers
- [ ] Em dashes, en dashes, or pipes used as layout separators
- [ ] Purple gradients on white backgrounds (the AI giveaway)
- [ ] Identical padding values across all `div` containers
- [ ] Cookie-cutter pricing cards (identical rounded rectangles in a row)
- [ ] Light-gray background cards where whitespace would suffice

---

## Spacing Precision

### The Precision Rule

Every pixel of spacing must be intentional. Default padding values (`p-4`, `p-6`) indicate lazy spacing.

**Guideline:** If a gap looks "fine," either double it or remove it entirely. Intermediate values rarely feel intentional.

### Invisible Containers

Let alignment create the "box," not background color:

```html
<!-- BAD: Background creates the container -->
<div class="card" style="background: #f5f5f5; padding: 16px;">
  Content
</div>

<!-- GOOD: Whitespace creates the container -->
<section class="content-block">
  <h2>Section Title</h2>
  <p>Content...</p>
</section>

<style>
.content-block {
  margin: 48px 0;
}
.content-block h2 {
  font-size: 1.5rem;
  margin-bottom: 16px;
}
</style>
```

---

## Visual Tension

### Opposing Elements

Create interest by pairing contrasting characteristics:

- **Size:** Massive `h1` next to tiny `caps` label
- **Weight:** 900 weight next to 300 weight
- **Family:** Serif headlines with sans-serif body
- **Case:** ALL CAPS next to lowercase
- **Width:** Condensed text next to wide tracking

```css
.tension-example {
  display: flex;
  align-items: baseline;
  gap: 24px;
}

.tension-example .main {
  font-size: 4rem;
  font-weight: 900;
  letter-spacing: -0.03em;
}

.tension-example .label {
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #888;
}
```

---

## Remember

This skill complements `frontend-design`:
- **frontend-design** provides creative direction and aesthetic exploration
- **editorial-design** provides quality constraints and anti-pattern enforcement

Use both together: explore bold directions with frontend-design, then verify editorial standards are met with this skill.
