# Demos And Screenshots

Superpowers are workflow tools. The most useful demos show the user's request, what the agent did differently, and the result.

Keep demos short. A good demo should answer: "When would I use this, and what pain does it remove?"

## Recommended Demo Format

Each demo should include:

- **Skill or plugin:** the Superpower being demonstrated.
- **Scenario:** the user goal or problem.
- **Before:** what usually goes wrong, takes extra effort, or requires repeated prompting.
- **After:** how the Superpower improves the workflow.
- **Artifact:** screenshot, GIF, terminal snippet, generated spec, plan excerpt, or review excerpt.
- **Result:** what changed for the user.
- **Client tested:** Claude Code, Codex, Gemini CLI, Copilot, OpenCode, or another client.

## Suggested Demo Types

| Demo Type | Best For | Notes |
| --- | --- | --- |
| Screenshot | Browser companion screens, menu choices, approval gates. | Keep text legible. Prefer one focused screen over a full desktop capture. |
| GIF or short video | Multi-step flows such as brainstorming to spec or plan execution. | Keep it under 30 seconds when possible. |
| Terminal snippet | Agent handoffs, plan execution, verification commands. | Trim unrelated logs. Show enough context to understand the flow. |
| Markdown excerpt | Generated specs, implementation plans, review findings. | Use short excerpts with links to the full file when available. |
| Before/after pair | Quality-of-life improvements. | Show the pain point and the improved path side by side. |

## Demo Ideas For Superpowers Enhanced

| Skill | Demo Idea | Artifact |
| --- | --- | --- |
| `brainstorming-enhanced` | A rough feature request becomes a short approved spec before any code changes. | Browser screenshots plus generated spec excerpt. |
| `writing-plans` | An approved spec becomes a task-by-task implementation plan with exact files and tests. | Plan excerpt and verification checklist. |
| `subagent-driven-development` | A plan is implemented with spec-review and code-quality review loops after each task. | Review snippets showing an issue caught and fixed. |
| `executing-plans` | The same written plan is executed inline when subagents are unavailable. | Terminal transcript showing task checkoffs and final verification. |

## File Organization

Use this structure as demos are added:

```text
docs/
  demos.md
  demos/
    superpowers-enhanced/
      README.md
      brainstorming-enhanced-browser.md
      brainstorming-enhanced-browser/
        approval-screen.png
        approach-selection.gif
      writing-plans-example.md
      subagent-review-loop.md
```

Store large binary assets outside the main README. Link to them from the demo page so the marketplace landing page stays concise.

The Superpowers Enhanced demo index is [docs/demos/superpowers-enhanced/README.md](demos/superpowers-enhanced/README.md).

## Screenshot Guidance

For browser companion screenshots:

- capture one decision screen at a time;
- crop browser chrome unless it helps explain the flow;
- keep option text readable;
- avoid showing private repository names, secrets, or local paths unless they are necessary;
- pair the screenshot with one or two sentences explaining the user benefit.

For terminal screenshots or snippets:

- prefer copied text over images when possible;
- remove unrelated logs;
- include the exact command only when it matters;
- show verification results when the demo claims better reliability.

## Writing Guidance

Use plain language and focus on outcomes:

- "Clarifies requirements before coding" is better than "multi-modal browser-first deliberation layer."
- "Creates a reviewable implementation plan" is better than "plan synthesis."
- "Works across agent clients with thin manifests" is better than "provider abstraction."

Avoid claiming that a workflow works in a client until it has been tested there.
