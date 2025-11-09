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

Open the project in Cursor and use these sample prompts to get started:

#### Initial Setup Prompts

```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a [Next.js/Python/Rust/etc.] project
```

```
@.cursorrules Add project-specific rules for a [web app/API/CLI tool/mobile app]
```

```
@docs/ Create documentation structure for [your project type]
```

#### Adding Rules

```
@.cursor/rules/README.md Create a new rule for [coding standards/API patterns/testing]
```

```
Following @.cursor/rules/README.md, add a modular rule for [specific concern]
```

#### Setting Up Workflows

```
@docs/workflows/README.md Create a commit workflow that [your requirements]
```

```
@docs/workflows/README.md Set up a workflow for [feature development/bug fixes/releases]
```

#### Creating Agent Specs

```
@docs/agents/README.md Create an agent specification for [backend/frontend/testing/docs]
```

```
Following the pattern in @docs/agents/README.md, define a [specialized agent type]
```

#### Project Configuration

```
@.gitignore @.cursorignore Update these files for a [Node.js/Python/Go/Java] project
```

```
Add [build tool/package manager/framework] specific ignores to @.gitignore
```

### 3. Review and Iterate

The template provides skeletons and patterns. Work with Cursor to:
- Fill in documentation
- Add project-specific rules
- Create workflows for your team
- Define specialized agents as needed

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

Keep rules focused and context-appropriate by organizing them in `.cursor/rules/`:
- Each rule can target specific file types or contexts
- Rules can be automatically applied or manually invoked
- See `.cursor/rules/README.md` for patterns

### LLM-Optimized Documentation

Documentation is structured for easy discovery with `@` references:
- `@docs/CURSOR.md` - Guide for using Cursor effectively
- `@docs/workflows/` - Common workflow patterns
- `@docs/agents/` - Specialized agent specifications

### Agentic Development

This template supports AI-driven development:
- Clear context boundaries
- Focused, discoverable documentation
- Patterns over rigid prescriptions
- Iterative, collaborative approach

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

