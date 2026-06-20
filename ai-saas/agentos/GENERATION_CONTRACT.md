# AgentOS — Generation Contract

> **Purpose:** This document defines the exact rules that the generated `index.html` must obey.
> **Status:** Locked — no exceptions without explicit review and contract revision.
> **Authoritative source:** WIREFRAME.md (overrides any conflicting content in prompt.md).
> 
> Every section below is a binding constraint on the code generator.
> Anything not explicitly listed as "Included" is forbidden.

---

## 1. Scope Lock

### Sections — Included (7 total, in order)

| # | Section | Status |
|---|---|---|
| 1 | Navbar (transparent → glass on scroll) | ✅ Required |
| 2 | Hero (full viewport, blended content/scene layout) | ✅ Required |
| 3 | Platform Dashboard (text-left + macOS window mockup) | ✅ Required |
| 4 | Features (3×2 grid, solid cards, custom SVGs) | ✅ Required |
| 5 | Stats (3 centered counters, no glass, no gradient text) | ✅ Required |
| 6 | CTA Waitlist (glass form, OS-consistent copy, full-bleed) | ✅ Required |
| 7 | Footer (3 columns, minimal, no "Legal" section) | ✅ Required |

### Sections — Excluded

| # | Section | Reason |
|---|---|---|
| — | Problem section (3-column pain point grid) | ❌ Forbidden. Removed by AGENTOS_REVIEW. Platform section replaces its narrative role. |
| — | Any section not listed above | ❌ Forbidden. |

### Visual Elements — Included

| Element | Specification | Source (WIREFRAME.md) |
|---|---|---|
| **Hero 3D scene** | OS kernel visualization: 2 concentric TorusGeometry rings + 12 data particles + 2–3 connecting beams | Section 3 |
| **Ring materials** | `MeshBasicMaterial` only — no `MeshPhysicalMaterial`, no `MeshStandardMaterial` | Section 3 |
| **Glass elements (exactly 3)** | Navbar only + Dashboard window only + CTA form container only | Sections 2, 4 |
| **Custom feature icons** | 6 inline SVGs: Kernel (concentric circles), Process (parallel bars), Memory (stacked layers), Shield (geometric), Terminal (bracket + cursor), Deploy (upward arrow) | Section 4 |
| **Trust bar marks** | 3 abstract geometric shapes (CSS-drawn) — no company logos, no text placeholders | Section 2 |
| **Footer columns (3)** | Platform: Features/Integrations/Changelog/Pricing — Developers: Documentation/API/SDKs/Status — Company: About/Blog/Careers/Contact | Section 7 |
| **Badge** | ⚡ "Now in Public Beta" — capsule style with glow | Section 2 |
| **Type scale** | Inter weights 400, 500, 600, 700 + JetBrains Mono 400, 500. **Do NOT load Inter 300 or Inter 800.** | Section 2 (change from original) |

### Visual Elements — Excluded

| Element | Reason |
|---|---|
| Neural network orbs (3 floating IcosahedronGeometry nodes) | ❌ Replaced by OS kernel rings |
| Particle field (> 12 particles in Three.js) | ❌ Max 12 particles in 3D scene |
| Wireframe overlays on geometries | ❌ Removed by AGENTOS_REVIEW |
| Gradient text (`background-clip: text`) on headlines, stats, or any text | ❌ Forbidden. Solid `--text-primary` only. |
| Stock/Lucide/Feather/FontAwesome icons | ❌ Forbidden. Custom SVGs only. |
| Fake company logos in trust bar | ❌ Forbidden. Abstract geometric marks only. |
| Floating orbs/textures beyond the 2 rings + 12 particles | ❌ Forbidden. |
| Page grid helper, starfield, fog, or any background decoration in Three.js scene | ❌ Forbidden. Pure dark background. |
| / "Ready to command your agent fleet?" copy | ❌ Forbidden. OS-consistent copy only. |
| "Product, Docs, Blog" nav labels | ❌ Forbidden. "Platform, Agents, Developers, Changelog" only. |
| "Get Early Access" CTA text | ❌ Forbidden. "Deploy AgentOS" only. |
| 4-column footer (Product/Resources/Company/Legal) | ❌ Forbidden. 3 columns, no "Legal." |
| Any `<img>` tag (zero external images) | ❌ Forbidden. Everything is CSS/SVG/Three.js. |

### Interactions — Included (exactly 8)

| # | Interaction | Specification | Source |
|---|---|---|---|
| A1 | Hero entrance stagger | 1.2s timeline: scene fade-in (0ms), headline slide-up (400ms), subheadline (600ms), CTAs (800ms), trust bar (1000ms) | Section 8 |
| A2 | 3D scene continuous rotation | Outer ring Y 0.004 rad/frame, inner ring X 0.003 + Y 0.006 rad/frame. Particles orbit with rings. | Section 3 |
| A3 | Section scroll reveals | IntersectionObserver, 15% threshold, fade-up translateY(30px → 0), 700ms, `cubic-bezier(0.16, 1, 0.3, 1)` | Section 8 |
| A4 | Counter animation | Stats section in viewport triggers count-up. 2s easeOutCubic via requestAnimationFrame. | Section 8 |
| A5 | Navbar glass transition | Hero exits viewport → navbar bg transparent → glass, 300ms ease | Section 8 |
| A6 | Primary CTA hover | scale(1.02) + box-shadow increase, 200ms ease, CSS transition only | Section 8 |
| A7 | Feature card hover | Border color shift from `rgba(255,255,255,0.06)` → `rgba(108,92,231,0.3)` + bg brighten from `rgba(255,255,255,0.03)` → `rgba(255,255,255,0.05)`, 300ms ease | Section 8 |
| A8 | Nav link underline | Animated underline via `background-size` technique, 300ms ease, CSS-only | Section 8 |

### Interactions — Excluded

| Interaction | Reason |
|---|---|
| Scroll progress bar | ❌ Removed by AGENTOS_REVIEW. Animation is decoration, not storytelling. |
| Scroll-to-top FAB | ❌ Removed. Unnecessary for 7-section single-scroll page. |
| Feature card tilt (CSS 3D rotate) | ❌ Removed. Gimmick factor exceeds value. |
| Feature card lift (translateY) | ❌ Removed. Border color shift is sufficient. |
| Secondary CTA hover effect | ❌ Removed. Cursor change is sufficient for secondary action. |
| Continuous button glow pulse | ❌ Removed. Static CTA with hover effect is more professional. |
| 3D camera orbit (Three.js mouse tracking) | ❌ Removed. CSS perspective rotation on container replaces it. |
| Magnetic buttons | ❌ Forbidden. Per-render-frame mouse tracking is over-engineered. |
| Mouse glow (radial gradient following cursor) | ❌ Forbidden. Decorative, not storytelling. |
| Custom cursor | ❌ Forbidden. When not pixel-perfect, it signals gimmick. |
| Parallax (scroll-driven depth layers) | ❌ Forbidden. Adds scroll listener complexity for marginal depth. |
| Any interaction not listed as Included above | ❌ Forbidden by default. |

---

## 2. Performance Budget

### Hard Limits — Must Not Exceed

| Metric | Budget | Notes |
|---|---|---|
| **Total page weight** | < 200 KB | Sum of HTML + CSS + JS + gzipped external resources |
| **HTML size** | < 35 KB | Single file target |
| **CSS size** | < 15 KB | Inline `<style>` block within `<head>` |
| **JS size (inline)** | < 12 KB | Inline `<script>` at end of `<body>` — no separate JS file |
| **Three.js CDN** | < 70 KB gzipped | r128 from `cdnjs.cloudflare.com` |
| **Google Fonts** | < 25 KB total | Inter (4 weights) + JetBrains Mono (2), subset to latin |
| **External requests** | ≤ 3 | Two Google Fonts URLs + Three.js CDN exactly |
| **3D scene particles** | exactly 12 | In the Three.js scene. No more. |
| **CSS dots in CTA** | exactly 20 | CSS-only, no Three.js, no JS. |
| **Animation types** | exactly 8 | As listed in Scope Lock above. |
| **Glass elements** | exactly 3 | Navbar, dashboard window, CTA form container. |
| **backdrop-filter blur** | ≤ 16px | Never 20px. |

### Performance Must-Haves

| Requirement | Specification |
|---|---|
| **Three.js pixel ratio** | `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` |
| **GPU compositing** | Animations use `transform` and `opacity` only. Never `width`, `height`, `top`, `left`, `margin`, `padding`. |
| **Font loading** | `font-display: swap` on all Google Fonts. Preconnect + crossorigin on font hosts. |
| **Deferred JS** | Inline `<script>` at end of `<body>`. External `<script defer>` for Three.js. |
| **No `<img>` tags** | Zero external images. Everything is CSS, SVG, or Three.js. |
| **No console.log** | Zero debug output in production code. Remove all console statements. |

### Lighthouse Targets

| Category | Minimum Score | Notes |
|---|---|---|
| **Performance** | ≥ 90 | Three.js + Google Fonts will cost 5–10 points. All other areas must be optimal. |
| **Accessibility** | ≥ 95 | Semantic HTML, ARIA labels, focus indicators, skip-to-content link. |
| **Best Practices** | ≥ 95 | HTTPS, no deprecated APIs, no console, no errors. |
| **SEO** | ≥ 95 | Meta tags, semantic structure, viewport meta, lang attribute. |

---

## 3. Quality Requirements

### Must Pass — No Exceptions

| Requirement | Verification Method |
|---|---|
| **Mobile responsive** | Test at 375px, 768px, 1024px, 1440px. Content must be readable and intentional at every width. |
| **No console errors** | Open DevTools console on page load. Zero errors. Zero warnings. |
| **No horizontal scrolling** | At any viewport width from 375px to 1440px. Test with DevTools device emulation. |
| **Lighthouse ≥ 90** | Run Lighthouse in Chrome Incognito. All 4 categories above threshold. |
| **Reduced motion support** | `@media (prefers-reduced-motion: reduce)` disables all animations. Content remains fully visible. All information is available without animation. |
| **Semantic HTML5** | `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`. Valid — no unclosed tags, no duplicate IDs. |
| **Skip-to-content link** | First focusable element: "Skip to main content" that jumps to `<main>`. |
| **Focus indicators** | Every interactive element has a visible `:focus-visible` outline (2px solid primary). |
| **ARIA labels** | Nav links, CTAs, social proof marks, SVG icons (where decorative vs informative). |

### Should Achieve

| Requirement | Guidance |
|---|---|
| **Smooth animations** | No jank, no dropped frames. Use `will-change: transform` on animated elements. |
| **Font appearance** | No flash of invisible text (FOIT). `font-display: swap` ensures text is immediately visible. |
| **Intentional at all widths** | Not just "responsive" — the layout should look **designed** at every breakpoint. No squished text, no orphaned elements, no awkwardly wide containers. |

---

## 4. Visual Requirements

### Must Preserve

| Visual Attribute | Specification |
|---|---|
| **OS metaphor** | "Operating system" language throughout. "Deploy AgentOS." No "fleet," "command," "get started," "sign up." |
| **Signature kernel visualization** | 2 concentric TorusGeometry rings (outer primary #6C5CE7, inner secondary #00CEC9). 12 particles traveling on paths. 2–3 pulsing connecting beams. Pure dark background. |
| **Typography hierarchy** | Inter for UI, JetBrains Mono for data. Use the `clamp()` scale from prompt.md (Inter weights 400, 500, 600, 700 only). Body text max-width: 70ch. |
| **Premium spacing** | Section padding: `clamp(4rem, 8vw, 8rem) vertical`. Horizontal padding: `clamp(1.5rem, 5vw, 4rem)`. Generous whitespace between elements. |
| **Dark theme** | `--bg-primary: #0A0A0F`. Not pure black. Blue-purple tint. All colors from the CSS custom properties palette. |
| **Color system** | Primary #6C5CE7, secondary #00CEC9, accent #FD79A8 (sparingly). Text: #F0F0F5 / #9494A8 / #6B6B80. All gradients subtle. |
| **Custom SVGs (6)** | Kernel icon (concentric circles). Process icon (parallel bars with flow line). Memory icon (stacked horizontal layers). Shield icon (simplified geometric). Terminal icon (angle bracket + cursor). Deploy icon (upward arrow with base). |
| **Glass exclusivity** | Only 3 elements use `backdrop-filter: blur(16px)`. All other cards/panels use solid `--bg-secondary` or `--bg-tertiary`. |
| **Abstract trust marks** | 3 geometric shapes (CSS, no images). Not company logos, not text. |

### Must Avoid

| Visual Pattern | Why |
|---|---|
| 3-column problem/pain grid | The most generic SaaS section pattern. Strictly forbidden. |
| Fifty-fifty hero split (text left, visual right) | Replaced by blended content/scene layout with gradient vignette. |
| Gradient text (`-webkit-background-clip: text`) on any text element | Signals "we needed to make this interesting." Solid text is more premium. |
| Glass on any element beyond the 3 approved | Every-glass = template signal. 3 curated glass elements = intentional design. |
| Neural network visual language (dots + lines) | The page is about AgentOS, not "generic AI." |
| Stock icon sets (Lucide, Feather, FontAwesome, Heroicons) | Templates use these. Custom SVGs cost ~2 KB and signal originality. |
| Tailwind/Bootstrap utility classes or CDN tags | Forbidden by CLAUDE.md and DESIGN_PRINCIPLES.md. |
| Template footer (4-column Product/Resources/Company/Legal) | Replaced by 3 specific columns with no placeholder links. |
| Chart.js, D3, or any data visualization library | Mini metric graph in dashboard must be an inline SVG, not a library. |
| Large decorative background images or patterns | No `<img>` tags. No `url()` backgrounds that reference external files. |

---

## 5. Delivery Requirements

### Output Format

| Requirement | Specification |
|---|---|
| **Single file** | `index.html` — complete, self-contained. |
| **No build step** | Open `index.html` in a browser. That's it. No npm, no bundler, no build command. |
| **No framework** | Zero React, Vue, Svelte, Angular, or any front-end framework. |
| **No Tailwind** | Zero Tailwind CDN, zero Tailwind classes, zero Tailwind config. |
| **No CSS preprocessors** | Pure CSS. No SCSS, Less, PostCSS, styled-components. |
| **GitHub Pages ready** | The file must render correctly when served from `https://malackmohammedhassan.github.io/awesome-ai-landings/ai-saas/agentos/`. Use relative paths only. No path assumptions. |

### Code Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="AgentOS — The operating system for autonomous agents.">
  <title>AgentOS — The OS for Autonomous Agents</title>

  <!-- Preconnect + Google Fonts (2 requests) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="..." rel="stylesheet">

  <style>
    /* CSS custom properties — full design token set */
    /* Reset + base styles */
    /* Navbar */
    /* Hero + 3D container */
    /* Platform dashboard */
    /* Features grid */
    /* Stats */
    /* CTA */
    /* Footer */
    /* Responsive breakpoints */
    /* Reduced motion */
  </style>
</head>
<body>
  <a href="#main" class="skip-link">Skip to main content</a>

  <nav id="navbar">...</nav>

  <main id="main">
    <section id="hero" class="section-reveal">...</section>
    <section id="platform" class="section-reveal">...</section>
    <section id="features" class="section-reveal">...</section>
    <section id="stats" class="section-reveal">...</section>
    <section id="cta" class="section-reveal">...</section>
  </main>

  <footer id="footer">...</footer>

  <!-- Three.js CDN -->
  <script defer src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

  <script>
    // Three.js scene setup (~55 lines)
    // Scroll interactions (IntersectionObserver, navbar, counter)
    // Reduced motion listener
  </script>
</body>
</html>
```

### External Dependencies (Exhaustive)

| Dependency | Version | Source | Size (gzip) |
|---|---|---|---|
| Three.js | r128 | `cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js` | ~67 KB |
| Inter font | v18+ | Google Fonts via `fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700` | ~15 KB |
| JetBrains Mono | v2+ | Google Fonts via `fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500` | ~8 KB |

**No other external dependencies are permitted.**

---

## 6. Acceptance Checklist

This is the review checklist that verifies the generated page after implementation. Every item must pass.

### Structure & Delivery

- [ ] File is `index.html` in `ai-saas/agentos/` (not root, not elsewhere)
- [ ] Opens directly from file system without errors
- [ ] Opens from GitHub Pages URL without errors
- [ ] No build step required
- [ ] Single file, no external CSS/JS files (beyond Three.js + Google Fonts)
- [ ] No `<img>` tags anywhere
- [ ] No Tailwind, Bootstrap, React, or framework CDN scripts

### Section Completeness

- [ ] **7 sections** exist, in order: Navbar, Hero, Platform, Features, Stats, CTA, Footer
- [ ] Problem section does **NOT** exist
- [ ] Navbar has 4 specific links: Platform, Agents, Developers, Changelog
- [ ] Navbar CTA says "Deploy AgentOS" — not "Get Early Access"
- [ ] Hero CTA says "Deploy AgentOS"
- [ ] CTA section headline says "Ready to deploy the operating system?" — not "fleet"
- [ ] Trust bar uses abstract geometric marks (not fake company logos)
- [ ] Feature cards use 6 custom SVGs (not Lucide/Feather)
- [ ] Stats numbers use solid `--text-primary` (no gradient text)
- [ ] Footer has 3 columns (Platform, Developers, Company) — no "Legal"
- [ ] Footer link text is specific (SDKs, Changelog, API Reference) — no "Privacy Policy"

### Visual Fidelity

- [ ] All visual elements match WIREFRAME.md ASCII layouts (desktop, tablet, mobile)
- [ ] Dark theme uses `#0A0A0F` base (not pure black `#000000`)
- [ ] Primary color is `#6C5CE7` (violet-purple)
- [ ] Secondary color is `#00CEC9` (teal-cyan)
- [ ] Glass (`backdrop-filter: blur(16px)`) is used on **exactly 3 elements**: navbar (after scroll), dashboard window, CTA form container
- [ ] No glass on feature cards, stats, footer, or any other element
- [ ] Feature cards use solid `--bg-tertiary` (`#1A1A2E`) with 1px border
- [ ] Hero headline uses solid white text — no `background-clip: text` gradient
- [ ] All text uses Inter (body) and JetBrains Mono (data/code) — correct weights
- [ ] Inter 300 and 800 are **NOT** loaded
- [ ] Typography uses `clamp()` values from the type scale specification
- [ ] Body text max-width is 70ch

### Animation & Interaction

- [ ] **8 animation types** present (no more, no fewer): hero stagger, 3D rotation, scroll reveals, counters, navbar glass, CTA hover, card border hover, nav underline
- [ ] **6 animation types removed**: progress bar, scroll-to-top FAB, card tilt, card lift, secondary CTA hover, button glow pulse
- [ ] Progress bar does **NOT** exist
- [ ] Scroll-to-top FAB does **NOT** exist
- [ ] Magic mouse effects (magnetic buttons, mouse glow) do **NOT** exist
- [ ] Parallax does **NOT** exist
- [ ] Feature cards do **NOT** tilt or lift on hover — only border color shifts
- [ ] Secondary CTA ("Watch Demo") has no hover effect — cursor change only
- [ ] `prefers-reduced-motion` disables all animations without hiding content
- [ ] Scroll reveals use `transform: translateY` + `opacity` only (GPU composited)
- [ ] Counter animation uses `requestAnimationFrame` with easeOutCubic

### 3D Scene (Hero)

- [ ] Scene contains **exactly 2** TorusGeometry rings
- [ ] Outer ring: primary #6C5CE7, `MeshBasicMaterial`, opacity ~0.35, Y rotation 0.004 rad/frame
- [ ] Inner ring: secondary #00CEC9, `MeshBasicMaterial`, opacity ~0.3, X+Y compound rotation
- [ ] No `MeshPhysicalMaterial` or `MeshStandardMaterial` used
- [ ] **Exactly 12** particles traveling along ring paths
- [ ] 2–3 connecting beams with opacity pulse
- [ ] Pure dark background — no grid helper, no starfield, no fog
- [ ] `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` enforced
- [ ] Three.js container uses CSS `perspective` on mousemove (±2deg)
- [ ] WebGL fallback exists: CSS concentric rotating rings + orbiting dots when Three.js fails
- [ ] Scene fades out as hero scrolls past viewport (opacity 1 → 0)

### Responsive Behavior

- [ ] 375px: all content stacks vertically, 3D scene is 200px height, features 1-column, stats 1-column, footer 2-column
- [ ] 768px: hero stacks, features 2-column, stats 3-column, dashboard stacks (text above mockup)
- [ ] 1024px+: full desktop layout as specified
- [ ] No horizontal scroll at any width (375px → 1440px)
- [ ] Touch devices: no hover-dependent content. Taps briefly apply hover state then reset.
- [ ] CSS perspective rotation is not applied on touch devices

### Performance & Quality

- [ ] Lighthouse Performance ≥ 90
- [ ] Lighthouse Accessibility ≥ 95
- [ ] Lighthouse Best Practices ≥ 95
- [ ] Lighthouse SEO ≥ 95
- [ ] Total page weight < 200 KB
- [ ] External requests ≤ 3 (Two Google Fonts + Three.js CDN)
- [ ] Zero console errors
- [ ] Zero console.log / console.warn / console.error statements
- [ ] All animations use only `transform` and `opacity` (no layout-triggering properties)
- [ ] Fonts load with `font-display: swap`
- [ ] Skip-to-content link present and functional
- [ ] `:focus-visible` outline on all interactive elements
- [ ] Semantic HTML5 landmarks present (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`)
- [ ] No duplicate IDs
- [ ] Valid HTML5 (no unclosed tags)

### Originality Checks

- [ ] Page does **NOT** resemble a Tailwind showcase or Tailwind UI component
- [ ] Page does **NOT** use standard SaaS template patterns (no problem grid, no 50/50 hero split, no 4-col footer)
- [ ] Page does **NOT** use AI startup visual clichés (neural network, floating brain, sparkle icons)
- [ ] Page icon set is **NOT** Lucide, Feather, FontAwesome, or Heroicons
- [ ] Page could not be mistaken for a generic "dark SaaS template"
- [ ] The hero 3D scene is specifically an **OS kernel visualization** (rings + data flow), not a generic abstract scene

### Meta

- [ ] GitHub Pages compatible — no absolute URLs, no assumed base path
- [ ] Page title is descriptive and includes "AgentOS"
- [ ] Meta description is present and meaningful
- [ ] Lang attribute is `"en"` on `<html>`

---

## 7. Signature Lock

The generator must preserve this exact signature visual:

> **Two concentric rings (outer primary violet, inner secondary teal) rotating at different speeds on different axes, with 12 luminous data particles traveling along fixed paths and 2–3 brief connecting beams pulsing between rings like processor clock cycles — all on a pure dark background with no grid, no fog, no starfield.**

If the generated page does not contain this specific visualization, the page has failed the contract regardless of other passing items.

---

## 8. Contract Violations

Any of the following constitutes an automatic failure:

| Violation | Severity |
|---|---|
| Any `<img>` tag present | ❌ Critical |
| Tailwind CDN or utility classes detected | ❌ Critical |
| Bootstrap or any framework detected | ❌ Critical |
| Progress bar or scroll-to-top FAB present | ❌ Critical |
| Problem section present | ❌ Critical |
| 3D scene has > 12 particles | ❌ Critical |
| Gradient text on any headline/stats | ❌ Critical |
| Grid helper, starfield, fog in Three.js scene | ❌ Critical |
| Glass on feature cards, stats, or footer | ❌ Moderate |
| Inter 300 or 800 loaded | ❌ Moderate |
| Stock icon set detected (Lucide/Feather) | ❌ Moderate |
| "Get Early Access," "fleet," or "command" in copy | ❌ Moderate |
| 4-column footer with "Legal" | ❌ Moderate |
| Missing WebGL fallback | ❌ Moderate |
| Console errors on page load | ❌ Critical |

---

*This contract is generated from WIREFRAME.md, AGENTOS_REVIEW.md, PLAN.md, prompt.md, and CLAUDE.md. It is the binding specification for the code generator. No deviation is permitted without an explicit contract revision.*
