# Best Practices

<!-- For AI: Load this when users need guidance on working effectively with Cursor -->

This guide covers best practices for effective AI-assisted development with Cursor.

## Core Principles

### 1. Be Specific

Vague requests get generic responses. Specific requests get targeted help.

❌ **Vague:** "Fix the bug"
✅ **Specific:** "Fix the null pointer error in UserService.getUser when user ID doesn't exist"

❌ **Too broad:** "Build the app"
✅ **Scoped:** "Create the authentication module with login and logout"

❌ **Unclear:** "Make it better"
✅ **Clear:** "Refactor this function to use async/await and add error handling"

### 2. Provide Context

Always provide relevant context with @ references.

❌ **No context:**
```
How do I add a new service?
```

✅ **With context:**
```
@docs/ARCHITECTURE.md @src/services/UserService.ts
How do I add a new TeamService following these patterns?
```

See [context.md](./context.md) for details.

### 3. Iterate Incrementally

Break large tasks into smaller, focused steps.

❌ **Too large:**
```
Build the entire user management system with CRUD, auth, and roles
```

✅ **Incremental:**
```
Step 1: Create User data model
Step 2: Add UserRepository for database access
Step 3: Create UserService with business logic
Step 4: Add authentication endpoints
Step 5: Implement role-based access control
Step 6: Write tests for each component
```

### 4. Review AI Suggestions

AI is a tool, not a replacement for your judgment.

**Always review:**
- Correctness - Does it do what it should?
- Error handling - Are edge cases covered?
- Security - Any vulnerabilities?
- Performance - Any obvious issues?
- Standards - Does it follow project conventions?
- Tests - Are tests needed?
- Documentation - Is it documented?

### 5. Use the Right Tool

Match the tool to the task:

| Task | Tool | Why |
|------|------|-----|
| Questions, planning, multi-file edits | AI Panel (⌘L or ⌘I) | Conversational and multi-file |
| Single-file edits | Inline Edit (⌘K) | Focused changes |
| Terminal commands | Terminal | Command help |

> **Note:** Both ⌘L and ⌘I open the same AI Panel - there's no longer separate "Chat" and "Composer" modes.

See [features.md](./features.md) for details.

### 6. Leverage Documentation

Reference project docs frequently:

```
@docs/ @.cursorrules create a new module following project standards
```

```
@.cursor/rules/testing.md write tests for this feature
```

```
@docs/ARCHITECTURE.md ensure this fits the architecture
```

### 7. Use Modular Rules

Reference specific rules for focused guidance:

```
@.cursor/rules/documentation.md add comprehensive docs to this module
```

```
@.cursor/rules/testing.md test this component thoroughly
```

```
@.cursor/rules/architecture.md does this follow our patterns?
```

## Effective Prompting

### Structure Your Requests

**Good prompt structure:**
1. Context (@ references)
2. Current state
3. Desired outcome
4. Constraints/requirements

**Example:**
```
@src/api/users.ts @docs/API.md

Currently, the users API has GET and POST endpoints.

Add PUT and DELETE endpoints following the same patterns.

Requirements:
- Include input validation
- Add error handling
- Write tests
- Update API documentation
```

### Be Clear About Scope

**Define boundaries:**

✅ "Update UserService.ts only"
✅ "Changes limited to src/auth/ directory"
✅ "Don't modify database schema"

### Request Examples

When unsure, ask for examples:

```
Show me an example of [pattern] used in this codebase
```

```
@codebase show me how error handling is done
```

### Ask for Explanations

Understand before implementing:

```
Explain how authentication works in @src/auth/
before I add new features
```

## Working with Code

### Before Writing Code

1. **Understand the context** - What exists? What patterns are used?
2. **Plan the approach** - Discuss with AI Panel before implementing
3. **Check standards** - Review @.cursorrules and modular rules
4. **Find examples** - Look for similar code to follow

### While Writing Code

1. **Reference patterns** - "@existing/file.ts follow this pattern"
2. **Follow standards** - "@.cursor/rules/[rule].md follow these standards"
3. **Add tests** - Test as you go, not after
4. **Document** - Add docs while code is fresh

### After Writing Code

1. **Review** - Read through generated code carefully
2. **Test** - Run tests, try edge cases
3. **Lint** - Check for style issues
4. **Verify standards** - Does it follow project conventions?
5. **Update docs** - Keep documentation in sync

## Efficient Workflows

### Pattern: Learn → Plan → Implement → Verify

1. **Learn** (AI Panel)
```
@codebase how does feature X work?
@docs/ARCHITECTURE.md where should this go?
```

2. **Plan** (AI Panel)
```
What's the best approach for implementing Y?
```

3. **Implement** (AI Panel or Inline Edit)
```
Implement the feature following the planned approach
```

4. **Verify** (Terminal + AI Panel)
```
Run tests and review results
```

### Pattern: Fix Issues Incrementally

1. Identify the problem
2. Understand the cause
3. Fix the specific issue
4. Verify the fix
5. Check for related issues

**Don't:**
- Fix multiple unrelated issues at once
- Make large changes without understanding
- Skip verification steps

### Pattern: Refactoring Safely

1. Ensure tests exist and pass
2. Make small, incremental changes
3. Run tests after each change
4. Keep commits small
5. Document why you refactored

## Managing Context

### Start Conversations Fresh

Long conversations lose context. Start new chats for new topics.

**When to start fresh:**
- Switching to unrelated task
- Context feels lost
- AI gives inconsistent answers
- Starting a new feature

### Progressive Context Loading

Load context progressively, not all at once:

```
Step 1: @docs/ARCHITECTURE.md - Understand structure
Step 2: @src/services/ - See patterns
Step 3: Create new service following patterns
```

Not:
```
@docs/ @src/ @tests/ @everything/ create something
```

### Re-provide Context

If AI seems confused, re-provide context:

```
To clarify: I'm working on @src/auth/AuthService.ts
trying to add token refresh functionality
```

## Common Mistakes

### Mistake: Vague Requests

❌ "It doesn't work"
✅ "@src/login.ts the email validation on line 23 always returns false"

### Mistake: No Context

❌ "Create a service"
✅ "@src/services/UserService.ts create a TeamService following this pattern"

### Mistake: Too Much at Once

❌ "Add auth, implement CRUD, set up database, add tests, deploy"
✅ "Add login endpoint with JWT authentication"

### Mistake: Ignoring Standards

❌ "Add documentation" (generic)
✅ "@.cursor/rules/documentation.md add JSDoc following project standards"

### Mistake: Not Reviewing

❌ Accept all AI suggestions blindly
✅ Review, test, and verify each suggestion

### Mistake: Wrong Tool

❌ Using Inline Edit for multi-file changes
✅ Use AI Panel for multi-file changes

### Mistake: Forgetting Tests

❌ Implement feature, forget tests
✅ "@.cursor/rules/testing.md add tests while implementing"

## Tips by Task Type

### Adding Features

1. Understand requirements clearly
2. Plan approach with @docs/ARCHITECTURE.md
3. Find similar examples with @codebase
4. Implement incrementally
5. Add tests concurrently
6. Document as you go

### Fixing Bugs

1. Reproduce the bug
2. Understand the cause
3. Write a failing test
4. Fix the issue
5. Verify test passes
6. Check for similar issues

### Refactoring

1. Ensure tests exist
2. Understand current implementation
3. Plan refactoring approach
4. Make small changes
5. Run tests frequently
6. Document changes

### Writing Tests

1. Reference @.cursor/rules/testing.md
2. Follow existing test patterns
3. Test behavior, not implementation
4. Cover edge cases
5. Keep tests focused

### Adding Documentation

1. Follow @.cursor/rules/documentation.md
2. Explain "why" not just "what"
3. Include examples
4. Keep concise but complete
5. Update when code changes

## Quality Checklist

Before considering work done:

- [ ] Code works correctly
- [ ] Edge cases handled
- [ ] Errors handled appropriately
- [ ] Tests written and passing
- [ ] Documentation added/updated
- [ ] Follows project standards
- [ ] No obvious performance issues
- [ ] Security considered
- [ ] Linter passes
- [ ] Reviewed by human (you!)

## Keyboard Efficiency

Learn shortcuts for speed:

- `⌘L` or `⌘I` / `Ctrl+L` or `Ctrl+I` - AI Panel
- `⌘K` / `Ctrl+K` - Inline Edit
- `⌘⇧P` / `Ctrl+Shift+P` - Command Palette

See [shortcuts.md](./shortcuts.md) for complete list.

## Remember

1. **Specific** requests get better results
2. **Context** is critical for quality
3. **Iterate** in small steps
4. **Review** everything AI generates
5. **Use** the right tool for the job
6. **Follow** project standards
7. **Test** as you go
8. **Document** while fresh

---

**For AI Agents:** Reference this when users need general guidance on working with Cursor effectively. For specific issues, see [troubleshooting.md](./troubleshooting.md).

**See also:**
- [features.md](./features.md) - Which tool to use
- [context.md](./context.md) - Providing context
- [workflows.md](./workflows.md) - Step-by-step processes
- [shortcuts.md](./shortcuts.md) - Keyboard shortcuts

