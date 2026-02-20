# Project Development Methodology

> Applies to all new projects. Defines directory structure, file naming, and development workflow.

## Directory Structure

```
project-name/
├── CLAUDE.md               # AI development instructions (project-level)
├── docs/                   # All documentation
│   ├── product-design.md   # Product design (features, users, scenarios, UI)
│   ├── tech-architecture.md# Technical architecture (stack, modules, data flow)
│   ├── visual-standard.md  # Visual & interaction design standard (colors, fonts, spacing, components)
│   ├── project-progress.md # Iteration plan & progress tracking
│   ├── marketing-posts.md  # Social media marketing materials
│   ├── visual-prototype.html # Visual prototype (open in browser to preview)
│   ├── plans/              # Design documents (brainstorming output)
│   └── scripts/            # Build/deploy helper scripts
├── code/                   # Application source code (frontend + backend)
├── home/                   # Product website / Landing page
├── worker/                 # Cloud functions / Backend services
└── deploy/                 # Deployment config (CI/CD, Docker, etc.)
```

## Core File Naming

| File | Purpose | Required |
|------|---------|----------|
| `CLAUDE.md` | AI instructions: project structure, tech decisions, dev commands | ✅ |
| `docs/product-design.md` | Product positioning, target users, scenarios, UI layout, feature list | ✅ |
| `docs/tech-architecture.md` | Tech stack, architecture diagram, module responsibilities, data flow, API design | ✅ |
| `docs/visual-standard.md` | Design tokens, color system, typography, spacing, component specs | ✅ |
| `docs/visual-prototype.html` | Single-file HTML visual prototype, viewable in browser | ✅ |
| `docs/project-progress.md` | Phased iteration plan with clear deliverables and status per phase | ✅ |
| `docs/marketing-posts.md` | Product slogan, one-liner, social media launch materials | Optional |

## Project Launch Workflow (Sequential)

### Phase 0: Brainstorming
- Define the problem to solve and target users
- Discuss feature boundaries (what to build, what NOT to build)
- Decide product form (desktop app / web / mobile / CLI)
- Decide business model (free / freemium / paid)
- Output: aligned understanding, ready for next phase

### Phase 1: Product Design Document
- Write `docs/product-design.md`
- Include: product positioning, user personas, core user scenarios, UI layout (ASCII diagrams), feature list, interaction details
- All feature details finalized at this stage — no ambiguity
- Confirm supported platforms (macOS / Windows / Linux / Web / iOS / Android)

### Phase 2: Technical Architecture Document
- Write `docs/tech-architecture.md`
- Include: tech stack choices with rationale, architecture diagram, module breakdown, data flow, API design, third-party dependencies
- Record key technical decisions (what was chosen, why, what was rejected)

### Phase 3: Visual Standard
- Write `docs/visual-standard.md`
- Include: design tokens (colors, fonts, spacing, border-radius, shadows), component specs, responsive rules, dark mode
- Build `docs/visual-prototype.html` based on the visual standard (single file, viewable in browser)

### Phase 4: Brand Definition
- Finalize product name
- Finalize slogan
- Design app icon
- Build landing page (`home/index.html`)
- Write `docs/marketing-posts.md` (optional, for product launch)

### Phase 5: Iteration Plan
- Write `docs/project-progress.md`
- Split into phases: Phase 0 → Phase N, each with clear goals and deliverables
- Start from MVP, iterate incrementally
- Update status after each phase completion

### Phase 6: Implementation
- Develop according to `project-progress.md` phase order
- Update progress document after each phase
- Write `CLAUDE.md` to capture project context and key design decisions

## Documentation Maintenance

After completing each feature or phase, always update related documents:

1. `docs/project-progress.md` — Update phase status, add completed items
2. `docs/product-design.md` — Add new features to feature list, sync design changes
3. `docs/tech-architecture.md` — Sync new modules, tech stack changes, storage path changes
4. `CLAUDE.md` — Add new design decisions, commands, storage paths
5. Remove outdated content — Deprecated approaches, removed features, obsolete descriptions should be deleted, not commented out
6. Documentation updates and code changes should be in the same commit

## General Development Standards

- Default language: English (UI, code comments, error messages, variable names)
- i18n: centralized translation dictionary, default locale `en`
- Fonts: local bundles (@fontsource etc.), no external CDN dependency
- Documentation language: written in the team's primary language
- Exported files default to the same directory as the source file
- No hardcoded secrets (API keys, credentials go in config files or env vars)

## CLAUDE.md Writing Guide

Project-level CLAUDE.md should include:
1. One-line project description
2. Project structure (directory tree + key file descriptions)
3. Dev commands (install / dev / build / test)
4. Key design decisions (each: decision + rationale)
5. Data storage locations (database, config files, cache paths)
6. Naming conventions (localStorage key prefix, API path style, etc.)
