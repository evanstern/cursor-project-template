# Troubleshooting

<!-- For AI: Load this when users experience issues with Cursor -->

Common issues and solutions when working with Cursor.

## AI Not Following Rules

### Problem
AI-generated code doesn't match project standards or ignores rules.

### Solutions

**1. Reference Rules Explicitly**
```
@.cursorrules @.cursor/rules/documentation.md
Create a new module following these standards
```

**2. Check Rule Frontmatter**
- Are globs correct for your file types?
- Is `alwaysApply` set appropriately?
- Is YAML valid?

**3. Verify Rule Loading**
Ask: "What rules are you following?"

**4. Be More Specific**
Instead of: "Follow the rules"
Try: "Follow the testing patterns in @.cursor/rules/testing.md"

---

## Context Overload

### Problem
AI seems confused or gives inconsistent answers.

### Solutions

**1. Reduce Context**
Load only what's needed:
```
❌ @src/ @docs/ @tests/
✅ @src/services/UserService.ts
```

**2. Start Fresh**
Long conversations lose focus. Start a new chat.

**3. Progressive Loading**
Load context step by step:
```
Step 1: @docs/ARCHITECTURE.md - understand structure
Step 2: @src/services/ - see patterns
Step 3: create new service
```

**4. Use Quick References**
Instead of full docs, use:
- `@docs/QUICK_REFERENCE.md`
- `@.cursor/rules/QUICK_REFERENCE.md`

---

## Changes Too Broad

### Problem
AI Panel modifies too many files or makes unwanted changes.

### Solutions

**1. Be More Specific**
```
❌ "Update the authentication"
✅ "Update AuthService.ts to add token refresh, don't modify other files"
```

**2. Scope the Change**
```
Changes should be limited to src/auth/ directory only
```

**3. Use Inline Edit**
For single-file changes, use `⌘K` instead of the AI Panel.

**4. Break Into Steps**
Instead of one large change, make multiple focused changes.

---

## AI Doesn't Have Enough Context

### Problem
AI gives generic or incorrect answers.

### Solutions

**1. Add File References**
```
@src/api/users.ts explain how this works
```

**2. Add Documentation Context**
```
@docs/ARCHITECTURE.md @src/services/
How should I structure a new service?
```

**3. Provide Background**
```
I'm working on the authentication system.
Currently, we use JWT tokens.
I need to add refresh token support.
@src/auth/AuthService.ts
```

**4. Use @Codebase for Discovery**
```
@codebase where is authentication handled?
```

---

## Lost Context in Long Sessions

### Problem
AI forgets earlier conversation or gives inconsistent answers.

### Solutions

**1. Start New Session**
Fresh start when switching topics or losing focus.

**2. Re-provide Context**
```
To clarify: I'm working on @src/auth/login.ts
We were discussing token refresh
```

**3. Summarize Progress**
```
So far we've:
1. Added token refresh to AuthService
2. Updated the login flow
Now I need to add error handling
```

---

## Rules Not Being Applied

### Problem
Modular rules aren't being used automatically.

### Solutions

**1. Check Glob Patterns**
```yaml
globs:
  - '**/*.test.ts'    # Correct
  - 'tests/**/*.ts'   # Also correct
  - '*.test.ts'       # Wrong - not recursive
```

**2. Check alwaysApply**
```yaml
alwaysApply: false  # Must match file glob
alwaysApply: true   # Always included
```

**3. Reference Manually**
```
@.cursor/rules/testing.md write tests for this
```

**4. Verify File Location**
Rules must be in `.cursor/rules/` directory.

---

## Type Errors After AI Changes

### Problem
TypeScript errors after AI generates code.

### Solutions

**1. Check Types Match**
```
@src/types/ verify these types match the API
```

**2. Ask for Fix**
```
Fix TypeScript errors in @src/services/UserService.ts
```

**3. Provide Type Context**
```
@src/types/User.ts use this type definition
```

**4. Verify Imports**
Check that imports point to correct files.

---

## Tests Failing After Changes

### Problem
Tests break after AI makes changes.

### Solutions

**1. Run Tests Incrementally**
Run tests after each change, not at the end.

**2. Ask for Test Updates**
```
Update tests in @tests/UserService.test.ts to match changes
```

**3. Verify Test Patterns**
```
@.cursor/rules/testing.md
Do these tests follow our patterns?
```

**4. Check for Breaking Changes**
Ensure API contracts haven't changed unexpectedly.

---

## Performance Issues

### Problem
Cursor is slow or unresponsive.

### Solutions

**1. Reduce Context**
Don't load entire directories:
```
❌ @src/
✅ @src/services/UserService.ts
```

**2. Use Semantic Search**
Instead of loading many files:
```
@codebase where is X implemented?
```

**3. Close Unused Files**
Close files you're not actively editing.

**4. Restart Cursor**
Sometimes a restart helps.

---

## Commit Messages Don't Follow Convention

### Problem
AI suggests non-conventional commit messages.

### Solutions

**1. Reference Standards**
```
@.cursorrules create a conventional commit message for these changes
```

**2. Specify Format**
```
Create commit message in format: type(scope): subject
Types: feat, fix, docs, refactor, test, chore
```

**3. Review and Edit**
Always review commit messages before committing.

---

## File Not Found Errors

### Problem
AI can't find files you reference.

### Solutions

**1. Check Path**
Ensure path is relative to workspace root:
```
✅ @src/services/UserService.ts
❌ @UserService.ts
```

**2. Check File Exists**
Verify file actually exists at that path.

**3. Use File Search**
```
⌘P (Mac) or Ctrl+P (Windows) to find file
```

**4. Use @Codebase**
```
@codebase find UserService
```

---

## AI Suggests Outdated Patterns

### Problem
AI uses old patterns instead of project standards.

### Solutions

**1. Reference Current Patterns**
```
@src/services/UserService.ts follow this pattern, not outdated approaches
```

**2. Update Rules**
Add rules for preferred patterns:
```
@.cursor/rules/ create rule for [modern pattern]
```

**3. Be Explicit**
```
Use async/await, not callbacks
Use ES6 modules, not CommonJS
```

---

## Error Messages Not Helpful

### Problem
AI doesn't understand error messages.

### Solutions

**1. Provide Full Error**
Copy entire error message, not just summary.

**2. Provide Context**
```
I'm getting this error:
[paste full error]

In file: @src/api/users.ts
At line: 45
When doing: fetching user data
```

**3. Show Code**
```
The error happens in this code:
[show relevant code section]
```

---

## Keyboard Shortcuts Not Working

### Problem
Expected shortcuts don't work.

### Solutions

**1. Check OS**
- Mac: `⌘` key
- Windows/Linux: `Ctrl` key

**2. Check Customizations**
Access: `⌘K ⌘S` (Mac) or `Ctrl+K Ctrl+S` (Windows)

**3. Try Command Palette**
`⌘Shift+P` or `Ctrl+Shift+P` → type action

**4. Check for Conflicts**
Other apps might intercept shortcuts.

---

## Quick Diagnostic Checklist

When something's not working:

- [ ] Am I using the right tool? (AI Panel vs Inline Edit)
- [ ] Have I provided enough context? (@ references)
- [ ] Are my requests specific enough?
- [ ] Is the file path correct?
- [ ] Are rules in the right location?
- [ ] Have I tried starting a fresh session?
- [ ] Have I checked @docs/TROUBLESHOOTING.md (main troubleshooting)?

---

## Getting More Help

If issues persist:

1. **Check Main Troubleshooting**
   `@docs/TROUBLESHOOTING.md` - Project-wide issues

2. **Check Documentation**
   - [basics.md](./basics.md) - Core concepts
   - [features.md](./features.md) - Tool capabilities
   - [context.md](./context.md) - Context management
   - [best-practices.md](./best-practices.md) - Working effectively

3. **Search Codebase**
   `@codebase [your issue]` - Find similar problems/solutions

4. **Ask in Chat**
   Describe your issue with context and what you've tried

---

**For AI Agents:** Use this to help users diagnose and fix common issues. For project-specific problems, refer to `@docs/TROUBLESHOOTING.md`.

**See also:**
- [best-practices.md](./best-practices.md) - Prevent issues
- [context.md](./context.md) - Provide better context
- `@docs/TROUBLESHOOTING.md` - Project-wide troubleshooting

