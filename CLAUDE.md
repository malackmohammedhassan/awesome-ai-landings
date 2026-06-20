# CLAUDE.md — Awesome AI Landings

## Repository Mission

A curated showcase of premium AI-generated landing pages.

The objective is not quantity — it's creating pages that demonstrate world-class design, interaction, and front-end craftsmanship. Every page should feel worthy of a real product launch or design showcase.

Benchmark: Stripe, Linear, Vercel, Apple, Framer, Webflow award winners.

If a page feels generic, it fails.

---

## Repository Structure

```
categories/
  category-name/
    design-pattern/
      ├── index.html     ← Self-contained landing page
      ├── prompt.md      ← The exact prompt that created it
      ├── preview.png    ← Screenshot at 1440×900
      └── notes.md       ← Design notes, learnings, techniques
```

Categories: `ai-saas/`, `coffee/`, `fashion/`, `automotive/`, `fintech/`, `interactive-3d/`

Folder names are **design patterns** (e.g., `operating-system`, `sneaker-drop`), not company names.

---

## Page Standards

Every page must:
- Have a unique visual identity — no two pages share a layout or color system
- Be responsive — desktop (>=1024px), tablet (768-1023px), mobile (<768px)
- Score Lighthouse > 90 in all four categories
- Include animation — hero entrance + scroll reveals + micro-interactions
- Include a 3D effect — CSS 3D transforms or Three.js
- Feel premium — would you ship this to a client?
- Use zero external paid assets — everything inline or from free CDNs
- Have zero console errors

---

## Technical Stack

- Single self-contained `index.html` — vanilla HTML, CSS, JavaScript
- Inline SVGs for icons (no Lucide/Feather/FontAwesome)
- Three.js (CDN) for WebGL scenes when needed
- Google Fonts (subset to used weights only)
- CSS `clamp()` for responsive typography
- IntersectionObserver for scroll animations
- `prefers-reduced-motion` respected

**Avoid:** React, Next.js, Tailwind, build pipelines, complex dependencies.

---

## The Benchmark Page

The first page — [`categories/ai-saas/operating-system/`](categories/ai-saas/operating-system/) — is the benchmark. It documents the full generation process in its `notes.md`:

```
Prompt → Design Review → Wireframe → Contract → Revise → Generate → Validate
```

Future pages follow a simplified workflow:
```
Prompt → Generate → Validate → notes.md
```

---

## Quality Gate

Before marking a page complete:

- [ ] Responsive (375px + 1440px tested)
- [ ] prompt.md saved
- [ ] preview.png saved
- [ ] notes.md written
- [ ] No console errors
- [ ] Lighthouse > 90
- [ ] Visual identity unique
- [ ] Animations smooth
- [ ] Repository structure correct

---

## Decision Rule

Premium beats complex. Elegant beats clever. Polished beats ambitious.
