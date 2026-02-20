# AI Project Template

A structured project template for AI-assisted software development. It defines a standardized directory layout, documentation conventions, and a phased development workflow — designed to work seamlessly with AI coding assistants like Claude Code.

## What's Inside

- **Documentation-first workflow** — product design, tech architecture, visual standards must be defined before writing code
- **AI Skills** — `new-project` (phase guardian) and `post-feature` (doc update reminder) enforce the workflow automatically
- **Pre-commit hook** — blocks commits when prerequisite docs are missing, warns when code changes lack doc updates
- **Phased development** — Phase 0 (brainstorming) → Phase 6 (implementation), each with clear inputs and outputs

## Template Structure

```
ai-project-template/
├── CLAUDE.md                          # Methodology (English)
├── CLAUDE.zh.md                       # Methodology (中文)
├── README.md                          # This file
├── skills/                            # Claude Code Skills
│   ├── new-project/SKILL.md           # Phase guardian - blocks code before docs
│   └── post-feature/SKILL.md          # Doc update reminder after features
├── docs/
│   └── scripts/
│       └── pre-commit                 # Git pre-commit hook script
└── .claude/
    ├── CLAUDE.md                      # Global AI instructions (with guard rules)
    └── skills/                        # Skills (also here for global install)
        ├── new-project/SKILL.md
        └── post-feature/SKILL.md
```

## Quick Start

### Option A: New Project (from template)

```bash
# 1. Clone the template
git clone https://github.com/user/ai-project-template.git my-new-project
cd my-new-project

# 2. Install skills (project-level)
mkdir -p .claude/skills
cp -r skills/new-project skills/post-feature .claude/skills/

# 3. Install pre-commit hook
cp docs/scripts/pre-commit .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit

# 4. Start Claude Code and begin with Phase 0
# In Claude Code, type: /new-project
```

### Option B: Existing Project (add workflow)

```bash
cd your-existing-project

# 1. Copy skills
mkdir -p .claude/skills
cp -r ~/ai-project-template/skills/new-project .claude/skills/
cp -r ~/ai-project-template/skills/post-feature .claude/skills/

# 2. Copy methodology doc
cp ~/ai-project-template/CLAUDE.md ./CLAUDE.md  # or CLAUDE.zh.md for Chinese

# 3. Install pre-commit hook
cp ~/ai-project-template/docs/scripts/pre-commit .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit

# 4. Create docs/ directory
mkdir -p docs/plans docs/scripts
```

### Option C: Global Install (all projects)

Install skills globally so they work in every project without per-project setup:

```bash
# 1. Copy skills to global Claude Code config
mkdir -p ~/.claude/skills
cp -r ~/ai-project-template/skills/new-project ~/.claude/skills/
cp -r ~/ai-project-template/skills/post-feature ~/.claude/skills/

# 2. Copy global AI instructions (with guard rules)
cp ~/ai-project-template/.claude/CLAUDE.md ~/.claude/CLAUDE.md
```

After global install, `new-project` and `post-feature` skills are available in every project. The pre-commit hook still needs per-project install (see below).

### Pre-commit Hook (per-project)

The pre-commit hook must be installed in each project's `.git/hooks/`:

```bash
# Install in any project
cp ~/ai-project-template/docs/scripts/pre-commit .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit
```

**What it does:**

1. **Blocks commits** if you're committing code files (`code/`, `worker/`, `home/`, `deploy/`) but prerequisite docs don't exist yet (`product-design.md`, `tech-architecture.md`, `visual-standard.md`)
2. **Warns you** (with 3-second pause) if you're committing code but no doc files are in the same commit
3. **Reminds you** if `CLAUDE.md` doesn't exist

Bypass when needed: `git commit --no-verify`

## Skills Usage

### `/new-project` — Phase Guardian

**When:** Starting a new project or writing code in a fresh repo.

**What it does:**
1. Checks which Phase 1-3 docs exist
2. If any are missing, **refuses to write code** and guides you through creating them
3. Walks you through product design → tech architecture → visual standard interactively
4. Only unlocks coding after all prerequisites are complete

**How to use in Claude Code:**
```
> /new-project
```
Or just ask Claude to write code in an empty project — the skill triggers automatically via the guard rules in CLAUDE.md.

### `/post-feature` — Documentation Update

**When:** After completing a feature, fixing a bug, or before committing code.

**What it does:**
1. Asks what you just implemented
2. Analyzes which docs are affected
3. Generates a specific update checklist
4. Updates docs if you agree
5. Reminds you to commit docs + code together

**How to use in Claude Code:**
```
> /post-feature
```
Or say "done", "finished", "feature complete" — the guard rules in CLAUDE.md prompt the AI to invoke this skill.

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

## How the Guards Work

Three layers of protection against skipping steps:

```
Layer 1: CLAUDE.md Guard Rules
  → AI reads these every session
  → Refuses to write code if Phase 1-3 docs missing
  → Auto-reminds doc updates after features

Layer 2: Skills (new-project / post-feature)
  → Structured interactive workflows
  → Triggered by /command or AI auto-detection
  → Guides you step-by-step

Layer 3: Pre-commit Hook
  → Hard block at git level
  → Cannot commit code without docs (unless --no-verify)
  → Warns when code changes lack doc updates
```

## Languages

- [English](CLAUDE.md)
- [中文](CLAUDE.zh.md)

## License

MIT
