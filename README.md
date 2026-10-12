# Herdr Agent Orchestration Skill

A lightweight companion skill for deciding when Herdr multi-agent coordination is worth its setup and integration costs, then coordinating only the independent work needed.

## Contents

- `SKILL.md` — orchestration decision criteria, role boundaries, agent lifecycle, result integration, and safety notes.

## Requirements

- Herdr installed and running.
- The agent must be inside a Herdr-managed pane with `HERDR_ENV=1`.
- The official Herdr `herdr` skill should also be available for current CLI syntax and detailed safety rules.

This skill does not replace the official Herdr CLI reference. It supplements it with a conservative orchestration policy: keep small or tightly coupled tasks with one agent; parallelize substantial independent slices only when expected time savings exceed coordination costs.

## Install

Install this skill with the Skills CLI:

```sh
npx skills add DeclanJeon/herdr-agent-orchestration-skill --skill herdr-agent-orchestration-skill -g
```

Or copy this directory into a supported agent's skill directory.

## License and attribution

The orchestration guidance in this package is original local guidance, provided under the MIT License; see `LICENSE`.

The official Herdr CLI instructions remain maintained by the Herdr project and are not copied into this package. Herdr itself is licensed under Apache-2.0. Any future redistributed material copied from the official repository must retain its applicable notices and license terms.
