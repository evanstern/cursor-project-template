# Cursor Basics

<!-- For AI: Load this for core concepts about Cursor -->

## What is Cursor?

Cursor is an AI-powered code editor built on VS Code. It's designed for **agentic coding** - a development approach where AI assistants actively participate in the development process.

## Core Capabilities

Cursor provides three main tools for AI-assisted development:

### 1. AI Panel (⌘L or ⌘I / Ctrl+L or Ctrl+I)
The main AI assistant panel for conversations, questions, planning, and multi-file editing. Both shortcuts open the same panel.

### 2. Inline Edit (⌘K / Ctrl+K)
Direct code modifications within the editor for focused changes.

### 3. Terminal
AI-aware terminal that can suggest commands and explain output.

## Agentic Development

This project embraces **agentic coding principles**:

- **AI as Collaborator**: The AI actively participates in development
- **Context-Aware**: AI understands your codebase and project structure
- **Iterative**: Work in small, focused steps
- **Guided**: Rules and documentation guide AI behavior

## How It Works

1. **You provide context** - Use @ references to point AI to relevant files/docs
2. **AI understands** - Cursor reads your code, docs, and rules
3. **AI assists** - Generates code, explains concepts, suggests improvements
4. **You review** - Always verify and test AI-generated code

## Key Concepts

### Context is King
The more relevant context you provide, the better the AI performs. Learn to use:
- `@files` - Reference specific files
- `@folders` - Reference directories
- `@docs` - Reference documentation
- `@codebase` - Semantic search

See [context.md](./context.md) for details.

### Rules Guide Behavior
Rules tell the AI how to work on your project:
- Core rules in `.cursorrules`
- Modular rules in `.cursor/rules/`
- Project-specific patterns and standards

See `@.cursorrules` and `@.cursor/rules/README.md` for more.

### Right Tool for the Job
Use the appropriate Cursor feature for your task:
- **Questions/Planning/Multi-file changes** → AI Panel (⌘L or ⌘I)
- **Quick edits** → Inline Edit (⌘K)
- **Terminal commands** → Terminal

See [features.md](./features.md) for details.

## Getting Started

### Step 1: Understand the Features
Read [features.md](./features.md) to learn what each Cursor feature does.

### Step 2: Master Context Management
Read [context.md](./context.md) to learn how to provide effective context.

### Step 3: Follow Best Practices
Read [best-practices.md](./best-practices.md) for working effectively.

### Step 4: Try Common Workflows
Read [workflows.md](./workflows.md) for step-by-step processes.

## Learning Philosophy

### Start Simple
Begin with basic tasks using the AI Panel and Inline Edit.

### Provide Good Context
Always reference relevant files and docs with @.

### Iterate
Break large tasks into smaller, manageable steps.

### Review Everything
AI is a tool, not a replacement for your judgment.

## Next Steps

- **Learn features**: [features.md](./features.md)
- **Master context**: [context.md](./context.md)
- **Best practices**: [best-practices.md](./best-practices.md)
- **Common workflows**: [workflows.md](./workflows.md)

---

**For AI Agents:** This file covers core concepts. Load specific feature files when users need detailed guidance on particular aspects.

