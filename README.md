# Cursor Project Template

A minimal, universal GitHub template for projects using **agentic Cursor-based development**.

## What Is This?

This template provides scaffolding for projects that leverage AI-powered development with Cursor IDE. It's designed to be:

- **Universal** - Works with any language, framework, or project type
- **Minimal** - Only includes what every project needs
- **LLM-Optimized** - Structured for easy discovery by AI assistants
- **Modular** - Organize rules and documentation as your project grows

## Features

- 📋 **Modular Rules System** - Keep AI guidance focused and context-appropriate
- 📚 **Documentation Structure** - LLM-friendly documentation organization
- 🤖 **Agent Patterns** - Guidelines for specialized AI agents
- 🔄 **Workflow Templates** - Patterns for common development workflows
- ⚙️ **Configuration Files** - `.cursorrules`, `.cursorignore`, `.gitignore` templates

## Quick Start

### 1. Use This Template

Click the "Use this template" button on GitHub to create a new repository, or clone directly:

```bash
git clone https://github.com/yourusername/cursor-project-template.git my-new-project
cd my-new-project
rm -rf .git
git init
```

### 2. Customize for Your Project

Open the project in Cursor and use AI to customize the template. See `@PROMPTS.md` for ready-to-use prompts organized by task:

**Quick examples:**
```
@PROMPTS.md @docs/PROJECT_SETUP.md Set up this project as a [language/framework] project
```

```
@PROMPTS.md show me the setup prompt for [TypeScript/Python/Go/Rust]
```

For all customization prompts, see:
- **`@PROMPTS.md`** - Complete library of structured prompts
- **`@docs/PROJECT_SETUP.md`** - Detailed setup guide
- **`@QUICK_START.md`** - Quick start for AI agents

### 3. Explore the Structure

The template includes:
- **Discovery files** - `@.cursor/MANIFEST.md`, `@QUICK_START.md`
- **Setup guides** - `@docs/PROJECT_SETUP.md`, `@PROMPTS.md`
- **Documentation** - `@docs/` directory with focused guides
- **Rules** - `.cursorrules` and `.cursor/rules/`

See **`@.cursor/MANIFEST.md`** for a complete project map.

## What's Included

```
cursor-project-template/
├── .cursorrules              # Core universal rules
├── .cursorignore            # Files to exclude from Cursor context
├── .gitignore               # Git exclusions
├── LICENSE                  # MIT License
├── README.md                # This file
├── .cursor/
│   └── rules/               # Modular rule files
│       ├── README.md        # Rules pattern guide
│       ├── documentation.md # Documentation standards
│       ├── testing.md       # Testing approaches
│       └── architecture.md  # Architecture patterns
├── docs/
│   ├── README.md            # Documentation index
│   ├── CURSOR.md            # Working with Cursor guide
│   ├── PROJECT_SETUP.md     # Customization guide
│   ├── ARCHITECTURE.md      # Architecture documentation
│   ├── CONTRIBUTING.md      # Contribution guidelines
│   ├── workflows/
│   │   └── README.md        # Workflow patterns guide
│   └── agents/
│       └── README.md        # Agent specialization guide
└── .github/
    └── README.md            # GitHub template info
```

## Core Concepts

### Modular Rules
Rules organized in `.cursor/rules/` for focused, context-appropriate guidance.  
→ See `@.cursor/rules/README.md` and `@.cursor/rules/SCHEMA.md`

### LLM-Optimized Documentation
Documentation structured for AI discovery with `@` references and focused files.  
→ See `@docs/cursor/index.md` for Cursor guide  
→ See `@docs/README.md` for documentation index

### Agentic Development
AI-driven development with clear context boundaries and discoverable resources.  
→ See `@QUICK_START.md` for AI agent orientation  
→ See `@docs/cursor/best-practices.md` for effective collaboration

## What's NOT Included

This template makes **no assumptions** about:
- Programming language
- Framework or libraries
- Build tools or package managers
- Testing frameworks
- CI/CD systems
- Deployment infrastructure

Add these as your project requires.

## Best Practices

### Working with AI

- **Be Specific**: "Add error handling to the login function" vs "Fix the bug"
- **Provide Context**: Use `@` references to relevant files and docs
- **Iterate**: Break large tasks into smaller, focused steps
- **Review**: Always review and test AI-generated code

### Organizing Rules

- Keep `.cursorrules` minimal and universal
- Add specific rules to `.cursor/rules/` as patterns emerge
- Use glob patterns to target specific file types
- Document why each rule exists

### Documentation

- Keep docs up-to-date as the project evolves
- Use skeletons as starting points, fill in as needed
- Link between related documents
- Write for both humans and AI readers

## Resources

- [Cursor Documentation](https://cursor.sh/docs)
- [Trunk-Based Development](https://trunkbaseddevelopment.com/)
- [Conventional Commits](https://www.conventionalcommits.org/)

## Contributing

This template is designed to be improved by the community. If you have suggestions:

1. Use it in a real project
2. Note what works and what doesn't
3. Submit issues or PRs with improvements

See `docs/CONTRIBUTING.md` for guidelines.

## License

MIT License - see [LICENSE](LICENSE) for details.

---

**Ready to start?** Open this project in Cursor and try the sample prompts above to customize it for your needs.

