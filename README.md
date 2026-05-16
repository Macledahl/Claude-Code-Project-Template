# Claude Code Project Template

This is a starter template for projects using Claude Code. It includes configuration files and guidelines to help you get started quickly.

## Project Structure

- `.claude/` - Claude Code specific settings
  - `settings.local.json` - Local overrides for Claude Code behavior (not committed)
- `.gitignore` - Specifies files and directories to ignore in version control
- `CLAUDE.md` - Project-specific instructions for Claude Code

## Configuring Claude Code

### settings.local.json

The `.claude/settings.local.json` file allows you to customize Claude Code's behavior for this project without committing sensitive or machine-specific settings to the repository. This is commonly used to configure alternative models (like those from OpenRouter) instead of the default Claude model.

**Common configurations:**
- Permission allowlists (to reduce prompts)
- Environment variables
- Hook configurations
- Custom keybindings
- Model configuration (for using custom models like OpenRouter)

**Example:**
```json
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "your-openrouter-api-key-here",
    "ANTHROPIC_BASE_URL": "https://openrouter.ai/api",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "nvidia/nemotron-3-super-120b-a12b:free",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "nvidia/nemotron-3-super-120b-a12b:free",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "nvidia/nemotron-3-super-120b-a12b:free"
  }
}
```

> **Note:** This file is intentionally excluded from version control via `.gitignore` to prevent committing local configurations or secrets. Replace `"your-openrouter-api-key-here"` with your actual OpenRouter API key when configuring locally.

## Version Control (.gitignore)

The following files/directories are intentionally excluded from Git:

| File/Pattern | Reason |
|--------------|--------|
| `secret.json` | May contain API keys, database credentials, or other sensitive information |
| `config.json` | Local configuration that varies between developers or environments |
| `.env` | Environment variables (often containing secrets) |
| `.claude/settings.local.json` | Local Claude Code settings overrides (not committed to repository) |
| `*.log` | Log files that may contain sensitive information or debugging data |
| `*.db` | Database files that may contain sensitive data |
| `*.sqlite` | SQLite database files that may contain sensitive data |
| `logs/` | Log directories that may contain sensitive information or debugging data |
| `__pycache__/` | Python bytecode cache directories |
| `*.py[cod]` | Compiled Python files (.pyc, .pyo, .pyd) |
| *$py.class | Compiled Python artifacts (Jython/PyPy) |
| `*.so` | Shared object files (compiled C extensions) |
| `.Python` | Python-related build artifacts |
| `env/`, `venv/`, `ENV/` | Python virtual environment directories |
| `*.egg-info/` | Python package metadata directories |
| `dist/` | Distribution directories (from setup.py) |
| `build/` | Build directories |

These exclusions help prevent accidental commitment of sensitive data, build artifacts, and environment-specific files while still allowing the template to be safely shared.

## Getting Started

### Installation
To ensure compatibility with free models from providers like OpenRouter.ai, install Claude Code version 2.0.64:

**Windows PowerShell:**
```powershell
& ([scriptblock]::Create((irm https://claude.ai/install.ps1))) 2.0.64
```

**Linux/macOS:**
```bash
curl -fsSL https://claude.ai/install.sh | bash -s 2.0.64
```

This specific version activates free model functionality without requiring a Claude subscription. After installation, Claude Code will automatically update to the latest version upon your next PC restart, while maintaining compatibility with free models as long as you continue using them.

1. Clone this template to start a new project
2. Copy `.claude/settings.local.json.example` to `.claude/settings.local.json` and customize as needed
3. Review and update `CLAUDE.md` with your project-specific goals, plans, and instructions
4. Begin development with Claude Code!

## Using Claude Code

With this template, Claude Code will:
- Follow the guidelines in `CLAUDE.md`
- Respect the permission settings in `.claude/settings.local.json`
- Ignore locally defined files per `.gitignore`

## Make it yours

`/setupdotclaude` gets you most of the way. To take it the rest of the way:

- `rules/code-quality.md`. Naming conventions to match your team's style. Comment guidelines, code marker format, import order.
- `rules/frontend.md`. Pick your design principle. Highlight the component framework your project actually uses.
- `rules/security.md`. Add paths specific to your project's sensitive areas, beyond the defaults.
- `CLAUDE.md`. Architectural decisions, domain knowledge, workflow quirks unique to your project.
- `CLAUDE.local.md`. Personal preferences (gitignored). Rename the `.example` file to start.
- `hooks/format-on-save.sh`. If detection missed your formatter, uncomment the right section manually.

The defaults are foundations. Your edits on top are what make Claude effective for *your* project.

## Skills (slash commands)

Skills are invoked with `/name` in your Claude Code session. All except `/test-writer` are manual only.

| Command | Arguments | Description |
|---------|-----------|-------------|
| `/setupdotclaude` | `[focus area]` | Bootstrap and customize dotclaude in any project. If `.claude/` is missing, the skill copies the bundled template in (rules, hooks, settings, agents, skills, `CLAUDE.md`). Then it scans your codebase to detect language, framework, package manager, test runner, linter, and architecture, and customizes every config file to match. Confirms every change before applying. |
| `/debug-fix` | `[issue #, error, or description] [--fast]` | Find and fix a bug. Default is the careful path: reproduce, investigate, write a regression test, fix, commit. Add `--fast` for emergency production mode (`hotfix/` branch from production, minimal change, critical tests only, ships a `[HOTFIX]` PR). Warns if a fast fix turns out to be complex. |
| `/ship` | `[commit message or PR title]` | Full shipping workflow. Scans changes, stages files (skipping secrets, locks, and build output), drafts a commit message in the repo's style, pushes, and creates a PR. Every step requires confirmation. |
| `/pr-review` | `[PR #, "staged", file path, or omit]` | Delegates review to specialist agents: `@code-reviewer`, `@security-reviewer` (if security-related code changed), `@performance-reviewer` (if perf-sensitive), `@doc-reviewer` (if docs changed). Synthesizes a unified report with severity-ranked findings. |
| `/tdd` | `[feature description or function signature]` | Strict red-green-refactor TDD loop. One failing test, then minimum code to pass, then refactor. Commits after each green-plus-refactor cycle. Works simple to complex: degenerate cases, happy path, variations, edge cases, errors. |
| `/explain` | `[file, function, or concept]` | Explains code with a one-sentence summary, a mental model analogy, an ASCII diagram, key non-obvious details, and a modification guide. Focuses on the why and the landmines, not the obvious. |
| `/refactor` | `[file, function, or pattern]` | Safe refactoring with tests as a safety net. Writes tests first if none exist, plans transformations, makes small testable steps, and verifies after each one. Never mixes refactoring with behavior changes. |
| `/test-writer` | *(auto-triggers)* | Writes comprehensive tests for new or changed code. Discovers changes via `git diff`, maps all code paths (happy, edge, error, concurrency), writes one test per scenario with Arrange-Act-Assert. The only skill that can auto-trigger. Claude may invoke it after you add new features. |
| `/context-budget` | `[--api]` | Estimates per-turn token cost of this project's `.claude/` and `CLAUDE.md`. Reports always-loaded vs path-scoped vs invoked-only, ranks top contributors, flags entries over budget. Default heuristic is `chars/4`. Add `--api` for Anthropic-tokenizer exact counts (requires `$ANTHROPIC_API_KEY`). |
| `/caveman` | `[lite\|full\|ultra\|wenyan]` | Compress every reply. Levels stick until session end. |
| `/caveman-commit` | | Conventional Commit messages, ≤50 char subject. Why over what. |
| `/caveman-review` | | One-line PR comments: `L42: 🔴 bug: user null. Add guard.` |
| `/caveman-stats` | | Real session token usage + lifetime savings + USD. Tweetable line via `--share`. |
| `/caveman-compress` | `<file>` | Rewrite memory file (e.g. `CLAUDE.md`) into caveman-speak. Cuts ~46% input tokens every session. Code/URLs/paths byte-preserved. |
| `caveman-shrink` | | MCP middleware. Wraps any MCP server, compresses tool descriptions. [npm](https://www.npmjs.com/package/caveman-shrink). |
| `cavecrew-*` | | Caveman subagents (investigator/builder/reviewer). ~60% fewer tokens than vanilla, main context lasts longer. |

## Agents (subagents)

Agents are specialized Claude instances that run in their own isolated context. Auto-delegated based on the task, or you can invoke any of them explicitly with `@agent-name` in your prompt.

| Agent | When it's used | What it does |
|-------|----------------|--------------|
| `@code-reviewer` | Auto-delegated by `/pr-review`, or invoke directly | Reviews code for correctness and maintainability. Catches off-by-one errors, null dereferences, logic bugs, race conditions, error handling gaps, excessive complexity, and missing tests. Focuses on real issues with evidence, not style nitpicks. |
| `@security-reviewer` | Auto-delegated by `/pr-review` when security-related code changes | Senior security engineer doing static analysis. Covers injection (SQL, command, XSS, template, path traversal), auth and authorization flaws, data exposure, cryptography issues, dependency vulnerabilities, and input validation gaps. Reports severity, attack vector, and concrete fix for each finding. |
| `@performance-reviewer` | Auto-delegated by `/pr-review` when performance-sensitive code changes | Finds real bottlenecks, not theoretical micro-optimizations. Checks for N+1 queries, missing indexes, unbounded queries, memory leaks, repeated computation, blocking I/O on hot paths, unnecessary re-renders, bundle size issues, and lock contention. Only flags issues with measurable impact. |
| `@frontend-designer` | Auto-delegated when building UI, or invoke directly | Creates distinctive, production-grade frontend UI that avoids generic AI aesthetics. Enforces design tokens, picks an appropriate design principle (glassmorphism, brutalism, editorial, and so on), ensures accessibility (WCAG), and prevents common anti-patterns like purple gradients, centered-everything layouts, and overused fonts. |
| `@doc-reviewer` | Auto-delegated by `/pr-review` when documentation changes | Reviews docs for accuracy by cross-referencing actual source code. Verifies function signatures, code examples, config options, and file paths. Identifies stale references, missing prerequisites, undocumented error cases, and unclear instructions. |

### Using agents directly

You can invoke any agent in your prompt:

```
@security-reviewer Review the auth middleware changes in src/middleware/auth.ts
```

```
@frontend-designer Build a dashboard page for the analytics module
```

```
@code-reviewer Check my staged changes before I commit
```

Agents run in isolated context. They don't see your conversation history, but they have access to the full codebase through their allowed tools.

## Customization guide

| Want to... | Do this |
|---|---|
| Add project-specific rules | Create `.claude/rules/your-rule.md` |
| Scope rules to file paths | Add `paths:` frontmatter to rule files |
| Add a team workflow | Create `.claude/skills/your-skill/SKILL.md` |
| Add a specialist reviewer | Create `.claude/agents/your-agent.md` |
| Enforce behavior deterministically | Add a hook in `settings.json` |
| Override settings locally | Copy `settings.local.json.example` to `.claude/settings.local.json` |
| Personal CLAUDE.md overrides | Rename `CLAUDE.local.md.example` to `CLAUDE.local.md` |

### Example: project-specific rule

```yaml
---
paths:
  - "src/billing/**"
---

# Billing Module

- All monetary values use cents (integers), never floating point dollars
- Tax calculations must use the tax-engine service, never inline math
- Every billing mutation must be idempotent with a unique request ID
```

---
*Template last updated: 2026-05-16*