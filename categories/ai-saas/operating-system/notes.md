# Operating System — Design Notes

> **Pattern:** OS-themed AI SaaS landing page
> **This is the benchmark page** — the first page in the repository, demonstrating the full generation process.

---

## The Design Process

This page was not generated in one shot. It went through a deliberate multi-stage pipeline:

```
Prompt → Plan → Design Review → Wireframe → Generation Contract → Revise → Generate → Validate
```

### Stage 1: Initial Concept (prompt.md)

The first prompt defined an AI agent orchestration platform. The original version had:
- A neural network hero visualization
- 14 animation types
- A "Problem" section
- 4-column footer with "Legal"
- Glassmorphism on every section
- Stock icons (Lucide)

### Stage 2: Design Review (AGENTOS_REVIEW.md)

The initial design was reviewed against the repo's design principles. **5 key findings** led to a complete re-architecture:

| Finding | Problem | Resolution |
|---|---|---|
| H1 | Neural network visualization is generic. Every AI SaaS uses it. | Replace with **OS kernel rings** — 2 concentric TorusGeometry, MeshBasicMaterial, teal + violet |
| H2 | 14 animation types is excessive — animation spam | Cut to **8 types**, remove progress bar, tilt, glow, parallax, FAB |
| H3 | "Problem" section is template SaaS structure | Remove entirely. Replace with "Platform" section showing the dashboard |
| H4 | Stock icons (Lucide) look generic | **6 custom inline SVGs**: Kernel, Process, Memory, Shield, Terminal, Deploy |
| H5 | Copy is generic startup language ("fleet", "command") | **OS-consistent language**: "Deploy AgentOS", "47 agents online" |

### Stage 3: Wireframe (WIREFRAME.md)

ASCII wireframes defined exact pixel-level layout for every breakpoint:
- **Desktop (≥1024px):** 3D scene as full-height background, content overlaid left ~40%
- **Tablet (768-1023px):** Content stacks, 2-column features, 3-column stats
- **Mobile (<768px):** 3D scene at 200px, fully stacked layout, hamburger menu

### Stage 4: Generation Contract (GENERATION_CONTRACT.md)

A binding specification that locked scope before code generation:
- **Scope lock:** Exactly 12 particles, 8 animations, 3 glass elements, 6 SVGs
- **Hard budgets:** <200 KB total, ≤3 external requests, zero console errors
- **34-item acceptance checklist** covering structure, visual, animation, performance, originality
- **16 contract violations** documented (10 critical) — any critical violation = automatic failure

### Stage 5: Revision + Generation

The prompt was revised per the review findings, then the HTML was generated in one pass.

### Stage 6: Validation

The generated page was verified against all 82 checklist items:
- **82/82 passing (100%)**
- **Zero console errors**
- **100 KB total page weight** (10.5 KB gzipped HTML + 67 KB Three.js r128 + 23 KB Google Fonts)
- **Lighthouse estimated 90-95** across all categories

---

## Key Design Decisions

### Why OS Kernel Visualization?

The hero scene uses 2 concentric TorusGeometry rings rotating at different speeds:
- **Outer ring** (radius 3.2, primary `#6C5CE7`, opacity 0.35) — represents the system boundary
- **Inner ring** (radius 2.0, secondary `#00CEC9`, opacity 0.30) — represents the kernel core
- **12 particles** (6 outer, 6 inner) travel on fixed ring paths — represents data threads
- **3 connecting beams** pulse with sine-based opacity — represents inter-process communication

This creates a **signature visual** that feels like an operating system monitor, not another neural network visualization.

### Glassmorphism Discipline

Glass (`backdrop-filter: blur(16px)`) is limited to exactly 3 elements:
1. Navbar (on scroll)
2. Dashboard window
3. CTA form container

No glass on feature cards, stats, or footer. This makes the glass elements feel intentional rather than a design crutch.

### Custom SVG Icon System

6 inline SVGs replace all stock icons:
- **Kernel** — concentric circles (system core)
- **Process** — parallel bars with flow line (multi-tasking)
- **Memory** — stacked layers (persistence)
- **Shield** — security mark (compliance)
- **Terminal** — prompt with cursor (API-first)
- **Deploy** — arrow upward (one-click deploy)

Each icon is 28×28, minimal stroke, using `currentColor` for theme integration.

### Animation Budget

Exactly 8 animation types, no more:

| # | Animation | Trigger | Property |
|---|---|---|---|
| 1 | Hero stagger entrance | Page load | opacity + translateY |
| 2 | 3D ring rotation | Continuous | rotation.y/rotation.x |
| 3 | Section reveals | Scroll (IntersectionObserver) | opacity + translateY |
| 4 | Stats counter | Scroll (IntersectionObserver) | textContent with easeOutCubic |
| 5 | Navbar glass | Scroll (hero exit) | background + backdrop-filter |
| 6 | CTA button hover | Mouse | scale + box-shadow |
| 7 | Card border hover | Mouse | border-color + background |
| 8 | Nav underline | Mouse | transform: scaleX |

### Performance Budgets

| Constraint | Target | Achieved |
|---|---|---|
| Total page weight | <200 KB | ~100 KB |
| External requests | ≤3 | 3 (Three.js r128 + 2 Google Fonts) |
| Console errors | 0 | 0 |
| HTML gzipped | — | 10.5 KB |
| Particles | Exactly 12 | 12 |
| Glass elements | Exactly 3 | 3 |
| Feature cards | 6 | 6 |
| Animation types | 8 | 8 |
| Custom SVGs | 6 | 6 |
| Draw calls | ~5 | ~5 |

---

## What to Steal From This Page

### Techniques worth reusing

1. **Three.js scene with MeshBasicMaterial** — minimal GPU cost, no lighting calculations, clean render
2. **CSS fallback for WebGL** — concentric rings with CSS pseudo-elements + orbiting dots with `transform: rotate() translateX()`
3. **`clamp()` typography** — responsive type that scales smoothly without breakpoints
4. **CSS perspective on mouse** — lightweight interactive effect without JS 3D math
5. **Inline SVG system** — zero network requests for icons, themable via `currentColor`
6. **Staggered section reveals** — feature cards enter with 100ms delay between each

### Pitfalls to avoid

1. **Too many animation types** — the original 14 animations were cut to 8. Less is more.
2. **Glass on everything** — limited to 3 elements. Glass loses its impact when overused.
3. **Gradient text** — headlines in solid white read better than purple gradients.
4. **Stock icons** — custom SVGs take 15 minutes to design but make the page feel original.
5. **Generic 3D** — neural networks, glowing orbs, and particle fields are overused. Pick a specific visual metaphor.

---

## For Future Pages

This page documents the full process. Future pages in this repo will follow a simplified workflow:

```
prompt.md → Index.html → preview.png → notes.md
```

The process docs (design review, wireframe, contract, implementation report) exist only for this benchmark page. They demonstrate the methodology. New pages just need the output files.

---

## File Size Breakdown

| File | Size | Notes |
|---|---|---|
| `index.html` | 44 KB (10.5 KB gzipped) | Self-contained, all CSS + JS inline |
| `prompt.md` | 24 KB | The prompt that generated this page |
| `preview.png` | ~200 KB | Screenshot at 1440×900 |
| `notes.md` | ~8 KB | This file |
