# Project Manifest

<!-- For AI: This is your entry point. Read this first to understand what exists in this project. -->

## Template Information

- **Template**: Cursor Project Template
- **Version**: 1.0.0
- **Purpose**: Universal scaffolding for Cursor-based agentic development
- **Metadata**: See `.cursor/template.json` for machine-readable details

## Project Status

**Setup Status**: Template (not yet customized)
**Project Type**: To be determined
**Primary Language**: To be determined
**Framework**: To be determined

> Once this template is used for a real project, update these fields.

## Core Configuration Files

### Rules & Configuration
- **`.cursorrules`** - Universal rules (READ FIRST for AI behavior)
- **`.cursor/rules/`** - Modular rules directory
  - `README.md` - Guide to modular rules system
  - `documentation.md` - Documentation standards
  - `testing.md` - Testing patterns
  - `architecture.md` - Architecture principles
  - `SCHEMA.md` - Modular rule frontmatter schema
  - `QUICK_REFERENCE.md` - Quick rules summary
- **`.cursor/template.json`** - Machine-readable template metadata
- **`.cursor/MANIFEST.md`** - This file

### Ignore Files
- **`.gitignore`** - Git exclusions
- **`.cursorignore`** - Cursor context exclusions

### GitHub
- **`.github/README.md`** - Template usage instructions

### Other Root Files
- **`README.md`** - Project overview and getting started
- **`LICENSE`** - MIT License
- **`QUICK_START.md`** - Quick start guide for AI agents
- **`PROMPTS.md`** - Structured customization prompts

## Documentation Structure

### Main Documentation (`docs/`)
- **`README.md`** - Documentation index
- **`QUICK_REFERENCE.md`** - Quick reference guide
- **`PROJECT_SETUP.md`** - How to customize this template
- **`SETUP_WIZARD.md`** - **NEW:** Guided setup with phases & verification
- **`ONBOARDING.md`** - **NEW:** Post-setup guide for using template features
- **`ARCHITECTURE.md`** - Architecture documentation skeleton
- **`CONTRIBUTING.md`** - Contributing guidelines skeleton
- **`TROUBLESHOOTING.md`** - Common issues and solutions

### Setup & Decision Tracking
- **`docs/decisions/`** - **NEW:** Architecture Decision Records (ADRs)
  - `README.md` - ADR guide and best practices
  - `000-template.md` - ADR template for documenting decisions
  - Add numbered ADRs: `001-initial-setup.md`, `002-[decision].md`, etc.
- **`docs/templates/`** - **NEW:** Reusable templates
  - `VERIFICATION.md` - Setup verification checklist template

### Cursor Guide (`docs/cursor/`)
- **`index.md`** - Overview and navigation
- **`basics.md`** - Core Cursor concepts
- **`features.md`** - Chat, Composer, Inline Edit
- **`context.md`** - Context management (@ references)
- **`workflows.md`** - Common workflow patterns
- **`shortcuts.md`** - Keyboard shortcuts reference

> Legacy: `docs/CURSOR.md` redirects to `docs/cursor/index.md`

### Workflows (`docs/workflows/`)
- **`README.md`** - Workflow patterns guide
- **`setup.md`** - **NEW:** Initial project setup workflow

**Add workflow docs as needed:**
- `commit.md` - Commit workflow
- `feature.md` - Feature development
- `bugfix.md` - Bug fixing
- `testing.md` - Testing workflow

### Agents (`docs/agents/`)
- **`README.md`** - Agent specialization guide

**Add agent specs as needed:**
- `BACKEND.md` - Backend development agent
- `FRONTEND.md` - Frontend development agent
- `TESTING.md` - Testing agent
- `DOCUMENTATION.md` - Documentation agent

## Quick Navigation for AI

### First Time in Project?
1. Read **`.cursorrules`** - Understand core rules
2. Read **`QUICK_START.md`** - Get oriented
3. Check **`.cursor/template.json`** - See project metadata
4. Review this manifest

### Common Tasks
- **Setup project**: `@docs/SETUP_WIZARD.md` (guided) or `@PROMPTS.md` (quick)
- **Understand rules**: `@.cursor/rules/README.md`
- **Use Cursor effectively**: `@docs/cursor/index.md`
- **Customize template**: `@docs/PROJECT_SETUP.md`
- **Document decisions**: `@docs/decisions/000-template.md`
- **Troubleshoot**: `@docs/TROUBLESHOOTING.md`

### Need Specific Guidance?
- **Documentation standards**: `@.cursor/rules/documentation.md`
- **Testing patterns**: `@.cursor/rules/testing.md`
- **Architecture principles**: `@.cursor/rules/architecture.md`
- **Modular rule schema**: `@.cursor/rules/SCHEMA.md`
- **Decision recording**: `@docs/decisions/README.md`
- **Setup verification**: `@docs/templates/VERIFICATION.md`
- **Post-setup onboarding**: `@docs/ONBOARDING.md`

## File Tree Overview

```
cursor-project-template/
├── .cursorrules              # Core universal rules
├── .cursorignore            # Cursor exclusions
├── .gitignore               # Git exclusions
├── LICENSE                  # MIT License
├── README.md                # Project overview
├── QUICK_START.md           # AI quick start guide
├── PROMPTS.md               # Structured prompts
├── .cursor/
│   ├── MANIFEST.md          # This file (project map)
│   ├── template.json        # Template metadata (enhanced tracking)
│   └── rules/               # Modular rules
│       ├── README.md        # Rules guide
│       ├── SCHEMA.md        # Frontmatter schema
│       ├── QUICK_REFERENCE.md
│       ├── documentation.md
│       ├── testing.md
│       └── architecture.md
├── .github/
│   └── README.md            # Template instructions
└── docs/
    ├── README.md            # Doc index
    ├── QUICK_REFERENCE.md   # Quick reference
    ├── PROJECT_SETUP.md     # Setup guide
    ├── SETUP_WIZARD.md      # **NEW** Guided phased setup
    ├── ONBOARDING.md        # **NEW** Post-setup feature guide
    ├── ARCHITECTURE.md      # Architecture docs
    ├── CONTRIBUTING.md      # Contributing guide
    ├── TROUBLESHOOTING.md   # Common issues
    ├── decisions/           # **NEW** Architecture Decision Records
    │   ├── README.md        # ADR guide
    │   └── 000-template.md  # ADR template
    ├── templates/           # **NEW** Reusable templates
    │   └── VERIFICATION.md  # Verification checklist
    ├── cursor/              # Cursor guide (split)
    │   ├── index.md
    │   ├── basics.md
    │   ├── features.md
    │   ├── context.md
    │   ├── workflows.md
    │   └── shortcuts.md
    ├── workflows/           # Workflow patterns
    │   ├── README.md
    │   └── setup.md         # **NEW** Setup workflow
    └── agents/              # Agent specs
        └── README.md
```

## What Gets Customized

When you use this template for a real project, you'll add:

### Project-Specific Files
- Language/framework configs (package.json, requirements.txt, etc.)
- Build tool configs
- CI/CD configs (.github/workflows/)
- Environment files (.env.example)
- Source code directories (src/, lib/, etc.)
- Test directories

### Updated Template Files
- **`.cursorrules`** - Add project-specific rules
- **`.cursor/rules/`** - Add custom modular rules
- **`.cursor/template.json`** - Track project metadata and setup progress
- **`docs/ARCHITECTURE.md`** - Fill in your architecture
- **`docs/CONTRIBUTING.md`** - Your contribution process
- **`docs/decisions/`** - Document important decisions (ADRs)
- **`.gitignore`** - Add project-specific ignores
- **`README.md`** - Your project description

### New Documentation
- **`docs/decisions/001-initial-setup.md`** - Setup decisions
- **`VERIFICATION.md`** (root) - Project-specific verification checklist (delete after use)
- API documentation
- Database schema docs
- Deployment guides
- User guides

## Maintenance Notes

### Keep Updated
As the project evolves, update:
- This manifest when adding new doc sections
- `.cursor/template.json` when customizing (tracks progress & decisions)
- Documentation when architecture changes
- ADRs in `docs/decisions/` for important technical decisions
- Rules in `.cursor/rules/` as patterns emerge

### Template Version
Check `.cursor/template.json` for current template version. When template updates, review changelog for new features.

### New Features (v1.1)
- ✨ **Setup Wizard**: Phased guided setup (`@docs/SETUP_WIZARD.md`)
- ✨ **Decision Records**: ADR templates and guide (`@docs/decisions/`)
- ✨ **Verification**: Comprehensive verification checklist (`@docs/templates/VERIFICATION.md`)
- ✨ **Onboarding**: Post-setup feature guide (`@docs/ONBOARDING.md`)
- ✨ **Enhanced Tracking**: Better progress tracking in `template.json`
- ✨ **Setup Workflow**: Step-by-step setup process (`@docs/workflows/setup.md`)

These improvements address common pain points:
- 🎯 Reduces information overload with phased approach
- 🎯 Clarifies decision points with ADRs
- 🎯 Makes template features obvious with onboarding
- 🎯 Provides verification checkpoints
- 🎯 Documents "why" behind choices

---

**For AI Agents**: This manifest is designed for you. Use it to understand the project structure quickly and navigate to relevant resources efficiently. When users ask about "what exists" or "where to find X", reference this file first.

