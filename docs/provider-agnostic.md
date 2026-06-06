# Provider-Agnostic Design

ST3V3 Marketplace should make useful agent workflows portable across providers and clients. The workflow should not depend on one model, one vendor, or one terminal app.

Provider-agnostic does not mean every client behaves identically today. It means the core workflow is written in a way that can travel, and any client-specific behavior is small, visible, and justified.

## Core Principle

Keep the Superpower provider-neutral.

A Superpower should be mostly plain instructions, Markdown docs, scripts, tests, and small helper tools. Claude Code, Codex, Gemini CLI, Copilot, OpenCode, and other clients can then expose the same workflow through their own plugin, skill, extension, or instruction systems.

## Layers

| Layer | Responsibility | Example |
| --- | --- | --- |
| Marketplace | Lists plugins, explains purpose, links to source, and keeps metadata discoverable. | This repository. |
| Plugin | Packages skills, helper scripts, docs, tests, and assets. | `superpowers-enhanced`. |
| Skill | Teaches the agent when and how to perform one workflow. | `writing-plans`. |
| Client manifest | Makes the plugin installable or discoverable in a specific agent client. | `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`. |
| Client hook | Optional runtime glue for permissions, commands, lifecycle hooks, or UI integration. | Browser companion launch helpers. |

## Thin Manifest Rule

Client-specific files should stay as small as possible. They can include:

- names, versions, descriptions, authors, and source URLs;
- install and authentication policy where needed;
- pointers to shared skill directories;
- display metadata for marketplace UIs;
- client-specific defaults or permission notes.

They should not duplicate the workflow itself. If `brainstorming-enhanced` changes, that change should live in the shared skill, not in five separate provider manifests.

## What Belongs In A Shared Skill

Shared skills should contain the parts that make the workflow valuable:

- when the agent should use the skill;
- what steps the agent should follow;
- what artifacts the agent should produce;
- when the agent should ask the user for input;
- how the agent should verify work;
- what helper scripts or local tools are required.

This keeps the useful behavior inspectable by humans and portable across clients.

## When To Add Client-Specific Support

Add a client-specific surface when at least one of these is true:

- the client needs a manifest to install or discover the plugin;
- the client needs permission or hook configuration for a helper tool;
- the client supports a useful UI, command, or lifecycle hook;
- there is a tested install path and a user-facing reason to support it.

Do not add runtime hooks just because a client supports them. Each hook should remove friction or improve reliability.

## Client Notes

| Client | Current Marketplace Role | Notes |
| --- | --- | --- |
| Claude Code | Marketplace metadata and plugin manifest support. | Listed through `.claude-plugin/marketplace.json`; plugin source has `.claude-plugin/plugin.json`. |
| Codex | Marketplace metadata and reusable skills for agent workflows. | Listed through `.agents/plugins/marketplace.json`; plugin source has `.codex-plugin/plugin.json`. |
| Gemini CLI | Planned target after install/runtime path is tested. | Browser companion may need client-specific background-process guidance. |
| Copilot | Planned documentation target if skill packaging becomes practical. | Support should wait for a clear extension surface. |
| OpenCode | Planned plugin or skill exposure when runtime hooks are useful. | Explicit support should be added only after the install path is tested. |

## Documentation Standard

Every plugin listed in this marketplace should answer:

- What problem does it solve?
- Who should use it?
- Which skills or tools does it include?
- What does each skill do in plain language?
- Which clients are supported today?
- Which clients are planned but untested?
- What does the user need installed?
- What does a successful demo look like?
- Where should screenshots, GIFs, or generated artifacts be linked?

This keeps provider-agnostic from becoming vague. It should mean portable, tested where claimed, and honest about client differences.
