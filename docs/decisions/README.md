# Architecture Decision Records (ADRs)

This directory contains Architecture Decision Records for this project. ADRs document important technical decisions made during development.

## What are ADRs?

Architecture Decision Records are lightweight documents that capture important architectural decisions along with their context and consequences. They help:

- **Future you** remember why decisions were made
- **Team members** understand the reasoning behind choices
- **AI agents** understand project context and constraints
- **New contributors** get up to speed quickly

## When to Create an ADR

Create an ADR when making decisions about:

- Technology choices (frameworks, libraries, tools)
- Architectural patterns (monorepo vs. multi-repo, microservices vs. monolith)
- Data storage solutions (database types, caching strategies)
- External services and integrations
- Security approaches
- Development workflows
- Build and deployment strategies

**Rule of thumb:** If you're choosing between alternatives and the choice will be hard to reverse, document it.

## ADR Format

Use the template in `000-template.md`. Each ADR should have:

1. **Title** - Short, descriptive name
2. **Status** - Proposed, Accepted, Deprecated, Superseded
3. **Context** - What problem are we solving?
4. **Decision** - What did we decide?
5. **Consequences** - What are the trade-offs?
6. **Alternatives Considered** - What else did we think about?

## Naming Convention

```
[number]-[short-title].md

Examples:
001-initial-setup.md
002-choose-database.md
003-monorepo-structure.md
004-authentication-strategy.md
```

Numbers should be sequential. Use three digits with leading zeros.

## Creating a New ADR

### Manual Creation

1. Copy `000-template.md`
2. Rename with next sequential number
3. Fill in all sections
4. Commit with the code that implements the decision

### Using AI

```
@docs/decisions/000-template.md Create an ADR for [decision topic]
```

The AI will:
- Use the next available number
- Fill in the template with your decision
- Ask clarifying questions if needed

## ADR Lifecycle

### Proposed
Decision is being considered but not yet implemented.

### Accepted
Decision has been made and is being followed.

### Deprecated
Decision is no longer recommended but existing code may still follow it.

### Superseded
Decision has been replaced by a new one. Link to the superseding ADR.

## Examples

### Example: Choosing a Database

**Good ADR:**
```markdown
# 002: Use PostgreSQL for Primary Database

**Status:** Accepted  
**Date:** 2025-01-15  
**Deciders:** [Team/Person]

## Context
We need a database for our application that supports complex queries,
has good TypeScript support, and can scale to millions of records.

## Decision
We will use PostgreSQL as our primary database.

## Consequences
**Positive:**
- Strong ACID compliance
- Excellent query performance
- Great TypeScript ORMs available
- JSON support for flexible data

**Negative:**
- More complex setup than SQLite
- Requires separate server/container
- Steeper learning curve for team

**Neutral:**
- Need to run migrations
- Requires backup strategy

## Alternatives Considered
- **MongoDB:** Rejected due to lack of schema enforcement
- **MySQL:** Rejected due to less feature-rich than PostgreSQL
- **SQLite:** Rejected due to concurrent access limitations

## References
- [PostgreSQL Docs](https://postgresql.org/docs)
- [TypeORM with PostgreSQL](https://typeorm.io)
```

### Example: Monorepo Decision

**Good ADR:**
```markdown
# 003: Use Monorepo with Turborepo

**Status:** Accepted  
**Date:** 2025-01-15  
**Deciders:** [Team/Person]

## Context
We have a frontend and backend that share TypeScript types. We need
to decide between a monorepo or separate repositories.

## Decision
We will use a monorepo structure with Turborepo for orchestration.

## Consequences
**Positive:**
- Easy to share types between frontend/backend
- Single place for all code
- Simplified CI/CD
- Easier refactoring across packages

**Negative:**
- Single repository grows larger
- Need to learn Turborepo
- Requires workspace setup

## Alternatives Considered
- **Separate repos:** Rejected due to type sharing complexity
- **Nx:** Rejected as overkill for our current needs
- **Plain npm workspaces:** Rejected due to lack of caching

## Implementation Notes
- Packages in `packages/` for shared code
- Apps in `apps/` for deployables
- Shared TypeScript config in `packages/typescript-config`

## References
- [Turborepo Docs](https://turbo.build)
- [Monorepo Best Practices](https://monorepo.tools)
```

## Tips for Writing Good ADRs

### Be Specific
❌ "We chose a database"
✅ "We chose PostgreSQL 15 with TypeORM 0.3"

### Explain the Why
Don't just state what you decided. Explain:
- What problem led to this decision?
- What constraints influenced the choice?
- What trade-offs were considered?

### Document Alternatives
Show you considered other options. For each alternative:
- What was it?
- Why wasn't it chosen?
- Under what circumstances might it be reconsidered?

### Keep It Concise
ADRs should be readable in 2-3 minutes. Focus on:
- Essential context
- Clear decision
- Key consequences

Avoid:
- Excessive background information
- Implementation details (put those in docs/)
- Tutorials or how-to guides

### Update Status
When decisions change:
- Don't delete old ADRs
- Mark as "Deprecated" or "Superseded"
- Create new ADR with updated decision
- Link between old and new

## Using ADRs with AI Agents

### Reference in Prompts

Give AI context about decisions:

```
@docs/decisions/ We decided to use PostgreSQL. Help me implement [feature]
```

```
Following our ADRs in @docs/decisions/, add [new component]
```

### Create ADRs During Development

When making a decision:

```
@docs/decisions/000-template.md Document my decision to use [technology] for [purpose]
```

AI will:
1. Ask clarifying questions about context
2. Prompt for alternatives considered
3. Help identify consequences
4. Create properly formatted ADR

### Review ADRs Before Major Changes

Before refactoring or changing architecture:

```
@docs/decisions/ Review our past decisions. I want to change [aspect].
What ADRs might be affected?
```

## ADR Maintenance

### Regular Reviews

Periodically review ADRs:
- Are decisions still valid?
- Have circumstances changed?
- Should any be deprecated?

### Link to Code

In code comments, reference relevant ADRs:

```typescript
// Database connection configured per ADR-002
export const db = new PostgreSQL({...});
```

### Update Status

When decisions change:

```markdown
# 002: Use PostgreSQL for Primary Database

**Status:** Superseded by ADR-015  
**Date:** 2025-01-15  
**Superseded:** 2025-06-20

[original content...]

## Superseded By
This decision was replaced by ADR-015 which chose Supabase 
for managed PostgreSQL with built-in auth.
```

## Benefits of ADRs

### For Solo Developers
- Remember your own reasoning months later
- Understand why you chose certain approaches
- Avoid repeating past mistakes

### For Teams
- Share context across team members
- Onboard new developers faster
- Align on technical direction
- Reduce repeated discussions

### For AI Collaboration
- AI understands project constraints
- Better suggestions that fit architecture
- Consistent with past decisions
- Less need to re-explain choices

## Questions?

- See `000-template.md` for the ADR template
- Check example ADRs in this directory
- Reference `@docs/ARCHITECTURE.md` for high-level architecture

---

**Remember:** ADRs are lightweight and valuable. Don't overthink them. A short ADR is better than no ADR. Start documenting your decisions today!

