# Quick Reference

<!-- For AI: Load this for a fast overview instead of reading multiple detailed docs -->

One-page reference for key concepts and resources in this project.

## Project Overview

**Template:** Cursor Project Template v1.0  
**Purpose:** Universal scaffolding for agentic development  
**Status:** Check `@.cursor/template.json` for customization state

## Essential Files

```
READ FIRST:
  @.cursorrules           - Core rules
  @.cursor/MANIFEST.md    - Complete project map
  @QUICK_START.md         - AI agent quick start

SETUP:
  @PROMPTS.md             - Customization prompts
  @docs/PROJECT_SETUP.md  - Setup guide

UNDERSTANDING CURSOR:
  @docs/cursor/index.md   - Cursor guide overview
  @docs/cursor/basics.md  - Core concepts
  @docs/cursor/context.md - @ references

TROUBLESHOOTING:
  @docs/TROUBLESHOOTING.md       - Project issues
  @docs/cursor/troubleshooting.md - Cursor issues
```

## Cursor Shortcuts

```
⌘L or ⌘I / Ctrl+L or Ctrl+I  - AI Panel
⌘K / Ctrl+K                   - Inline Edit
⌘P / Ctrl+P                   - Go to File
⌘Shift+P / Ctrl+Shift+P       - Command Palette
```

> **Note:** Both ⌘L and ⌘I open the same AI Panel.

## Context References

```
@file.ts           - Specific file
@folder/           - Directory
@symbol            - Function/class
@docs/file.md      - Documentation
@codebase query    - Semantic search
@web query         - Web search
```

## Rules System

**Core Rules:** `.cursorrules` - Always active  
**Modular Rules:** `.cursor/rules/` - Context-specific

**Loading:**
- Auto: Files matching `globs` in frontmatter
- Manual: `@.cursor/rules/rule-name.md`

**Creating:**
See `@.cursor/rules/SCHEMA.md` for schema

## Directory Structure

```
/
├── .cursorrules             # Core rules
├── .cursorignore            # Cursor exclusions
├── QUICK_START.md           # AI quick start
├── PROMPTS.md               # Setup prompts
├── .cursor/
│   ├── MANIFEST.md          # Project map
│   ├── template.json        # Metadata
│   └── rules/               # Modular rules
├── docs/
│   ├── README.md            # Doc index
│   ├── QUICK_REFERENCE.md   # This file
│   ├── PROJECT_SETUP.md     # Setup
│   ├── ARCHITECTURE.md      # Architecture
│   ├── CONTRIBUTING.md      # Contributing
│   ├── TROUBLESHOOTING.md   # Issues
│   ├── cursor/              # Cursor guide (split)
│   ├── workflows/           # Workflow patterns
│   └── agents/              # Agent specs
└── .github/
    └── README.md            # Template info
```

## Common Tasks

**Setup Project:**
```
@PROMPTS.md @docs/PROJECT_SETUP.md
Set up for [language/framework]
```

**Add Rule:**
```
@.cursor/rules/README.md @.cursor/rules/SCHEMA.md
Create rule for [concern]
```

**Add Feature:**
```
@docs/ARCHITECTURE.md @existing/similar-code.ts
Create [feature] following patterns
```

**Fix Bug:**
```
@problematic/file.ts
Issue: [description]
Error: [message]
```

**Add Tests:**
```
@.cursor/rules/testing.md @code/file.ts
Write comprehensive tests
```

**Add Docs:**
```
@.cursor/rules/documentation.md
Document this [module/function/class]
```

## Workflow Patterns

**Feature Development:**
1. Plan (AI Panel)
2. Implement (AI Panel)
3. Polish (Inline Edit)
4. Test (Terminal)

**Bug Fix:**
1. Reproduce
2. Understand (AI Panel)
3. Fix (Inline Edit)
4. Verify (Terminal)

**Refactoring:**
1. Ensure tests exist
2. Plan approach (AI Panel)
3. Small changes (AI Panel)
4. Test after each

## Best Practices

**Be Specific:**
❌ "Fix the bug"  
✅ "Fix null error in UserService.get() when ID invalid"

**Provide Context:**
❌ "Create service"  
✅ "@src/services/UserService.ts create TeamService following this"

**Iterate:**
❌ "Build entire auth system"  
✅ "Step 1: Add login endpoint"

**Review:**
Always review, test, and verify AI output

## Decision Trees

### Which Tool?

```
Need to...
├─ Ask/Plan/Multi-file edits → AI Panel (⌘L or ⌘I)
├─ Edit 1 file → Inline Edit (⌘K)
└─ Run command → Terminal
```

### Which Context?

```
Want to...
├─ Reference file → @file.ts
├─ Follow pattern → @example/file.ts
├─ Follow rules → @.cursor/rules/rule.md
├─ Understand architecture → @docs/ARCHITECTURE.md
└─ Find something → @codebase query
```

### Having Issues?

```
Problem with...
├─ Cursor behavior → @docs/cursor/troubleshooting.md
├─ Project setup → @docs/TROUBLESHOOTING.md
├─ Rules → @.cursor/rules/README.md
└─ General → @docs/README.md
```

## Key Principles

1. **Context is King** - Use @ references
2. **Be Specific** - Detailed requests get better results
3. **Iterate** - Small steps, frequent testing
4. **Review** - AI assists, you decide
5. **Follow Rules** - Reference `.cursorrules` and modular rules
6. **Document** - Keep docs and code in sync

## File Naming Conventions

- **Components:** PascalCase (`UserProfile.tsx`)
- **Utilities:** kebab-case (`format-date.ts`)
- **Types:** kebab-case (`user-types.ts`)
- **Hooks:** camelCase (`useAuth.ts`)
- **Rules:** kebab-case (`api-design.md`)
- **Docs:** CAPS or kebab (`README.md`, `api-guide.md`)

## Git Workflow

**Trunk-Based Development** (default)
- Main branch: `main`
- Feature branches: Short-lived
- Commit format: `type(scope): subject`

**Commit Types:**
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation
- `refactor` - Code refactoring
- `test` - Tests
- `chore` - Maintenance

## Troubleshooting Quick Fixes

**AI not following rules:**
→ Reference explicitly: `@.cursorrules @.cursor/rules/testing.md`

**Too much context:**
→ Load selectively: `@specific/file.ts` not `@entire/directory/`

**Lost context:**
→ Start new chat, re-provide context

**Types don't match:**
→ Check `@src/types/` (or equivalent)

**Tests failing:**
→ Run incrementally, check test patterns

## Getting Help

1. **Check:** `@.cursor/MANIFEST.md` - What exists?
2. **Search:** `@codebase [topic]` - Find examples
3. **Ask:** Provide context with @references
4. **Read:** Load relevant docs from `@docs/`

## Resources

**Internal:**
- `@.cursor/MANIFEST.md` - Complete map
- `@docs/README.md` - Documentation index  
- `@.cursorrules` - Core rules
- `@PROMPTS.md` - Customization prompts

**Cursor Docs:**
- `@docs/cursor/index.md` - Overview
- `@docs/cursor/features.md` - Tools
- `@docs/cursor/context.md` - @ references
- `@docs/cursor/best-practices.md` - Tips

**External:**
- [Cursor Docs](https://cursor.sh/docs)
- [Conventional Commits](https://conventionalcommits.org)

---

**For AI Agents:** Use this as a quick reference instead of loading multiple detailed docs. Load specific docs only when needed.

**For Humans:** Bookmark this page for quick lookups. For detailed info, see full documentation in `@docs/`.

