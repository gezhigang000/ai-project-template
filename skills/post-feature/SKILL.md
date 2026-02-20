---
name: post-feature
description: Triggered after completing a feature - checks which docs need updating and guides the update process
---

# Post-Feature Documentation Update

This skill MUST be invoked when:
- User says "done", "finished", "complete", "feature is ready"
- Code changes have been made
- About to commit code

## Workflow

### Step 1: Analyze What Changed

Ask the user:
```
What did you just implement? (brief summary)
```

Based on the answer, determine impact scope:
- New feature → update `product-design.md` + `project-progress.md`
- Architecture change (new module, storage, API) → update `tech-architecture.md` + `CLAUDE.md`
- UI/visual change → check if `visual-standard.md` needs update
- Tech stack change → update `tech-architecture.md`
- New command/script → update `CLAUDE.md`

### Step 2: Read Current Docs

Read the potentially affected docs:
```bash
cat docs/project-progress.md docs/product-design.md docs/tech-architecture.md CLAUDE.md
```

### Step 3: Generate Update Checklist

Output a specific checklist:

```
📝 Documentation Update Checklist

Based on the changes, these docs need updating:

[ ] docs/project-progress.md
    - Mark Phase X as complete
    - Update status of "Implement Y" item

[ ] docs/product-design.md
    - Add new feature "Z" to feature list
    - Update interaction flow section

[ ] docs/tech-architecture.md
    - Add new module "W" to architecture diagram
    - Document new storage path ~/.app/data.db

[ ] CLAUDE.md
    - Add decision: "Chose SQLite over PostgreSQL because..."
    - Add command: npm run migrate
    - Add storage path: ~/.app/data.db

Would you like me to make these updates now?
```

### Step 4: Execute Updates

If user agrees, update each file one by one:

1. Read current file
2. Identify exact section to modify
3. Use `Edit` tool to make surgical edits (never rewrite entire file)
4. Confirm: "✅ Updated docs/xxx.md"

**Update Guidelines:**
- **Add** new content, don't rewrite existing
- **Delete** obsolete info (don't comment it out)
- Keep formatting consistent with existing style
- Chinese for product/design docs, English for code comments

### Step 5: Git Commit Reminder

After all docs updated, output:

```
✅ All docs updated

Next step: Commit everything together

git add docs/ CLAUDE.md [your code files]
git commit -m "feat: [your feature] + doc updates"
```

**Important:** Doc updates and code changes MUST be in the same commit (as per global CLAUDE.md rules).

## Edge Cases

**If user says "I'll update docs later":**

❌ Push back gently:
```
⚠️ Updating docs later usually means forgetting forever.

It takes 2 minutes now. The changes are fresh in your mind.

Shall we do it quickly?
```

**If no docs exist in the project:**

Output:
```
⚠️ This project has no docs/ directory.

Looks like it wasn't started with the new-project flow.

Would you like me to:
1. Create missing docs retroactively?
2. Skip docs for this project?
```

**If the change is truly trivial (typo fix, comment change):**

Output:
```
This looks like a trivial change. Docs probably don't need updating.

Proceed with commit?
```

## Rules

- **Always invoke this skill after code changes**
- Never assume "docs don't need updating" - always check
- Surgical edits only - don't regenerate entire files
- If user repeatedly ignores doc updates, remind once per session, then respect their choice
- Output must be concise - checklist format, not essay
