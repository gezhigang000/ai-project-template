# AI Project Template

A structured project template for AI-assisted software development. It defines a standardized directory layout, documentation conventions, and a phased development workflow — designed to work seamlessly with AI coding assistants like Claude Code.

## What's Inside

This template provides a complete methodology for launching new projects:

- **Standardized directory structure** — clear separation of docs, source code, landing page, backend services, and deployment config
- **Documentation-first workflow** — product design, tech architecture, visual standards, and iteration plans are all defined before writing code
- **Phased development process** — from brainstorming (Phase 0) through implementation (Phase 6), each phase has clear inputs and outputs
- **AI-ready project context** — `CLAUDE.md` gives AI assistants the project structure, tech decisions, and conventions they need to contribute effectively

## Project Structure

```
project-name/
├── CLAUDE.md                  # AI development instructions
├── docs/
│   ├── product-design.md      # Product positioning, users, scenarios, features
│   ├── tech-architecture.md   # Tech stack, modules, data flow, API design
│   ├── visual-standard.md     # Design tokens, component specs, responsive rules
│   ├── project-progress.md    # Iteration plan & progress tracking
│   ├── visual-prototype.html  # Single-file visual prototype (open in browser)
│   ├── marketing-posts.md     # Launch materials (optional)
│   ├── plans/                 # Brainstorming & design documents
│   └── scripts/               # Build/deploy helper scripts
├── code/                      # Application source code
├── home/                      # Product website / Landing page
├── worker/                    # Cloud functions / Backend services
└── deploy/                    # Deployment config (CI/CD, Docker, etc.)
```

## Development Phases

| Phase | Focus | Key Output |
|-------|-------|------------|
| 0 | Brainstorming | Problem definition, feature boundaries, product form |
| 1 | Product Design | `docs/product-design.md` — users, scenarios, UI, features |
| 2 | Tech Architecture | `docs/tech-architecture.md` — stack, modules, APIs |
| 3 | Visual Standard | `docs/visual-standard.md` + `visual-prototype.html` |
| 4 | Brand Definition | Product name, slogan, icon, landing page |
| 5 | Iteration Plan | `docs/project-progress.md` — phased roadmap from MVP |
| 6 | Implementation | Build according to plan, update progress as you go |

## Usage

1. Clone or use this repo as a template for your new project
2. Start from Phase 0 — work through each phase sequentially
3. Fill in the documentation templates under `docs/`
4. Use `CLAUDE.md` to give AI assistants full project context

## Languages

- [English](CLAUDE.md)
- [中文](CLAUDE.zh.md)

## License

MIT
