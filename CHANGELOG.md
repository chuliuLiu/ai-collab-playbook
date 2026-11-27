# Changelog

All notable changes to this playbook are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow semantic versioning.

## [1.3.0] - 2026-11-27

### Added
- `skills/11-deployment-ops.md`: deployment and ops conventions — backup before change, migration baseline alignment, systemd / Nginx / subpath rules, human-only execution gate, log anchors, rollback path.
- `AGENTS.md` rule 9: deployment and ops pointer.
- Both READMEs: "Adopt in your project" / "在自己的项目中落地" — forward guidance for applying the playbook to a project, replacing progress reporting.
- CI: link check now covers `llms.txt`; new check ensures every skill is listed in the index.

### Changed
- Removed progress reporting from the playbook body: `## 状态` / `## Status`, the version roadmap in `skills/05`, and the roadmap-sync rule in `CONTRIBUTING.md`. Release history is maintained only in this changelog.
- Deployment conventions are now recorded in `skills/11` instead of being marked as planned in the READMEs.

## [1.2.0] - 2026-11-27

### Added
- `skills/10-review-and-merge.md`: AI commit review gate — four-step review order (scope → intent → tests → behavior), AI-specific red flags, merge decision table, conflict priority, accountability record.
- `AGENTS.md` rule 8: merge gate (human decides, AI self-report is not evidence).

### Changed
- Repo published to `chuliuLiu/ai-collab-playbook` (Public, `main`); READMEs replaced decision-stage sections with current repository state.
- Fixed stale statements: `llms.txt` no longer says Private; HANDOFF reflects shipped state; removed `docs/` reference that does not exist.
- **Scope narrowed**: this repo is now the reference standard for a single agent advancing a project. Multi-agent handoff material (`handoff/`, agent-role workflow, tool-specific examples) removed to a separate research project. `skills/05` renamed to `05-retrospective.md`; CI handoff check removed.

## [1.1.0] - 2026-11-27

### Added
- `skills/09-context-token-efficiency.md`: context and token efficiency rules (DSH session review + Anthropic official cost model).
- `AGENTS.md` rule 7: context discipline (one task per session, precise reads, terse output, protect cache).
- `README.en.md`: English front door with language switch links.
- `.github/workflows/validate-links.yml`: relative link and naming checks.
- `CHANGELOG.md`, `CONTRIBUTING.md`, `llms.txt`.

### Changed
- Renamed all files and directories to lowercase kebab-case ASCII (GitHub-safe URLs).
- `README.md` now links to English version.
- **Scope changed**: `projects/` project handbooks are now gitignored and ship as separate repositories; this repo contains the playbook only and is safe to publish. CI enforces that `projects/` stays untracked.

## [1.0.0] - 2026-11-27

### Added
- Initial layout: `AGENTS.md`, `README.md`, `specs/_template/`, `handoff/`, `projects/`.
- Nine conventions distilled from seven real projects, including `current-solution-statement.md`.
- Seven project handbooks: blockly-linkdog, dsh-linkdog, dsh-linkdog-pet, linkdog-emotion-lab, linkdogdm, xiaozhi-oneclick, xiaozhi-server.
- Five workflow skills (clarify → spec → tasks → implement → handoff) plus three cross-project skills (sync / verification / secrets).

[1.3.0]: https://github.com/chuliuLiu/ai-collab-playbook/compare/ff016de...HEAD
[1.2.0]: https://github.com/chuliuLiu/ai-collab-playbook/compare/6a06318...ff016de
[1.1.0]: https://github.com/chuliuLiu/ai-collab-playbook/commit/6a0631880cb8ad825f866632f1e4663f5d72645c
[1.0.0]: https://github.com/chuliuLiu/ai-collab-playbook/commit/6a0631880cb8ad825f866632f1e4663f5d72645c
