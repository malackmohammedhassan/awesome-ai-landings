# AgentOS — Prompt Specification

> This is the benchmark page for the entire Awesome AI Landings repository.
> The quality of everything that follows is defined by what this page achieves.
> Every parameter below is the result of deliberate design decisions.
> **Do not cut corners.**

---

## AI Tool

This prompt is designed for:
- **Primary:** Claude (Sonnet 4 or Opus) / Hermes Agent
- **Alternative:** Cursor with Claude model
- **Model:** Any frontier model with strong CSS/JS/Three.js generation capability

---

## Category

AI SaaS — Agent infrastructure platform

---

## Role

You are a senior product designer and front-end engineer at a top-tier design agency. You specialize in premium SaaS landing pages for AI-first companies. You combine mastery of visual design (typography, color theory, composition, motion design) with expert front-end engineering (CSS, JavaScript, Three.js, WebGL). You have shipped production landing pages for companies like Vercel, Linear, Stripe, and Apple. You never use templates, never use Tailwind/Bootstrap, and never rely on stock assets. Every design you create is original, distinctive, and unforgettable.

---

## Audience

The page is for:
- AI engineers and CTOs evaluating agent infrastructure platforms
- Technical founders building agent-based products
- Enterprise decision-makers researching AI orchestration tools
- Developers tired of stitching together 15 tools to manage a single agent

They are:
- Technically sophisticated — they inspect your animations, check console, resize the window
- Visually literate — they've seen every SaaS template and are bored by all of them
- Attention-scarce — you have 3 seconds to prove this is different
- Quality-sensitive — a broken hover state erases trust in the product

---

## Brand

| Attribute | Value |
|---|---|
| **Name** | AgentOS |
| **Tagline** | "The operating system for autonomous agents" |
| **Archetype** | Magician + Creator |
| **Personality** | Visionary, precise, ambitious, futuristic, trustworthy |
| **Voice** | Confident and visionary — "we're building the future of AI infrastructure" but grounded in technical credibility |
| **Core promise** | One platform to design, deploy, and orchestrate AI agents at scale. No more stitching together tools. One OS for your autonomous workforce. |

**Brand backstory (for visual tone only, not page copy):**
AgentOS started as an internal tool at a frontier AI lab. Engineers needed a unified control plane for hundreds of autonomous agents running diverse tasks — research, coding, customer support, data analysis. The existing tools were fragmented, brittle, and unobservable. So they built their own. Now it's a platform.

---

## Visual Style

| Attribute | Value |
|---|---|
| **Style** | Futuristic, cyberpunk-lite, glassmorphism |
| **Core metaphor** | "A mission control center for autonomous intelligence" — think NASA's Mission Control redesigned by Apple, fused with a neural network visualization |
| **Texture / feel** | Smooth glass surfaces, subtle grid lines (inspired by Fluent Design), floating UI panels, holographic interface elements, depth through layered translucency |
| **Inspirations** | Her (2013) OS UI, Windows Fluent Design System, Interstellar docking sequence, Apple Vision Pro glass, Linear's minimalist dark theme, Stripe's documentation aesthetic |
| **Key visual motif** | Floating geometric orbs (neural nodes) connected by luminous particle lines, all rendered in Three.js, responding to mouse movement |

---

## Color System

```css
:root {
  /* Core brand */
  --primary: #6C5CE7;
  --primary-light: #A29BFE;
  --primary-dark: #4834D4;
  --secondary: #00CEC9;
  --accent: #FD79A8;

  /* Status / utility */
  --warning: #FDCB6E;
  --success: #00B894;
  --error: #D63031;

  /* Backgrounds — deep space with blue-purple tint */
  --bg-primary: #0A0A0F;
  --bg-secondary: #12121A;
  --bg-tertiary: #1A1A2E;

  /* Glass surfaces */
  --glass-bg: rgba(255, 255, 255, 0.03);
  --glass-border: rgba(255, 255, 255, 0.08);
  --glass-hover: rgba(255, 255, 255, 0.06);
  --glass-blur: 20px;

  /* Text */
  --text-primary: #F0F0F5;
  --text-secondary: #9494A8;
  --text-tertiary: #6B6B80;

  /* Gradients */
  --gradient-hero: linear-gradient(135deg, #0A0A0F 0%, #1A1A2E 40%, #0A0A0F 100%);
  --gradient-glass: linear-gradient(135deg, rgba(108, 92, 231, 0.15), rgba(0, 206, 201, 0.05));
  --gradient-accent: linear-gradient(135deg, var(--primary), var(--secondary));
  --gradient-cta: linear-gradient(135deg, var(--primary), #8B5CF6);

  /* Shadows */
  --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 8px 32px rgba(0, 0, 0, 0.4);
  --shadow-lg: 0 16px 48px rgba(0, 0, 0, 0.5);
  --shadow-glow: 0 0 30px rgba(108, 92, 231, 0.3);
  --shadow-glow-strong: 0 0 60px rgba(108, 92, 231, 0.5);
}
```

**Usage rules:**
- Primary (#6C5CE7) is for main interactive elements, active states, hero accent glow
- Secondary (#00CEC9) for secondary badges, data stream accents, secondary hover states
- Accent (#FD79A8) used sparingly — only for emphasis (notification dots, "new" badges, urgent CTA pulsing)
- Text primary on glass surfaces needs a slightly lower contrast for depth effect
- All gradients should be subtle — the page feels premium through restraint, not saturation

---

## Typography

| Property | Value |
|---|---|
| **Primary font** | Inter (Google Fonts) |
| **Weights used** | 300, 400, 500, 600, 700, 800 |
| **Monospace font** | JetBrains Mono (Google Fonts) |
| **Monospace weights** | 400, 500 — for data displays, code samples, metrics |

**Font loading:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

**Type scale:**

| Token | Size | Weight | Line Height | Usage |
|---|---|---|---|---|
| `--text-hero` | clamp(2.5rem, 5vw, 4.5rem) | 700 | 1.08 | Hero headline |
| `--text-h1` | clamp(2rem, 3.5vw, 3rem) | 600 | 1.15 | Section headlines |
| `--text-h2` | clamp(1.5rem, 2.5vw, 2rem) | 600 | 1.2 | Sub-section titles |
| `--text-h3` | clamp(1.25rem, 1.5vw, 1.5rem) | 600 | 1.25 | Card titles |
| `--text-body` | clamp(1rem, 1.25vw, 1.125rem) | 400 | 1.6 | Body copy |
| `--text-small` | 0.875rem | 400 | 1.5 | Captions, meta |
| `--text-mono` | 0.875rem | 400 | 1.5 | Code, data |
| `--text-button` | 1rem | 600 | 1 | Button labels |
| `--text-label` | 0.75rem | 600 | 1 | Overline labels, uppercase + letter-spacing |

**Body text max-width:** 70ch for readability.

---

## Layout

**Page structure — 8 sections:**

```
┌─────────────────────────────────────────┐
│ NAVBAR (transparent → glass on scroll)  │
│  [Logo] [Product] [Docs] [Blog] [CTA]   │
├─────────────────────────────────────────┤
│ HERO — full viewport                     │
│  Left: Headline + Sub + CTAs + Trust bar │
│  Right: Three.js neural orb scene        │
├─────────────────────────────────────────┤
│ PROBLEM — 3-column pain point grid       │
│  "Agent infrastructure is broken"        │
├─────────────────────────────────────────┤
│ PLATFORM — dashboard showcase            │
│  macOS-style window with AgentOS UI      │
├─────────────────────────────────────────┤
│ FEATURES — 3×2 grid with icons           │
│  "Everything you need to scale agents"   │
├─────────────────────────────────────────┤
│ STATS — 3 animated counters              │
│  "Trusted by engineering teams"          │
├─────────────────────────────────────────┤
│ CTA WAITLIST — full-bleed with particles │
│  "Ready to command your agent fleet?"    │
├─────────────────────────────────────────┤
│ FOOTER — minimal, 4-column               │
│  Product | Resources | Company | Legal   │
└─────────────────────────────────────────┘
```

**Grid system:** CSS Grid for section-level layout, Flexbox for component-level arrangement.

**Breakpoints:**

| Breakpoint | Layout behavior |
|---|---|
| >= 1024px | Full desktop layout — hero split 50/50, 3-column problem grid, 3×2 features, multi-column footer |
| 768px — 1023px | Tablet — hero stacks (scene on top or below), 2-column feature grid, reduced decorative 3D |
| < 768px | Mobile — fully stacked single column, hamburger nav, scene moved behind hero (subtle via reduced particles), touch-friendly |

**Section padding:** `padding: clamp(4rem, 8vw, 8rem) clamp(1.5rem, 5vw, 4rem)` — generous whitespace.

**Max content width:** 1200px, centered with auto margins. Hero may be full-width.

---

## 3D Effects

### Hero Scene — Three.js (primary)

**Setup:**
- Renderer: WebGL with antialiasing, `alpha: true`, `setPixelRatio(Math.min(window.devicePixelRatio, 2))`
- Scene: dark background matching `--bg-primary`
- Camera: PerspectiveCamera with slight initial angle (15° offset from center)

**Objects (3–5 floating geometric orbs):**
- Mix of icosahedrons, octahedrons, and dodecahedrons
- Sizes: 0.8–1.5 units radius
- Colors: primary (#6C5CE7), secondary (#00CEC9), white (semi-transparent)
- Materials: MeshPhysicalMaterial with `roughness: 0.2`, `metalness: 0.8`, `transmission: 0.3`, `clearcoat: 0.4`
- Each orb has a subtle wireframe overlay (slightly larger, opacity 0.2)
- Orb rotation: 0.005–0.015 rad/frame on Y and X axes (different rates per orb)

**Particle system:**
- ~200 luminous dots in a spherical distribution around the orbs
- Colors: blend of primary and secondary
- Size: 2–4px, opacity 0.3–0.8
- Connected by lines when particles are within 3 units of each other (semi-transparent, 0.5px)
- Particles have subtle velocity (drift in random directions, 0.001 units/frame)

**Energy threads between orbs:**
- Bezier curves connecting certain orb pairs
- Animated opacity: pulse between 0.3–1.0 over 2–3s (different phase per connection)
- Color: lerp between the two connected orbs' colors
- Line width: 1px with glow effect (secondary slightly transparent line underneath)

**Mouse interaction:**
- Camera orbits target by ±0.3 radians on Y, ±0.15 on X based on normalized mouse position
- Smooth lerp (0.05 factor) — the camera doesn't snap, it glides
- Orbs subtly gravitate toward cursor in 2D screen space (very subtle, 0.1 unit max displacement)
- Mouse inactivity (3s): orbs resume gentle float animation

**Scroll interaction:**
- As user scrolls, the 3D scene scales down (transform: scale from 1 to 0.7) and fades (opacity: 1 to 0.3)
- At 100% scroll of hero section, scene is fully faded
- Capped at hero section height — no 3D rendering below the fold (saves performance)

**Fallback (if WebGL unavailable):**
- Replace Three.js scene with CSS-only animated gradient mesh
- 3–4 floating CSS circles with `border-radius: 50%` + `backdrop-filter: blur()` + slow translateY animation
- Particle connections become impossible, but the visual emptiness is filled by CSS shapes

### Feature Cards — CSS 3D (secondary)

```css
.feature-card {
  perspective: 1000px;
  transform-style: preserve-3d;
  transition: transform 0.3s ease;
}

.feature-card:hover {
  transform: rotateY(8deg) rotateX(5deg);
}

.feature-card-glow {
  position: absolute;
  inset: 0;
  background: radial-gradient(600px circle at var(--mouse-x, 50%) var(--mouse-y, 50%),
    rgba(108, 92, 231, 0.1),
    transparent 40%);
  pointer-events: none;
}
```

### Glass Panels — backdrop-filter

Every card, feature box, and dashboard mockup uses:
```css
background: rgba(255, 255, 255, 0.03);
backdrop-filter: blur(20px);
-webkit-backdrop-filter: blur(20px);
border: 1px solid rgba(255, 255, 255, 0.08);
border-radius: 16px;
```

---

## Scroll Interactions

| Interaction | Implementation | Details |
|---|---|---|
| **Progress bar** | Fixed top `<div>` | 3px height, gradient-bg (primary → secondary), width scales from 0% to 100% based on `scrollY / (docHeight - winHeight)` |
| **Navbar transform** | IntersectionObserver on hero | Transparent bg → glass bg + shadow once hero exits viewport. Smooth 300ms transition. |
| **Section reveals** | IntersectionObserver (85% threshold) | Each section animates in using `clip-path: polygon(0 100%, 100% 100%, 100% 100%, 0 100%)` → `polygon(0 0, 100% 0, 100% 100%, 0 100%)` over 800ms, ease `cubic-bezier(0.16, 1, 0.3, 1)` |
| **Counter animation** | IntersectionObserver on stats section | Numbers count from 0 to final value over 2s using `requestAnimationFrame` with easeOutCubic |
| **Parallax depth** | Hero scene and background | Three.js scene has layered depth; hero background grid moves at 0.2x scroll speed, orbs at 0.5x, content at 1x |
| **Scroll-to-top** | FAB appears after 50% scroll | Circular button with arrow icon, smooth `window.scrollTo({ top: 0, behavior: 'smooth' })`, fades in/out 300ms |

**Progress bar code pattern:**
```javascript
const progressBar = document.getElementById('progress-bar');
window.addEventListener('scroll', () => {
  const h = document.documentElement;
  const pct = (h.scrollTop || document.body.scrollTop) / (h.scrollHeight - h.clientHeight);
  progressBar.style.transform = `scaleX(${Math.min(pct, 1)})`;
});
```
(Use `transform: scaleX()` for GPU-composited performance instead of `width`.)

**Section reveal code pattern:**
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('revealed');
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });

document.querySelectorAll('.section-reveal').forEach(el => observer.observe(el));
```

---

## Mouse Interactions

| Interaction | Behaviour | Implementation |
|---|---|---|
| **Magnetic buttons** | CTA buttons subtly follow cursor | JS tracks mouse position relative to button center, applies `transform: translate(dx * 0.2, dy * 0.2)` with 100ms transition |
| **Mouse glow** | Radial gradient spotlight follows cursor in hero | `mousemove` listener updates CSS custom properties `--mouse-x`, `--mouse-y` on hero container; used in `radial-gradient()` for a subtle light sweep |
| **Card tilt** | Feature cards tilt on hover | JS calculates mouse position within card, applies `rotateY` and `rotateX` proportional to distance from center (max ±8deg) |
| **3D scene orbit** | Three.js camera follows mouse | Normalized mouse position maps to camera orbit target (lerp factor 0.05 for smoothness) |
| **Nav link underline** | Hover reveals animated underline | CSS-only: `background-size: 0% 2px` → `100% 2px` on hover, 300ms ease, using `linear-gradient` background |

**Important:** All mouse interactions must degrade gracefully on touch devices. No hover-dependent content. Touch users get the same information without the effects.

---

## Animation System

### Entrance Timeline — Hero

| Element | Delay | Duration | Animation | Easing |
|---|---|---|---|---|
| 3D scene background | 0ms | 600ms | Fade in (opacity 0 → 1) | ease-out |
| 3D orbs | 200ms | 800ms | Fade + scale (0.8 → 1) | power2.out |
| Hero headline | 400ms | 700ms | Slide up (translateY 40px → 0) + opacity | cubic-bezier(0.16, 1, 0.3, 1) |
| Hero subheadline | 600ms | 700ms | Slide up (translateY 30px → 0) + opacity | same easing |
| CTA buttons | 800ms | 500ms | Slide up + opacity + stagger 100ms between buttons | same easing |
| Trust bar | 1000ms | 600ms | Fade up + opacity | ease-out |

### Section Reveals

Each section (except hero) uses:
```css
.section-reveal {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1),
              transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}

.section-reveal.revealed {
  opacity: 1;
  transform: translateY(0);
}
```

Child elements within a section can stagger:
```javascript
// After section reveals, stagger children with 100ms delay each
children.forEach((el, i) => {
  el.style.transitionDelay = `${i * 100}ms`;
});
```

### Feature Cards Entrance

Cards in the feature grid enter with stagger (index × 100ms delay):
- Fade + scale (0.95 → 1) + translateY(20px → 0)
- Duration: 500ms per card
- Easing: `cubic-bezier(0.16, 1, 0.3, 1)`

### Continuous Animations

| Element | Animation | Duration | Notes |
|---|---|---|---|
| Hero orbs | translateY oscillation (±8px) | 4s, sine wave | Random phase per orb |
| Particle lines | Opacity pulse (0.6 → 1.0 → 0.6) | 3s | Each connection has unique phase |
| Background grid | Slow horizontal pan | 20s | CSS translateX infinite loop |
| Button glow | Subtle box-shadow pulse | 3s | Only on primary CTA, intensity ±10% |
| Stats counter digits | Count-up on scroll trigger | 2s | Once per session |

### Hover States

| Element | Transformation | Duration | Easing |
|---|---|---|---|
| Primary CTA | scale(1.03) + shadow increase + brightness(1.1) | 200ms | ease-out |
| Secondary CTA | border-color shift toward primary + subtle bg fill | 250ms | ease-out |
| Feature cards | translateY(-4px) + shadow-md → shadow-lg + border-glow | 300ms | ease-out |
| Nav links | underline slide-in (background-size technique) | 300ms | ease |
| Social / footer links | color shift to primary | 200ms | ease |

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

Content must be fully visible and functional with reduced motion. No information is hidden behind animations.

---

## Sections — Detailed Content

### 1. Navbar

```
Layout: [Logo] [Product ▼] [Docs] [Blog] [Get Early Access]

States:
  - Top of page: transparent, logo white, links white/translucent
  - After scroll: bg rgba(10, 10, 15, 0.85), backdrop-filter blur(20px),
    border-bottom 1px solid rgba(255,255,255,0.05)

Logo: "AgentOS" in medium weight, with a small abstract icon (cube with
      glowing node inside — inline SVG, 28×28px)

CTA button: small size, gradient primary → primary-dark, border-radius 8px
```

### 2. Hero

```
Layout: Full viewport height (100vh). Split 50/50.

Left column (content):
  Label: ⚡ "Now in Public Beta" — small capsule badge with glow
  Headline: "The operating system\nfor autonomous agents"
            (two lines, expressive line-height 1.08, gradient text)
  Subheadline: "Design, deploy, and orchestrate AI agents across any
                environment. One platform. Infinite scale."
  CTA group:
    [Get Early Access] — primary gradient button, large, shadow-glow
    [Watch Demo ▸] — ghost button with animated arrow on hover
  Trust bar: "Trusted by engineering teams at"
             3 placeholder brand logos (CSS-drawn, no images)
             "Join 5,000+ engineers"

Right column:
  Three.js scene described in the 3D Effects section above.
  The scene fills its container (100% width/height of the right half).

Text gradient for headline:
  background: linear-gradient(135deg, #F0F0F5 0%, #A29BFE 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
```

### 3. Problem — "Agent infrastructure is broken"

```
Layout: 3-column grid, centered content

Headline (section title): "Building with agents shouldn't\nrequire 15 tools"
Description: "Current infrastructure forces teams to piece together
              fragmented solutions. We're fixing that."

Three pain points, each with icon + title + description:

  Icon (puzzle piece)  → "Fragmented toolchain"
  Description: "Monitoring in one tool, memory in another, orchestration in a
                third. Your agents are scattered across 15 dashboards."

  Icon (eye-off)       → "Blind debugging"
  Description: "When an agent makes the wrong decision, finding out why
                requires reading through endless log files."

  Icon (refresh-cw)    → "Scaling breaks everything"
  Description: "Your proof of concept works. Your production deployment
                collapses. Scaling agents isn't linear — it's exponential pain."

Each card:
  - Glass background with subtle hover lift
  - Icon in primary color (24×24px, inline SVG or Lucide)
  - Title in text-primary, description in text-secondary
  - Hover: border-glow + slight translateY(-4px)
```

### 4. Platform — "One control center"

```
Layout: Side-by-side (40% text, 60% visual)

Headline: "See everything. Control everything."
Description: "Monitor, debug, and orchestrate your entire agent fleet from a
              single dashboard. Real-time agent activity, metrics, logs, and
              controls — all in one place."

Visual: A macOS-style window mockup (purely CSS/HTML)

  Window frame:
    - Rounded corners (12px), glass background, subtle shadow
    - Traffic light dots (red/yellow/green) in top-left corner
    - Title bar: "AgentOS Dashboard — 47 agents online"

  Dashboard content inside:
    - Left sidebar: agent list with search + 4 sample agents
      Each has a name, status indicator (green/yellow/red dot), last active time
    - Main panel: split into three sections
      1. Agent activity feed (chat-like messages: "Agent-7: Research complete.
         Source evaluation done. Confidence: 0.94")
      2. Mini metric graph (a simple SVG line chart showing agent throughput)
      3. Log stream (monospace text with timestamps, scrolling in real-time)

All dashboard elements are CSS/HTML mockups — no actual data, just beautiful UI.
Use subtle grid lines, monospace for log data, color-coded status badges.
```

### 5. Features — "Everything you need to scale agents"

```
Layout: 3×2 grid of glass cards

Section headline + description above grid.
Stagger entrance: cards enter left-to-right, top-to-bottom.

Each card (130px × 160px min content):

  1. Multi-Agent Orchestration
     Icon: git-branch (branching paths)
     "Coordinate hundreds of agents with intelligent task routing and
      dependency management. Agents collaborate, not collide."

  2. Real-Time Monitoring
     Icon: activity (heartbeat line)
     "Watch your agents think in real-time. Full traceability into every
      decision, every tool call, every output."

  3. Built-in Memory
     Icon: database (cylinder)
     "Persistent context that survives across sessions. Your agents remember
      conversations, learn from feedback, and build knowledge over time."

  4. Security & Compliance
     Icon: shield (checkmark)
     "SOC 2 compliant. End-to-end encryption. Fine-grained access controls.
      Enterprise-grade security baked into every layer."

  5. API-First Design
     Icon: terminal (code bracket)
     "REST APIs, WebSocket streams, and SDKs in Python, TypeScript, Go, Rust,
      and Java. Integrate in minutes, not days."

  6. One-Click Deploy
     Icon: cloud-upload (upload arrow)
     "From localhost to production in seconds. Kubernetes-native, auto-scaling,
      with built-in rollbacks and canary deployments."

Card design:
  - Glass background (rgba white 0.03 + backdrop-filter)
  - Rounded corners (16px)
  - Padding: 32px
  - Icon in top-left (36×36px, primary color with subtle glow)
  - Title (h3) + Description (body)
  - Hover: 3D tilt effect + glow border + slight lift
```

### 6. Stats — "Trusted by engineering teams"

```
Layout: Centered, 3 large numbers with labels

Section headline: "Already powering the future of AI"
Subheadline: "Teams building autonomous systems trust AgentOS for reliability
              and performance."

Three stats, displayed horizontally:

  "10,000+"    — agents deployed
  "99.99%"     — platform uptime
  "< 50ms"     — average latency

Each stat:
  - Number: 4rem, bold, gradient text (primary → secondary)
  - Label: 1rem, text-secondary, uppercase letter-spacing
  - Counter animates from 0 on scroll trigger (2s duration, easeOutCubic)
  - Below: subtle separator line (gradient, 60px wide)

For "99.99%", animate from 99.90 to 99.99 (realism).
For "< 50ms", animate from 100 down to 50 (reverse count).
```

### 7. CTA — Waitlist

```
Layout: Full-bleed, centered, with subtle background particle effect

Background: Dark with very subtle Three.js or CSS particle system
  (20 small dots drifting slowly, no interaction needed)

Headline: "Ready to command\nyour agent fleet?"
Subheadline: "Join 5,000+ engineers building the future of autonomous AI."

Form: Email input + CTA button
  Input: Glass-style, dark bg, primary focus ring, placeholder "Enter your email"
  Button: Large, gradient CTA with glow shadow, "Get Early Access"
  On submit: success message replaces form (no actual backend)

Social proof:
  Row of 5 avatar circles (CSS initials, each a different gradient color)
  "+ 5,000+ engineers waiting"

Small note below: "No spam. Unsubscribe anytime."
```

### 8. Footer

```
Layout: 4-column grid + bottom bar

Columns:
  Product        | Resources        | Company      | Legal
  Features       | Documentation    | About        | Privacy Policy
  Integrations   | API Reference    | Blog         | Terms of Service
  Changelog      | Community        | Careers      | Cookie Policy
  Pricing        | Status           | Contact      | GDPR

Bottom bar:
  "© 2026 AgentOS. All rights reserved."
  "Built with AgentOS" — inline SVG of the AgentOS cube icon

Design: Minimal, small text (0.875rem), reduced opacity
  links (0.6 → 0.8 on hover), glass top-border.
```

---

## Interactions — Summary

| Interaction | Trigger | Effect |
|---|---|---|
| Page load | Auto | Hero entrance stagger (1.3s timeline) |
| Scroll past hero | Scroll | Navbar transparent → glass |
| Scroll progress | Scroll | Top progress bar fills |
| Section enters viewport | Scroll | Clip-path reveal animation |
| Stats in view | Scroll | Numbers count up from 0 |
| Mouse move in hero | Mouse | 3D scene camera orbits + glow follow |
| Mouse move on card | Mouse | 3D tilt rotateY/X |
| Mouse move on CTA | Mouse | Magnetic pull toward cursor |
| Mouse hover on CTA | Hover | Scale + glow + brightness |
| Hover nav link | Hover | Underline slide-in |
| Hover feature card | Hover | Lift + glow border |
| Click CTA | Click | Smooth scroll to waitlist |
| Touch (mobile) | Tap | All interactions work without hover |
| prefers-reduced-motion | System | All animations disabled, content static |

---

## Performance Constraints

| Constraint | Specification |
|---|---|
| **Critical CSS** | All above-the-fold styles inlined in `<head>` within `<style>` block |
| **JavaScript** | All JS deferred: `<script defer>` for external, at end of `<body>` for inline |
| **External requests** | Maximum 4: Google Fonts (1), Three.js (1), no others |
| **Three.js CDN** | `https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js` or `https://unpkg.com/three@0.160.0/build/three.module.js` |
| **No external images** | Zero `<img>` tags. Everything is CSS, SVG, or Three.js. |
| **Font embedding** | Preconnect + subset to used weights only |
| **Total page weight** | < 500 KB total (HTML + CSS + JS + fonts) |
| **Lighthouse target** | > 90 Performance, > 95 Accessibility, > 95 Best Practices, > 95 SEO |
| **GPU compositing** | Animations only use `transform`, `opacity`, `clip-path` — never layout-triggering properties |
| **Three.js pixel ratio** | `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` |
| **WebGL fallback** | CSS gradient + floating elements if Three.js fails to load |
| **No console.log** | Zero debug output in production |
| **prefers-reduced-motion** | Full suppression of all non-essential animations |

---

## Output Requirements

1. **Single file:** `index.html` — complete, self-contained landing page
2. **CSS:** All in a single `<style>` block within `<head>`. No `<link>` to external CSS files (except Google Fonts). No inline `style=""` attributes.
3. **JavaScript:** All in a single `<script>` block at end of `<body>` (below `</main>`). External libraries loaded via CDN with `<script defer>`.
4. **Semantic HTML5:** Use `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`. Valid HTML5 — no unclosed tags, no duplicate IDs.
5. **Responsive:** Works and looks intentional at 375px, 768px, 1024px, and 1440px. No horizontal scroll at any width.
6. **Accessibility:** Skip-to-content link, ARIA labels, focus indicators, `prefers-reduced-motion`, semantic landmarks, alt text on functional SVGs.
7. **Design uniqueness:** Page must not resemble any template, Tailwind UI component, or other demo. It must be visually original while feeling professionally familiar.
8. **No paid assets:** Everything must be free — Google Fonts, open-source CDN libraries. Zero attribution-required resources.
9. **Production-ready:** Remove all comments, debugging code, placeholder text. Every element must look final.
10. **Size constraint:** `<style>` block must efficiently group shared styles. No unnecessary duplication. Use CSS custom properties for consistency.

---

## Quality Checklist (for the generator)

Before marking this prompt as executed:

- [ ] Does the 3D scene render without console errors?
- [ ] Does the page reach 90+ across all Lighthouse categories?
- [ ] Does every scroll animation trigger correctly?
- [ ] Does every hover interaction feel polished?
- [ ] Does the mobile layout look intentional (not squished)?
- [ ] Is there zero horizontal scroll at 375px?
- [ ] Are all animations GPU-composited?
- [ ] Does `prefers-reduced-motion` disable animations without hiding content?
- [ ] Is the WebGL fallback reasonable?
- [ ] Would you proudly put this in a portfolio? (If no, regenerate.)

---

## Generation Date

<!-- To be filled after generation -->

---

*This prompt follows the Awesome AI Landings PROMPT_FRAMEWORK.md specification.*
*It is the benchmark for all future pages in this repository.*
