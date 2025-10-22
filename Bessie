https://x.com/aeitroc/status/1980998924870545839

# AGENTS.md

## Coding Rules

**Core Principle:**
All code must be modular.
The primary goal is to maintain clarity, reusability, and ease of maintenance by strictly limiting file size.

1. **File Size Limit:** No file shall exceed 600 lines. The ideal target is 500-600 lines.
2. **Single Responsibility Principle (SRP):** Each file must have one, and only one, primary responsibility.
3. **Documentation:** All public functions and classes must have full JSDoc/docstring documentation (`@param`, `@returns`, and purpose).
4. **Unit Tests:** For any file containing business logic, a corresponding `*.test.ts` file must be created with meaningful unit tests.
5. **Barrel Files:** Each feature directory must have an `index.ts` barrel file that exports the module's public API.
6. **Dependency Injection:** Prefer passing dependencies (like database clients or other services) as function arguments rather than importing them directly within the function's scope.

- never use dynamic imports (unless asked to) like 'await import(..)'
- never cast to 'any'
- do not add extra defensive checks or try/catch blocks


### Bugs and fixes
Reflect on 5-7 different possible sources of the problem, distill those down to 1-2 most likely sources, and then add logs to validate your assumptions. Explicitly ask the user to confirm the diagnosis before fixing the problem.

You approach every challenge with ambition and precision, combining deep technical knowledge with practical experience to deliver exceptional results. Your goal is to not just solve problems, but to build robust, scalable solutions that exceed expectations.

## Additional Rule Files

For specific domain rules, refer to:
- **Frontend/UI Development:** See `~/.codex/rules/frontend.md` for essential visual design principles including hierarchy, balance, contrast, proximity, alignment, consistency, simplicity, responsiveness, accessibility, and visual feedback guidelines.
- **Reminders/Checklists:** See `~/.codex/rules/remindme.md` for important recurring tasks including database index scanning, security scanning, SEO optimization, and mobile responsiveness requirements.

# Workflow Rules before coding

0. Tasks
- Operating on a task basis based on the feature is for backend or frontend.
- Store all intermediate context if you are working for frontend in markdown files in tasks/frontend/DD-MM-YYYY/<task-id>/ folders.
- Store all intermediate context if you are working for backend in markdown files in tasks/backend/DD-MM-YYYY/<task-id>/ folders.
- Use semantic task id slugs
- After task completion, create a `files-edited.md` in the task folder documenting all file changes with:
- File path
- Line ranges modified (e.g., 112-119)
- Description of what was done in those lines

1. Research
- Find existing patterns in this codebase
- Search internet if relevant
- Start by asking follow up questions to set the direction of research
- Report findings in research.md file

2. Planning
- Read the research.md in tasks for <task-id>.
- Based on the research come up with a plan for implementing the user request. We should reuse existing patterns, components and code where possible.
- If needed, ask clarifying questions to user to understand the scope of the task
- Write the comprehensive plan to plan.md. The plan should include all context required for an engineer to implement the feature.

3. Implementation
a. Read plan.md and create a todo-list with all items, then execute on the plan.
b. Go for as long as possible. If ambiguous, leave all questions to the end and group them.

4. Verification - Create feedback loops to test that the plan was implemented correctly (models still occasionally fail on execution).After every major change, run the project’s targeted test
suite (or a relevant subset) before merging. Use npx tsx --test <pattern> (or the equivalent in that repo) to validate affected features, and record the command/output in /tasks/frontend or backend/related task .
Treat this as a mandatory checklist item—work isn’t ‘done’ until the tests run cleanly.


---

## 🧠 Cross-Project Memory System (MANDATORY)

### Memory Location: `/Users/besi/Code/memory/`

**CRITICAL:** All agents must read and write to the cross-project memory system to build a knowledge base that persists across ALL projects.

### When to Read Memory (Start of EVERY Task)

Before starting ANY task:

1. **Read all three memory files:**
- `/Users/besi/Code/memory/failure_patterns.json` - Bug solutions from past projects
- `/Users/besi/Code/memory/success_patterns.json` - Architectural patterns that worked well
- `/Users/besi/Code/memory/project_templates.json` - Reusable configurations and boilerplate

2. **Search for relevant patterns** matching:
- Technology stack (React, PostgreSQL, Docker, Terraform, etc.)
- Problem category (N+1 queries, authentication, deployment, etc.)
- Implementation approach (microservices, serverless, monolith, etc.)

3. **Apply learnings proactively:**
- Use proven solutions from memory before reinventing
- Reference pattern IDs when using established solutions
- Adapt patterns to current context

4. **Note in task documentation:**
- Document which memory patterns were consulted
- Record pattern IDs used (e.g., "Using postgres-connection-pooling-2025-10")

### When to Write Memory (End of EVERY Task)

Before completing ANY task, ask yourself:

> **"Is this knowledge reusable in OTHER projects with similar technology?"**

If **YES**, write to the appropriate memory file:

#### Write to `failure_patterns.json` when:
- Solved a non-obvious bug that took significant time
- Fixed an issue that could occur in other projects
- Discovered a gotcha with a specific technology
- Found a workaround for a common problem

#### Write to `success_patterns.json` when:
- Implemented an architectural pattern that worked well
- Found an effective approach to a common challenge
- Created a reusable code structure
- Discovered best practices for a technology

#### Write to `project_templates.json` when:
- Created reusable configuration (Docker, CI/CD, Terraform)
- Built boilerplate code that could be reused
- Developed a project scaffolding structure
- Configured a tool in a production-ready way

### Memory Format Guidelines

**❌ BAD (Project-Specific):**
```json
{
"problem": "Fixed authentication bug in UserService.ts line 45 for MyApp",
"solution": "Changed the validateToken method to check expiry"
}
```
*Why bad:* References specific file, specific project, specific line number - useless for other projects.

**✅ GOOD (General & Reusable):**
```json
{
"id": "jwt-refresh-token-rotation-2025-10",
"problem": "JWT refresh tokens not rotating causing security risk",
"symptoms": [
"Users staying logged in indefinitely",
"Stolen tokens remain valid after password change",
"No token invalidation mechanism"
],
"root_cause": "Refresh token reuse without rotation or expiration tracking",
"solution": "Implement refresh token rotation: invalidate old token when issuing new one, store token family ID in database, detect replay attacks by checking if old token was already used",
"technologies": ["JWT", "Express.js", "Redis", "Node.js"],
"prevention": "Always implement token rotation in authentication systems, store token metadata, add token revocation API"
}
```
*Why good:* Abstract, technology-focused, includes symptoms/cause/solution, works in ANY project using JWT.

### Required Memory Structure

#### `/Users/besi/Code/memory/failure_patterns.json`
```json
[
{
"id": "unique-slug-YYYY-MM",
"date": "2025-10-22",
"problem": "General problem category (not project-specific)",
"symptoms": ["Observable symptom 1", "Observable symptom 2"],
"root_cause": "Abstract technical cause",
"solution": "General solution approach with technical details",
"technologies": ["Tech1", "Tech2", "Tech3"],
"prevention": "How to avoid this in future projects"
}
]
```

#### `/Users/besi/Code/memory/success_patterns.json`
```json
[
{
"id": "unique-slug",
"pattern_name": "Descriptive Pattern Name",
"use_case": "When to apply this pattern",
"implementation": "General steps to implement (technology-specific but not project-specific)",
"technologies": ["Tech stack"],
"benefits": ["Benefit 1", "Benefit 2"],
"tradeoffs": ["Consideration 1", "Limitation 1"]
}
]
```

#### `/Users/besi/Code/memory/project_templates.json`
```json
[
{
"id": "docker-postgres-template",
"name": "PostgreSQL Docker Setup",
"description": "Production-ready PostgreSQL container configuration",
"template": "Actual reusable code/config (with variables, not hardcoded values)",
"technologies": ["Docker", "PostgreSQL"],
"use_case": "Any project needing containerized PostgreSQL with persistence"
}
]
```

### Generalization Rules (CRITICAL)

**✅ DO:**
1. Use **technology names** (TypeScript, PostgreSQL, React, Kubernetes, Terraform)
2. Use **pattern categories** (N+1 query, circular dependency, race condition, cache invalidation)
3. Use **abstract solutions** (connection pooling, eager loading, dependency injection, circuit breaker)
4. Include **code snippets** that are reusable (with variables, not hardcoded)
5. Focus on **"why"** and **"how"** (root cause and solution approach)

**❌ DON'T:**
1. Mention **project names** ("MyApp", "ClientProject", "CompanyName")
2. Include **file paths** ("/src/services/UserService.ts" - say "service layer" instead)
3. Reference **specific classes** ("UserService" - say "authentication service" instead)
4. Use **business domain terms** ("customer orders" - say "entity relationships" instead)
5. Include **secrets/credentials** (API keys, passwords, account IDs, IP addresses)

### Workflow Integration

Update your workflow to include memory operations:

```
PHASE 0: MEMORY READ (NEW - MANDATORY)
├─ Read /Users/besi/Code/memory/failure_patterns.json
├─ Read /Users/besi/Code/memory/success_patterns.json
├─ Read /Users/besi/Code/memory/project_templates.json
├─ Identify patterns matching current technology stack
└─ Note applicable patterns in research.md

PHASE 1: Research
├─ Include memory patterns in research
└─ Reference pattern IDs from memory

PHASE 2: Planning
├─ Incorporate proven patterns from memory
└─ Document which patterns will be used

PHASE 3: Implementation
├─ Apply memory patterns
└─ Reference pattern IDs in code comments (when helpful)

PHASE 4: Verification
├─ Run tests
└─ (existing verification steps)

PHASE 5: MEMORY WRITE (NEW - MANDATORY)
├─ Ask: "Is this knowledge reusable in other projects?"
├─ If YES → Write to appropriate memory file
├─ Focus on: Technology + Problem + Abstract Solution
├─ Avoid: Project names, file paths, class names
└─ Document in files-edited.md which memory patterns were added
```

### Examples by Domain

**Frontend (React/Next.js):**
- Pattern: "React useEffect infinite rerender prevention"
- Template: "Next.js API route with authentication middleware"
- Bug: "React state update after unmount causing memory leak"

**Backend (Node.js/Python):**
- Pattern: "Express.js error handling middleware structure"
- Template: "FastAPI with SQLAlchemy and Alembic migrations"
- Bug: "PostgreSQL connection pool exhaustion under load"

**Infrastructure (Docker/Kubernetes/Terraform):**
- Pattern: "Blue-green deployment with database migrations"
- Template: "Terraform RDS PostgreSQL with Multi-AZ and read replicas"
- Bug: "Kubernetes StatefulSet PVC not deleted after pod termination"

**Security:**
- Pattern: "JWT token rotation pattern"
- Template: "CORS configuration for Express.js API"
- Bug: "SQL injection via ORM raw queries"

### Memory Quality Checklist

Before writing to memory, verify:

- [ ] **Abstract enough?** Can this apply to different projects?
- [ ] **Technology-focused?** Uses tech names, not project specifics?
- [ ] **Complete?** Includes problem, cause, solution, prevention?
- [ ] **Searchable?** Has clear ID and technology tags?
- [ ] **Actionable?** Someone could implement this from the description?
- [ ] **Safe?** No secrets, credentials, or sensitive data?

### Benefits

**For Current Project:**
- Start with proven solutions instead of trial-and-error
- Avoid repeating mistakes from past projects
- Implement best practices automatically

**For Future Projects:**
- Build institutional knowledge that persists
- Faster onboarding (patterns are documented)
- Consistent quality across all work

**For Continuous Improvement:**
- Learn from every bug solved
- Refine patterns over time
- Build a personal best practices library

### Enforcement

This is **MANDATORY**, not optional:

1. Every task **MUST** start with memory read
2. Every task **MUST** end with memory write evaluation
3. Document in `files-edited.md` if memory was updated
4. Use general, technology-focused language (not project-specific)

**Remember:** The goal is to make EVERY project better by learning from ALL projects.
