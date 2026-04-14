# Memory Governance Operations

## Read

Read in this order:

1. `SKILL.md`
2. `operations.md`
3. `memory.md`
4. `corrections.md` when recent corrections or failures may matter
5. `learning.md` when deciding whether to write or promote
6. `.ai-memory/memory.md` if the project root contains `.ai-memory/`
7. `.ai-memory/corrections.md` if the project root contains `.ai-memory/`

## Precedence

Always apply:

1. current explicit user instruction
2. project memory
3. global memory

If project and global memory conflict:

- keep both records
- follow project memory in the current repository
- do not silently rewrite the global rule
- let `memory-evolution` decide whether the conflict needs compression or clarification

## Scope Decision

Write to global memory when the lesson:

- applies across projects
- describes a durable preference or workflow
- is not tied to one repository structure

Write to project memory when the lesson:

- only applies to the current repository
- depends on project commands, layout, modules, or team conventions
- would likely be wrong outside the current project

## Project Memory Creation

If project memory is needed and missing:

1. explain why it is needed
2. show `New-Item -ItemType Directory .ai-memory`
3. wait for confirmation
4. create `.ai-memory/`
5. create `memory.md` and `corrections.md`
6. if `.gitignore` exists in the project root, append `/.ai-memory/` when it is not already present
7. initialize project `memory.md` with the same section layout as the global `memory.md`

Never create project memory silently.

## Write Targets

- `memory.md`: stable rules, preferences, and durable strategies
- `corrections.md`: fresh failures, fresh corrections, and not-yet-stable lessons

Default to `corrections.md` first.
