# AI Collaboration Playbook

[简体中文](README.md) · [English](README.en.md)

A reference standard for a single AI agent working on a project: read it before starting, follow it while coding, self-check against it when closing out. Stable conventions only — no live project state.

> **Scope**: This repo contains the playbook only and is safe to make public. Project handbooks live in `projects/`, are gitignored, and ship as separate repositories.

## How it works

1. **The repo is a behavioral baseline.** It holds reusable conventions and templates only — no live project state.
2. **Two rule layers.** Root `AGENTS.md` is thin global policy; thick project handbooks are maintained in each project's own repo, not here. Nearest wins.
3. **Spec first.** No code before `spec.md` → `plan.md` → `tasks.md` is approved by a human.
4. **Minimal diff.** Touch only what the task requires. No speculative refactors.
5. **Verifiable done.** Every task has a self-check; unverified is not done.
6. **Context is finite.** One task per session, precise reads, terse output, protect prompt cache. See `skills/09`.
7. **Merging has a gate.** AI output is untrusted input; a human decides what merges. See `skills/10`.

## Layout

| Path | Purpose |
|---|---|
| `AGENTS.md` | Global rules, read by every agent at session start |
| `specs/_template/` | Five templates, including `current-solution-statement.md` |
| `skills/01`–`skills/10` | On-demand workflows: clarify → spec → tasks → implement → retrospective, plus sync / verification / secrets / context efficiency / AI commit review and merge |
| `llms.txt` | Agent-facing site entry index (optional, for web publishing) |

`projects/` holds local project handbooks. It is gitignored and shipped as separate repositories — never committed here.

## Workflow

```
Need → clarify criteria → agree structure
     → set mechanisms (config / version / migration) → small steps with self-checks
     → verify and record (change list + decisions)
```

An agent reads `AGENTS.md` plus the project handbook (kept in that project's own repo), follows `skills/`, self-checks with `skills/07`, and passes the merge gate in `skills/10`. No project state lives here.

## Nine conventions distilled from real projects

1. Missing a single "current solution statement" is the biggest pain → `specs/_template/current-solution-statement.md`
2. Function-level diff beats file-level diff → `skills/06`
3. One source of truth per domain → `skills/08`
4. Layered secrets with fail-closed defaults → `skills/08`
5. AI rules were scattered; this repo unifies them → `AGENTS.md`
6. Human does the last step: agents never start services or touch hardware → `skills/07`
7. Static checks before runtime checks → `skills/07`
8. Context hygiene is code hygiene → `skills/09`
9. Deployment conventions repeat across projects → planned `skills/11`

## Repository

- **URL**: `https://github.com/chuliuLiu/ai-collab-playbook`
- **Default branch**: `main`
- **Visibility**: Public (playbook only, no project-sensitive data)
- **CI**: every push checks kebab-case filenames, resolvable relative links, and that `projects/` stays untracked

Usage: clone → read `AGENTS.md` before starting → follow `skills/` for execution and self-checks. This repo holds no project state; state belongs in each project's own repo.

## Conventions used in this repo

- Lowercase kebab-case for all file and directory names; ASCII paths only.
- Markdown headings in the language of the file; identifiers (API names, env vars, CLI flags, protocol fields, error codes) stay verbatim.
- Relative links only, so clones work.
- Conventional Commits: `<type>(<scope>): <what>`, one commit per agent per stage.

## Before publishing

- [ ] `git ls-files projects/` returns nothing (CI also enforces this).
- [ ] Confirm no keys, tokens, customer data or private chat logs are present.
- [ ] Language links in both READMEs still resolve; Chinese version wins on conflict.
- [ ] LICENSE type decided (none added yet).

Details and full conventions live in the Chinese README — that is the maintained source of truth. This English page is a concise front door; when the two diverge, the Chinese version wins.

## Status

- [x] Global rules and layout
- [x] Templates, including current-solution statement
- [x] Nine workflows
- [x] Conventions distilled from seven projects (handbooks live in separate repos)
- [x] AI commit review and merge conventions (`skills/10`)
- [x] Scope narrowed to single-agent reference standard; multi-agent handoff material removed to a separate project
- [ ] Deployment and ops conventions (`skills/11`)
- [ ] First end-to-end dry run
