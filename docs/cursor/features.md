# Cursor Features

<!-- For AI: Load this when users need to understand specific Cursor tools -->

This guide covers Cursor's main features and when to use each.

## 1. AI Panel (⌘L or ⌘I / Ctrl+L or Ctrl+I)

### What It Is
The main AI assistant interface for conversations, planning, and multi-file editing. Both `⌘L` and `⌘I` open the same panel - there's no longer a distinction between "Chat" and "Composer" modes.

### When to Use the AI Panel

#### For Conversations & Planning
- **Questions**: "How does [feature] work in this codebase?"
- **Planning**: "How should I structure [new feature]?"
- **Debugging**: "Why is [component] not working?"
- **Code Review**: "Review this function for potential issues"
- **Learning**: "Explain this pattern"
- **Discussions**: Talk through approaches before implementing

#### For Multi-File Editing
- **Multi-file changes**: "Add [feature] across the codebase"
- **Feature implementation**: "Create [new module] with tests and docs"
- **Refactoring**: "Extract this logic into a separate module"
- **Scaffolding**: "Set up [new component/service/page]"
- **Large-scale changes**: Anything touching 2+ files

### Example Sessions

**Conversation & Planning:**
```
You: How should I add user authentication?
Cursor: [analyzes codebase and suggests approach]

You: Show me an example with JWT tokens
Cursor: [provides code example with JWT]

You: What about refresh tokens?
Cursor: [explains refresh token strategy]
```

**Multi-File Implementation:**
```
Create a user authentication module with login, logout, and token refresh.
Include error handling and tests.
```

**Refactoring:**
```
Extract the database logic from UserService into a UserRepository.
Update all imports and ensure tests still pass.
```

**Scaffolding:**
```
Create a new API endpoint for team management at /api/teams
with GET, POST, PUT, and DELETE operations.
```

### Best Practices for the AI Panel

✅ **Do:**
- Provide context with @ references
- Ask specific questions
- Break complex topics into smaller questions
- Request examples
- Be specific about scope for multi-file changes

✅ **Be Specific About Scope:**
- ✅ "Create a UserService class in src/services/"
- ❌ "Make a service"

✅ **Provide Context:**
- Reference existing patterns: "@src/services/TeamService.ts"
- Reference docs: "@docs/ARCHITECTURE.md"
- Reference rules: "@.cursor/rules/testing.md"

✅ **Break Down Large Tasks:**
Instead of: "Build the entire auth system"
Try: "Create the authentication service with login and logout"
Then: "Add token refresh to the authentication service"
Then: "Add password reset to the authentication service"

❌ **Don't:**
- Ask vague questions without context
- Forget to reference relevant files/docs
- Request changes to 10+ files at once
- Use for single-file edits (use Inline Edit instead)

## 2. Inline Edit (⌘K or Ctrl+K)

### What It Is
Direct code modifications within the editor. Best for focused, single-file changes.

### When to Use Inline Edit

- **Quick fixes**: Select code, describe the change
- **Documentation**: "Add comprehensive JSDoc"
- **Formatting**: "Refactor to use async/await"
- **Focused changes**: "Extract this into a separate function"
- **Small improvements**: "Add error handling here"
- **Single-file edits**: Anything within one file

### How It Works

1. **Select code** - Highlight the code you want to modify
2. **Press ⌘K** (or Ctrl+K)
3. **Describe change** - Tell Cursor what to do
4. **Review** - Accept, reject, or modify the suggestion

### Example Uses

**Add Documentation:**
```
Select: function calculateTotal(price, tax) { ... }
Edit: Add comprehensive JSDoc documentation
```

**Refactor:**
```
Select: if (user && user.email) { sendEmail(user.email) }
Edit: Use optional chaining
```

**Extract Function:**
```
Select: [10 lines of validation logic]
Edit: Extract this into a validateUser function
```

**Fix Issue:**
```
Select: const data = JSON.parse(response)
Edit: Add try-catch for parsing errors
```

### Best Practices for Inline Edit

✅ **Do:**
- Select the relevant code first
- Be specific about the change
- Use for single-file modifications
- Review the change before accepting

❌ **Don't:**
- Use for multi-file changes (use the AI Panel)
- Give vague instructions
- Select too much or too little code

## 3. Terminal

### What It Is
AI-aware terminal that can help with commands and debugging.

### Capabilities

- **Suggest commands** based on your project and context
- **Debug errors** in command output
- **Explain commands** and their options
- **Generate scripts** for common tasks

### Example Uses

**Get Command Suggestions:**
```
You: How do I run tests?
Terminal: Suggests appropriate test command based on your project
```

**Debug Errors:**
```
[Error appears in terminal]
You: What does this error mean?
Terminal: Explains error and suggests fixes
```

**Explain Commands:**
```
You: What does this command do?
Terminal: Breaks down the command and explains each part
```

## Choosing the Right Tool

Use this decision tree:

```
Need to...
│
├─ Ask questions / plan approach / multi-file edits
│  └─ Use AI PANEL (⌘L or ⌘I)
│
├─ Edit single file / quick fix
│  └─ Use INLINE EDIT (⌘K)
│
└─ Run commands / debug terminal
   └─ Use TERMINAL
```

## Combining Tools

Often you'll use multiple tools in sequence:

**Example Workflow:**
1. **[AI Panel]** "How should I structure this feature?"
2. **[AI Panel]** "Implement the feature as discussed"
3. **[Inline Edit]** Fix small issues in individual files
4. **[AI Panel]** "Review the implementation for issues"
5. **[Terminal]** Run tests and verify

## Common Patterns

### Pattern: Feature Development
```
1. AI Panel - Plan approach and implement across files
2. Inline Edit - Polish individual files
3. Terminal - Test and verify
```

### Pattern: Bug Fix
```
1. AI Panel - "@file.ts why is this failing?"
2. Inline Edit - Fix the specific issue
3. Terminal - Run tests
```

### Pattern: Refactoring
```
1. AI Panel - "How can I improve @module.ts?"
2. AI Panel - "Refactor as suggested"
3. Inline Edit - Touch-ups
4. Terminal - Verify nothing broke
```

## Tips

### For the AI Panel
- Provide context early in the conversation
- Ask follow-up questions to clarify
- Use for understanding before implementing
- Be specific about file locations for multi-file changes
- Reference existing patterns
- Break into smaller tasks if needed

### For Inline Edit
- Select the right amount of code
- Be clear about the change
- Use for focused, single-file edits

### For Terminal
- Let AI suggest commands when unsure
- Ask for explanations of errors
- Use for command discovery

---

**For AI Agents:** Reference this when users ask "which tool should I use?" or need help choosing between the AI Panel and Inline Edit.

**See also:**
- [basics.md](./basics.md) - Core concepts
- [context.md](./context.md) - Providing context
- [workflows.md](./workflows.md) - Step-by-step processes

