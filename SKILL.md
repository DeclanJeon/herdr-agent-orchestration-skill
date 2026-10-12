---
name: herdr-agent-orchestration-skill
description: "Use when a task explicitly involves Herdr and may benefit from coordinating multiple coding agents or running independent work in parallel."
license: Apache-2.0
---

# Herdr Agent Orchestration

Use Herdr only when `HERDR_ENV=1` is set. This skill supplements the official `herdr` skill; load that skill for CLI syntax, pane IDs, startup states, and safety rules.

## Decide whether to parallelize

Before creating panes or agents, compare the likely parallel-time savings with startup, coordination, merge, and verification costs.

Use one agent for small, sequential tasks, tasks with shared mutable files, or work whose decomposition is unclear. Add agents only when at least two substantial slices can progress independently and each has a clear output or file boundary. For background commands without reasoning or decisions, use a pane command instead of an agent.

## Coordinate a useful team

1. Inspect the current workspace, pane, available agent kinds, and working directory. Keep work in the current workspace and tab unless the user requests another layout.
2. Define the goal, acceptance criteria, role assignments, file ownership, and integration points before launching agents. Do not assign overlapping edits to multiple agents.
3. Create only the needed sibling panes, preserve the caller's working directory, and use `--no-focus` for background work.
4. Start each requested agent kind in an available shell pane. Send a bounded assignment with relevant context, deliverable, constraints, and acceptance criteria; avoid vague prompts like “help with this task.”
5. Track each worker by its live agent name or the returned pane ID. Inspect state and read its actual output. A submitted prompt, active status, or claimed completion alone is not evidence of a finished deliverable.
6. Integrate in the coordinating pane. Inspect changes and artifacts, resolve interface conflicts, run relevant verification, and report incomplete work and evidence gaps. Do not stop at the coordination step: the requested outcome must be delivered end to end.

If an agent is blocked on an approval or question, inspect the UI and ask the user before responding. If a prompt stalls or times out, inspect current state and output before retrying; the original request may already have been delivered. Stop spawning agents when remaining coordination costs exceed parallel benefit.

## Example role split

For a substantial change with independent areas: assign one agent to inspect the existing API contract and propose constraints (read-only), another to implement an isolated UI slice, and keep integration, cross-slice verification, and final delivery with the coordinating agent. Choose different roles and boundaries to match the actual task; do not force this example onto small work.
