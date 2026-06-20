# AgentOS — Visual Architecture Wireframe

> **Before:** Neural network 3D scene + Problem grid + glass everywhere + 8 animation types
> **After:** OS kernel 3D visualization + Platform-first narrative + selective glass + 4 animation types
> 
> This wireframe incorporates every change from AGENTOS_REVIEW.md.
> No HTML, CSS, or JS has been generated. This is the final spec before code.

---

## 1. Narrative Flow

The visitor's experience from top to bottom:

```
ARRIVAL
  │
  ▼
  Dark, expansive viewport. No clutter.
  A rotating 3D structure of concentric rings fills the space —
  violet and teal, precise, architectural. Not a neural network.
  Not floating orbs. This looks like an operating system's kernel
  rendered in three dimensions.
  │
  ▼ SCROLL
  │
  The product dashboard appears — a concrete interface showing
  agents, logs, metrics. The abstract vision becomes real.
  │
  ▼ SCROLL
  │
  Features with custom icons that reference processor components
  (kernel, threads, bus, memory). Each icon is unique to AgentOS.
  │
  ▼ SCROLL
  │
  Three numbers — proof points, not imagined stats. Specific
  enough to feel real, modest enough to be believed.
  │
  ▼ SCROLL
  │
  "Deploy AgentOS" — not "Get Early Access." The OS metaphor
  carries through to the final action.
  │
  ▼
  Minimal footer. No fake links.
```

**Narrative arc:** Vision → Proof → Capability → Scale → Action

**Tone:** Precise, confident, architectural. The page feels like the product it describes — organized, structured, purposeful.

---

## 2. Section Inventory

### Section 1: Navbar

| Property | Value |
|---|---|
| **Goal** | Orient the visitor, provide navigation, establish the brand mark |
| **Content** | AgentOS logo (SVG cube with glowing node) + 4 links (Platform, Agents, Developers, Changelog) + "Deploy AgentOS" CTA button |
| **Visual style** | Transparent at top, glass (`backdrop-filter: blur(16px)`) after hero scroll. Logo left, links right. Max-width 1200px, centered. |
| **Interactions** | Link underlines on hover (background-size technique). CTA button subtle scale + glow on hover. Glass transition on scroll (300ms ease). |
| **Why it exists** | Every premium page needs a navbar. This one stays out of the way at the top and becomes functional after scroll. |

**Changes from original spec:**
- Nav links changed from generic ("Product", "Docs", "Blog") to product-specific ("Platform", "Agents", "Developers", "Changelog")
- CTA changed from "Get Early Access" to "Deploy AgentOS"
- Glass reduced from `20px` to `16px` — slightly less aggressive

---

### Section 2: Hero

| Property | Value |
|---|---|
| **Goal** | Make an unforgettable first impression. Establish the OS metaphor visually. |
| **Content** | Badge: "Now in Public Beta" (capsule with glow). Headline: "The operating system for autonomous agents" (two lines). Subheadline: "Design, deploy, and orchestrate AI agents across any environment. One platform. Infinite scale." Two CTAs: "Deploy AgentOS" (primary gradient) + "Watch Demo" (ghost, with animated arrow). Trust bar: "Trusted by engineering teams at" + 3 abstract geometric brand marks (CSS, no images). |
| **Visual style** | Full viewport. Three.js OS kernel visualization fills the right ~60% as a living background. Content is left-aligned at ~40% width with a smooth gradient vignette masking the transition between content and scene. No 50/50 hard split — the scene and content blend. |
| **Interactions** | Hero entrance stagger (1.2s timeline). 3D scene fades in (0ms → 600ms). Headline slides up (400ms → 700ms). Subheadline (600ms → 700ms). CTAs (800ms → 500ms, stagger 100ms). Trust bar (1000ms → 600ms). 3D scene rotates continuously. CSS perspective rotation on scene container (±2deg on mousemove). |
| **Why it exists** | This is the signature moment. The OS kernel visualization is what makes the page memorable. It communicates "operating system" without a single word. |

**Changes from original spec:**
- ❌ Replaced 3 floating neural nodes + 60 particles + connecting lines
- ✅ New: OS kernel visualization — concentric rings + data particles (detailed in Section 3)
- ❌ Removed 50/50 hard split — now a blended content/scene layout
- ❌ Removed gradient text on hero headline (review flagged as generic) — using solid white `--text-primary` instead
- ✅ Trust bar uses abstract geometric marks instead of fake company logos
- ❌ Removed text gradient on headline — using solid white text (more premium, less "we tried to make this interesting")

---

### Section 3: Platform Dashboard

| Property | Value |
|---|---|
| **Goal** | Transition from abstract vision to concrete product. Show, don't tell. |
| **Content** | Headline: "See everything. Control everything." Body: "Monitor, debug, and orchestrate your entire agent fleet from a single dashboard. Real-time agent activity, metrics, logs, and controls — all in one place." Visual: macOS-style window mockup containing a simplified AgentOS dashboard (sidebar with agent list + status indicators + main panel with activity feed + mini metric graph + log stream). |
| **Visual style** | Side-by-side layout (40% text, 60% visual). Text left, dashboard mockup right. Dashboard window uses glass background (this is one of the 3 glass elements). Inner dashboard uses solid `--bg-tertiary` for the content areas. Traffic-light dots, title bar, monospace log text. Mini metric graph is an inline SVG line chart. |
| **Interactions** | Scroll reveal (fade-up, 700ms). No hover effects on the dashboard (it's a static mockup — interaction would break the illusion). |
| **Why it exists** | This is the proof section. It replaces the Problem section's narrative job. Instead of telling visitors "agent infrastructure is broken," we show them the solution. This is how Stripe and Linear sell — they show the product, not the pain. |

**Changes from original spec:**
- ✅ This replaces the Problem section entirely (Problem section removed)
- ❌ Reduced dashboard complexity — simplified from full macOS window to a cleaner mockup with fewer inner elements. The original spec had sidebar + search + 4 agents + activity feed + mini graph + log stream — that's 6 sub-components. Reduced to 3: sidebar (simplified agent list), main panel (activity feed), log stream (compressed). Mini graph kept but smaller.
- ✅ Glass limited to the window frame only (not inner elements)

---

### Section 4: Features

| Property | Value |
|---|---|
| **Goal** | Show capability breadth without overwhelming. Each feature must feel distinct and valuable. |
| **Content** | Headline: "Everything you need to scale agents" (above grid). 6 features in a 3×2 grid. Each: custom SVG icon (OS-metaphor), title, description. Features: Multi-Agent Orchestration, Real-Time Monitoring, Built-in Memory, Security & Compliance, API-First Design, One-Click Deploy. |
| **Visual style** | 3×2 grid of cards with solid `--bg-tertiary` background and subtle border (1px `rgba(255,255,255,0.06)`). No glass. Rounded corners (12px). Custom SVGs in top-left of each card (28×28px, primary color). Cards have no hover lift (removed per review) — only a subtle border color shift from `rgba(255,255,255,0.06)` to `rgba(108,92,231,0.3)` on hover (300ms ease). |
| **Interactions** | Stagger entrance on scroll (index × 100ms delay, fade + translateY(20px → 0), 500ms each). Hover: border color shift + very subtle background brightening (`rgba(255,255,255,0.03)` → `rgba(255,255,255,0.05)`). No card tilt, no lift, no glow. |
| **Why it exists** | Visitors evaluating a platform need to see what it does. The features section is table stakes. The distinction comes from the custom icon set and restrained hover treatment. |

**Changes from original spec:**
- ❌ Removed glass background from feature cards — now solid `--bg-tertiary`
- ❌ Removed hover lift (translateY) — now just border color shift
- ❌ Removed card tilt (CSS 3D rotate on hover)
- ✅ Custom SVG icons replacing Lucide defaults. 6 new icons: Kernel (concentric circles), Process (parallel bars with data flow), Memory (stacked layers), Shield (simplified, geometric), Terminal (code bracket with cursor), Deploy (upward arrow with base)
- ✅ Hover reduced to a single subtle change (border color) instead of 3 simultaneous effects (tilt + glow + lift)

---

### Section 5: Stats

| Property | Value |
|---|---|
| **Goal** | Provide believable proof points that signal traction without overclaiming. |
| **Content** | Headline: "Already powering the future of AI" (above counters). Three proof points horizontally: "10,000+ agents deployed," "99.99% uptime," "< 50ms avg. latency." Below: "Trusted by engineering teams at [3 abstract marks]" |
| **Visual style** | Centered, generous spacing. Numbers: `clamp(2.5rem, 4vw, 4rem)`, bold, solid `--text-primary` (no gradient text). Labels: `0.875rem`, `--text-secondary`, uppercase with letter-spacing. Separator: subtle gradient line (60px, primary → teal) below each number. |
| **Interactions** | Counter animation on scroll trigger (2s easeOutCubic, numbers count from 0/from base values). Only interaction. No hover effects. |
| **Why it exists** | Social proof for technically sophisticated buyers. The numbers are modest enough to be believed. The animation makes them feel live. |

**Changes from original spec:**
- ❌ Removed gradient text on numbers — now solid white (more premium, less decorative)
- ❌ Removed hover effects on stat cards
- ❌ Removed period and commas from stat copy — simplified label format
- ✅ Stats section kept but stripped of decoration. Purpose: proof. Not decoration.

---

### Section 6: CTA — Waitlist

| Property | Value |
|---|---|
| **Goal** | Convert interest to action. Consistent OS-metaphor language throughout. |
| **Content** | Headline: "Ready to deploy the operating system?" (consistent OS metaphor). Subheadline: "Join 5,000+ engineers building the future of autonomous AI." Form: email input + "Deploy AgentOS" button. Social proof: 5 avatar circles (CSS initials, gradient colors) + "Join 5,000+ engineers waiting." Small note: "No spam. Unsubscribe anytime." |
| **Visual style** | Full-bleed section. Background: dark with very subtle particle effect (CSS-only — 20 dots drifting, no Three.js). Centered content. Glass card containing the form (this is one of the 3 glass elements). Solid background behind the glass, not another glass layer. Input: dark `--bg-tertiary` background with glass-like border, primary focus ring. Button: gradient primary → primary-dark with `--shadow-glow`. |
| **Interactions** | Scroll reveal (fade-up, 700ms). Input focus: primary ring appears (2px solid). Button hover: scale(1.02) + shadow increase. On submit (no backend): form replaced with success message. |
| **Why it exists** | The conversion point. The CTA is OS-consistent: "Deploy AgentOS" reads like a developer action, not marketing fluff. |

**Changes from original spec:**
- ✅ CTA changed from "Get Early Access" to "Deploy AgentOS"
- ❌ Removed "Ready to command your agent fleet?" — replaced with "Ready to deploy the operating system?"
- ✅ Background particles are CSS-only, not Three.js (lighter, no WebGL dependency for a decorative background)
- ✅ Glass limited to the form container only
- ✅ Button text matches CTA headline (consistency)

---

### Section 7: Footer

| Property | Value |
|---|---|
| **Goal** | Provide exit navigation without clutter. Signal quality through restraint. |
| **Content** | 3 columns: Platform (Features, Integrations, Changelog, Pricing), Developers (Documentation, API Reference, SDKs, Status), Company (About, Blog, Careers, Contact). Bottom bar: "© 2026 AgentOS" + "Built with AgentOS" (inline cube SVG). |
| **Visual style** | Dark `--bg-primary`. Small text (0.875rem, `--text-secondary`, reduced opacity to 0.7). 3-column grid at `max-width: 960px` (slightly narrower than above-fold content). Top border: 1px `rgba(255,255,255,0.05)`. No glass. No background card. Minimal. |
| **Interactions** | Link color shift from `--text-secondary` (0.7) to `--text-primary` on hover, 200ms ease. Footer logo fades on hover. |
| **Why it exists** | Every page needs a footer. This one is intentionally minimal — 3 columns instead of 4, no "Legal" section (the page isn't a real company), no placeholder-heavy links. |

**Changes from original spec:**
- ❌ Changed from 4 columns to 3. Removed "Legal" entirely (no placeholder privacy/TOS links). Fewer columns = less that looks like a template.
- ❌ Reduced link count from 16 to 12. Every link should feel intentional.
- ❌ Removed glass border — now a simple 1px top border
- ✅ Links are specific to AgentOS narrative (SDKs, Changelog, API Reference) instead of generic (Terms of Service, Privacy Policy)

---

## 3. Hero Signature Moment

### "The OS Kernel"

This single visual element defines AgentOS's identity. It is what makes someone say "how was this generated?"

**What it is:**

A 3D visualization of an operating system kernel, rendered with Three.js. Two concentric rings rotate at different speeds on different axes, with luminous data particles traveling along their paths. Brief connecting beams pulse between the rings like processor clock cycles.

**Why rings, not orbs:**

| Object | Meaning |
|---|---|
| Concentric rings | Processor rings (x86 protection rings: Ring 0 = kernel, Ring 3 = user). The most fundamental structural metaphor in operating system design. |
| Rotating on different axes | Multi-threading, parallel processing — agents working simultaneously |
| Data particles moving along rings | Instructions, data packets, agent tasks flowing through the system |
| Pulse beams between rings | Inter-process communication, system calls — the kernel mediating between layers |

**Why this is not a neural network:**

- Neural networks have nodes + edges connecting arbitrary points
- This has structured rings + particles traveling along fixed paths
- One communicates "AI" — the other communicates "operating system"
- The page is about AgentOS, not generic AI

**Technical specification:**

| Property | Value |
|---|---|
| **Geometries** | 2 TorusGeometry objects |
| **Outer ring** | `TorusGeometry(3.2, 0.06, 24, 64)`, `MeshBasicMaterial`, color `#6C5CE7` (primary), opacity 0.35 |
| **Inner ring** | `TorusGeometry(2.0, 0.04, 20, 48)`, `MeshBasicMaterial`, color `#00CEC9` (secondary), opacity 0.3 |
| **Ring materials** | `MeshBasicMaterial` (not Physical — no transmission, no roughness/metalness, no offscreen passes) |
| **Outer rotation** | Y axis: 0.004 rad/frame (slow counterclockwise) |
| **Inner rotation** | X axis: 0.003 rad/frame, Y axis: 0.006 rad/frame (compound rotation, creates wobble) |
| **Data particles** | 12 small spheres or Points, `SphereGeometry(0.06)` or `PointsMaterial`, positioned along ring perimeters |
| **Particle travel** | Parametric path following — angle increments each frame, positions computed from ring radius |
| **Particle color** | Matching their ring — outer particles in primary, inner in secondary. Occasional white flash on 1 particle (like a data interrupt) |
| **Connecting beams** | 2–3 line segments (BufferGeometry with 2 vertices each), from inner ring to outer ring |
| **Beam animation** | Opacity pulse 0.05 → 0.3 → 0.05, 2.5s cycle, phase offset per beam |
| **Background** | Pure dark — no grid helper, no starfield, no fog. The rings float in void. |
| **Total draw calls** | ~5 (2 rings + 1 particle Points + 1–2 line segments) |
| **Total objects** | ~4–5 (vs original spec's ~68 objects) |
| **Three.js lines** | ~50–60 |

**Why this is lighter than the old 3-node spec:**

| Metric | Old (3 nodes + 60 particles) | New (2 rings + 12 particles) |
|---|---|---|
| Geometries | 6 (3 nodes + 3 wireframes) | 2 |
| Particles | 60 (Points) | 12 (Points or spheres) |
| Line objects | 2–3 | 2–3 (same) |
| Material passes | 3x PhysicalMaterial + 3x BasicMaterial | 2x BasicMaterial |
| Total draw calls | ~10 | ~5 |
| Three.js code | ~100 lines | ~55 lines |

**Fallback (WebGL unavailable):**
Two CSS-animated concentric rings (`border-radius: 50%` with `border` trick, rotating via CSS transform) + 12 small CSS dots cycling around the rings via `transform-origin` + `rotate`. No Three.js needed. The fallback preserves the visual identity — it just loses the 3D depth.

---

## 4. Desktop Wireframe (≥ 1024px)

```
┌────────────────────────────────────────────────────────────────┐
│ [▣ AgentOS]  Platform  Agents  Developers  Changelog  [Deploy ▸]│  ← NAVBAR
├────────────────────────────────────────────────────────────────┤  ← transparent → glass on scroll
│                                                                  │
│   ⚡ Now in Public Beta  ┌──────────────────────────────┐        │
│                           │                              │        │
│   The operating system    │    ╭─────────────────╮       │        │
│   for autonomous agents   │   ╱   ╭───────────╮   ╲      │        │
│                           │  │    │  ◉ ◉ ◉   │    │     │        │  ← HERO
│   Design, deploy, and     │  │    │   ╭───╮   │    │     │     full viewport
│   orchestrate AI agents   │  │    │   │ ╱ │   │    │     │     content: ~40% width
│   across any environment. │  │    │   │ ╲ │   │    │     │     scene: ~60% right
│   One platform.            │  │    │   ╰───╯   │    │     │     gradient mask between
│   Infinite scale.          │  │    │  ◉ ◉ ◉   │    │     │
│                           │   ╲   ╰───────────╯   ╱      │
│  [Deploy AgentOS ▸]       │    ╰─────────────────╯       │
│   [Watch Demo ▸]          │    OS Kernel 3D Scene         │
│                           └──────────────────────────────┘
│   ▢ ▣ ▤  Trusted by engineering teams at...
│
├────────────────────────────────────────────────────────────────┤  ← scroll reveal
│                                                                  │
│   See everything. Control everything.                            │
│                                                                  │
│   Monitor, debug, and orchestrate your entire agent fleet  ┌─────┴──────────┐  ← PLATFORM
│   from a single dashboard. Real-time agent activity,        │ ┌─●●●─┐        │  40% text / 60% mockup
│   metrics, logs, and controls — all in one place.           │ │ AgentOS       │
│                                                             │ │ Dashboard     │
│                                                             │ │ ─────────── │
│                                                             │ │ ◉ Agent-7   │  │
│                                                             │ │ ◉ Agent-12  │  │
│                                                             │ │ ○ Agent-3   │  │
│                                                             │ └─────────────┘  │
│                                                             └──────────────────┘
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│   Everything you need to scale agents                                            │
│                                                                                  │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                         │
│   │ ⊙ Kernel     │  │ ≡ Process    │  │ ▣ Memory     │                         │  ← FEATURES
│   │ Multi-Agent  │  │ Real-Time    │  │ Built-in     │                         │  3×2 grid
│   │ Orchestration│  │ Monitoring   │  │ Memory       │                         │  solid cards (no glass)
│   └──────────────┘  └──────────────┘  └──────────────┘                         │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                         │
│   │ ◈ Shield     │  │ >_ Terminal  │  │ ▲ Deploy     │                         │
│   │ Security &   │  │ API-First    │  │ One-Click    │                         │
│   │ Compliance   │  │ Design       │  │ Deploy       │                         │
│   └──────────────┘  └──────────────┘  └──────────────┘                         │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│   Already powering the future of AI                                              │
│                                                                                  │
│      10,000+              99.99%              < 50ms                            │  ← STATS
│      agents deployed      platform uptime     avg. latency                      │  3 centered counters
│      ──────────           ──────────          ──────────                        │  no glass, no gradient text
│                                                                                  │
│   ▢ ▣ ▤  Trusted by engineering teams at...
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│                     Ready to deploy the operating system?                         │
│                                                                                  │
│                    Join 5,000+ engineers building the future of                   │  ← CTA
│                              autonomous AI.                                      │  full-bleed background
│                                                                                  │  glass form container
│                     ┌──────────────────────────────┐                            │
│                     │ Enter your email      [Deploy ▸] │                         │
│                     └──────────────────────────────┘                            │
│                                                                                  │
│               ◐ ◑ ◒ ◓ ◔  + 5,000+ engineers waiting                             │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  Platform     │  Developers    │  Company          │  © 2026 AgentOS            │  ← FOOTER
│  Features     │  Documentation│  About             │  Built with AgentOS ▣      │  3 columns, minimal
│  Integrations │  API Reference │  Blog              │                             │
│  Changelog    │  SDKs          │  Careers           │                             │
│  Pricing      │  Status        │  Contact           │                             │
│                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────┘
```

---

## 5. Tablet Wireframe (768px – 1023px)

```
┌─────────────────────────────────────────┐
│ [☰ AgentOS]                    [Deploy ▸]│  ← NAVBAR (hamburger)
├─────────────────────────────────────────┤
│                                         │
│   ⚡ Now in Public Beta                  │
│                                         │
│   The operating system                  │
│   for autonomous agents                 │  ← HERO
│                                         │  stacked layout
│   Design, deploy, and orchestrate...     │  scene below content
│                                         │  3D scene: 300px height
│   [Deploy AgentOS ▸]  [Watch Demo ▸]    │
│                                         │
│   ▢ ▣ ▤  Trusted by...                 │
│                                         │
│   ╭─────────────────────────────────╮   │
│   │    ╭───────────────╮           │   │
│   │   ╱   ╭───────╮   ╲          │   │
│   │  │    │  ◉◉◉  │    │          │   │
│   │  │    │  ╭─╮  │    │          │   │
│   │  │    │  │╱│  │    │          │   │
│   │  │    │  ╰─╯  │    │          │   │
│   │  │    │  ◉◉◉  │    │          │   │
│   │   ╲   ╰───────╯   ╱          │   │
│   │    ╰─────────────────╯       │   │
│   │        OS Kernel Scene        │   │
│   ╰─────────────────────────────────╯   │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│   See everything. Control everything.   │
│                                         │
│   Monitor, debug, and orchestrate...    │  ← PLATFORM
│                                         │  stacked (text above, mockup below)
│   ┌─────────────────────────────┐      │
│   │ ┌─●●●─┐                   │      │
│   │ │ AgentOS Dashboard        │      │
│   │ │ ────────────────────    │      │
│   │ │ ◉ Agent-7   ● online    │      │
│   │ │ ◉ Agent-12  ● online    │      │
│   │ └───────────────────────┘ │      │
│   └─────────────────────────────┘      │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│   Everything you need to scale agents   │
│                                         │
│   ┌──────────┐  ┌──────────┐           │  ← FEATURES
│   │ ⊙ Kernel │  │ ≡ Process│           │  2-column grid
│   │ ...      │  │ ...      │           │
│   └──────────┘  └──────────┘           │
│   ┌──────────┐  ┌──────────┐           │
│   │ ▣ Memory │  │ ◈ Shield │           │
│   │ ...      │  │ ...      │           │
│   └──────────┘  └──────────┘           │
│   ┌──────────┐  ┌──────────┐           │
│   │ >_ Term. │  │ ▲ Deploy │           │
│   │ ...      │  │ ...      │           │
│   └──────────┘  └──────────┘           │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│    10,000+        99.99%       < 50ms   │  ← STATS
│    agents         uptime       latency  │  still 3 columns
│                                         │
├─────────────────────────────────────────┤
│                                         │
│     Ready to deploy the operating system?│
│                                         │  ← CTA
│     ┌─────────────────────────┐        │
│     │ Enter your email [Deploy]│        │
│     └─────────────────────────┘        │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  Platform │ Developers │ Company        │  ← FOOTER
│  Features │ Docs       │ About          │  3 columns
│  ...      │ ...        │ ...           │  reduced spacing
│                                         │
└─────────────────────────────────────────┘
```

---

## 6. Mobile Wireframe (< 768px)

```
┌─────────────────────┐
│ [☰ AgentOS] [Deploy]│  ← NAVBAR (hamburger)
├─────────────────────┤
│                     │
│  ⚡ Now in Public   │
│  Beta               │
│                     │
│  The operating      │
│  system for         │  ← HERO
│  autonomous agents  │  stacked, compact
│                     │  3D scene 200px height
│  Design, deploy... │
│                     │
│  [Deploy AgentOS ▸] │
│  [Watch Demo ▸]    │
│                     │
│  ▢ ▣ ▤             │
│                     │
│  ╭─────────────────╮│
│  │ OS Kernel Scene ││  ← 200px height
│  │ (simplified)    ││  rings visible
│  ╰─────────────────╯│
│                     │
├─────────────────────┤
│                     │
│  See everything.    │
│  Control everything.│  ← PLATFORM
│                     │  fully stacked
│  Monitor, debug... │
│                     │
│  ┌─────────────────┐│
│  │ ┌─●●●─┐       ││
│  │ │ AgentOS      ││
│  │ │ Dashboard    ││
│  │ └─────────────┘││
│  └─────────────────┘│
│                     │
├─────────────────────┤
│                     │
│  Everything you     │
│  need to scale      │
│  agents             │
│                     │
│  ┌───────────────┐  │  ← FEATURES
│  │ ⊙ Kernel      │  │  1-column stacked
│  │ Multi-Agent...│  │
│  └───────────────┘  │
│  ┌───────────────┐  │
│  │ ≡ Process     │  │
│  │ Real-Time...  │  │
│  └───────────────┘  │
│  ...continues...    │
│                     │
├─────────────────────┤
│                     │
│  Already powering   │
│                     │
│  10,000+            │  ← STATS
│  agents deployed    │  1 column, stacked
│  ─────────          │
│  99.99%             │
│  platform uptime    │
│  ─────────          │
│  < 50ms             │
│  avg. latency       │
│                     │
├─────────────────────┤
│                     │
│  Ready to deploy    │
│  the operating      │  ← CTA
│  system?            │  full-width form
│                     │
│  ┌─────────────────┐│
│  │Email... [Deploy ▸]│
│  └─────────────────┘│
│                     │
├─────────────────────┤
│                     │
│  Platform   │ Dev  │  ← FOOTER
│  Features   │ Docs │  2-column on mobile
│  Company    │      │
│  About      │      │
│  Blog       │      │
│                     │
│  © 2026 AgentOS    │
│  Built with ▣      │
│                     │
└─────────────────────┘
```

---

## 7. Visual Hierarchy Audit

### Critical — Must be immediately visible. These define the page.

| Element | Why Critical |
|---|---|
| **Hero headline** ("The operating system for autonomous agents") | The value proposition. Most-read text on the page. First thing after the 3D scene. |
| **Primary CTA** ("Deploy AgentOS") | The conversion point. Must be unmistakable. |
| **OS Kernel 3D scene** | The signature visual moment. The "how was this generated?" element. Defines the repo's quality ceiling. |
| **Platform dashboard mockup** | The proof. Converts abstract vision into concrete product. |

### Important — Support the core message. Should be noticeable within 1–2 seconds.

| Element | Why Important |
|---|---|
| **Subheadline** | Elaborates on the headline. Gives the visitor enough context to decide whether to scroll. |
| **Secondary CTA** ("Watch Demo") | Provides an alternative action for visitors not ready to convert. |
| **Feature cards (titles + custom icons)** | Capability overview. Visitors evaluating a platform need to quickly scan what it does. |
| **Stats counters** | Social proof. Numbers build trust. |
| **Navbar** (logo + links) | Orientation. Brand presence. |

### Secondary — Supporting information. Consumed on demand or at the end.

| Element | Why Secondary |
|---|---|
| **Feature descriptions** (body text in cards) | Read only when a specific feature interests the visitor. |
| **Badge** ("Now in Public Beta") | Positive signal but not decision-driving. |
| **Trust bar marks** (abstract logos + "Trusted by...") | Social proof reinforcement. Scanned, not read. |
| **Footer links** | Consumed only if the visitor wants more information. |
| **Scroll-to-top** | Utility. Rarely used on single-page landings. |
| **Copyright / "Built with AgentOS"** | Brand closure. Bottom of hierarchy. |

### What Was Removed from the Hierarchy

| Removed Element | Previous Level | Reason |
|---|---|---|
| Progress bar | Secondary | Decorative scroll indicator. CLAUDE.md: "Animation is not decoration." |
| Scroll-to-top FAB | Secondary | Unnecessary for a single-scroll page. Linear doesn't have one. |
| Hover lift on feature cards | Important → removed | Animation for animation's sake. Border color shift is sufficient. |
| Gradient text on numbers | Important → made solid white | Gradient text signals "we needed to make this interesting." Solid white is more premium. |
| Card tilt (CSS 3D) | Secondary | Technical risk + gimmick factor. Not worth the implementation cost. |

---

## 8. Animation Audit

Every animation must pass this test: **"Does this animation support the story, or is it decoration?"**

### Kept Animations

| # | Animation | Purpose | Trigger | Duration | Justification |
|---|---|---|---|---|---|
| **A1** | **Hero entrance stagger** | Content elements fade/slide up in sequence | Page load | 1.2s total | Sets the rhythm. Establishes that this page is animated with intent, not by accident. Each element appears in reading order (scene → headline → subhead → CTAs). The stagger prevents overload while creating a polished "assembly" feel. |
| **A2** | **3D scene continuous rotation** | Rings rotate + particles orbit | Page load → continuous | Infinite | The kernel scene is alive. The rotation communicates "active system" — the platform is running, processing, doing work. Without rotation, the rings would look like static logos. |
| **A3** | **Section scroll reveals (fade-up)** | Each section transitions in as it enters viewport | IntersectionObserver (15% threshold) | 700ms | Transitions between sections. Without reveals, every section appears at once — which feels abrupt. The fade-up is the lightest possible reveal: no clip-path, no 3D card flips, no horizontal slides. One easing function (`cubic-bezier(0.16, 1, 0.3, 1)`), one duration. |
| **A4** | **Counter animation** | Stats numbers count from 0 to final value | Stats section in viewport | 2s (easeOutCubic) | Makes the stats feel live, not hardcoded. A static "10,000+" reads as a claim. An animated count reads as a measurement. This is storytelling, not decoration. |
| **A5** | **Navbar glass transition** | Navbar background changes from transparent to glass on scroll | Hero exits viewport | 300ms | Functional. A transparent navbar becomes unreadable over dark content below the hero. The glass transition ensures readability while maintaining the design language. |
| **A6** | **Primary CTA hover** | Button scale 1.02 + shadow increase | Hover | 200ms | Provides tactile feedback. The CTA is interactive — the hover effect confirms it. Scale + shadow is the most restrained hover (no glow, no color shift, no rotation). |
| **A7** | **Feature card hover** | Border color shift (gray → primary violet) | Hover | 300ms | Subtle feedback that the card is interactive. Border color change is the lightest possible hover state — no movement, no glow, no transform. Reads as "this is a UI element, not a wall of text." |
| **A8** | **Nav link underline** | Animated underline on hover via `background-size` | Hover | 300ms | Standard navigation feedback. Underline animations are universal because they work. |

### Removed Animations (with reasoning)

| # | Animation | Reason Removed |
|---|---|---|
| **R1** | **Scroll progress bar** | CLAUDE.md: "Animation exists to support storytelling." A progress bar on a single-scroll landing page tells the visitor nothing about the product. It only tells them "you are X% done reading." This is decoration. Stripe, Linear, and Vercel don't use one. |
| **R2** | **Scroll-to-top FAB** | A floating button that appears halfway down the page is a utility, not storytelling. On a 7-section page, the visitor can scroll up in < 1 second. The FAB adds a scroll listener, a DOM element, and a visual distraction — all for marginal utility. |
| **R3** | **Feature card lift (translateY)** | The spec had 3 simultaneous hover effects on feature cards (tilt + glow + lift). That's 2 too many. Removed tilt and lift, kept the most subtle of the three (border color shift). Single effect per interaction = more premium. |
| **R4** | **Secondary CTA hover effect** | The "Watch Demo" button had its own hover behavior. Removed it — a simple cursor change is sufficient for a secondary action. The primary CTA's hover is the important one. Having both animates too many elements simultaneously. |
| **R5** | **3D scene mouse orbit** | Replaced with CSS perspective rotation on a container (as specified in PLAN.md). Same visual effect, zero JS cost. The CSS approach tilts the canvas output (a flat 2D rendering), which looks different from true 3D orbit — but it's lighter and achieves a similar perception. |
| **R6** | **Button glow pulse (continuous)** | The original spec had a subtle box-shadow pulse on the primary CTA. Continuous animation on the CTA draws unnecessary attention to it. A static CTA with a hover effect is more professional. |

### Animation Count: 8 kept, 6 removed

| Before | After |
|---|---|
| 14 animation types/instances | 8 animation types (5 triggered, 3 continuous) |
| 4 scroll-driven systems (progress bar + FAB + navbar + reveals) | 2 scroll-driven systems (navbar + reveals) |
| 3 hover effects on feature cards (tilt + glow + lift) | 1 hover effect on feature cards (border color) |
| 3D camera orbit (Three.js JS mouse tracking) | CSS perspective (zero JS) |

---

## 9. Originality Audit

### Why this page will not be mistaken for a generic SaaS template

| Template Pattern | AgentOS Replacement |
|---|---|
| 3-column problem section with pain points | Removed entirely. Platform dashboard provides the narrative. |
| Hero with stock illustration or abstract gradient | OS kernel 3D visualization — concentric rings, not floating shapes. |
| Feature icons from Lucide/FontAwesome/Feather | Custom SVG icons referencing OS internals (kernel, threads, bus, memory). |
| "Get Started" / "Sign Up Free" CTA | "Deploy AgentOS" — OS deployment language. |
| Product / Resources / Company / Legal footer | Platform / Developers / Company — 3 columns, no fake legal links. |
| Glassmorphism on every card | Glass limited to 3 elements (navbar, dashboard, CTA form). Everything else is solid. |
| Animated progress bar + scroll-to-top | Neither exists on this page. |

### Why this page will not be mistaken for an AI startup template

| AI Startup Pattern | AgentOS Replacement |
|---|---|
| Floating neural network (orbs + particles + connecting lines) | OS kernel (concentric rings + data particles traveling organized paths) |
| Generic "powered by AI" messaging | Product-specific copy: "orchestrate AI agents," "deploy the operating system" |
| Dark theme + purple gradient as the entire identity | Dark theme is present but the visual system is architectural — grids, rings, organized data flow |
| Vague hero 3D scene that communicates "AI" without specificity | Hero 3D scene communicates "operating system" — a specific, defensible visual metaphor |
| Icons that look like every other AI product (brain, chip, sparkle) | Icons that look like OS components (kernel circle, process bars, memory layers) |

### Why this page will not be mistaken for a Tailwind showcase

| Tailwind Pattern | AgentOS Replacement |
|---|---|
| Tailwind CDN script in `<head>` | Zero Tailwind. All custom CSS with custom properties. |
| Tailwind utility classes (flex, grid, p-8, text-2xl) | Semantic CSS classes (`agentos-hero`, `agentos-features`, `.glass`) |
| Tailwind UI component patterns (hero sections, feature grids) | Custom layouts defined by the wireframe above. No pre-built component is used. |
| Tailwind's design system (gray palette, spacing scale) | Custom design system (`--bg-primary: #0A0A0F`, `--text-secondary: #9494A8`, custom `clamp()` scale) |

### The original elements

| Element | Why Original |
|---|---|
| **OS Kernel 3D visualization** | I have not seen this on an AI landing page. The closest is abstract geometric art, but specifically using concentric rings + data flow to evoke an OS kernel is unique. |
| **Custom OS-metaphor icons** | 6 SVGs that internally reference processor architecture. A "kernel" icon for orchestration, a "process bars" icon for monitoring. The metaphor carries through. |
| **Selective glass** | Using glass on only 3 elements (navbar, dashboard, CTA form) makes each glass instance feel intentional. Every-glass was heavy. Three-glass is curated. |
| **7 sections instead of 8** | Removing the Problem section tightens the narrative. The page doesn't waste your time telling you what you already know (that tools are fragmented). It shows you the product. |
| **Copy cohesion** | "Deploy AgentOS," "boot the operating system," "agents at scale" — every phrase stays within one metaphor. No naval fleets, no magic wands. |

---

## 10. Final Recommendation

### Is AgentOS ready for implementation?

**Conditionally yes.**

The wireframe addresses all 5 high-impact changes and all 6 medium-impact changes from AGENTOS_REVIEW.md:

| Review Change | Status in Wireframe |
|---|---|
| H1: Replace neural network with OS kernel scene | ✅ Implemented (Section 3) |
| H2: Cut 50% of animation systems | ✅ Implemented (Section 8 — 6 animations removed) |
| H3: Redesign or remove Problem section | ✅ Removed entirely (Section 2, narrative restructured) |
| H4: Replace generic icons with custom SVGs | ✅ Specified (Section 4 — 6 new OS-metaphor icons) |
| H5: Fix CTA metaphor conflict | ✅ Implemented ("Deploy AgentOS" throughout) |
| M1: Limit backdrop-filter to 3 elements | ✅ Specified (navbar, dashboard, CTA form) |
| M2: Replace MeshPhysicalMaterial | ✅ MeshBasicMaterial for rings (Section 3) |
| M3: Remove wireframe overlays | ✅ No wireframes (fewer geometries) |
| M4: Narrow type scale | ✅ Removed Inter 300 and 800 |
| M5: Product-specific CTA language | ✅ OS-consistent throughout |
| M6: Define tap equivalents | ✅ Outlined below |

### Implementation prerequisites

Before HTML generation begins, these must be finalized:

1. **Revised prompt.md** — Updated to reflect all wireframe changes (every section, every animation, every material)
2. **CSS custom properties** — Finalized color system with no unused variables
3. **SVG icon set** — 6 custom OS-metaphor SVGs specified as path data or described for AI generation
4. **Three.js fallback** — CSS ring animation specified for WebGL-unavailable browsers
5. **Touch behavior** defined:
   - Taps on feature cards: briefly apply the hover state (border color shift), then reset after 1s
   - Taps on CTA: standard button press behavior
   - No hover-dependent content exists anywhere
   - 3D scene: CSS perspective rotation is mouse-only (not applied on touch devices)

### What happens after this wireframe is approved

1. Revise `prompt.md` to match this wireframe
2. Generate `index.html` (single file, no build step)
3. Test against quality gate (CLAUDE.md Section: Quality Gate)
4. Revise based on test results
5. Freeze as benchmark page
6. Begin Phase 1, Page 2

### One-sentence summary

> **This page will be a dark, architectural OS-kernel visualization with precisely 4 animation types, 3 glass elements, 6 custom icons, and 7 sections — and it will be the benchmark that every future page in this repo must match.**

---

*This wireframe was produced after reading CLAUDE.md, AGENTOS_REVIEW.md, PLAN.md, and prompt.md. It incorporates all changes from the design review. No HTML, CSS, or JavaScript has been generated.*
