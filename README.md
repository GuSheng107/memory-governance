---
name: memory-governance
description: Manage global and project memory for IDE coding work. Use before writing code, modifying code, fixing bugs, debugging, analyzing exceptions or logs, investigating root causes, refactoring, designing implementations, writing tests, or reviewing code. Read global memory first, then inspect the project root `.ai-memory/`; when project memory exists it overrides global memory for that project. If project memory is needed but missing, ask the user before creating it and never create `.ai-memory/` silently.
---

# Memory Governance

## Overview

Use this skill before any coding, debugging, analysis, test, or refactor task. Resolve which memory files apply, which scope wins, and whether project memory may be created.

Prefer reading and scope selection first. Do not start by writing memory.

## Read Order

Load only what the task needs, in this order:

1. `operations.md`
2. `memory.md`
3. `corrections.md` when recent fixes, failures, or follow-up corrections may matter
4. `learning.md` when deciding whether something should be written or promoted
5. Check whether the project root contains `.ai-memory/`
6. If present, read `.ai-memory/memory.md`
7. If present, read `.ai-memory/corrections.md`

Keep this precedence:

1. Current explicit user instruction
2. Project memory
3. Global memory

More detail lives in `references/scope-and-precedence.md`.

## Mandatory Proactive Triggers

Use this skill first for:

- writing new code
- modifying code
- fixing bugs
- debugging
- explaining exceptions or stack traces
- analyzing logs
- investigating root causes
- refactoring or architecture changes
- performance optimization
- implementation design
- writing tests
- code review or quality review

## Workflow

1. Confirm the task is in a proactive trigger case.
2. Read global memory and decide whether project-specific context is needed.
3. Check whether `.ai-memory/` exists in the project root.
4. If it exists, read project memory and apply the precedence order.
5. If it does not exist but the task clearly needs project memory, ask for confirmation before creating it.
6. Distill the active constraints into task guidance; do not dump raw memory files back to the user.
7. When the task ends, hand off failures, corrections, reusable wins, memory bloat, and used-skill review to `memory-evolution`.

## Scope Rules

Use global memory for:

- cross-project preferences
- durable working rules
- reusable debugging or implementation patterns
- lessons that are not tied to one repository

Use project memory for:

- repository structure
- module boundaries
- build, test, and run commands
- team conventions
- pitfalls that only apply in this project

Do not write these into stable memory:

- one-off command output
- temporary instructions for only this turn
- unverified guesses
- secrets, tokens, cookies, or personal data

## Project Memory Creation

If `.ai-memory/` is missing and project memory is clearly needed:

1. Show the command `New-Item -ItemType Directory .ai-memory`
2. Wait for user confirmation
3. Create `.ai-memory/memory.md`
4. Create `.ai-memory/corrections.md`
5. If `.gitignore` exists in the project root, add `/.ai-memory/` to it
6. Create project `memory.md` with the same section layout as the global `memory.md`, but keep the content project-scoped

Do not create the directory or files without confirmation.

Bootstrap details live in `references/project-memory-bootstrap.md`.

## Write Boundaries

Follow these rules:

- put fresh but unstable lessons in `corrections.md` first
- promote only stable, reusable rules to `memory.md`
- do not duplicate the same lesson across files
- if project memory conflicts with global memory, preserve both records but follow project memory in the current project

Let `memory-evolution` decide promotion, compression, and deeper review.

## Output Style

Tell the user only the task-relevant outcome, for example:

- project memory is active and overrides global memory here
- the project has no `.ai-memory/`; confirmation is required before creating it
- the rule belongs to global memory and should not be stored as project memory

Do not paste full memory files unless the user explicitly asks to inspect them.
