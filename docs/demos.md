# Demos And Screenshots

Marketplace demos should help users decide whether to open, install, or inspect a listed plugin. They should be short, discovery-focused, and linked to plugin-owned examples whenever possible.

Detailed demos for a specific plugin belong in that plugin's repository.

## Recommended Marketplace Demo Format

Each marketplace demo should include:

- **Plugin:** the listed plugin being demonstrated.
- **Scenario:** the user goal or problem.
- **Client tested:** the agent client used for the demo.
- **Artifact:** screenshot, GIF, terminal snippet, generated doc excerpt, or link to the plugin repo demo.
- **Result:** what changed for the user.
- **Source link:** the plugin repository or documentation page with the full example.

## Suggested Demo Types

| Demo Type | Best For | Notes |
| --- | --- | --- |
| Screenshot | Marketplace discovery screens or a single plugin entry point. | Keep it focused on discovery, not detailed workflow internals. |
| GIF or short video | Showing install/discovery flow across a client. | Keep it under 30 seconds when possible. |
| Terminal snippet | Showing a plugin install or marketplace lookup. | Trim unrelated logs. |
| Plugin repo link | Detailed skill demos, screenshots, generated specs, plans, or review examples. | Prefer this for plugin-specific workflow behavior. |

## File Organization

Use this structure for marketplace-level demos:

```text
docs/
  demos.md
  demos/
    marketplace/
      claude-code-listing.md
      codex-listing.md
```

Plugin-specific screenshots, GIFs, and generated artifacts should live in the plugin repository and be linked from the marketplace docs.

## Writing Guidance

Use plain language and focus on discovery:

- "Listed for Claude Code and Codex" is better than a long explanation of the plugin internals.
- "Full workflow demo lives in the plugin repo" is better than duplicating the same demo in two repositories.
- "Open the source repository for skill details" is better than copying skill docs into the marketplace.
