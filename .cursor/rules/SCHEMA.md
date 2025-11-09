# Modular Rules Schema

<!-- For AI: Load this when creating or validating modular rule files -->

This document defines the formal schema for modular rule files in `.cursor/rules/`.

## File Format

Modular rules use Markdown files with YAML frontmatter.

### Structure

```markdown
---
[YAML frontmatter]
---

[Markdown content]
```

## Frontmatter Schema

### Required Fields

#### `description` (string)
**Required:** Yes  
**Type:** String  
**Purpose:** Brief description shown in Cursor UI

**Example:**
```yaml
description: Documentation standards and best practices
```

**Guidelines:**
- Keep under 100 characters
- Describe what the rule covers
- Be specific but concise

### Optional Fields

#### `globs` (array of strings)
**Required:** No  
**Type:** Array of strings  
**Default:** None (manual invocation only)  
**Purpose:** File patterns this rule applies to

**Example:**
```yaml
globs:
  - '**/*.ts'
  - '**/*.tsx'
  - '**/*.js'
```

**Glob Syntax:**
- `**` - Matches any number of directories
- `*` - Matches any characters except `/`
- `?` - Matches single character except `/`
- `{a,b}` - Matches `a` or `b`

**Common Patterns:**
```yaml
# All TypeScript files
- '**/*.ts'

# Test files
- '**/*.test.ts'
- '**/*.spec.ts'

# Specific directory
- 'src/api/**/*.ts'

# Multiple extensions
- '**/*.{ts,tsx,js,jsx}'
```

#### `alwaysApply` (boolean)
**Required:** No  
**Type:** Boolean  
**Default:** `false`  
**Purpose:** Whether to always include this rule regardless of file type

**Example:**
```yaml
alwaysApply: true
```

**When to use `true`:**
- Core project standards that apply everywhere
- Universal coding principles
- Critical security practices

**When to use `false`:**
- Context-specific rules (testing, documentation)
- Language-specific patterns
- Optional guidelines

## Complete Examples

### Example 1: Auto-Attached Rule

```yaml
---
description: Testing standards and best practices
globs:
  - '**/*.test.ts'
  - '**/*.test.js'
  - '**/*.spec.ts'
  - '**/*_test.py'
alwaysApply: false
---

# Testing Standards

This rule applies when editing test files.

## Test Structure

Use AAA pattern (Arrange, Act, Assert)...
```

**Behavior:** Automatically loaded when editing files matching the globs.

### Example 2: Always-Applied Rule

```yaml
---
description: Core security practices
alwaysApply: true
---

# Security Standards

These rules apply to all code.

## Never Do
- Don't commit secrets
- Don't use eval()
- Always validate input
```

**Behavior:** Always included in every context.

### Example 3: Manual Rule

```yaml
---
description: Database migration guidelines
---

# Database Migrations

Guidelines for creating and running migrations.

## Before Creating Migration
1. Check existing migrations
2. Plan changes carefully
3. Test on local database
```

**Behavior:** Only used when explicitly referenced with `@.cursor/rules/migrations.md`.

## Content Guidelines

### Markdown Structure

Use standard Markdown with these recommendations:

**Use Clear Headings:**
```markdown
# Rule Title

## Section

### Subsection
```

**Use Code Blocks:**
````markdown
```language
code example
```
````

**Use Lists:**
```markdown
- Bullet point 1
- Bullet point 2

1. Numbered item 1
2. Numbered item 2
```

**Use Tables:**
```markdown
| Column 1 | Column 2 |
|----------|----------|
| Value 1  | Value 2  |
```

### Content Best Practices

**Be Specific:**
❌ "Write good code"
✅ "Use async/await for asynchronous operations"

**Provide Examples:**
```markdown
❌ **Bad:**
\`\`\`typescript
// bad example
\`\`\`

✅ **Good:**
\`\`\`typescript
// good example
\`\`\`
```

**Explain Why:**
```markdown
## Use TypeScript Strict Mode

**Why:** Catches type errors at compile time, not runtime.

**How:**
\`\`\`json
{
  "compilerOptions": {
    "strict": true
  }
}
\`\`\`
```

**Keep Focused:**
One rule = one concern. Don't mix testing + documentation + architecture in one file.

## Validation

### Valid Rule File

```yaml
---
description: API design patterns
globs:
  - 'src/api/**/*.ts'
alwaysApply: false
---

# API Design

## RESTful Principles
...
```

✅ Valid because:
- Has required `description`
- Globs are properly formatted
- alwaysApply is boolean
- Content is markdown

### Invalid Examples

**Missing description:**
```yaml
---
globs:
  - '**/*.ts'
---
```
❌ Error: `description` is required

**Invalid glob:**
```yaml
---
description: Test rule
globs: '**/*.ts'  # Should be array
---
```
❌ Error: `globs` must be an array

**Invalid alwaysApply:**
```yaml
---
description: Test rule
alwaysApply: "yes"  # Should be boolean
---
```
❌ Error: `alwaysApply` must be boolean

**No frontmatter separator:**
```yaml
---
description: Test rule
# Missing closing ---

Content here
```
❌ Error: Frontmatter not properly closed

## Testing Your Rules

### 1. Check YAML Validity

Ensure frontmatter is valid YAML:
- Proper indentation (2 spaces)
- Closing `---`
- Valid types

### 2. Test Glob Patterns

Check if globs match intended files:
```bash
# Test glob pattern
find . -path './src/**/*.test.ts'
```

### 3. Verify Loading

Reference the rule and verify it loads:
```
@.cursor/rules/your-rule.md is this rule loading correctly?
```

### 4. Check Behavior

Test automatic loading:
- Edit a file matching glob
- Verify rule is applied

## Common Patterns

### Pattern: Language-Specific Rule

```yaml
---
description: Python coding standards
globs:
  - '**/*.py'
alwaysApply: false
---

# Python Standards

PEP 8 compliance, type hints, docstrings...
```

### Pattern: Context-Specific Rule

```yaml
---
description: Component documentation
globs:
  - 'src/components/**/*.tsx'
  - 'src/components/**/*.jsx'
alwaysApply: false
---

# Component Documentation

Every component must have...
```

### Pattern: Universal Rule

```yaml
---
description: Code quality fundamentals
alwaysApply: true
---

# Code Quality

Applies to all code regardless of type...
```

## File Naming

**Convention:** `kebab-case.md`

**Examples:**
- `documentation.md`
- `testing.md`
- `api-design.md`
- `security-practices.md`

**Avoid:**
- `DOCUMENTATION.md` (all caps)
- `Documentation.md` (PascalCase)
- `documentation_standards.md` (snake_case)

## Rule Organization

### Directory Structure

```
.cursor/rules/
├── README.md              # Guide to modular rules
├── SCHEMA.md              # This file
├── QUICK_REFERENCE.md     # Rules summary
├── documentation.md       # Universal doc standards
├── testing.md             # Universal test patterns
├── architecture.md        # Universal architecture
├── python-standards.md    # Language-specific
├── typescript-standards.md # Language-specific
├── api-design.md          # Domain-specific
└── security.md            # Domain-specific
```

### Grouping Rules

**By Language:**
- `python-standards.md`
- `typescript-standards.md`
- `go-standards.md`

**By Domain:**
- `api-design.md`
- `database.md`
- `frontend-patterns.md`
- `backend-patterns.md`

**By Concern:**
- `testing.md`
- `documentation.md`
- `security.md`
- `performance.md`

## Troubleshooting

### Rule Not Loading

**Check:**
1. Is file in `.cursor/rules/` directory?
2. Is YAML frontmatter valid?
3. Do globs match your file?
4. Try manual reference: `@.cursor/rules/your-rule.md`

### Rule Conflicts

**Problem:** Multiple rules give conflicting guidance

**Solution:**
- Make globs more specific
- Consolidate related rules
- Use rule hierarchy (specific overrides general)

### Performance Issues

**Problem:** Too many rules slow down Cursor

**Solution:**
- Use globs to limit auto-loading
- Set `alwaysApply: false` for optional rules
- Consolidate similar rules

## Best Practices Summary

1. **Required description** - Always include
2. **Use globs wisely** - Auto-load only relevant contexts
3. **Keep focused** - One rule, one concern
4. **Provide examples** - Show good/bad patterns
5. **Explain why** - Don't just say what, explain why
6. **Test rules** - Verify they load and work
7. **Document patterns** - Show common use cases
8. **Keep updated** - Remove outdated guidance

---

**For AI Agents:** Use this schema when creating or validating modular rule files. Ensure all rules conform to this spec.

**See also:**
- [README.md](./README.md) - Guide to modular rules system
- [QUICK_REFERENCE.md](./QUICK_REFERENCE.md) - Quick schema reference

