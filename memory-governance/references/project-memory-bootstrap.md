# Project Memory Bootstrap

## When Bootstrap Is Allowed

Initialize project memory only when all of these are true:

- the task clearly needs project-specific memory
- the project root has no `.ai-memory/`
- the user explicitly confirms creation

## Required Command

Show this command first:

```powershell
New-Item -ItemType Directory .ai-memory
```

Run it only after confirmation.

## Required Files

Create at minimum:

- `.ai-memory/memory.md`
- `.ai-memory/corrections.md`

If the project root already contains `.gitignore`, add this line when it is not already present:

```gitignore
/.ai-memory/
```

Do not create `.gitignore` just for this step unless the user explicitly asks.

Suggested initial content:

```markdown
# Project Memory

## Stable Rules

- No stable project rules recorded yet.

## Notes

- Mirror the section layout of the global memory file, but keep all entries project-scoped.
```

Use `memory.md` as the project-scoped counterpart of the global memory file: same section layout, different scope.

```markdown
# Project Corrections

## Active Corrections

- No active project correction entries yet.
```
