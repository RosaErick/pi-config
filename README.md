# Pi Agent Configuration

Version-controlled global configuration for [Pi](https://pi.dev), with private data and generated files excluded from Git.

## Setup

1. Install Pi and clone this repository to a location of your choice.
2. Review `settings.json`: adjust local paths, select your preferred models, and review package sources before running Pi.
3. Back up any existing `~/.pi/agent` directory, including credentials and sessions, before replacing it with a symlink to your clone. Alternatively, copy only the settings you need into your existing configuration.
4. Configure authentication locally and install any external skills referenced by your settings.

Never delete a directory that is still targeted by a symlink for active credentials or sessions.

## Repository scope

The `.gitignore` allowlist supports:

- `settings.json` and optional `keybindings.json`.
- Global instructions and system prompt files.
- Custom resources in `extensions/`, `skills/`, `prompts/`, and `themes/`.
- Root dependency manifests and lockfiles.

Optional files and empty directories may not be present. Keep project-specific `.pi/` configuration in its own project repository and manage external skills separately.

## Privacy

New root files are ignored unless explicitly allowed. Credentials, sessions, model configuration and caches, trust decisions, downloaded packages, and dependencies are excluded. Keep custom provider configuration in an untracked `models.json`.

**Git ignore rules are not secret detection.** Never put credentials or private information in tracked files. Use environment variables or local credential storage, and review changes before committing or publishing.

## Maintenance

Review package sources before installing them; third-party extensions can execute code. Pin package versions or Git refs when reproducibility matters.

From the repository directory:

```bash
git status --short
git diff
# Review new files before staging them.
git add <reviewed-files>
git diff --cached
git commit -m "Update Pi configuration"
```

Use `/reload` to refresh supported resources, or restart Pi after configuration changes. Commits and pushes are manual.

## License

[MIT](LICENSE). Third-party packages retain their own licenses.
