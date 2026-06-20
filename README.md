# Awesome AI Landings

> A curated showcase of premium AI-generated landing pages — crafted by prompts, powered by AI, designed for impact.

Every page in this repository was generated entirely by AI using structured prompts. No templates. No stock assets. No hand-coding. Each design is a unique artifact demonstrating what's possible when you treat AI as a design partner.

---

## Featured Designs

| Design Pattern | Category | Tech | Preview |
|---|---|---|---|
| [**Operating System**](categories/ai-saas/operating-system/) | AI SaaS | Three.js + CSS | [preview.png](categories/ai-saas/operating-system/preview.png) |
| _Next up →_ | AI SaaS | — | — |

---

## Why This Exists

Can AI produce production-grade landing pages with 3D effects, scroll animations, and premium aesthetics?

This repo is an experiment in prompt engineering + design quality. Each page is:
- Generated from a structured prompt (see [PROMPT_FRAMEWORK.md](./PROMPT_FRAMEWORK.md))
- Documented with the exact prompt that created it (`prompt.md`)
- Designed to teach: "How is this made?"

The **benchmark page** ([Operating System](categories/ai-saas/operating-system/)) includes full process documentation in `notes.md` — from prompt through design review, wireframe, generation contract, to implementation.

Future pages keep it simple: `index.html`, `prompt.md`, `preview.png`, `notes.md`.

---

## Categories

| # | Category | Pages | Status |
|---|---|---|---|
| 1 | **AI SaaS** — AI products, agents, platforms | 10 | ✅ 1 / 10 complete |
| 2 | **Coffee** — Cafés, roasters, coffee culture | 10 | ⬜ Planning |
| 3 | **Fashion & Luxury** — Watches, sneakers, streetwear | 10 | ⬜ Planning |
| 4 | **Automotive** — Hypercars, EVs, racing | 10 | ⬜ Planning |
| 5 | **Fintech** — Banking, investing, payments | 10 | ⬜ Planning |
| 6 | **Interactive 3D** — WebGL, immersive experiences | 10 | ⬜ Planning |

---

## Repository Structure

```
awesome-ai-landings/
├── README.md
├── ROADMAP.md
├── DESIGN_PRINCIPLES.md
├── PROMPT_FRAMEWORK.md
├── LANDINGS_INDEX.md
│
└── categories/
    ├── ai-saas/
    │   ├── operating-system/    ← benchmark page
    │   │   ├── index.html
    │   │   ├── prompt.md
    │   │   ├── preview.png
    │   │   └── notes.md
    │   ├── swarm-network/       (planned)
    │   ├── command-center/      (planned)
    │   └── ...
    ├── coffee/                  (planned)
    ├── fashion/                 (planned)
    ├── automotive/              (planned)
    ├── fintech/                 (planned)
    └── interactive-3d/          (planned)
```

Each landing page folder contains:

| File | Purpose |
|---|---|
| `index.html` | The generated landing page. Self-contained, single file. |
| `prompt.md` | The exact prompt that created the page. The most valuable artifact. |
| `preview.png` | Screenshot at 1440×900. Shows the page at a glance. |
| `notes.md` | Design notes, process learnings, what to steal from this page. |

Folder names describe **design patterns** (e.g. `operating-system`, `sneaker-drop`, `hypercar`) — not fictional companies. Visitors search for effects and techniques, not startup names.

---

## How Prompts Are Structured

Every page starts with a recipe. The [PROMPT_FRAMEWORK.md](./PROMPT_FRAMEWORK.md) defines 12 parameters that shape each design:

```
Role → Audience → Brand → Visual Style → Color System →
Layout → Animations → 3D Effects → Sections →
Interactions → Performance Constraints → Output Requirements
```

Open any `prompt.md` to see the recipe in action. Feed it to Claude, Hermes, or Cursor to reproduce the page.

---

## How to Use

```bash
git clone https://github.com/malackmohammedhassan/awesome-ai-landings.git
cd awesome-ai-landings
# Open any index.html in your browser
```

### Generate a new page
1. Choose a design pattern and category
2. Follow the prompt recipe in [PROMPT_FRAMEWORK.md](./PROMPT_FRAMEWORK.md)
3. Generate with your AI tool of choice
4. Submit via pull request

---

## Quality Standards

Every landing page must pass:

- ✅ **Unique visual identity** — no two pages look alike
- ✅ **Responsive** — desktop and mobile
- ✅ **Lighthouse score > 90** — all four categories
- ✅ **Animation** — at least one scroll-triggered animation
- ✅ **3D effect** — CSS 3D transforms or Three.js
- ✅ **Premium feel** — would you ship this to a client?
- ✅ **No external paid assets** — everything inline or from free CDNs

Full principles in [DESIGN_PRINCIPLES.md](./DESIGN_PRINCIPLES.md).

---

## Roadmap

| Phase | Category | Status |
|---|---|---|
| 1 | AI SaaS (10 pages) | ✅ 1 / 10 complete |
| 2 | Coffee (10 pages) | ⬜ Not started |
| 3 | Fashion & Luxury (10 pages) | ⬜ Not started |
| 4 | Automotive (10 pages) | ⬜ Not started |
| 5 | Fintech (10 pages) | ⬜ Not started |
| 6 | Interactive 3D (10 pages) | ⬜ Not started |

See [ROADMAP.md](./ROADMAP.md) for details and [LANDINGS_INDEX.md](./LANDINGS_INDEX.md) for the full catalog.

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) (coming soon) for guidelines on:
- Adding a new landing page
- Using the prompt framework
- Quality review process
- PR workflow

---

## License

MIT — see [LICENSE](./LICENSE).

---

*Built with prompts, not templates. Every line of code was generated by AI.*
