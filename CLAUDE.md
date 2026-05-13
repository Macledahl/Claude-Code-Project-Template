# Claude Code Project Template

## Edit Tool Rules
- If an Edit fails with "string not found", ALWAYS re-read the file before retrying
- Never attempt the same edit twice without re-reading
- After 2 consecutive Edit failures on the same file, use the Read tool to display the current contents, then construct a new edit based on what you actually see
- Do not "give up and say it builds" — verify the edit actually applied

## Project Overview
This template provides a starting point for projects using Claude Code. It includes essential configuration files and guidelines to streamline development workflows.

## Goals
- Establish consistent Claude Code configuration across projects
- Provide clear instructions for AI-assisted development
- Maintain a clean repository by excluding local/config files
- Enable quick project setup for new team members

## Development Guidelines

### Working with Claude Code
1. Always respect the Edit Tool Rules when making changes
2. Refer to this CLAUDE.md for project-specific instructions
3. Local overrides can be configured in `.claude/settings.local.json`
4. Follow standard coding practices and conventions

### Making Changes
- Use the Read tool to examine files before editing
- Construct precise edits based on actual file contents
- Verify that edits were applied correctly
- Avoid making assumptions about file contents

## Configuration

### Local Settings
Project-specific Claude Code settings should be placed in:
`.claude/settings.local.json`

This file is excluded from version control (see .gitignore) and can contain:
- Permission allowlists to reduce prompts
- Environment variables
- Custom hooks
- Keybindings
- Model preferences

### Version Control
The following files are intentionally excluded from Git:
- `secret.json` - Contains sensitive credentials
- `config.json` - Local configuration variations
- `.env` - Environment variables (often with secrets)
- `.claude/settings.local.json` - Local Claude Code settings overrides (not committed to repository)

This prevents accidental commitment of sensitive information while allowing the template to be shared safely.

## Getting Started
1. Copy this template to start a new project
2. Copy `.claude/settings.local.json.example` to `.claude/settings.local.json` and customize as needed
3. Update this CLAUDE.md with project-specific goals and instructions
4. Begin development with Claude Code!

## Plugin Initialization
The caveman plugin auto-activates for Claude Code when installed via the official one‑line installer. No manual plugin commands or reloads are needed.

To install caveman for Claude Code (and other agents), run the appropriate installer:
- macOS/Linux/WSL/Git Bash: `curl -fsSL https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.sh | bash`
- Windows PowerShell 5.1+: `irm https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.ps1 | iex`

After installation, caveman is active by default in full mode. Switch compression levels with `/caveman lite|full|ultra` or revert to normal speech with "stop caveman" or "normal mode".

(Optional) See the caveman README for per‑agent details and advanced configuration.

## Project Tracking
Use Claude Code's task management features to track progress:
- Create tasks for features, bugs, and improvements
- Update task status as work progresses
- Reference tasks in commit messages when appropriate

## Best Practices
- Keep commits focused and meaningful
- Write clear commit messages explaining the "why"
- Test changes thoroughly before committing
- Document important decisions in this file or project documentation

## Maintenance
- Regularly review and update this CLAUDE.md as the project evolves
- Ensure .gitignore remains appropriate for project needs
- Check that settings.local.json contains only local overrides

---
*Template initialized: 2026-05-13*
*Last updated: 2026-05-13*