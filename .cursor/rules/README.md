# Modular Rules in Cursor

This directory contains modular rule files that provide focused, context-specific guidance to AI assistants working on your project.

## What Are Modular Rules?

Modular rules allow you to organize AI guidance into focused, manageable pieces rather than one large `.cursorrules` file. Each rule file can:

- Target specific file types (e.g., only apply to `*.test.ts` files)
- Be automatically applied or manually invoked
- Focus on a single concern (documentation, testing, architecture, etc.)
- Be easily enabled, disabled, or modified

## Benefits

### For You
- **Easier to maintain** - Each rule file is focused and manageable
- **Better organization** - Group related rules together
- **Flexible control** - Enable/disable rules as needed
- **Clear responsibility** - One rule, one concern

### For the AI
- **Reduced context** - Only relevant rules are loaded
- **Clearer guidance** - Focused instructions per context
- **Better performance** - Less irrelevant information to process
- **Consistent behavior** - Clear expectations per file type

## Rule File Structure

Each rule file uses YAML frontmatter followed by markdown content:

```markdown
---
description: Brief description of what this rule covers
globs:
  - 'src/**/*.ts'
  - 'tests/**/*.test.ts'
alwaysApply: false
---

# Rule Title

Your rule content here in markdown format.

## Section 1
- Guideline 1
- Guideline 2

## Section 2
More guidance...
```

### Frontmatter Fields

- **`description`** (required) - Brief description shown in Cursor UI
- **`globs`** (optional) - File patterns this rule applies to
  - Uses glob syntax: `**/*.ts`, `src/**/*.py`, etc.
  - If omitted, rule must be manually invoked
- **`alwaysApply`** (optional, default: false) - If true, always include this rule

## When to Use Which Setting

### `alwaysApply: true`
Use for rules that should ALWAYS be active:
- Core coding standards
- Critical security practices
- Universal documentation requirements

**Example:** Core code quality rules

### `alwaysApply: false` with `globs`
Use for context-specific rules:
- Test file conventions (apply only to `*.test.ts`)
- Component patterns (apply only to `components/**/*.tsx`)
- API standards (apply only to `api/**/*.py`)

**Example:** Testing rules that only apply to test files

### No `globs` field
Use for rules you want to manually invoke:
- Architecture decision records
- Specialized workflows
- Optional patterns

**Example:** Migration guides, refactoring patterns

## Included Rule Examples

This template includes skeleton rules to demonstrate patterns:

### `documentation.md`
- Documentation standards for your project
- JSDoc/docstring requirements
- README patterns
- **Usage:** `@.cursor/rules/documentation.md write comprehensive docs for this module`

### `testing.md`
- Testing patterns and conventions
- Test structure guidelines
- Coverage expectations
- **Usage:** Applied automatically to test files via globs

### `architecture.md`
- Architectural patterns and decisions
- Code organization principles
- Design guidelines
- **Usage:** `@.cursor/rules/architecture.md review this design`

## Creating New Rules

### 1. Identify the Need

Create a new rule when you notice:
- Repeated corrections in similar contexts
- Inconsistent patterns across the codebase
- Need for specialized guidance in certain areas

### 2. Choose a Scope

Decide if the rule should be:
- **Always active** - Fundamental to all code
- **Auto-attached** - Applies to specific file types
- **Manual** - Invoked when needed

### 3. Create the File

```bash
# Create a new rule file
touch .cursor/rules/my-new-rule.md
```

### 4. Use the Template

```markdown
---
description: Brief description of this rule
globs:
  - 'path/to/**/*.ext'
alwaysApply: false
---

# Rule Title

## Purpose
Why this rule exists

## Guidelines
- Specific guidance 1
- Specific guidance 2

## Examples

Good:
\`\`\`language
// good example
\`\`\`

Bad:
\`\`\`language
// bad example
\`\`\`

## References
- Link to related docs
- Link to external resources
```

## Rule Ideas for Your Project

Common rule files projects often need:

- **`api-design.md`** - REST/GraphQL API patterns
- **`security.md`** - Security best practices
- **`performance.md`** - Performance considerations
- **`accessibility.md`** - A11y requirements
- **`git-workflow.md`** - Commit conventions, branching
- **`code-review.md`** - Review checklist and standards
- **`mobile-specific.md`** - Mobile platform guidelines
- **`backend-patterns.md`** - Backend-specific patterns
- **`frontend-patterns.md`** - Frontend-specific patterns
- **`database.md`** - Database interaction patterns

## Using Rules in Cursor

### Automatic Application

Rules with `globs` are automatically included when editing matching files:

```typescript
// Editing src/api/users.test.ts
// testing.md is automatically active (matches test globs)
```

### Manual Reference

Reference any rule explicitly with `@`:

```
@.cursor/rules/architecture.md help me design a new module
```

```
Following @.cursor/rules/api-design.md, create a new endpoint
```

### Combining Rules

Reference multiple rules for comprehensive guidance:

```
Following @.cursor/rules/documentation.md and @.cursor/rules/testing.md,
create a new utility function with tests and docs
```

## Best Practices

### Keep Rules Focused
- One concern per rule file
- Aim for 50-200 lines per rule
- If a rule grows too large, split it

### Be Specific
- Provide concrete examples
- Show good and bad patterns
- Explain the "why" behind rules

### Update Regularly
- Review rules as project evolves
- Remove outdated guidance
- Add new patterns as they emerge

### Test Your Rules
- Reference rules and see if AI follows them
- Refine based on results
- Document what works

### Don't Over-Engineer
- Start with few rules
- Add more as real needs emerge
- Remove rules that aren't helping

## Troubleshooting

### Rule Not Being Applied

**Problem:** Auto-attached rule isn't working

**Solutions:**
- Check glob pattern matches your files
- Verify frontmatter YAML is valid
- Try manual reference with `@`

### Too Much Context

**Problem:** AI seems confused with many rules

**Solutions:**
- Make rules more specific with globs
- Set `alwaysApply: false` for optional rules
- Split large rules into focused ones

### Rules Conflict

**Problem:** Rules give conflicting guidance

**Solutions:**
- Review and align contradicting rules
- Use more specific globs to separate contexts
- Consolidate related rules

## Examples from Real Projects

### Web Application

```
.cursor/rules/
├── README.md
├── react-patterns.md      # Component patterns
├── api-integration.md     # API client usage
├── styling.md             # CSS/styling conventions
├── testing.md             # Jest/RTL patterns
└── accessibility.md       # A11y requirements
```

### API Backend

```
.cursor/rules/
├── README.md
├── api-design.md          # REST endpoint patterns
├── database.md            # ORM/query patterns
├── authentication.md      # Auth patterns
├── error-handling.md      # Error response patterns
└── testing.md             # API test patterns
```

### Mobile App

```
.cursor/rules/
├── README.md
├── navigation.md          # Navigation patterns
├── native-modules.md      # Native bridge usage
├── performance.md         # Mobile perf guidelines
├── offline-first.md       # Offline sync patterns
└── testing.md             # Mobile testing
```

## Resources

- [Cursor Documentation](https://cursor.sh/docs) - Official Cursor docs
- [Glob Patterns](https://github.com/isaacs/minimatch) - Glob syntax reference

## Questions?

- Check `docs/CURSOR.md` for general Cursor usage
- Review `docs/PROJECT_SETUP.md` for setup guidance
- Look at example rules in this directory

---

**Remember:** Rules are guidelines for AI assistants. They should help, not hinder. Start simple, iterate based on real needs, and keep them maintainable.

