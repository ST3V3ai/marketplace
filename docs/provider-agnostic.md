# Provider-Agnostic Marketplace Design

ST3V3 Marketplace should make agent workflow plugins discoverable across providers and clients. The marketplace should not depend on one model, one vendor, or one terminal app.

This document describes the marketplace layer only. Plugin-owned workflow details belong in the plugin repository.

## Catalog Principle

Keep marketplace entries thin and portable.

The marketplace should answer:

- what plugin is listed;
- where the source repository lives;
- which client surfaces can discover it today;
- which clients are planned or untested;
- where to find detailed plugin documentation.

The marketplace should not duplicate full skill instructions, helper scripts, implementation plans, or long workflow explanations.

## Layers

| Layer | Responsibility | Owned By |
| --- | --- | --- |
| Marketplace | Lists plugins, publishes marketplace manifests, links to source, and keeps discovery metadata readable. | This repository. |
| Plugin repository | Packages skills, helper scripts, docs, tests, assets, and plugin-specific demos. | The plugin source repo. |
| Client manifest | Makes a plugin installable or discoverable in a specific client. | Usually the marketplace repo for catalog entries, and the plugin repo for installable plugin metadata. |
| Client hook | Optional runtime glue for permissions, commands, lifecycle hooks, or UI integration. | The plugin source repo. |

## Thin Manifest Rule

Client-specific marketplace files should stay small. They can include:

- marketplace name and display description;
- plugin name;
- source URL;
- short plugin description;
- category;
- install or authentication policy where the marketplace format requires it;
- version only when the marketplace format expects it.

They should not copy the plugin's detailed docs. If a plugin changes its workflow or skill list, the plugin repository should be updated first. The marketplace entry should change only when discovery metadata changes.

## Client Notes

| Client | Current Marketplace Role | Notes |
| --- | --- | --- |
| Claude Code | Marketplace metadata support. | Listed through `.claude-plugin/marketplace.json`. |
| Codex | Agent marketplace metadata support. | Listed through `.agents/plugins/marketplace.json`. |
| Gemini CLI | Planned/untested. | Add only after a tested install or discovery path exists. |
| Copilot | Planned/untested. | Add only when plugin packaging or documentation is practical. |
| OpenCode | Planned/untested. | Add only when runtime hooks or plugin packaging provide value. |

## Listing Checklist

Before adding a new marketplace plugin, confirm:

- the source repository is public or otherwise accessible to the intended users;
- the plugin has a clear purpose statement;
- the install/discovery path has been tested for every supported client claim;
- dependencies are documented in the plugin repo;
- screenshots or demos have an obvious home;
- provider-specific behavior is documented instead of hidden in prompts.

This keeps provider-agnostic from becoming vague. It should mean portable where claimed, tested where listed, and honest about client differences.
