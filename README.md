# ST3V3 Marketplace

ST3V3 Marketplace is a catalog for agent workflow plugins. It publishes marketplace metadata, short plugin descriptions, and links to the repositories that contain the actual plugin source.

This repo should stay focused on the marketplace itself:

- what is listed;
- where the plugin source lives;
- which marketplace/client surfaces are supported;
- what standards a plugin should meet before being added;
- where demos, screenshots, and listing notes belong.

Detailed documentation for a plugin belongs in that plugin's own repository.

## Listed Plugins

| Plugin | Source | Marketplace Status | Summary |
| --- | --- | --- | --- |
| [Superpowers Enhanced](docs/plugins/superpowers-enhanced.md) | [ST3V3ai/superpowers-enhanced](https://github.com/ST3V3ai/superpowers-enhanced) | Listed for Claude Code and Codex-style agent marketplace surfaces. | Browser-first workflow skills for agentic software development. |

## Marketplace Surfaces

This repository currently publishes metadata for:

- Claude Code: [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json)
- Codex and agent marketplace surfaces: [.agents/plugins/marketplace.json](.agents/plugins/marketplace.json)

Each marketplace entry should be thin. It should identify the plugin, point to the source repository, and provide enough human-readable summary text for discovery. The workflow logic, install details, screenshots, and skill documentation should live in the plugin repository.

## Provider-Agnostic Catalog

The marketplace is intended to support plugins that can work across agent and LLM clients such as Claude Code, Codex, Gemini CLI, Copilot, OpenCode, and future tools.

Provider-agnostic here means:

- plugin source is not locked to one vendor unless clearly documented;
- client-specific manifests are small and easy to audit;
- support claims are limited to clients with a tested install or discovery path;
- planned or experimental clients are labeled honestly.

See [Provider-Agnostic Marketplace Design](docs/provider-agnostic.md) for the listing model.

## Plugin Listing Standard

Every plugin listed here should document:

- source repository;
- current marketplace status;
- supported and planned clients;
- a short purpose statement;
- runtime or install dependencies at a high level;
- where to find detailed plugin docs;
- where to find screenshots, demos, or examples.

The detailed skill catalog, workflow explanation, and implementation notes belong in the plugin source repository.

## Demos And Screenshots

Marketplace demos should help users decide whether to open or install a plugin. They should stay short and link to plugin-owned assets where possible.

See [Demos And Screenshots](docs/demos.md) for the recommended marketplace demo format.

## Dependencies

This marketplace repository has no package manager dependencies. There is no `package.json`, lockfile, Python project file, Cargo manifest, or Go module in this repo.

Plugin runtime dependencies are documented in each plugin repository.
