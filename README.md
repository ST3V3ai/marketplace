# ST3V3 Marketplace

ST3V3 Marketplace lists workflow plugins for coding agents and LLM clients. The focus is quality of life: fewer repeated prompts, clearer decisions, better planning, stronger review loops, and results that are easier for a human to inspect.

This repository is intentionally small. It does not contain the full plugin source. It publishes marketplace metadata, human-readable documentation, and links to the plugin repositories that provide the actual skills and helper tools.

## What Is A Superpower?

A Superpower is a reusable workflow an agent can follow.

Instead of relying on every user to write the perfect prompt, a Superpower gives the agent a named operating procedure. It can tell the agent when to ask clarifying questions, when to write a spec, how to create an implementation plan, how to execute that plan, when to run tests, and when to stop for review.

Good Superpowers are:

- **Human-readable:** stored as plain instructions, Markdown, scripts, and small helper tools.
- **Goal-focused:** designed around common user outcomes, not provider branding.
- **Reviewable:** they produce artifacts such as specs, plans, screenshots, test output, or review notes.
- **Portable:** they can be exposed through different clients such as Claude Code, Codex, Gemini CLI, Copilot, OpenCode, and future tools.

The point is not to make the agent more complicated. The point is to make useful behavior repeatable.

## Why This Marketplace Exists

Modern agents are powerful, but the user often still has to manage the workflow by hand:

- reminding the agent to clarify requirements before coding;
- asking for a plan after the agent already started editing;
- checking whether tests were actually run;
- steering long tasks back on track;
- translating the same workflow between different LLM clients.

This marketplace is meant to package those habits into installable, documented plugins. The long-term direction is a provider-agnostic catalog of Superpowers that help users achieve goals faster, with less friction and better results.

## Plugin Catalog

| Plugin | Status | What It Does | Useful When |
| --- | --- | --- | --- |
| [Superpowers Enhanced](docs/plugins/superpowers-enhanced.md) | Listed | Browser-first brainstorming, implementation planning, and reviewed execution workflows for agentic software development. | A user has a rough idea, feature request, bug fix, or implementation plan and wants a more reliable path from intent to verified result. |

More plugins can be added as separate marketplace entries when they have a clear purpose, install path, dependency story, and at least one useful demo.

## Current Plugin: Superpowers Enhanced

Superpowers Enhanced provides four workflow skills:

| Skill | Plain-English Use | Result |
| --- | --- | --- |
| `brainstorming-enhanced` | Clarify a new feature or behavior change before implementation. | Questions, tradeoffs, an approved design, and a written spec. |
| `writing-plans` | Turn an approved spec or clear requirements into implementation steps. | A task-by-task plan with files, tests, commands, and verification notes. |
| `subagent-driven-development` | Execute an implementation plan with fresh subagents and review gates when the client supports subagents. | Implemented tasks plus spec-compliance and code-quality review loops. |
| `executing-plans` | Execute a written plan inline when subagents are unavailable or inappropriate. | Step-by-step implementation with verification and completion reporting. |

Read the full plugin page at [docs/plugins/superpowers-enhanced.md](docs/plugins/superpowers-enhanced.md).

## Provider-Agnostic Direction

The marketplace should support many agent clients without rewriting the workflow for every provider.

The working model is:

- keep the core workflow in shared skill files and docs;
- keep provider-specific manifests thin;
- add runtime hooks only when they remove real friction;
- document supported, planned, and untested clients honestly.

See [Provider-Agnostic Design](docs/provider-agnostic.md) for the current model.

## Demos And Screenshots

Superpowers make more sense when people can see them working. This marketplace should collect small demos for each plugin and skill:

- screenshots of browser companion screens;
- short GIFs or videos of approval flows;
- terminal snippets showing handoffs and verification;
- before/after examples showing reduced rework;
- links to generated specs, plans, or review excerpts.

Use [Demos And Screenshots](docs/demos.md) as the contribution format.

## Marketplace Files

This repository currently publishes metadata for:

- Claude Code: [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json)
- Codex and agent marketplace surfaces: [.agents/plugins/marketplace.json](.agents/plugins/marketplace.json)

The current listed plugin source is:

```text
https://github.com/ST3V3ai/superpowers-enhanced.git
```

## Dependencies

This marketplace repository has no package manager dependencies. There is no `package.json`, lockfile, Python project file, Cargo manifest, or Go module in this repo.

The listed `superpowers-enhanced` plugin has its own runtime needs:

- Node.js 18+ for the local browser companion used by `brainstorming-enhanced`.
- `ws@8.19.0` in the plugin's `tests/brainstorm-server/package.json` and lockfile for WebSocket tests.

Browsing this marketplace or reading its manifests does not require installing Node packages from this repository.
