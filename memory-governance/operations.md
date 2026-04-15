# Memory Governance Operations

## Read

Read in this order:

1. `SKILL.md`
2. `operations.md`
3. `memory.md`
4. `corrections.md`
5. `learning.md` when deciding whether to write or promote
6. verify whether the project root contains `.ai-memory/`
7. if `.ai-memory/` exists and both project files exist, read `.ai-memory/memory.md`
8. if `.ai-memory/` exists and both project files exist, read `.ai-memory/corrections.md`
9. if `.ai-memory/` exists but either project file is missing, treat project memory as partial and ask before repairing it

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

If `.ai-memory/` already exists but one or both project files are missing:

1. explain that project memory is only partially initialized
2. list the missing file or files
3. ask for confirmation before creating the missing file or files
4. repair only the missing file or files
5. if `.gitignore` exists in the project root, append `/.ai-memory/` when it is not already present

## Write Targets

- `memory.md`: stable rules, preferences, and durable strategies
- `corrections.md`: fresh failures, fresh corrections, and not-yet-stable lessons

Default to `corrections.md` first.
