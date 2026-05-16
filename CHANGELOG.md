# Changelog
All notable changes to this project will be documented in this file.

## [1.1.0] - 2026-05-16
### Added
- caveman plugin installed, adding:
  - .claude/agents/ with predefined agent types (code-reviewer, doc-reviewer, frontend-designer, performance-reviewer, security-reviewer)
  - .claude/hooks/ with security and workflow hooks (block-dangerous-commands, scan-secrets, session-start, format-on-save, etc.)
  - .claude/rules/ with coding standards (code-quality, security, testing, error-handling, database, frontend)
  - .claude/skills/ with skill definitions for caveman modes (lite/full/ultra), cavecrew subagents, commit message generation, file compression, help, review, stats, and utility skills (context-budget, debug-fix, explain, pr-review, refactor, setupdotclaude, ship, tdd, test-writer)
  - Updated .gitignore to exclude logs and databases

## [1.0.0] - 2026-05-13
### Added
- settings.local.json.example addet for customize Claude Code's behavior. Template for other LLM API from openrouter.ai
- .gitignore filled withe filenames and extantions to excluded from Git commits. To secure that tokens and passwords is not shared online.