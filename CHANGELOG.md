# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2026-10-02

### Added
- Initial release: `agent-workspace` / `aws` CLI to create, list, snapshot and
  destroy git worktrees for parallel AI agents, with persistent state and a
  JSON output mode for automation
- Containerised workspace setup (`Dockerfile`, `docker-compose.yml`)
- GitHub Actions test workflow and a PyPI publish workflow triggered on release
  publication

### Changed
- The PyPI distribution is published as **`agent-workspace-py`**. The shorter
  `agent-workspace` name is registered on PyPI to an unrelated project
  (dropxhq/agent-workspace, a restricted file-operation workspace for AI
  agents with Rust bindings), so installing that name would not give you this
  worktree manager. This rename lands *before* the first publication, so there
  is no upgrade path to document: nothing was ever released under the
  colliding name. Only the distribution name changed — the `agent_workspace`
  import package, the `agent-workspace` and `aws` console scripts, and the
  GitHub repository name are all unchanged.

### Fixed
- `test_not_a_repo` no longer fails on checkouts whose temporary directory sits
  inside a Git repository, where `find_repo()` resolves to the enclosing
  repository instead of raising
- Workspace task text is sanitized for git ref safety (fixes #49)
