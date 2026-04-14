# Scope And Precedence

## Core Order

Always decide in this order:

1. current explicit user instruction
2. project memory
3. global memory

## Global Memory Examples

- "Keep final answers concise by default."
- "For risky shell operations, verify the target path first."
- "In debugging work, confirm reproduction evidence before guessing."

## Project Memory Examples

- "This repository uses `pnpm test:unit` as the default test command."
- "This service requires code generation before compile."
- "Migration files in this directory must not be edited by hand."

## Conflict Handling

When the same topic differs across scopes:

- follow project memory in the current project
- do not auto-delete the global rule
- let `memory-evolution` decide whether to clarify, compress, or split the rule
