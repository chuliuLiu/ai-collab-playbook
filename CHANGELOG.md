# Changelog

All notable changes to this playbook are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow semantic versioning.

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

[1.1.0]: https://github.com/REPLACE_ME/ai-collab-playbook/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/REPLACE_ME/ai-collab-playbook/releases/tag/v1.0.0
