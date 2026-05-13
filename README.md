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

For more information on Claude Code features, refer to the official documentation.

---
*Template last updated: 2026-05-13*