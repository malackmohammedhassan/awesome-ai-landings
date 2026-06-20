# AgentOS — Implementation Plan

> This is the bridge between prompt specification and generated code.
> Every dependency, byte, and strategy is declared before any HTML is written.

---

## 1. Library & Dependency Audit

| Dependency | Version | Size (gzip) | Why | Alternative Considered |
|---|---|---|---|---|
| **Three.js** | r152 (CDN) | ~67 KB | Hero 3D scene with agent nodes | CSS-only (wouldn't be premium enough) |
| **Google Fonts — Inter** | 300–800 | ~45 KB | Primary UI typeface | System fonts (not premium enough) |
| **Google Fonts — JetBrains Mono** | 400, 500 | ~15 KB | Code/data elements | System monospace (acceptable fallback) |
| **Total external** | | **~127 KB** | | |

**Dependencies we deliberately exclude:**

| Library | Reason Cut |
|---|---|
| GSAP / ScrollTrigger | 50+ KB for animations we can do with IntersectionObserver + CSS transitions |
| AOS.js | 20 KB for scroll reveals we can do in 15 lines of JS |
| Particles.js / tsParticles | 40+ KB for particle effects Three.js handles natively |
| Font Awesome | 30+ KB for icons we can inline as SVG |
| Bootstrap / Tailwind | Explicitly forbidden by DESIGN_PRINCIPLES.md |
| jQuery | 2026 — no explanation needed |

**Total external payload:** ~127 KB gzipped (3 requests: Three.js, Inter, JetBrains Mono).

---

## 2. Page Architecture

```
index.html
├── <head>
│   ├── Google Fonts preconnect (2 links)
│   ├── <style> — all CSS (~8 KB minified)
│   │   ├── CSS custom properties (color system, typography)
│   │   ├── Global reset & base styles
│   │   ├── Glassmorphism utilities (.glass)
│   │   ├── Navbar (transparent → glass)
│   │   ├── Hero layout + 3D scene container
│   │   ├── Section layouts (problem, platform, features, stats, cta, footer)
│   │   ├── Feature card grid + hover effects
│   │   ├── Stats counters
│   │   ├── CTA form
│   │   ├── Scroll reveal classes (.reveal, .revealed)
│   │   ├── Progress bar
│   │   ├── Responsive breakpoints (1024, 768, 375)
│   │   └── Reduced motion
│   └── viewport + meta tags
│
├── <body>
│   ├── Skip-to-content link
│   ├── <header> — Navbar
│   ├── <main>
│   │   ├── <section id="hero"> + Three.js canvas
│   │   ├── <section id="problem">
│   │   ├── <section id="platform">
│   │   ├── <section id="features">
│   │   ├── <section id="stats">
│   │   ├── <section id="cta">
│   │   └── <footer>
│   └── <script defer src="three.min.js"> + inline <script>
│       ├── Three.js scene setup
│       ├── Agent nodes creation
│       ├── Particle field
│       ├── Animation loop
│       ├── Scroll reveal IntersectionObserver
│       ├── Progress bar
│       ├── Counter animation
│       ├── Navbar scroll handler
│       ├── Resize handler
│       └── WebGL fallback detection
```

---

## 3. File Size Budget

| Component | Target (minified) | Worst Case |
|---|---|---|
| HTML (structure) | 8 KB | 12 KB |
| CSS (in `<style>`) | 8 KB | 12 KB |
| Three.js scene JS (inline) | 12 KB | 16 KB |
| Scroll + interaction JS | 4 KB | 6 KB |
| Total HTML file | **32 KB** | **46 KB** |

**Total page transfer:** ~160 KB (HTML + fonts + Three.js CDN)

| Metric | Target |
|---|---|
| Total page weight | < 200 KB |
| External requests | 3 (Three.js + 2 font files) |
| Time to Interactive (fast 3G) | < 3s |

---

## 4. Three.js Scene Specification (Reduced)

This is where the biggest scope reduction happens.

### Objects

| Element | Count | Details |
|---|---|---|
| Agent nodes | 3 | IcosahedronGeometry(1.2), MeshPhysicalMaterial, colors: primary, secondary, white |
| Wireframe overlays | 3 | Slightly larger, opacity 0.15, matching node colors |
| Particles | ~60 | PointsMaterial, random positions within 6-unit sphere, size 2–5px, opacity 0.2–0.6 |
| Connecting lines | 2–3 | LineBasicMaterial between nodes, opacity 0.3 |

**Removed from original spec:**
- ❌ 200 particles → 60 particles
- ❌ Energy threads (bezier curves) → simple straight lines
- ❌ Particle-to-particle proximity connections → none
- ❌ Camera orbit → removed entirely (scene rotates slightly via CSS perspective on parent, not Three.js)
- ❌ Orb gravitation toward cursor → removed

### Animation

| Element | Animation |
|---|---|
| Node rotation | 0.01 rad/frame on Y axis (constant) |
| Node float | Sinusoidal bounce (±0.15 units, 3s cycle, different phase per node) |
| Particles | Static position (no drift — cheaper) |
| Connecting lines | Subtle opacity pulse (0.2 → 0.5 → 0.2, 4s) |
| Scene scroll fade | Opacity 1→0 as hero scrolls past viewport |

### Mouse Interaction (Simplest Possible)

```
The entire scene container has a CSS transform: perspective(800px) and
rotates slightly (±2deg) on mousemove. The Three.js scene is a child of
this container so it inherits the rotation naturally.

This is a CSS transform on a div — not a Three.js camera operation.
Zero performance cost. Zero JS math for camera orbits.
```

### WebGL Fallback

```javascript
// Check WebGL support
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');
const webglSupported = gl instanceof WebGLRenderingContext;

if (!webglSupported) {
  // Remove Three.js container, show CSS placeholder:
  // 3 floating gradient circles with backdrop-filter blur
  // Slow CSS translateY animation on each
  // The hero still looks premium — just without 3D depth
}
```

---

## 5. Scroll Interaction Strategy

| Feature | Implementation | Lines of JS |
|---|---|---|
| **Section reveals** | IntersectionObserver (1 observer, 1 callback) | ~15 |
| **Progress bar** | Single scroll listener, `transform: scaleX()` | ~8 |
| **Navbar glass** | IntersectionObserver on hero (1 line: `toggle` class) | ~5 |
| **Counters** | 1 observer, `requestAnimationFrame` count-up | ~25 |

**No GSAP. No ScrollTrigger. No AOS.js. All native JS under 60 lines.**

### Implementation Pattern

```javascript
// One observer for all reveals
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('revealed');
      revealObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });
document.querySelectorAll('.reveal').forEach(el => revealObserver.observe(el));

// One listener for progress bar
let ticking = false;
window.addEventListener('scroll', () => {
  if (!ticking) {
    requestAnimationFrame(() => {
      const pct = window.scrollY / (document.body.scrollHeight - window.innerHeight);
      progressBar.style.transform = `scaleX(${Math.min(pct, 1)})`;
      ticking = false;
    });
    ticking = true;
  }
});
```

---

## 6. Performance Strategy

| Principle | Implementation |
|---|---|
| **Critical CSS inlined** | All above-fold styles in `<head>`, no external CSS files |
| **JS deferred** | Three.js loaded via `<script defer>`, inline JS at end of `<body>` |
| **GPU compositing** | Animations use `transform`, `opacity`, `clip-path` only — never `width`, `height`, `top`, `left` |
| **Three.js pixel limit** | `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` — saves GPU on 3x/4x screens |
| **Animation frame throttling** | `requestAnimationFrame` for Three.js (naturally caps at display refresh) |
| **Reduced motion** | `prefers-reduced-motion` media query disables all CSS animations + skips Three.js render loop |
| **No layout thrash** | Read/write separation in scroll handlers (no forced reflows) |
| **Font-display: swap** | Text remains visible during font load (UX > font perfection) |
| **Zero images** | No `<img>` tags — everything is CSS, SVG, or Three.js |

---

## 7. Lighthouse Strategy

| Category | How We Hit 90+ |
|---|---|
| **Performance** | ~160 KB transfer, 3 requests, GPU-composited animations, deferred JS, no render-blocking resources, font-display swap |
| **Accessibility** | Semantic HTML5 landmarks, skip-to-content link, ARIA labels, focus indicators, 4.5:1 contrast ratio, alt text on SVGs, reduced-motion support |
| **Best Practices** | HTTPS-ready (GitHub Pages), no console.log, no eval(), no outdated libraries, images have explicit dimensions (zero images — this is free) |
| **SEO** | `<title>`, `<meta description>`, Open Graph tags, semantic heading hierarchy (h1 → h2 → h3), descriptive link text, structured data-friendly |

---

## 8. Responsive Strategy

| Breakpoint | Layout | Three.js |
|---|---|---|
| >= 1024px | Full desktop — hero split 50/50, 3-col problem grid, 3×2 features, multi-col footer | Full scene with 3 nodes + particles |
| 768–1023px | Tablet — hero stacks vertically, 2-col feature grid, reduced hero padding | Scene container height reduced, same 3 nodes |
| < 768px | Mobile — single column stacked, hamburger nav, hero content above scene | Scene container small (250px height), 3 nodes visible but smaller, particles count reduced to ~30 via JS check |

**Mobile-specific adjustments:**
- All hover effects become tap equivalents
- Card tilt disabled (no hover on mobile)
- No magnetic effects
- Touch targets >= 44px
- CTA buttons full-width

---

## 9. Color & Visual Consistency

All values centralized in CSS custom properties (already defined in prompt.md):

```css
:root {
  --primary: #6C5CE7;
  --primary-light: #A29BFE;
  --secondary: #00CEC9;
  --accent: #FD79A8;
  --bg-primary: #0A0A0F;
  --bg-secondary: #12121A;
  --glass-bg: rgba(255, 255, 255, 0.03);
  --glass-border: rgba(255, 255, 255, 0.08);
  --text-primary: #F0F0F5;
  --text-secondary: #9494A8;
  --gradient-accent: linear-gradient(135deg, var(--primary), var(--secondary));
  --shadow-glow: 0 0 30px rgba(108, 92, 231, 0.3);
}
```

**Glassmorphism utility:**
```css
.glass {
  background: var(--glass-bg);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
}
```

**Icons:** All inline SVGs or Lucide-style path data (no external icon library).
~20 icons max, each ~200 bytes of path data → ~4 KB total inlined in HTML.

---

## 10. Fallback Strategy Summary

| Failure Mode | Fallback |
|---|---|
| WebGL unavailable | CSS gradient spheres + blur, 3 floating circles with CSS animation |
| Three.js CDN fails | `window.onerror` detects module failure → show CSS fallback |
| Google Fonts blocked | `font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif` — system fonts as immediate fallback |
| JavaScript disabled | `<noscript>` tag with message: "Enable JavaScript for the full experience" + static hero image (CSS gradient) |
| prefers-reduced-motion | All animations disabled, content fully visible and functional |
| Touch device (no hover) | All hover effects use `@media (hover: hover)` guard |
| Screen reader | Semantic HTML + ARIA labels + skip-to-content + proper heading hierarchy |

---

## 11. Generation Constraints for the AI

When generating `index.html`:

1. **Single file output** — the HTML file IS the entire page
2. **No build step** — open index.html in browser, it works
3. **No JS modules** — no `type="module"`, no `import` — CDN scripts via `<script>` tags
4. **Three.js via CDN script tag** — `src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"` — loaded synchronously before inline Three.js code
5. **All CSS in one `<style>` block** in `<head>` — no `<link>` except Google Fonts
6. **All custom JS in one `<script>` block** at end of `<body>` — no inline event handlers
7. **Zero console.log** — debug output is automatic rejection
8. **Valid HTML5** — run through validator before delivery
9. **Semantic class scheme** — `agentos-hero`, `agentos-features`, `agentos-cta` — namespaced to avoid collisions if someone copies code

---

## 12. What We Cut vs Original Spec

| Original Spec | Revised Plan | Reason |
|---|---|---|
| 5 orbs | 3 nodes | Same visual impact, less code, fewer GPU draw calls |
| 200 particles | 60 particles | 200 vs 60 looks identical to a visitor |
| Energy threads (Bezier) | Simple straight lines | Bezier curves add ~40 lines of Three.js math for negligible visual gain |
| Camera orbit (JS) | CSS perspective rotation | Same feel, zero JS cost |
| Magnetic buttons | Static hover effects | Magnetic buttons require per-frame mouse tracking — overengineered for a hero CTA |
| Clip-path reveals | Fade-up + translateY | Clip-path animations are heavier to composite and look janky on some browsers |
| GSAP/ScrollTrigger | IntersectionObserver | 50 KB library saved, same result |
| Custom cursor | Removed entirely | Custom cursors feel gimmicky unless perfectly executed — not worth the risk on page #1 |
| Mouse glow follow | Removed | Another per-frame mouse listener that adds complexity without visible quality difference |

**What we kept:** glassmorphism, dark theme, premium typography, 3D hero, scroll reveals, progress bar, counters, responsive, Lighthouse > 90, Single file.

---

## 13. Success Criteria

Before this page is merged:

- [ ] Lighthouse > 90 in all 4 categories (test incognito, no extensions)
- [ ] Zero console errors (open DevTools on load, scroll all sections)
- [ ] 3D scene renders at 60fps (DevTools Performance tab)
- [ ] WebGL fallback renders correctly (test in Safari or disable WebGL in DevTools)
- [ ] All 8 sections visible and readable at 375px width
- [ ] No horizontal scroll at any width
- [ ] All interactive elements have focus states (tab through the page)
- [ ] prefers-reduced-motion enabled → no animations, content fully visible
- [ ] File size < 50 KB (excluding CDN libraries)
- [ ] Page loads without JavaScript (CSS fallback visible, noscript message)

---

## 14. Estimated Line Count

| Component | Lines (approx) |
|---|---|
| HTML structure | ~120 |
| CSS (in `<style>`) | ~350 |
| Three.js scene | ~100 |
| Scroll + interactions | ~60 |
| Counter animation | ~30 |
| Fallback + setup | ~40 |
| **Total** | **~700 lines** |

This is intentionally lean. 700 lines of well-organized code > 2,000 lines of sprawling features.

---

*This plan is part of the Awesome AI Landings repository. It exists to catch architectural problems before code is generated.*
