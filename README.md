# Pi Agent Configuration

Global settings and custom resources for [Pi](https://pi.dev).

## Setup

1. Install Pi and clone this repository to a location of your choice.
2. Review `settings.json`: adjust local paths, select your preferred models, and review package sources before running Pi.
3. Back up any existing `~/.pi/agent` directory, including credentials and sessions, before replacing it with a symlink to your clone. Alternatively, copy only the settings you need into your existing configuration.
4. Configure authentication locally and install any external skills referenced by your settings.

Never delete a directory that is still targeted by a symlink for active credentials or sessions.

## Configuration

- **Model:** `gpt-6-astra` via `openai-codex`.
- **Interface:** dark theme, regular terminal UI, hardware cursor enabled.
- **Skills:** external skill directory configured in `settings.json`.

### Packages

| Package | Version | Purpose |
| --- | --- | --- |
| `pi-subagents` | `0.68.0` | Agent delegation and workflows |
| `pi-web-access` | `0.29.0` | Web search and content fetching |
| `pi-mcp-adapter` | `2.34.0` | MCP server integration |
| `pi-lens` | `4.2.0` | Code navigation and diagnostics |
| `@companion-ai/feynman` | `0.3.47` | Scientific research tools |
| `pi-memory` | `0.4.2` | Persistent memory |
| [`mitsupi`](https://github.com/mitsuhiko/agent-stuff) | Git `122e299` | Selected workflow extensions |

### Enabled Mitsupi extensions

- **btw:** `/btw` side chat for tangential questions.
- **notify:** terminal notifications when the agent finishes.
- **todos:** `/todos` task browser and `todo` tool.
- **control:** `/control-sessions` and tools for messaging live sessions.
- **files:** `/files` browser with Git status and session references.
- **goal:** `/goal` objectives with automatic continuation.
- **review:** `/review` and `/end-review` for code reviews.

Other Mitsupi extensions, skills, prompts, and themes are disabled. Notifications require a compatible terminal; Quick Look in `/files` is macOS-only.

## License

[MIT](LICENSE). Third-party packages retain their own licenses.
