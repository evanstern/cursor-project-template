# Rules Quick Reference

<!-- For AI: Load this for a quick rules summary instead of README.md -->

Quick reference for modular rules system.

## Available Rules

### Universal Rules

**`.cursorrules`**
- Core project rules
- Always active
- Universal principles

### Modular Rules (`.cursor/rules/`)

**`documentation.md`**
- Documentation standards
- JSDoc/docstring requirements
- Applied to: Code files (via globs)

**`testing.md`**  
- Testing patterns
- Test structure guidelines
- Applied to: Test files (via globs)

**`architecture.md`**
- Architecture principles
- Design patterns
- Applied to: Manual reference

## Rule Loading

### Automatic
Rules with `globs` in frontmatter load automatically:
```yaml
globs:
  - '**/*.test.ts'  # Loads when editing test files
```

### Manual
Reference explicitly with @:
```
@.cursor/rules/architecture.md
```

### Always
Rules with `alwaysApply: true` always load

## Creating Rules

### Minimal Rule

```yaml
---
description: Brief description
---

# Rule Content

Markdown content here
```

### With Auto-Loading

```yaml
---
description: Brief description
globs:
  - '**/*.ts'
  - '**/*.tsx'
alwaysApply: false
---

# Rule Content
```

### Always-Applied

```yaml
---
description: Brief description
alwaysApply: true
---

# Rule Content
```

## Schema Quick Reference

**Required:**
- `description` (string) - Brief description

**Optional:**
- `globs` (array) - File patterns
- `alwaysApply` (boolean) - Always include?

See `@.cursor/rules/SCHEMA.md` for full schema.

## Common Globs

```yaml
# All TypeScript
- '**/*.ts'
- '**/*.tsx'

# Test files
- '**/*.test.ts'
- '**/*.spec.ts'

# Specific directory
- 'src/api/**/*.ts'

# Multiple extensions
- '**/*.{ts,js,jsx,tsx}'

# Python tests
- '**/*_test.py'
- '**/test_*.py'
```

## When to Create Rules

Create rule when you notice:
- Repeated corrections in similar contexts
- Inconsistent patterns across codebase
- Need for specialized guidance
- Language/framework-specific standards

## File Naming

Use **kebab-case**:
- `documentation.md` ✅
- `api-design.md` ✅  
- `testing-standards.md` ✅
- `DOCUMENTATION.md` ❌
- `documentation_standards.md` ❌

## Rule Organization

**By Language:**
- `python-standards.md`
- `typescript-standards.md`

**By Domain:**
- `api-design.md`
- `frontend-patterns.md`
- `backend-patterns.md`

**By Concern:**
- `testing.md`
- `documentation.md`
- `security.md`

## Best Practices

1. **One concern per rule** - Keep focused
2. **Provide examples** - Show good/bad patterns
3. **Explain why** - Not just what
4. **Test rules** - Verify they load
5. **Use globs wisely** - Auto-load relevant contexts only
6. **Keep updated** - Remove outdated guidance

## Quick Debugging

**Rule not loading?**
1. Check file in `.cursor/rules/`
2. Validate YAML frontmatter
3. Check globs match your file
4. Try manual: `@.cursor/rules/your-rule.md`

**Multiple rules conflict?**
1. Make globs more specific
2. Consolidate related rules
3. Document precedence

**Too many rules slow?**
1. Use globs to limit auto-loading
2. Set `alwaysApply: false`
3. Consolidate similar rules

## Example Rules by Project Type

### Web App (TypeScript/React)

```
.cursor/rules/
├── react-patterns.md      (Components)
├── api-integration.md     (API clients)
├── styling.md             (CSS/Tailwind)
├── testing.md             (Jest/RTL)
└── accessibility.md       (A11y)
```

### API Backend (Python)

```
.cursor/rules/
├── api-design.md          (REST patterns)
├── database.md            (ORM/queries)
├── authentication.md      (Auth patterns)
├── error-handling.md      (Errors)
└── testing.md             (Pytest)
```

### Mobile App (React Native)

```
.cursor/rules/
├── navigation.md          (Navigation)
├── native-modules.md      (Native bridge)
├── performance.md         (Mobile perf)
├── offline-first.md       (Sync)
└── testing.md             (Mobile tests)
```

## Common Patterns

**Auto-attach to test files:**
```yaml
---
description: Testing standards
globs:
  - '**/*.test.ts'
  - '**/*.spec.ts'
alwaysApply: false
---
```

**Always apply security rules:**
```yaml
---
description: Security practices
alwaysApply: true
---
```

**Manual reference for migrations:**
```yaml
---
description: Database migrations
# No globs - manual only
---
```

## Resources

**Full Guides:**
- `@.cursor/rules/README.md` - Complete guide
- `@.cursor/rules/SCHEMA.md` - Full schema

**Examples:**
- `@.cursor/rules/documentation.md` - Doc standards
- `@.cursor/rules/testing.md` - Test patterns
- `@.cursor/rules/architecture.md` - Architecture

---

**For AI Agents:** Use this for quick rules reference. Load full README or SCHEMA when users need detailed guidance.

**For Users:** Quick lookup for common rule patterns. See README for comprehensive guide.

