# Agent Specializations

This directory contains specifications for specialized AI agents that assist with different aspects of the project.

## What Are Agent Specializations?

Agent specializations are focused AI personas that excel at specific types of tasks. Instead of a general-purpose AI assistant, you can invoke specialized agents with deep expertise in particular domains.

## Why Use Specialized Agents?

### Benefits

**For Single-Domain Projects:**
- May not need specialized agents
- General AI with good rules may be sufficient

**For Multi-Domain Projects:**
- **Focused Expertise** - Agent knows domain-specific patterns
- **Better Context** - Relevant rules and knowledge loaded
- **Clearer Communication** - Explicit about what kind of help you need
- **Consistent Patterns** - Each domain follows its own standards

### When to Create Agent Specs

Create agent specifications when you have:
- **Multiple Platforms** - Web, mobile, backend, etc.
- **Different Tech Stacks** - Frontend (React) vs Backend (Python)
- **Specialized Roles** - Testing, documentation, DevOps
- **Domain Expertise** - Security, accessibility, performance

## Using Agents in Cursor

### Invoking an Agent

Prefix your request with the agent name:

```
[Backend] Create a new API endpoint for user management
```

```
[Frontend] Add a responsive navigation component
```

```
[Testing] Write E2E tests for the login flow
```

```
[Documentation] Document the authentication system
```

### Combining with Context

Reference agent specs and relevant context:

```
@docs/agents/BACKEND.md Following the patterns in @src/api/, create a new endpoint
```

### Switching Agents

Switch agents mid-conversation:

```
[Backend] Create the API endpoint
[Frontend] Now create the UI to call that endpoint
[Testing] Test the integration between them
```

## Agent Specification Structure

Each agent spec should include:

```markdown
# [Agent Name] Agent

## Role & Expertise

What this agent specializes in.

## Technologies

Specific tech stack this agent works with.

## Responsibilities

What types of tasks this agent handles.

## Patterns & Standards

Domain-specific patterns to follow.

## Examples

Common tasks and how to approach them.

## Resources

Links to relevant documentation.
```

## Common Agent Types

### Platform-Specific Agents

**Backend Agent**
- API development
- Database interactions
- Server-side logic
- Authentication/authorization

**Frontend Agent (Web)**
- UI components
- State management
- Browser APIs
- Styling and layout

**Mobile Agent**
- Native features
- Mobile-specific UI
- Platform differences (iOS/Android)
- Mobile performance

### Role-Specific Agents

**Testing Agent**
- Test strategy
- Writing tests
- Test automation
- QA processes

**Documentation Agent**
- Code documentation
- API documentation
- User guides
- Architecture docs

**DevOps Agent**
- Infrastructure
- CI/CD pipelines
- Deployment
- Monitoring

**Security Agent**
- Security reviews
- Vulnerability scanning
- Secure coding practices
- Authentication/authorization

**Performance Agent**
- Performance optimization
- Profiling
- Benchmarking
- Resource management

**Accessibility Agent**
- A11y compliance
- WCAG guidelines
- Assistive technology
- Inclusive design

## Creating Agent Specifications

### 1. Identify the Domain

What specific area needs specialized guidance?

Examples:
- Platform (web vs mobile vs backend)
- Technology (React vs Vue vs Angular)
- Role (testing vs documentation)
- Concern (security vs performance)

### 2. Define Expertise

What should this agent be expert in?

- Technologies used
- Patterns and practices
- Common challenges
- Best practices

### 3. Document Standards

What standards apply to this domain?

- Coding conventions
- File organization
- Naming patterns
- Testing requirements

### 4. Provide Examples

Show common tasks:

```markdown
## Common Tasks

### Creating a New Component

1. Create component file in `src/components/`
2. Use TypeScript with strict types
3. Add JSDoc documentation
4. Export from `index.ts`
5. Write tests in `.test.tsx`

Example:
\`\`\`typescript
// Good component example
\`\`\`
```

### 5. Link Resources

Point to relevant documentation:

- Internal docs
- External resources
- Framework docs
- Best practice guides

## Example Agent Spec

### Testing Agent Example

```markdown
# Testing Agent

## Role & Expertise

Specializes in software testing, quality assurance, and test automation.

## Technologies

- Testing Framework: Jest
- E2E Testing: Playwright
- Test Organization: Co-located with source

## Responsibilities

- Write unit tests
- Write integration tests
- Create E2E test scenarios
- Review test coverage
- Identify edge cases

## Patterns & Standards

### Test Structure
Follow AAA pattern (Arrange, Act, Assert)

### Test Naming
Use descriptive names: "should [expected behavior] when [condition]"

### Coverage Goals
Aim for 80%+ coverage on business logic

## Common Tasks

### Writing a Unit Test

1. Create test file next to source (`*.test.ts`)
2. Use AAA pattern
3. Test behavior, not implementation
4. Cover edge cases

### Writing E2E Tests

1. Create scenario in `tests/e2e/`
2. Use Playwright selectors
3. Test user journeys
4. Verify UI state

## Resources

- @.cursor/rules/testing.md
- @docs/TESTING.md (if it exists)
```

## Agent Specification Template

Use this template to create new agent specs:

```markdown
# [Agent Name] Agent

## Role & Expertise

[What this agent specializes in]

## Technologies

- **Primary Language**: [e.g., TypeScript]
- **Framework**: [e.g., React]
- **Tools**: [e.g., Jest, ESLint]
- **Platform**: [e.g., Web, iOS, Android]

## Responsibilities

What this agent handles:
- [Responsibility 1]
- [Responsibility 2]
- [Responsibility 3]

What this agent does NOT handle:
- [Out of scope 1]
- [Out of scope 2]

## Patterns & Standards

### [Pattern Category 1]

Description and guidelines.

### [Pattern Category 2]

Description and guidelines.

## Common Tasks

### [Task Name 1]

Steps to accomplish this task.

**Example:**
\`\`\`
[code example]
\`\`\`

### [Task Name 2]

Steps to accomplish this task.

## Best Practices

- [Best practice 1]
- [Best practice 2]
- [Best practice 3]

## Anti-Patterns to Avoid

- ❌ [Anti-pattern 1]
- ❌ [Anti-pattern 2]

## Resources

Internal:
- @docs/[relevant-doc].md
- @.cursor/rules/[relevant-rule].md

External:
- [External resource 1]
- [External resource 2]

## Questions to Ask When Stuck

1. [Helpful question 1]
2. [Helpful question 2]

---

**Invoke this agent:** `[Agent Name] [your request]`
```

## Managing Multiple Agents

### Agent Coordination

When multiple agents work together:

```
[Backend] Create the API endpoint
↓
[Frontend] Create UI to consume the endpoint
↓
[Testing] Test the integration
↓
[Documentation] Document the feature
```

### Shared Responsibilities

All agents should:
- Follow core project rules (`.cursorrules`)
- Maintain code quality
- Write documentation
- Handle errors appropriately
- Follow git conventions

### Agent-Specific Rules

Each agent can have its own modular rules:

```
.cursor/rules/
├── backend-patterns.md      (Backend agent)
├── frontend-patterns.md     (Frontend agent)
├── mobile-patterns.md       (Mobile agent)
└── testing-patterns.md      (Testing agent)
```

Reference in agent spec:

```markdown
## Modular Rules

This agent follows: @.cursor/rules/backend-patterns.md
```

## Best Practices

### Don't Over-Specialize

❌ **Too many agents:**
- React Component Agent
- React Hook Agent
- React Context Agent
- React Styling Agent

✅ **Right level:**
- Frontend (Web) Agent

### Keep Specs Focused

- Each agent has clear domain
- Avoid overlap between agents
- Clear boundaries of responsibility

### Update Regularly

- Review agent specs as project evolves
- Update when patterns change
- Remove unused agents
- Add new agents as needed

### Make Invocation Clear

Document how to invoke each agent:

```markdown
## Invoking This Agent

Prefix requests with `[Agent Name]`:

\`\`\`
[Backend] Create a new API endpoint
\`\`\`

Or reference the spec:

\`\`\`
@docs/agents/BACKEND.md Following these patterns, create an endpoint
\`\`\`
```

## Examples from Real Projects

### Web Application (React + Node.js)

```
docs/agents/
├── README.md
├── FRONTEND.md       # React web development
├── BACKEND.md        # Node.js API development
├── TESTING.md        # Jest + Playwright testing
└── DOCUMENTATION.md  # Technical writing
```

### Mobile App (React Native)

```
docs/agents/
├── README.md
├── MOBILE.md         # React Native development
├── IOS.md            # iOS-specific agent
├── ANDROID.md        # Android-specific agent
└── TESTING.md        # Mobile testing
```

### Full-Stack Monorepo

```
docs/agents/
├── README.md
├── WEB.md            # Frontend web
├── MOBILE.md         # Mobile apps
├── API.md            # Backend API
├── DATABASE.md       # Database/migrations
├── DEVOPS.md         # Infrastructure/deployment
├── TESTING.md        # QA and testing
└── DOCS.md           # Documentation
```

## Troubleshooting

### Agent Not Following Spec

**Problem:** Agent doesn't seem to follow the specification

**Solutions:**
- Reference the spec explicitly: `@docs/agents/AGENT.md`
- Be more specific about what patterns to follow
- Check if spec is clear and unambiguous
- Provide examples in the spec

### Too Much Context Switching

**Problem:** Constantly switching between agents is tedious

**Solutions:**
- Maybe you don't need specialized agents
- Combine related domains (e.g., web + mobile → "frontend")
- Use general AI with good modular rules instead

### Agents Have Conflicting Guidance

**Problem:** Different agents give contradictory advice

**Solutions:**
- Review agent specs for conflicts
- Define clear boundaries between agents
- Establish shared standards in `.cursorrules`
- Consolidate overlapping agents

## When NOT to Use Agents

You might not need agent specializations if:

- **Simple project** - Single platform, single technology
- **Small codebase** - Everything fits in one context
- **Solo developer** - No need for role separation
- **Consistent stack** - Same patterns everywhere

In these cases, well-written `.cursorrules` and modular rules may be sufficient.

## Resources

- [Cursor Documentation](https://cursor.sh/docs)
- [Agent-Based Software Development](https://en.wikipedia.org/wiki/Agent-oriented_programming)

---

**Remember:** Agent specializations are a tool, not a requirement. Use them when they add value by providing focused expertise for distinct domains in your project. Start simple and add specialization as needed.

