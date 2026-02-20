---
name: new-project
description: Start a new project with strict phase enforcement - blocks code writing until all prerequisite docs exist
---

# New Project Phase Guardian

This skill enforces the project startup process defined in your global CLAUDE.md. It MUST be invoked when:
- User says "new project", "start a new project", "create project"
- User asks to write code in a fresh repo without docs/

## Workflow

### Step 1: Check Current Phase

Check which files exist in the project root:

```bash
ls -la docs/product-design.md docs/tech-architecture.md docs/visual-standard.md docs/visual-prototype.html docs/project-progress.md 2>/dev/null
```

Determine current phase based on existing files:
- None → Phase 0 (brainstorming)
- product-design.md exists → Phase 1 complete
- tech-architecture.md exists → Phase 2 complete
- visual-standard.md exists → Phase 3 complete
- project-progress.md exists → Phase 5 complete

### Step 2: Block or Guide

**If user wants to write code but phases 1-3 are incomplete:**

❌ **REFUSE** to write any code. Output:

```
⚠️ Cannot write code yet. Missing prerequisite documents:

Required before coding:
[ ] docs/product-design.md (Phase 1)
[ ] docs/tech-architecture.md (Phase 2)
[ ] docs/visual-standard.md (Phase 3)

Would you like me to guide you through creating these first?
```

**If all prerequisites exist:**

✅ Proceed normally.

### Step 3: Interactive Phase Completion

If user agrees, guide through missing phases one by one:

**Phase 1 - Product Design:**
```
Let's define the product. Answer these:
1. What problem does it solve?
2. Who are the target users?
3. What are the 3 core features (MVP scope)?
4. Platform: Desktop / Web / Mobile / CLI?
5. Business model: Free / Freemium / Paid?
```

After answers, generate `docs/product-design.md` with full structure:
- Product positioning
- Target users
- Core scenarios
- Interface layout (ASCII diagram)
- Feature list
- Interaction details
- Supported platforms

**Phase 2 - Tech Architecture:**
```
Let's pick the tech stack:
1. Frontend framework? (React / Vue / Svelte / none)
2. Backend? (Node / Python / Rust / Go / serverless)
3. Database? (SQLite / PostgreSQL / Firebase / none)
4. Desktop framework? (Tauri / Electron / none)
```

Generate `docs/tech-architecture.md`:
- Tech stack with rationale
- Architecture diagram (ASCII/Mermaid)
- Module responsibilities
- Data flow
- API design
- Dependencies
- Key decisions (what was chosen, why, what was rejected)

**Phase 3 - Visual Standards:**
```
Define the design system:
1. Primary color (hex)?
2. Font family?
3. Style: Minimal / Modern / Retro / Corporate?
4. Dark mode support: Yes / No?
```

Generate `docs/visual-standard.md`:
- Design tokens (colors, fonts, spacing, radius, shadows)
- Component specs
- Responsive rules
- Dark mode palette (if applicable)

Then generate `docs/visual-prototype.html` as a single-file visual preview.

**Phase 4 - Branding (optional):**
Ask:
```
Ready for branding?
1. Product name
2. Slogan
3. Need landing page? (Yes/No)
```

If yes, generate `home/index.html` and optionally `docs/marketing-posts.md`.

**Phase 5 - Iteration Plan:**
```
Let's break this into phases:
```

Generate `docs/project-progress.md`:
- Phase 0-N breakdown
- Each phase: goal, deliverables, status
- Start with MVP, then iterate

### Step 4: Final Check

Before exiting, verify all required files exist:
```bash
ls docs/product-design.md docs/tech-architecture.md docs/visual-standard.md docs/project-progress.md
```

Output:
```
✅ All prerequisites complete. Ready to code!

Next: I'll write CLAUDE.md to document key decisions.
```

Then generate project-level `CLAUDE.md` from the template.

## Rules

- **Never write application code before Phase 3 is complete**
- If user insists "just write code", repeat the warning and refuse
- All generated docs must follow the template structures in global CLAUDE.md
- Document language: Chinese (as specified in global rules)
- Code/variable language: English
