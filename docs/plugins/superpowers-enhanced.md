# Superpowers Enhanced

Superpowers Enhanced is the first plugin listed in ST3V3 Marketplace. It packages workflow skills that help an agent move from a rough request to a reviewed implementation with fewer missed assumptions and fewer repeated prompts.

Repository:

```text
https://github.com/ST3V3ai/superpowers-enhanced.git
```

Current local plugin metadata reviewed for this page: `0.1.16`.

## What Problem It Solves

Many agent sessions fail in predictable ways:

- the agent starts coding before the goal is clear;
- the user has to keep asking for a plan;
- implementation work drifts from the original request;
- long tasks lose context;
- tests and review happen inconsistently;
- the workflow has to be re-explained in every client.

Superpowers Enhanced packages the desired behavior into named skills. The user can ask for the skill, or the client can trigger it when the request matches.

## What It Adds

Superpowers Enhanced gives agents a structured development workflow:

1. Explore the user's intent before implementation.
2. Turn the agreed direction into a written spec.
3. Convert the spec into an implementation plan.
4. Execute the plan with review checkpoints.
5. Fall back to inline execution when subagents are not available.

The plugin is intentionally workflow-focused. It does not replace the model, editor, repository, package manager, or agent client. It gives those tools better operating instructions.

## Skill Catalog

| Skill | Use It When | What It Does | What It Produces |
| --- | --- | --- | --- |
| `brainstorming-enhanced` | The user asks for a new feature, behavior change, app, component, or other creative work. | Explores context, asks clarifying questions, compares approaches, and waits for design approval before implementation. | Clarifying answers, approach tradeoffs, an approved design, and a written spec. |
| `writing-plans` | There is an approved spec or clear requirements for a multi-step task. | Turns the spec into concrete implementation tasks that another agent or engineer can follow without hidden context. | A task-by-task implementation plan with exact files, test commands, code snippets, verification steps, and commit points. |
| `subagent-driven-development` | There is a plan with independent tasks and the client supports subagents. | Dispatches fresh subagents for implementation, then runs spec-compliance and code-quality review loops after each task. | Implemented tasks, review feedback, fixes, final verification, and integration options. |
| `executing-plans` | There is a written plan, but subagents are unavailable or not appropriate. | Executes the plan inline, task by task, with plan review and verification. | Completed plan steps, verification output, and a concise completion report. |

## How The Skills Fit Together

```text
idea or request
  -> brainstorming-enhanced
  -> approved spec
  -> writing-plans
  -> implementation plan
  -> subagent-driven-development or executing-plans
  -> verified result
```

This separation is the main quality-of-life improvement. It keeps the agent from jumping straight into code before the problem is understood, and it gives users concrete artifacts they can review.

## Browser Companion

`brainstorming-enhanced` includes a local browser companion for questions, choices, design review screens, and completion handoffs. The companion is meant to reduce repeated terminal prompts and make visual or structured decisions easier.

The browser companion can be used for:

- opening requirements questions;
- option cards for approach selection;
- UI mockups and diagrams;
- design approval or revision gates;
- completion handoffs back to the terminal.

The companion needs Node.js 18+ at runtime. The marketplace itself does not run the companion; it only lists the plugin.

## Dependencies

This marketplace repository has no install-time dependencies.

The plugin source currently uses:

| Area | Dependency | Why |
| --- | --- | --- |
| Browser companion runtime | Node.js 18+ | Runs the local HTTP/WebSocket companion and helper scripts. |
| Browser companion tests | `ws@8.19.0` | WebSocket test dependency in `tests/brainstorm-server/package.json` and lockfile. |

Normal marketplace browsing and manifest discovery do not install those dependencies from this repository.

## Client Support

| Client | Status | Notes |
| --- | --- | --- |
| Claude Code | Listed | Marketplace entry exists in this repo; plugin source includes `.claude-plugin/plugin.json`. |
| Codex | Listed | Marketplace entry exists in this repo; plugin source includes `.codex-plugin/plugin.json`. |
| Gemini CLI | Planned/untested | Needs a tested install path and background-process guidance for the browser companion. |
| Copilot | Planned/untested | Needs a practical skill or extension packaging path. |
| OpenCode | Planned/untested | Support should be added when runtime hooks or plugin packaging provide real value. |

## Demo Ideas

Good demos for this plugin should show the workflow, not just the final code:

- A rough feature request becoming a short approved spec.
- A browser companion question or approach-selection screen.
- A generated implementation plan with checked-off tasks.
- A subagent review loop catching a spec mismatch.
- An inline execution flow for clients without subagents.
- A before/after example where the Superpower workflow avoids rework.

Use the format in [Demos And Screenshots](../demos.md) when adding examples.

## Marketplace Status

The marketplace currently exposes Superpowers Enhanced through Claude Code and Codex-style marketplace metadata:

- `../../.claude-plugin/marketplace.json`
- `../../.agents/plugins/marketplace.json`

Additional clients should be added as thin manifest layers when there is a tested install path.
