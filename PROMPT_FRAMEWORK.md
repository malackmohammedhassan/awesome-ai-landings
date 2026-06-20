# Prompt Framework

> The master recipe for generating premium landing pages with AI. Every page in this repo starts with a prompt built from these 12 parameters.

---

## Why a Framework?

Without structure, AI-generated designs drift toward the mean — generic, safe, forgettable. This framework forces specific, opinionated decisions at every layer. A good prompt produces a good page. A great prompt, built from these parameters, produces a great design.

---

## The 12 Parameters

Every prompt must address all 12 sections. Missing one is the difference between "looks AI-generated" and "looks like a real brand."

---

### 1. Role

Who is the AI acting as?

```
You are a senior product designer and front-end engineer at a top-tier
design agency. You specialize in premium landing pages for [category]
brands. You combine mastery of visual design (typography, color theory,
composition) with modern front-end engineering (CSS, JavaScript, Three.js).
```

**Why:** Setting the role primes the AI's knowledge distribution. A "senior designer" produces different output than a "junior developer."

---

### 2. Audience

Who is this page for?

```
The audience is [description]. They are:
- Technically sophisticated
- Visually literate
- Short on attention (make the first impression count)
- Evaluating whether this product/brand is premium
```

**Examples:**
- AI SaaS: CTOs, developers, founders evaluating AI tools
- Coffee: Urban professionals, specialty coffee enthusiasts
- Fintech: Investors, high-net-worth individuals, tech-forward consumers

**Why:** The AI adjusts tone, density, and visual language when it knows who's looking.

---

### 3. Brand

Define the fictional brand with specificity.

```
Brand name: [Name]
Tagline: [One line]
Brand archetype: [Magician / Hero / Explorer / Creator / Sage]
Personality: [3-5 adjectives]
Voice: [Technical, warm, authoritative, playful, minimalist]
Core promise: [What does this brand deliver?]
```

**Example for an AI SaaS brand:**
```
Brand name: Neural Cloud
Tagline: "Deploy intelligence. Scale without limits."
Brand archetype: Magician
Personality: Visionary, precise, bold, futuristic
Voice: Confident but accessible, technical but not cold
Core promise: Infinite AI compute, zero infrastructure headache
```

**Why:** A well-defined brand gives the AI a character to design for, not just a layout to fill.

---

### 4. Visual Style

The aesthetic direction.

```
Style: [Minimalist / Futuristic / Organic / Industrial / Luxe / Playful]
Key inspirations: [Design movements, known brands, visual references]
Core visual metaphor: [One unifying image or concept]
Texture / feel: [Smooth, glass-like, paper-textured, neon-edged, etc.]
```

**Examples:**
- AI SaaS: "Futuristic, clean, glassmorphism + floating 3D particles, dark mode with cyan/indigo gradient accents"
- Coffee: "Warm, organic, tactile, paper textures, rich browns + deep greens, hand-drawn flourishes"
- Fintech: "Sleek, sophisticated, dark theme with gold/emerald accents, data-driven layouts, precision typography"

**Why:** This is the north star for every visual decision.

---

### 5. Color System

Exact color specifications.

```css
:root {
  --primary: <hex>;
  --primary-light: <hex>;
  --primary-dark: <hex>;
  --secondary: <hex>;
  --accent: <hex>;
  --neutral-100: <hex>;
  --neutral-300: <hex>;
  --neutral-500: <hex>;
  --neutral-700: <hex>;
  --neutral-900: <hex>;
  --bg-primary: <hex>;
  --bg-secondary: <hex>;
  --text-primary: <hex>;
  --text-secondary: <hex>;
  --gradient-hero: <gradient>;
  --gradient-card: <gradient>;
  --shadow-sm / --shadow-md / --shadow-lg: <values>;
}
```

**Guidelines:**
- No more than 3 core colors + 1 accent
- Dark mode is preferred for AI SaaS and Fintech; light mode for Coffee and Creative
- Gradients should be subtle, not garish (unless the brand calls for neon)
- Always specify both background and text contrast pairs

---

### 6. Layout

The page structure.

```
Structure:
  Navbar: [Sticky/transparent, full-width/centered, logo left + links right + CTA]
  Hero: [Full-viewport / split / centered / diagonal-cut]
  Section 1: [Problem / Introduction]
  Section 2: [Solution / How it works]
  Section 3: [Features / Grid]
  Section 4: [Stats / Testimonials / Proof]
  Section 5: [Call to Action]
  Footer: [Links / social / legal]

Grid system: [CSS Grid / Flexbox / custom]
Max content width: [1100px / 1200px / full-bleed]
Section padding: [120px desktop, 60px mobile]
```

**Section options (choose 5–7):**
- Hero
- Logo cloud / social proof
- Problem illustration
- How it works (3-step)
- Features grid (3×2, 4×2, staggered)
- Stats / counters
- Testimonials (carousel or cards)
- Pricing (3 tiers)
- FAQ (accordion)
- Blog / resources preview
- CTA (final push)
- Footer

**Why:** Without specifying the structure, the AI may invent a boring 3-section layout or ramble into 15 sections.

---

### 7. Animations

The motion design spec.

```
Entrance:
  Hero: stagger children by [100ms], [fade + slide up], duration [600ms], ease [power2.out]
  Each section: [clip-path reveal / fade-up / scale-in] triggered at [80%] viewport intersection
  Duration: [500-800ms], ease: [cubic-bezier(0.16, 1, 0.3, 1)]

Scroll:
  Progress bar: [top-fixed, gradient matching brand]
  Parallax: [hero background moves at 0.3x scroll speed]
  [Section 3]: cards animate in from [left/right] staggered by [100ms]

Hover:
  Buttons: [scale 1.05 + shadow increase + subtle glow]
  Cards: [tilt on mouse move via 3D transform]
  Nav links: [underline slide-in or color shift]

Continuous:
  Background: [subtle gradient animation cycling over 10s]
  Floating element: [hero 3D shape rotates slowly on Y axis]
```

**Why:** Ambiguous animation instructions produce default/janky effects. Be specific about trigger, timing, and behaviour.

---

### 8. 3D Effects

3D is the differentiator. Specify how it's used.

```
3D approach: [CSS 3D transforms / Three.js / Pure CSS perspective]

If Three.js:
  Scene: [floating geometric shapes / particles / rotating logo / abstract environment]
  Interaction: [mouse-tracked rotation / scroll-driven depth]
  Performance: [renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))]
  Fallback: [static gradient background if WebGL unavailable]

If CSS 3D:
  Cards: [perspective: 1000px, rotateY on hover, transform-style: preserve-3d]
  Hero: [layered depth with translateZ]
  Depth elements: [at least 3 layers moving at different speeds]
```

**Golden rule:** 3D must serve the brand, not distract from it. A fintech page should not have playful bouncing cubes.

---

### 9. Sections Content

What goes in each section.

```
[Hero]
  Headline: [10 words max, benefit-driven]
  Subheadline: [20 words max, supporting value prop]
  Primary CTA: [Button text]
  Secondary CTA: [Link or ghost button]
  Visual: [3D scene / illustration / video bg / abstract art]

[Features — 3x2 grid]
  For each feature:
    Icon: [Lucide icon name]
    Title: [2-4 words]
    Description: [12-18 words]

[Stats]
  3 numbers with labels, animated counter on scroll

[Testimonials]
  2-3 quotes with name, title, company

[CTA]
  Headline: [benefit-driven]
  Button: [action-oriented]
```

---

### 10. Interactions

How the user interacts.

```
Mouse:
  Custom cursor: [yes/no — only if brand supports it]
  Magnetic buttons: [buttons subtly follow cursor within bounds]
  Card tilt: [3D rotateY based on mouse position]

Scroll:
  Scroll-triggered progress bar
  Sticky navigation highlights current section
  Scroll-triggered counter animation
  Section pins while content transforms (optional)

Click:
  Smooth scroll to sections via nav links
  Mobile hamburger with slide-in overlay
  Modal or expand for detail content (optional)

Touch:
  Swipe carousel for testimonials (mobile)
  Tap targets >= 44px
  No hover-dependent interactions
```

---

### 11. Performance Constraints

Hard requirements for the AI.

```
- Inline critical CSS in <head> for above-the-fold content
- Defer all JS with <script defer> or type="module"
- No external images unless essential (prefer CSS/SVG/Three.js)
- All animations use GPU-composited properties (transform, opacity)
- No render-blocking resources
- Total JS < 300KB, total CSS < 50KB
- Lighthouse target: > 90 all categories
```

---

### 12. Output Requirements

The exact deliverable format.

```
Generate a single file: index.html

Requirements:
  - All CSS in a single <style> block within the <head>
  - All JS in a single <script> block at end of <body>
  - External libraries via CDN (Three.js, GSAP, etc.)
  - Responsive: works at 375px, 768px, 1440px
  - Must pass HTML5 validation (no unclosed tags)
  - Font: Google Fonts, subset to used weights
  - Design must be unique — no similarity to any other page in the repo
```

---

## Putting It Together

Here's how a filled-out prompt looks:

```markdown
You are a senior product designer and front-end engineer at a top-tier
design agency specializing in AI SaaS landing pages...

[Brand]
Neural Cloud — "Deploy intelligence. Scale without limits."
Archetype: Magician. Personality: Visionary, precise, bold, futuristic.

[Audience]
CTOs, AI engineers, founders evaluating AI compute infrastructure.

[Visual Style]
Futuristic, glassmorphism, floating 3D particles. Dark theme.
Core metaphor: "Neural network as cosmic architecture."

[Color System]
:root {
  --primary: #6C63FF;
  --primary-light: #8B83FF;
  --primary-dark: #4A42CC;
  --accent: #00E5FF;
  --bg-primary: #0A0A1A;
  --bg-secondary: #12122A;
  ...
}

[Layout — 7 sections]
Navbar → Hero (full-viewport with 3D scene) → Problem → How it Works (3 steps)
→ Features (3×2 grid) → Stats (3 counters) → CTA → Footer

[Animations]
Hero: staggered entrance (100ms delay, fade+slide-up, 600ms)
Sections: fade-up at 80% viewport intersection
Buttons: scale 1.05 + glow on hover
Background: slow gradient shift over 10s

[3D]
Three.js scene in hero: floating hexagonal particles connected by lines,
mouse-tracked rotation, scroll-based depth shift.
Fallback: gradient mesh.

[Output]
Single index.html, all CSS in <style> in <head>, all JS deferred.
Responsive 375px-1440px. Google Fonts: Inter (300-700).
Unique design. Lighthouse > 90.
```

---

## Using the Framework

**Before writing a prompt:**
1. Pick the category (AI SaaS, Coffee, Fintech, etc.)
2. Define the brand (name, archetype, metaphor)
3. Pick the color direction
4. Ensure the metaphor hasn't been used before in that category

**After generation:**
1. Compare output to every parameter — was each followed?
2. Note where the AI deviated (and whether it was an improvement)
3. Add manual fixes if needed, document them in prompt.md
4. Validate against DESIGN_PRINCIPLES.md

---

## prompt.md Template

Every generated page needs this file in its folder:

```markdown
# [Landing Page Name] — Prompt

## AI Tool
[Claude / Hermes / Cursor + model name]

## Category
[Category name]

## Full Prompt

> [Paste the exact prompt here]

## Manual Edits
- [Edit 1: description]
- [Edit 2: description]

## Notes
- [Any observations, constraints, or learnings]

## Generation Date
YYYY-MM-DD
```

---

*The framework is a covenant between designer and machine. Follow it, and the machine builds what you see in your head.*
