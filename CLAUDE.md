# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workspace Overview

This is a monorepo for building professional landing pages with a Claude-driven workflow. It has two top-level concerns:

- `_core/claude-webkit-base/` — Reusable template, methodology, and 13 bundled skills that power the full 6-phase build workflow.
- `projects/` — Individual client sites. Currently: `marca-personal-carlos` (cinematic filmmaker portfolio for Carlos Martínez, Popayán, Colombia).

Each project under `projects/` has its own `.git` repo and its own `CLAUDE.md`. The frontend app also has its own `.git` at `projects/marca-personal-carlos/app/frontend/.git`.

## Active Project: marca-personal-carlos

**Frontend location:** `projects/marca-personal-carlos/app/frontend/`

### Dev Commands

```bash
cd projects/marca-personal-carlos/app/frontend
npm run dev        # starts Next.js dev server at http://localhost:3000
npm run build      # production build
npm run lint       # ESLint
```

### Deploy

```bash
# Vercel sandbox (no account needed)
bash .claude/skills/vercel-deploy/scripts/deploy.sh site
```

### If starting from scratch (Phase 3 scaffold)

```bash
npx create-next-app@latest site --typescript --tailwind --app --src-dir --no-import-alias --yes
cd site
npx shadcn@latest init -y
npx shadcn@latest add button card navigation-menu separator badge -y
npm install framer-motion lucide-react
```

## Tech Stack

- **Next.js 15+** (App Router, TypeScript)
- **Tailwind CSS 4** — utility-first, no custom CSS files
- **shadcn/ui** — accessible component primitives
- **Framer Motion** — animations
- **Lucide React** — icons (no emoji, no image icons)
- **Cloudinary CDN** — all video assets (not git-tracked; mapped in `content/data/video-sources.json`)
- **Vercel** — deployment

## Content Architecture

Content is kept separate from code — edit content without touching components:

| File | Purpose |
|------|---------|
| `content/copy/copy-final.md` | All page copy, CTA text, section labels |
| `content/data/portfolio-items.json` | 12 portfolio items (title, category, thumbnail paths, video paths) |
| `content/data/video-sources.json` | Cloudinary URLs for hero, AI transitions, and portfolio videos |
| `content/social-links/links.env.txt` | WhatsApp, Instagram, email links |

## 6-Phase Build Workflow

The `_core/claude-webkit-base/CLAUDE.md` defines the full methodology. Summary:

1. **Discovery** — 4-round questionnaire, design direction approval
2. **Design System** — colors, fonts, archetype selection
3. **Scaffold** — Next.js + shadcn setup
4. **Build** — write all page files (`layout.tsx`, `page.tsx`, components) without per-section approval
5. **QA** — dev server, visual screenshots (Playwright/Chrome Bridge), SEO audit
6. **Deploy** — Vercel build + share URL

Phase-specific CLAUDE.md files live at each layer:

- `_core/claude-webkit-base/CLAUDE.md` — full system prompt (skills, phases, design rules)
- `projects/marca-personal-carlos/CLAUDE.md` — project brief and goals
- `projects/marca-personal-carlos/app/frontend/CLAUDE.md` — frontend-specific (mirrors base)

## Bundled Skills (13)

Located at `_core/claude-webkit-base/.claude/skills/`. Invoke by name or `/skill-name`:

| Skill | When to use |
|-------|-------------|
| `frontend-design` | Design direction, layout decisions |
| `shadcn-ui` | shadcn component usage patterns |
| `humanizer` | Strip AI writing patterns from copy |
| `vercel-deploy` | Deploy to Vercel sandbox |
| `playwright-cli` | Visual QA screenshots |
| `chrome-bridge-automation` | Browser automation during QA |
| `seo-audit` | SEO analysis before deploy |
| `ui-ux-pro-max` | 161 palettes, 57 fonts, 50+ styles reference |
| `web-reader` | Extract content from URLs |
| `deep-research` | Web research for copy/industry context |
| `building-components` | Component construction patterns |
| `web-design-guidelines` | Design best practices |
| `vercel-react-best-practices` | Vercel + React optimization |

Project-specific skills at `projects/marca-personal-carlos/.claude/skills/`:
- `portfolio-sync` — sync portfolio JSON data to page
- `qa-publish-pass` — final QA checklist before publishing
- `small-batch-edit` — targeted 1–3 change edits without full rewrites

## Design Rules (Anti-AI-Slop)

From the base CLAUDE.md — strictly enforced:

**Forbidden visual patterns:** cyan-on-dark, purple-to-blue gradients, neon, glassmorphism, elastic easing, centered-everything layouts, generic card grids.

**Forbidden fonts:** Inter, Roboto, Arial, Open Sans, system UI defaults.

**Forbidden copy words:** delve, tapestry, landscape, showcase, vibrant, nestled, leverage, foster, innovative, cutting-edge.

**Rule of thumb:** "If someone would immediately say 'AI made this,' redesign it."

## Asset Notes

- `assets/videos/` is git-ignored — all videos hosted on Cloudinary
- Thumbnails are in `assets/portfolio/thumbnails/` organized by category (fitness-cinematografico, fitness-marca-personal, marcas-de-ropa, otros)
- Brand assets (logo, guidelines) in `assets/brand/`
