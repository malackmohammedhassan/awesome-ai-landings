# Design Principles

> The quality constitution of Awesome AI Landings. Every generated page must pass. No exceptions.

These principles exist to prevent generic, templated, or low-effort outputs. If a design doesn't feel premium, it doesn't land in the repo.

---

## Rule 1: No Templates

No two pages may share the same layout structure, color palette, or visual rhythm.

- Each page must have a unique composition, color identity, and typography pairing
- **No copying** — not even from yourself

A visitor should never feel déjà vu scrolling through two different pages.

---

## Rule 2: Unique Visual Identity

Every page answers: _What makes this design unforgettable?_

- Define a core visual metaphor (e.g., OS kernel rings, autonomous city, lava flow)
- That metaphor must appear consistently across hero, sections, and micro-interactions
- No two pages in the same category may use the same metaphor
- The identity must be apparent within the first 3 seconds of page load

---

## Rule 3: Responsive — Desktop + Mobile

Both breakpoints must look intentional, not broken.

| Breakpoint | Target | Behaviour |
|---|---|---|
| >= 1024px | Desktop | Full layout, multi-column, hover effects |
| 768–1023px | Tablet | Reflow to 2-column |
| < 768px | Mobile | Single column, touch targets >= 44px |

- No horizontal scroll on mobile
- Navigation collapses to hamburger
- Font sizes use `clamp()` or media queries
- Test in a real browser before submitting

---

## Rule 4: Lighthouse Score > 90

Every page must score **90+ in all four categories**: Performance, Accessibility, Best Practices, SEO.

**Constraints:**
- No render-blocking external resources
- Animations use `transform` and `opacity` only (GPU-composited)
- Total page weight < 500 KB (gzipped HTML + CSS + JS + fonts)

---

## Rule 5: No External Paid Assets

Everything must be free or from a free CDN.

**Allowed:** Google Fonts, Three.js, free icon SVGs (inline only), procedural CSS/SVG graphics

**Forbidden:** Paid icon sets, premium stock photography, licensed fonts, any resource requiring attribution

**Preference order for visuals:**
1. Pure CSS — best
2. Inline SVG — good
3. Three.js/WebGL — premium
4. Canvas API — acceptable

---

## Rule 6: Animation

Static pages are not allowed. Every page must include:

- **Hero entrance** — content staggers in on load (100–200ms per element)
- **Scroll-triggered reveals** — at least 3 sections animate into view via IntersectionObserver
- **Micro-interactions** — hover states on buttons, cards, or links

**Animation guidelines:**
- Duration: 300–800ms for entrance, 2–6s for continuous
- Easing: `cubic-bezier()` or material-style, never `linear`
- Respect `prefers-reduced-motion` — disable non-essential animations
- Never animate `width`, `height`, `top`, `left` — use `transform` and `opacity`

---

## Rule 7: Must Feel Premium

**Looks:**
- Generous whitespace (80–120px section padding desktop, 40–60px mobile)
- Refined typography (hierarchy, line-height 1.4–1.6, max-width 70ch body)
- Subtle depth (box-shadow, backdrop-filter, layered z-index)
- Color harmony (cohesive palette: primary, secondary, accent, neutral)
- No clutter — every element has purpose

**Feels:**
- Smooth (60fps animations, no jank)
- Transitions feel connected (shared color thread, repeating visual motif)
- The page tells a story — identity → detail → proof → action

**Doesn't:**
- No default browser styles (style all interactive elements)
- No broken layouts at any viewport
- No placeholder text — use real copy
- No console errors

---

## Rule 8: Performance Budget

| Asset | Limit |
|---|---|
| Total HTML | < 100 KB |
| Total external requests | < 10 |
| Lighthouse Performance | >= 90 |
| Time to Interactive | < 3s on fast 3G |

---

## Rule 9: Prompt Transparency

Every page must include a `prompt.md` that:
- Contains the **exact prompt** given to the AI
- Documents any manual edits after generation
- Lists the AI tool and model used

A page without its prompt is not a landing page — it's just an HTML file.

---

## Rule 10: Page Structure

Every page folder contains exactly:

```
index.html     ← The generated page. Self-contained, single file.
prompt.md      ← The exact prompt that created it.
preview.png    ← Screenshot at 1440×900.
notes.md       ← Design notes, learnings, what to steal.
```

No additional process documents per page. The benchmark page (Operating System) is the exception — its `notes.md` documents the full process as a reference.

---

## Enforcement

Before a page is marked complete:
1. Open `index.html` in a real browser — zero console errors
2. Run Lighthouse (Incognito, no extensions) — all > 90
3. Resize to 375px and 1440px — no layout breaks
4. Verify animations trigger on scroll
5. Read the `prompt.md` — is the prompt honest and complete?
6. Confirm no two pages share an identity

**Failing any check → page is rejected. Fix and resubmit.**

---

*These rules exist to protect the quality of this collection. If a rule feels too strict, the rule stays.*
