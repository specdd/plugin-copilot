---
name: specdd-review
description: Use when GitHub Copilot needs to review a diff, branch, pull request, changed files, or proposed changes against active SpecDD contracts, focusing on spec violations, behavioral regressions, missing checks, and concrete findings.
license: Apache-2.0
---

# SpecDD Review

Use this skill for code-review style review under SpecDD. Do not edit files
unless the user explicitly asks for changes.

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

1. Compare the diff against applicable `Must`, `Must not`, `Forbids`, `Scenario`, `Tasks`, and `Done when` entries.
2. Check whether verification matches the behavioral risk.
3. Report concrete findings, questions, or residual risk.

## Review Output

Lead with findings, ordered by severity. For each finding, include:

- File and line when available.
- The violated or risky SpecDD contract.
- The concrete behavior or regression risk.
- The smallest likely fix.

Then include open questions or assumptions. Keep summaries secondary and brief.
If there are no findings, say so clearly and mention any residual test or spec
coverage gap.

Do not invent requirements beyond the active specs. If behavior is underspecified,
call that out as an uncertainty rather than a violation.
