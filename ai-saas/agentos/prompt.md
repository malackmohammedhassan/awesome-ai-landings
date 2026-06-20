# AgentOS — Prompt Specification (Revised)

> **This is the benchmark page for the entire Awesome AI Landings repository.**
> Every parameter below has been updated per AGENTOS_REVIEW.md, WIREFRAME.md, and GENERATION_CONTRACT.md.
> The quality of everything that follows is defined by what this page achieves.
> Future users must be able to reproduce this landing page from this prompt.

---

## AI Tool

This prompt is designed for any frontier model with strong CSS/JS/Three.js generation capability. The stack is vanilla HTML, CSS, and JS with Three.js via CDN.

---

## Category

AI SaaS — Agent infrastructure platform

---

## Role

You are a senior product designer and front-end engineer at a top-tier design agency. You specialize in premium, original SaaS landing pages. You combine mastery of visual design (typography, color, composition, motion) with expert front-end engineering (CSS, JavaScript, Three.js). You have shipped production landing pages for Stripe, Linear, and Vercel. You never use templates, never use Tailwind/Bootstrap, and never rely on stock assets. Every design you create is original.

---

## Audience

- AI engineers and CTOs evaluating agent infrastructure platforms
- Technical founders building agent-based products
- Enterprise decision-makers researching AI orchestration tools
- Developers tired of stitching together 15 tools to manage a single agent

They are technically sophisticated (inspect animations, check console, resize windows), visually literate (bored by SaaS templates), attention-scarce (3 seconds to prove difference), and quality-sensitive (a broken hover erases trust).

---

## Brand

| Attribute | Value |
|---|---|
| **Name** | AgentOS |
| **Tagline** | "The operating system for autonomous agents" |
| **Archetype** | Magician + Creator |
| **Personality** | Visionary, precise, ambitious, futuristic, trustworthy |
| **Voice** | Confident, technical, grounded. OS-consistent language throughout. No "fleet," "command," or "get started." |
| **Core promise** | One platform to design, deploy, and orchestrate AI agents at scale. One OS for autonomous intelligence. |

---

## Visual Style

| Attribute | Value |
|---|---|
| **Style** | Futuristic, architectural, cyberpunk-lite with selective glassmorphism |
| **Core metaphor** | An operating system kernel visualized in 3D — precision, structure, organized data flow. Not a neural network. Not generic AI. |
| **Texture / feel** | Smooth dark surfaces, selective glass panels, organized data visualization. OS-level precision. Architectural. |
| **Key visual motif** | Two concentric rotating rings (violet + teal) with data particles traveling along fixed paths — an OS kernel visualization in Three.js |
| **Inspirations** | macOS window system, x86 protection rings (Ring 0 / Ring 3), Windows Fluent Design, Linear's dark theme, Stripe's documentation aesthetic |

**Critical: This page MUST NOT look like a generic AI startup template. No neural network visuals, no floating orbs with connecting lines, no brain/sparkle icons. The visual language is architectural and structured, not organic and flowing.**

---

## Color System

```css
:root {
  --primary: #6C5CE7;
  --primary-light: #A29BFE;
  --primary-dark: #4834D4;
  --secondary: #00CEC9;
  --accent: #FD79A8;

  --bg-primary: #0A0A0F;
  --bg-secondary: #12121A;
  --bg-tertiary: #1A1A2E;

  --glass-bg: rgba(255, 255, 255, 0.03);
  --glass-border: rgba(255, 255, 255, 0.08);
  --glass-hover: rgba(255, 255, 255, 0.06);
  --glass-blur: 16px;

  --text-primary: #F0F0F5;
  --text-secondary: #9494A8;
  --text-tertiary: #6B6B80;

  --gradient-cta: linear-gradient(135deg, #6C5CE7, #8B5CF6);
  --gradient-hero: linear-gradient(135deg, #0A0A0F 0%, #1A1A2E 40%, #0A0A0F 100%);

  --shadow-sm: 0 2px 8px rgba(0,0,0,0.3);
  --shadow-md: 0 8px 32px rgba(0,0,0,0.4);
  --shadow-lg: 0 16px 48px rgba(0,0,0,0.5);
  --shadow-glow: 0 0 30px rgba(108,92,231,0.3);
}
```

Do NOT use gradient text (`background-clip: text`) on any text element. All text is solid `--text-primary`.

---

## Typography

| Property | Value |
|---|---|
| **Primary font** | Inter (Google Fonts) |
| **Weights used** | 400, 500, 600, 700 — do NOT load 300 or 800 |
| **Monospace font** | JetBrains Mono (Google Fonts) |
| **Monospace weights** | 400, 500 — for data displays, metrics |

Type scale:

| Token | Size | Weight | Line Height | Usage |
|---|---|---|---|---|
| `--text-hero` | clamp(2.5rem, 5vw, 4.5rem) | 700 | 1.08 | Hero headline |
| `--text-h1` | clamp(2rem, 3.5vw, 3rem) | 600 | 1.15 | Section headlines |
| `--text-h2` | clamp(1.5rem, 2.5vw, 2rem) | 600 | 1.2 | Sub-section titles |
| `--text-h3` | clamp(1.125rem, 1.5vw, 1.375rem) | 600 | 1.25 | Card titles |
| `--text-body` | clamp(1rem, 1.25vw, 1.125rem) | 400 | 1.6 | Body copy |
| `--text-small` | 0.875rem | 400 | 1.5 | Captions, meta |
| `--text-mono` | 0.875rem | 400 | 1.5 | Code, data |

Body text max-width: 70ch.

---

## Layout — 7 Sections (no Problem section)

```
┌──────────────────────────────────────────────────┐
│ NAVBAR (transparent → glass on scroll)           │
│  [▣ AgentOS]  Platform  Agents  Developers  Changelog  [Deploy AgentOS ▸]
├──────────────────────────────────────────────────┤
│ HERO — full viewport, blended layout             │
│  Content left (~40% width), 3D scene as background│
│  Gradient vignette masks transition between     │
│  content and scene. No hard 50/50 split.        │
├──────────────────────────────────────────────────┤
│ PLATFORM — text (40%) + dashboard mockup (60%)  │
│  macOS-style window with AgentOS UI             │
│  Glass window frame (one of 3 glass elements)   │
├──────────────────────────────────────────────────┤
│ FEATURES — 3×2 grid of solid cards              │
│  6 custom SVG icons (OS-metaphor, not Lucide)   │
│  No glass. No hover lift. No tilt.              │
├──────────────────────────────────────────────────┤
│ STATS — 3 centered counters                     │
│  Solid text (no gradients). No glass.           │
├──────────────────────────────────────────────────┤
│ CTA WAITLIST — full-bleed with CSS particles    │
│  Glass form container (one of 3 glass elements) │
│  "Deploy AgentOS" — OS-consistent copy          │
├──────────────────────────────────────────────────┤
│ FOOTER — minimal, 3 columns                     │
│  No "Legal" section. No placeholder links.      │
│  Platform | Developers | Company                │
└──────────────────────────────────────────────────┘
```

Grid system: CSS Grid for section-level layout, Flexbox for component-level arrangement.

Breakpoints:
- >= 1024px: Full desktop
- 768–1023px: Tablet — hero stacks (scene below content), features 2-column, dashboard stacks
- < 768px: Mobile — fully stacked single column, hamburger nav, 3D scene 200px height

Section padding: `clamp(4rem, 6vw, 7rem) vertical`, `clamp(1.5rem, 5vw, 4rem) horizontal`.

Max content width: 1200px, centered.

---

## 3D Hero Scene — OS Kernel Visualization

### Concept

Replace the generic neural network (orbs + particles + connecting lines) with an OS kernel visualization: two concentric rings rotating on different axes, data particles traveling along fixed ring paths, and brief connecting beams pulsing like processor clock cycles. This communicates "operating system" — not "generic AI."

### Technical Specification

| Property | Value |
|---|---|
| **Library** | Three.js r128 via CDN |
| **Renderer** | WebGL with antialiasing, alpha: true, `setPixelRatio(Math.min(devicePixelRatio, 2))` |
| **Camera** | PerspectiveCamera, position z=8, no orbit controls |
| **Background** | Pure dark (no grid helper, no starfield, no fog) |

**Ring geometries:**
- Outer ring: `TorusGeometry(3.2, 0.06, 24, 64)`, `MeshBasicMaterial`, color `#6C5CE7`, opacity 0.35
- Inner ring: `TorusGeometry(2.0, 0.04, 20, 48)`, `MeshBasicMaterial`, color `#00CEC9`, opacity 0.3
- No `MeshPhysicalMaterial` or `MeshStandardMaterial`. Ever.

**Ring rotation:**
- Outer: Y axis, 0.004 rad/frame (slow counterclockwise)
- Inner: X axis 0.003 + Y axis 0.006 rad/frame (compound rotation, creates wobble)

**Data particles (exactly 12):**
- 6 particles on outer ring (primary #6C5CE7), 6 on inner ring (secondary #00CEC9)
- Small `SphereGeometry(0.06)`, `MeshBasicMaterial`
- Positioned via parametric path: `x = cos(angle) * radius, z = sin(angle) * radius`
- Starting angles distributed evenly: outer particles at n/6 × 2π, inner particles at n/6 × 2π + offset
- Travel speed: 0.004–0.007 rad/frame (slight variation per particle)
- One particle occasionally flashes white (like a data interrupt) — random trigger

**Connecting beams (2–3):**
- Line segments from inner ring to outer ring at fixed angles
- `BufferGeometry` with 2 vertices, `LineBasicMaterial`, primary color, opacity 0.15–0.4
- Opacity pulse: 0.05 → 0.3 → 0.05, 2.5s cycle, phase offset per beam (like system bus signals)

**Scene bounding:**
- Scene fills its container (hero right/background area)
- Opacity fades from 1 to 0 as hero scrolls past viewport

**Mouse interaction:**
- CSS perspective rotation on the Three.js container div (not Three.js camera)
- ±2deg on mousemove
- Pure CSS, zero JS cost
- Not applied on touch devices

**WebGL fallback:**
If Three.js fails to load or WebGL is unavailable:
- 2 CSS-animated concentric rings (border-radius: 50% with border trick, rotating via CSS transform)
- 12 small CSS dots cycling around the rings via transform-origin + rotate
- Preserves the visual identity (rings + orbiting dots) without Three.js

---

## Scroll Interactions

| Interaction | Implementation | Details |
|---|---|---|
| **Navbar transform** | IntersectionObserver on hero | Transparent → glass (blur 16px) + border-bottom when hero exits viewport. 300ms transition. |
| **Section reveals** | IntersectionObserver (15% threshold) | Fade-up: `opacity: 0, translateY(30px)` → `opacity: 1, translateY(0)`, 700ms, `cubic-bezier(0.16, 1, 0.3, 1)` |
| **Counter animation** | IntersectionObserver on stats | Numbers animate from 0/from base to final value. 2s easeOutCubic via requestAnimationFrame. |

The following are EXCLUDED: scroll progress bar, scroll-to-top FAB, parallax.

---

## Mouse Interactions

| Interaction | Implementation | Details |
|---|---|---|
| **CSS scene tilt** | Container div with `perspective: 800px`, CSS transform on mousemove | ±2deg. Zero JS. |
| **Primary CTA hover** | `scale(1.02)` + box-shadow increase | CSS transition, 200ms ease |
| **Secondary CTA hover** | Cursor change only — no transform, no glow | No hover animation |
| **Feature card hover** | Border color shift: `rgba(255,255,255,0.06)` → `rgba(108,92,231,0.3)` | CSS transition, 300ms ease |
| **Nav link hover** | Underline via `background-size` technique | CSS-only, 300ms ease |

The following are EXCLUDED: magnetic buttons, card tilt, card lift (translateY), button glow pulse, mouse glow, custom cursor.

---

## Animation System — 8 Types Only

### Hero Entrance Stagger (A1)

| Element | Delay | Duration | Animation | Easing |
|---|---|---|---|---|
| 3D scene | 0ms | 600ms | Fade in (opacity 0→1) | ease-out |
| Hero headline | 400ms | 700ms | Slide up (translateY 40px→0) + opacity | cubic-bezier(0.16, 1, 0.3, 1) |
| Hero subheadline | 600ms | 700ms | Slide up (translateY 30px→0) + opacity | same |
| CTA buttons | 800ms | 500ms | Slide up + stagger 100ms between buttons | same |
| Trust bar | 1000ms | 600ms | Fade up + opacity | ease-out |

### Continuous (A2)

- **3D scene rotation**: Rings rotate continuously. Particles orbit. Infinite.

### Scroll-Triggered (A3, A4, A5)

- **Section reveals**: Fade-up via IntersectionObserver, 700ms, unobserves after reveal
- **Counter animation**: Stats count-up on scroll enter, 2s easeOutCubic
- **Navbar transition**: Transparent → glass on hero exit, 300ms

### Hover (A6, A7, A8)

- Primary CTA: scale(1.02) + shadow, 200ms
- Feature cards: border color shift only, 300ms
- Nav links: underline slide-in, 300ms

### Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
  .section-reveal {
    opacity: 1;
    transform: none;
  }
}
```

All content must be fully visible and functional without animation.

---

## Sections — Detailed

### 1. Navbar

```
Layout: [▣ AgentOS]  Platform  Agents  Developers  Changelog  [Deploy AgentOS]
Logo: "AgentOS" in medium weight with abstract cube SVG (28×28px)
States:
  - Top: transparent bg, white text
  - After scroll: glass bg (blur 16px), border-bottom 1px rgba(255,255,255,0.05)
CTA button: gradient primary→primary-dark, border-radius 8px, padding 0.5rem 1.25rem
Hover: scale(1.02) + shadow increase, 200ms ease
```

### 2. Hero

```
Layout: Full viewport height. Blended content/scene layout.
  - 3D scene fills the hero as background (position: absolute, inset: 0)
  - Content overlaid on left (~40% width, max-width ~540px)
  - Gradient vignette masks transition: linear-gradient(to right, #0A0A0F 25%, transparent 70%)
  - Content: position: relative, z-index: 1

Content:
  Badge: ⚡ "Now in Public Beta" — small capsule, glow shadow
  Headline: "The operating system\nfor autonomous agents" — two lines, solid white text
  Subheadline: "Design, deploy, and orchestrate AI agents across any environment.
                One platform. Infinite scale." — text-secondary, max-width 50ch
  CTAs: [Deploy AgentOS ▸] (primary gradient, large, shadow-glow)
        [Watch Demo ▸] (ghost button, border 1px solid, animated arrow on hover)
  Trust bar: "Trusted by engineering teams at" + 3 abstract geometric marks
             (CSS-drawn shapes, not logos)
  Social proof: "Join 5,000+ engineers"

  Important: Hero headline uses SOLID WHITE TEXT (--text-primary).
  Do NOT apply gradient (background-clip: text) to the headline.
```

### 3. Platform Dashboard

```
Layout: Side-by-side, ~40% text / ~60% dashboard mockup
  Text left, dashboard mockup right.
  On tablet/mobile: stacks (text above, dashboard below)

  Headline: "See everything. Control everything."
  Body: "Monitor, debug, and orchestrate your entire agent fleet from a
         single dashboard. Real-time agent activity, metrics, logs, and
         controls — all in one place."

Dashboard mockup (macOS-style window):
  - Glass background (blur 16px) — this is ONE of the 3 glass elements
  - Rounded corners (12px), border 1px rgba(255,255,255,0.08)
  - Title bar: traffic light dots (red/yellow/green, CSS circles) + "AgentOS Dashboard"
  - Inner areas use solid --bg-tertiary (not glass)

  Three sub-components inside:
  1. Sidebar: 4 agent entries with status indicator dots (green/yellow/gray)
     Agent names: Agent-7, Agent-12, Agent-3, Agent-8
     Status: online, online, idle, online
  2. Main panel — activity feed + mini metric chart (inline SVG line)
     Activity: "Agent-7: Research complete. Source evaluation done. Confidence: 0.94"
     Chart: Simple SVG polyline, gradient fill underneath
  3. Log stream: Timestamped monospace entries
     "12:34:17 [INFO] Agent-7: task dispatched" (JetBrains Mono, color-coded)

  No hover effects on the dashboard (static mockup).
  No images. Everything is CSS/HTML/SVG.
```

### 4. Features

```
Layout: 3×2 grid of solid cards (no glass)

  Headline above grid: "Everything you need to scale agents"
  Cards: solid --bg-tertiary background, 1px border rgba(255,255,255,0.06),
         rounded corners (12px), padding 32px

  Custom SVG icons (6): inline SVGs, 28×28px, currentColor (primary)
    1. Kernel — 3 concentric circles (OS rings metaphor)
    2. Process — 3 parallel horizontal bars with vertical flow line
    3. Memory — 3 stacked horizontal layers with indent
    4. Shield — Simplified geometric shield with checkmark
    5. Terminal — Angle bracket + cursor (>_)
    6. Deploy — Upward arrow rising from horizontal base

  Feature titles + descriptions:
    1. Multi-Agent Orchestration — Coordinate hundreds of agents with intelligent
       task routing and dependency management. Agents collaborate, not collide.
    2. Real-Time Monitoring — Watch your agents think in real-time. Full traceability
       into every decision, every tool call, every output.
    3. Built-in Memory — Persistent context that survives across sessions. Your agents
       remember conversations, learn from feedback, and build knowledge over time.
    4. Security & Compliance — SOC 2 compliant. End-to-end encryption. Fine-grained
       access controls. Enterprise-grade security baked into every layer.
    5. API-First Design — REST APIs, WebSocket streams, and SDKs in Python, TypeScript,
       Go, Rust, and Java. Integrate in minutes, not days.
    6. One-Click Deploy — From localhost to production in seconds. Kubernetes-native,
       auto-scaling, with built-in rollbacks and canary deployments.

  Card hover: border color shifts from rgba(255,255,255,0.06) to rgba(108,92,231,0.3)
              + bg brightens from opacity 0.03 to 0.05
              Duration: 300ms ease. CSS transition only.

  NO glass on feature cards. NO hover lift (translateY). NO card tilt.
  Stagger entrance: index × 100ms delay, fade + translateY(20px→0), 500ms each.
```

### 5. Stats

```
Layout: Centered, 3 counter displays horizontally

  Headline: "Already powering the future of AI"
  Subheadline: "Teams building autonomous systems trust AgentOS for reliability
                and performance."

  Three stats:
    1. "10,000+" — agents deployed
    2. "99.99%" — platform uptime
    3. "< 50ms" — average latency

  Each stat:
    - Number: clamp(2.5rem, 4vw, 4rem), bold 700, SOLID --text-primary (no gradient)
    - Label: 0.875rem, --text-secondary, uppercase letter-spacing
    - Separator: 60px gradient line (primary → secondary) below each number

  Counter animation:
    - 2s easeOutCubic via requestAnimationFrame
    - "10,000+" animates from 0 to 10000
    - "99.99%" animates from 99.90 to 99.99
    - "< 50ms" animates from 100 down to 50

  No glass. No hover effects. No gradient text.
```

### 6. CTA Waitlist

```
Layout: Full-bleed section with CSS particle background

  Background: 20 CSS dots (border-radius: 50%) drifting slowly,
              positioned randomly, opacity 0.1–0.3
              No Three.js. Pure CSS animation.

  Headline: "Ready to deploy the operating system?"
  Subheadline: "Join 5,000+ engineers building the future of autonomous AI."

  Form (glass container — one of the 3 glass elements):
    - Input: --bg-tertiary background, glass-like border, primary focus ring (2px)
             placeholder "Enter your email"
    - Button: "Deploy AgentOS" — gradient primary→primary-dark, shadow-glow
    - On submit (no backend): form replaced inline with success message

  Social proof:
    - 5 avatar circles (CSS-drawn with initials, each a different gradient color)
    - "+ 5,000+ engineers waiting"

  Note: "No spam. Unsubscribe anytime."

  Glass is on the FORM CONTAINER only. Background is solid dark.
  Do NOT use Three.js for the CTA particles.
```

### 7. Footer

```
Layout: 3 columns (not 4), max-width 960px, top border 1px rgba(255,255,255,0.05)

  Columns:
    Platform          | Developers        | Company
    Features          | Documentation     | About
    Integrations      | API Reference     | Blog
    Changelog         | SDKs              | Careers
    Pricing           | Status            | Contact

  Bottom bar:
    "© 2026 AgentOS" + "Built with AgentOS ▣" (inline cube SVG)

  Styles:
    - Small text (0.875rem), --text-secondary, opacity 0.7
    - No glass
    - No background card
    - Link hover: color → --text-primary, 200ms ease

  No "Legal" section. No placeholder links (Privacy Policy, Terms of Service, etc.).
```

---

## Performance Constraints

| Constraint | Specification |
|---|---|
| **Total page weight** | < 200 KB |
| **HTML size** | < 35 KB |
| **CSS size** | < 15 KB (inline `<style>` in `<head>`) |
| **JS size (inline)** | < 12 KB (inline `<script>` at end of `<body>`) |
| **External requests** | ≤ 3: Google Fonts (2 requests) + Three.js CDN |
| **Three.js CDN** | `cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js` |
| **Zero external images** | No `<img>` tags. CSS/SVG/Three.js only. |
| **Particles (3D)** | Exactly 12 (SphereGeometry, not Points) |
| **CSS dots (CTA)** | Exactly 20 (border-radius: 50%, CSS positioned) |
| **Glass elements** | Exactly 3 (navbar, dashboard window, CTA form) |
| **Lighthouse target** | > 90 all categories |
| **GPU compositing** | Animations use `transform` and `opacity` only |
| **pixel ratio cap** | `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` |
| **WebGL fallback** | CSS concentric rings + orbiting dots |
| **No console.log** | Zero debug output in production |
| **prefers-reduced-motion** | Full suppression of all non-essential animations |

---

## Delivery Output

1. **Single file:** `index.html` — complete, self-contained
2. **CSS:** Single `<style>` block in `<head>`. No inline `style=""` attributes.
3. **JavaScript:** Single `<script>` block at end of `<body>`. External libs via `<script defer>`.
4. **Semantic HTML5:** `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`. Valid HTML5.
5. **Responsive:** 375px, 768px, 1024px, 1440px. No horizontal scroll.
6. **Accessibility:** Skip-to-content link, ARIA labels, focus indicators, `prefers-reduced-motion`.
7. **No paid assets:** Everything free/open-source. Zero attribution-required resources.
8. **GitHub Pages compatible:** Relative paths only. No absolute URLs.

---

## Quality Checklist

Before marking this prompt as executed:

- [ ] 3D scene has 2 concentric rings (not orbs/neural nodes)
- [ ] 3D scene uses MeshBasicMaterial only
- [ ] Exactly 12 particles in the 3D scene
- [ ] Page has 7 sections (Problem section does not exist)
- [ ] CTA copy says "Deploy AgentOS" — not "Get Early Access"
- [ ] Headline uses solid white text, not gradient
- [ ] Glass is on exactly 3 elements
- [ ] Feature icons are custom SVGs (not Lucide/Feather)
- [ ] Animations: 8 types only (hero stagger, 3D rotation, scroll reveals, counters, navbar glass, CTA hover, card hover, nav underline)
- [ ] Progress bar, FAB, card tilt, card lift do NOT exist
- [ ] No console errors on page load
- [ ] Lighthouse ≥ 90 all categories
- [ ] Mobile layout looks designed (not squished)
- [ ] `prefers-reduced-motion` works
- [ ] WebGL fallback renders acceptably
- [ ] Page feels premium and original — not like a template

---

*This prompt follows the Awesome AI Landings PROMPT_FRAMEWORK.md specification.*
*It has been revised per AGENTOS_REVIEW.md, WIREFRAME.md, and GENERATION_CONTRACT.md.*
*It is the authoritative source for generating the AgentOS benchmark page.*
