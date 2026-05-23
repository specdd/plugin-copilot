---
name: specdd-docs
description: Use when GitHub Copilot needs to write or update user, developer, release, onboarding, or operational documentation from SpecDD specs while preserving source contract boundaries and avoiding unsupported promises.
license: Apache-2.0
---

# SpecDD Docs

Use this skill to write or update documentation from specs.

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

1. Identify the audience and documentation file authority before editing.
2. Write docs that explain the specified behavior without expanding the contract.
3. Keep docs aligned with changed specs, tasks, examples, and tests.

## Documentation Rules

- Treat specs as source-adjacent contracts and docs as explanatory material.
- Do not add promises, APIs, guarantees, or workflows not supported by specs or implementation.
- Preserve important `Must not` and operational constraints when user-facing behavior depends on them.
- If docs reveal a spec gap, report the gap instead of silently inventing a rule.
- Keep prose concise and concrete.

Report the specs used, docs changed, and any behavior that remains underspecified.
