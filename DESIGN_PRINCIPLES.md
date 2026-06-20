# Design Principles

> The quality constitution of Awesome AI Landings. Every generated page must pass every rule. No exceptions.

These principles exist to prevent generic, templated, or low-effort outputs. If a design doesn't feel premium, it doesn't land in the repo.

---

## Rule 1: No Templates

No two pages may share the same layout structure, color palette, or visual rhythm.

- Each page must have a unique **composition** (header, hero, section layout)
- Each page must have a unique **color identity**
- Each page must have a unique **typography pairing**
- **No copying** — not even from yourself

A visitor should never feel déjà vu scrolling through two different pages.

---

## Rule 2: Unique Visual Identity

Every page answers: _What makes this brand unforgettable?_

- Define a core visual metaphor (e.g., "floating neural particles" for an AI, "liquid glass" for fintech)
- That metaphor must appear consistently across the hero, sections, and micro-interactions
- No two brands in the same category may use the same metaphor
- The identity must be apparent within the first 3 seconds of page load

---

## Rule 3: Responsive — Desktop + Mobile

Both breakpoints must look intentional, not broken.

| Breakpoint | Target | Behaviour |
|---|---|---|
| >= 1024px | Desktop | Full layout, multi-column, hover effects, parallax depth |
| 768px – 1023px | Tablet | Reflow to 2-column, reduce decorative complexity |
| < 768px | Mobile | Single column, stacked sections, touch-friendly targets (>= 44px) |

- No horizontal scroll on mobile
- Navigation must collapse to hamburger or bottom nav
- Font sizes must scale: at least `clamp()` or media-query-based
- Test the HTML in a real browser before submitting

---

## Rule 4: Lighthouse Score > 90

Every page must score **90+ in all four categories**:

| Metric | Minimum |
|---|---|
| Performance | 90 |
| Accessibility | 90 |
| Best Practices | 90 |
| SEO | 90 |

**Constraints:**
- No render-blocking external resources (unless critical CSS is inlined)
- Images must be optimized or use SVGs / CSS-only graphics
- No unminified JS in production
- Animations must prefer `transform` and `opacity` (GPU-composited properties)
- Total page weight (HTML + CSS + JS + fonts) < 500 KB for image-light pages, < 2 MB for pages with rich visuals

---

## Rule 5: No External Paid Assets

Everything must be free, self-hosted, or from a free CDN.

**Allowed:**
- Google Fonts (subset to the weights used)
- Font Awesome / Phosphor Icons (free tier, subset)
- Three.js / GSAP / Anime.js (CDN)
- Unsplash / Pexels (free stock images — but prefer CSS/SVG/Three.js visuals)
- Heroicons / Lucide icons

**Forbidden:**
- Paid icon sets (FontAwesome Pro, Iconscout Pro)
- Premium stock photography (Shutterstock, Getty)
- Licensed fonts not on Google Fonts
- Any resource that requires attribution as payment (if attribution is required but minimal, it must be in the page footer)

**Preference order for visuals:**
1. Pure CSS (gradients, shapes, blobs) — best
2. SVG (inline or sprite) — good
3. Three.js / WebGL (interactive 3D) — premium
4. Canvas API (particles, effects)
5. Free stock images (only if above aren't suitable)

---

## Rule 6: Must Have Animation

Static pages are not allowed. Every page must include:

**Essential animations (every page):**
- Hero entrance: content fades/slides in on load (staggered by 100–200ms per element)
- Scroll-triggered: at least 3 sections must animate into view (use IntersectionObserver or library equivalent)
- Micro-interaction: hover state changes on buttons, cards, or links (scale, glow, shift)

**Premium animations (at least 2 per page):**
- Parallax scrolling (background moves slower than foreground)
- Reveal animations (clip-path, mask, or blur reveal on scroll)
- Counter/numbers that animate on scroll into view
- Mouse-tracked effects (cursor follower, tilt on cards, spotlight)
- Morphing shapes (SVG path morphing or CSS shape shifts)
- Typewriter / text stagger (headlines that build character-by-character)
- Gradient shift (animated gradient backgrounds that slowly evolve)

**Animation guidelines:**
- Duration: 300–800ms for entrance, 2–6s for continuous
- Easing: `cubic-bezier()` or material-style easing, never `linear`
- Respect `prefers-reduced-motion` — disable all non-essential animations
- Never animate `width`, `height`, `top`, `left` (causes layout thrash) — use transforms

---

## Rule 7: Must Have Scroll Interaction

The page must feel alive as the user scrolls.

**Required:**
- At least one scroll-triggered reveal per section
- Scroll-based progress indicator (progress bar, floating nav highlight, or similar)

**Choose 2+ from:**
- Parallax depth layers (hero image/content moves at different speeds)
- Scroll-driven horizontal section (cards slide in from left/right on scroll)
- Scroll-triggered 3D rotation (a cube, card, or scene rotates as you scroll)
- Sticky sections that pin while content transforms through them
- Scroll-linked opacity/scale transitions (elements fade while scaling through a range)
- Scroll-to-top button (appears after scrolling past hero)

**Implementation:**
- Use `IntersectionObserver` (native) or `ScrollTrigger` (GSAP) or `AOS.js`
- If using a library, keep it lean — no 200 KB behemoths for 3 scroll effects
- Smooth scroll behavior on anchor links: `scroll-behavior: smooth`

---

## Rule 8: Must Feel Premium

"Premium" is subjective but enforced. A premium page:

**Looks:**
- Generous whitespace (padding: 80–120px on sections desktop, 40–60px mobile)
- Refined typography (proper hierarchy, line-height 1.4–1.6, max-width 70ch for body)
- Subtle shadows and depth (box-shadow, backdrop-filter, layered z-index)
- Color harmony (use a cohesive palette: primary, secondary, accent, neutral — not random colors)
- No clutter — every element has purpose

**Feels:**
- Loading state is intentional (skeleton or fade-in, never white flash)
- Everything is smooth (60fps animations, no jank)
- Transitions between sections feel connected (shared color thread, repeating visual motif)
- Micro-interactions reward exploration (hovering feels good)
- The page tells a story — hero → problem → solution → features → proof → call to action

**Doesn't:**
- No default browser styles showing (style all interactive elements)
- No broken layouts at any viewport width
- No placeholder text (Lorem ipsum) — use real copy
- No unstyled scrollbars (custom scrollbar styles or none)
- No console errors

---

## Rule 9: Performance Budget

Hard limits on every page:

| Asset | Limit |
|---|---|
| Total HTML | < 100 KB (minified) |
| Total CSS | < 50 KB (minified, inlined critical CSS) |
| Total JS | < 300 KB (minified, deferred) |
| Total fonts | < 100 KB (subset to used weights) |
| External requests | < 10 |
| Lighthouse Performance | >= 90 |
| Time to Interactive | < 3s on fast 3G |

---

## Rule 10: Accessibility

Every page must be navigable and understandable:

- Semantic HTML (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`)
- Skip-to-content link
- ARIA labels on interactive elements without visible text
- Color contrast ratio >= 4.5:1 for normal text, >= 3:1 for large text
- Focus indicators on all interactive elements
- Alt text on all images
- Tab order follows visual order
- `prefers-reduced-motion` respected

---

## Rule 11: Code Quality

- No inline `style=""` attributes (use `<style>` blocks or CSS files)
- Valid HTML5 (no unclosed tags, no duplicate IDs)
- Valid CSS (no syntax errors)
- No commented-out code blocks
- No console.log / debugging output in production
- Use semantic class names (BEM or utility-first, be consistent)

---

## Rule 12: Prompt Transparency

Every landing page must include a `prompt.md` that:
- Contains the **exact prompt** given to the AI
- Documents any manual edits made after generation
- Lists the AI tool and model used
- Notes any constraints or special instructions

A page without its prompt is not a landing page — it's just an HTML file.

---

## Enforcement

Before a page is merged:
1. Open `index.html` in a real browser
2. Run Lighthouse audit (Incognito, no extensions)
3. Resize to 375px and 1440px — take screenshots
4. Verify animations trigger (slow scroll through entire page)
5. Read the `prompt.md` — is the prompt honest and complete?
6. Check for console errors
7. Confirm no two pages share an identity

**Failing any check → page is rejected. Fix and resubmit.**

---

*These rules exist to protect the quality of this collection. If a rule feels too strict, the rule stays.*
