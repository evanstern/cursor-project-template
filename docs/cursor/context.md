# Context Management

<!-- For AI: Load this when users need to understand @ references -->

Cursor needs the right context to help effectively. This guide covers how to provide context using @ references.

## Why Context Matters

Without context, AI gives generic answers.  
With context, AI provides specific, relevant help.

**Example:**

❌ **Without context:**
```
You: How do I add authentication?
AI: [Generic authentication explanation]
```

✅ **With context:**
```
You: @docs/ARCHITECTURE.md @src/auth/ How do I add token refresh?
AI: [Specific guidance based on your architecture and existing code]
```

## The @ Symbol

Use `@` to reference context in Cursor:

- `@filename` - Reference a file
- `@folder/` - Reference a directory
- `@symbol` - Reference a function/class
- `@docs` - Search documentation
- `@web` - Search the web
- `@codebase` - Semantic search the code

## Types of Context

### @Files

Reference specific files:

```
@utils.ts how does this module work?
```

```
@UserService.ts add error handling to this service
```

```
Following @TeamService.ts, create a new GroupService
```

**When to use:**
- Asking about specific file
- Want AI to follow patterns from a file
- Modifying existing file

### @Folders

Reference entire directories:

```
@src/services/ explain the structure
```

```
@tests/ what test patterns are used?
```

```
Following patterns in @src/api/, create a new endpoint
```

**When to use:**
- Understanding directory structure
- Following patterns from multiple files
- Creating new files in a directory

**⚠️ Caution:** Loading entire folders uses many tokens. Be selective.

### @Code

Reference specific code symbols (functions, classes):

```
@formatDate what does this function do?
```

```
@UserRepository explain this class
```

```
@calculateTotal add tax parameter
```

**When to use:**
- Asking about specific function/class
- Modifying specific code
- Understanding implementation details

### @Docs

Reference documentation:

```
@docs/ARCHITECTURE.md what's the overall structure?
```

```
@.cursorrules what are the coding standards?
```

```
@docs/API.md what endpoints are available?
```

**When to use:**
- Following project standards
- Understanding architecture
- Checking conventions

### @Web

Search the web when needed:

```
@web latest React 19 features
```

```
@web how to implement WebSockets in Go
```

```
@web Python async best practices 2025
```

**When to use:**
- External knowledge needed
- Latest tech info
- Library/framework documentation

**⚠️ Note:** Uses network and may be slower. Use for external knowledge only.

### @Codebase

Semantic search across entire codebase:

```
@codebase where is authentication handled?
```

```
@codebase how are errors handled?
```

```
@codebase show me examples of database queries
```

**When to use:**
- Don't know where code is
- Looking for patterns
- Finding examples
- Discovering functionality

## Combining Context

Combine multiple contexts for better results:

```
Using @docs/ARCHITECTURE.md and @src/services/, 
show me how to add a new service
```

```
Following @.cursorrules and @.cursor/rules/testing.md,
write tests for @src/utils/formatters.ts
```

```
Based on @src/api/users.ts and @docs/API.md,
create a new teams endpoint
```

## Context Strategies

### Strategy: Exploratory Questions

When learning the codebase:

```
@codebase how does user authentication work?
```

Then drill down:

```
@src/auth/AuthService.ts explain this implementation
```

### Strategy: Pattern Following

When creating similar code:

```
Following the pattern in @src/services/UserService.ts,
create a TeamService
```

### Strategy: Standard Compliance

When following project rules:

```
@.cursorrules @.cursor/rules/documentation.md
document this new module
```

### Strategy: Contextual Implementation

When implementing features:

```
Based on @docs/ARCHITECTURE.md,
add a new data access layer for teams
```

## Best Practices

### ✅ Do

**Be Specific:**
```
@src/utils/date.ts explain formatRelativeTime
```

**Provide Relevant Context:**
```
@docs/ARCHITECTURE.md @src/services/ create a new service
```

**Layer Context:**
```
First: @docs/ what's the project structure?
Then: @src/api/ how are endpoints organized?
Finally: Create a new endpoint following those patterns
```

### ❌ Don't

**Load Everything:**
```
@src/ @docs/ @tests/ explain everything
```
*Too much context, wastes tokens*

**Be Vague:**
```
@project help me
```
*What file? What task?*

**Ignore Relevant Context:**
```
Create a new service
```
*Should reference @src/services/ for patterns*

## Token Efficiency

Context uses tokens. Be selective:

### Efficient Context Loading

✅ **Load what you need:**
```
@src/services/UserService.ts - ~500 tokens
```

❌ **Load whole directory:**
```
@src/services/ - ~5000 tokens (10 files)
```

### Smart Context Choices

**Instead of loading full documentation:**
```
@docs/cursor/index.md - Load overview first
@docs/cursor/features.md - Then specific topic if needed
```

**Instead of loading entire codebase:**
```
@codebase where is X? - Semantic search first
@specific/file.ts - Then load specific file
```

## Common Patterns

### Pattern: Understanding Existing Code

```
1. @codebase where is [feature] implemented?
2. @specific/file.ts explain this implementation
3. @related/file.ts how does this relate?
```

### Pattern: Following Conventions

```
1. @.cursorrules what are the standards?
2. @.cursor/rules/[specific].md specific guidelines
3. @example/file.ts show me an example
4. Create following those patterns
```

### Pattern: Implementing Features

```
1. @docs/ARCHITECTURE.md understand structure
2. @existing/similar.ts follow this pattern
3. @.cursor/rules/testing.md add tests per standards
```

## Troubleshooting Context

### Problem: AI Doesn't Understand

**Solution:** Add more specific context

❌ "It's not working"
✅ "@src/auth/login.ts the authentication fails at line 45"

### Problem: AI Gives Wrong Patterns

**Solution:** Reference correct examples

❌ "Create a service"
✅ "Following @src/services/UserService.ts, create TeamService"

### Problem: AI Ignores Standards

**Solution:** Explicitly reference rules

❌ "Add documentation"
✅ "@.cursor/rules/documentation.md add docs following these standards"

### Problem: Too Much Context Loaded

**Solution:** Be more selective

❌ "@src/ @docs/ @tests/"
✅ "@src/services/UserService.ts" (just what's needed)

## Quick Reference

```
CONTEXT TYPE          SYNTAX                    USE CASE
────────────────────────────────────────────────────────────
Specific File         @file.ts                  Precise reference
Directory             @folder/                  Multiple files
Code Symbol           @functionName             Specific function
Documentation         @docs/file.md             Project docs
Web Search            @web query                External info
Codebase Search       @codebase query           Find in project
```

## Examples by Task

### Task: Create New Feature

```
@docs/ARCHITECTURE.md @src/services/UserService.ts
Create a TeamService following the architecture and UserService pattern
```

### Task: Fix Bug

```
@src/components/LoginForm.tsx
The login button at line 45 doesn't validate email before submitting
```

### Task: Add Tests

```
@.cursor/rules/testing.md @src/utils/formatters.ts
Write comprehensive tests for the formatDate function
```

### Task: Understand Code

```
@codebase how does caching work?
[Gets answer pointing to specific files]
@src/cache/CacheService.ts explain this implementation
```

### Task: Refactor

```
@docs/ARCHITECTURE.md @src/api/users/routes.ts
Refactor this to follow the repository pattern from the architecture docs
```

---

**For AI Agents:** This is the most important guide for helping users provide good context. Reference it when users ask vague questions or don't provide enough context.

**See also:**
- [features.md](./features.md) - Which tool to use
- [best-practices.md](./best-practices.md) - Working effectively
- [troubleshooting.md](./troubleshooting.md) - Common issues

