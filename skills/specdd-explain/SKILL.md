---
name: specdd-explain
description: Use when GitHub Copilot needs to explain a SpecDD `.sdd` file, feature contract, or effective spec chain in succinct human language, covering purpose, scope, behavior, boundaries, tasks, scenarios, and uncertainty without editing or expanding the contract.
license: Apache-2.0
---

# SpecDD Explain

Use this skill to explain SpecDD contracts to a human. Keep the explanation
succinct and clear while including enough depth to understand the feature,
module, workflow, or file governed by the spec.

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

1. Identify the requested spec, target path, feature, behavior, or changed file.
2. Read the active bootstrap chain, then the applicable spec or effective spec chain.
3. Read explicit `References` only when they materially affect the explanation.
4. Explain what the contract means in plain language, not line by line.
5. Separate direct spec requirements from reasonable inference, missing context, and underspecified behavior.

## Explanation Rules

- Explain the purpose, scope, ownership, allowed changes, important behavior, boundaries, dependencies, scenarios, examples, tasks, and completion criteria that matter to the request.
- Preserve `Must`, `Must not`, `Forbids`, `Depends on`, public contracts, and write authority instead of softening them.
- Keep framework mechanics brief unless the user asks how SpecDD resolution works.
- Do not invent behavior, guarantees, workflows, or user stories beyond the active specs.
- Do not edit files unless the user explicitly asks for a spec or implementation change.
- If the user asks about one spec only, avoid expanding into sibling specs unless the active spec references them or they are needed to avoid a misleading explanation.

## Output

Prefer short sections such as:

- What this is
- Scope
- Behavior
- Boundaries
- Open or unclear points

Use prose or compact bullets. Quote sparingly. When something is inferred rather
than specified, label it as an inference.
