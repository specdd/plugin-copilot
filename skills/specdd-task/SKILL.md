---
name: specdd-task
description: Use when GitHub Copilot needs to find, add, interpret, organize, or update `Tasks` entries in SpecDD `.sdd` files, including task status changes after implementation and verification are complete.
license: Apache-2.0
---

# SpecDD Task

Use this skill for `Tasks` sections in `.sdd` files.

## Bootstrap Resolution

Before doing anything else in the target project, read bootstrap files in this exact order:

1. `.specdd/bootstrap.md`
2. `.specdd/bootstrap.project.md`, if it exists
3. `.specdd/bootstrap.local.md`, if it exists

Apply them in that order. Later files may narrow or specialize earlier rules, but must not silently weaken project contracts, inherited constraints, or write authority.

## Spec Chain Resolution

Before planning, editing, reviewing, testing, or reporting on a target:

1. Identify the target path, task, behavior, or changed files.
2. Resolve the effective spec chain using the active bootstrap rules.
3. Include same-directory basename specs when applicable.
4. Walk ancestor specs from the selected content root to the target.
5. Read explicit `References` only when they affect the requested work.
6. Identify the nearest local spec that grants write authority before any edit.

Do not infer authority from similar filenames, nearby files, symbols, module names, or conventions unless the active bootstrap or a governing spec explicitly defines that mapping.

## Workflow

1. Read the applicable spec chain for the requested scope, including inherited constraints.
2. Focus task handling on task-bearing specs that apply to the requested scope.
3. Treat parent tasks as planning context unless the user targets them directly.
4. Update task status only in the currently targeted spec unless instructed otherwise.

## Task Handling

- Add tasks only when they are local, actionable, and consistent with inherited constraints.
- Keep task text concise and implementation-oriented.
- Mark `[x]` only after the work and relevant checks are complete.
- Use `[!]` for blocked work and `[?]` for unresolved design decisions.
- Use `[-]` only when the task is intentionally skipped and the reason is clear.
- Do not use tasks to override `Must`, `Must not`, `Forbids`, or write authority.
- Do not complete unrelated tasks while handling a requested task.

When reporting, list task ids or exact task text, status changes, verification,
and any task that remains blocked or uncertain.
