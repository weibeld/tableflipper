# CLAUDE.md — Tableflipper

This repository defines Tableflipper, a Claude Code skill that makes Claude follow a fixed set of conventions for the requirements, architecture, and development work in a software project.

## Current state

The repository contains the following files:

- `SKILL.md`: the definition of the skill (see "Current development process" below)
- `.claude-plugin/plugin.json`: the manifest that makes this repository a Claude Code plugin. It defines the name and the version of the plugin.
- `README.md`: description for users (installation and usage)
- `notes.md`: development notes (considerations, background, and choices concerning the development of the skill)

Furthermore, the directory `tmp/` contains temporary files that are to be dissolved into the other content of this repository and deleted afterwards.

### Distribution

- Tableflipper is distributed as a Claude Code plugin that contains a single skill. The plugin is listed in the marketplace `weibeld`, which is defined in the repository weibeld/claude-marketplace.
- A new version is released by changing `version` in `.claude-plugin/plugin.json` and pushing. The marketplace repository does not need to be changed for a release.
- For local development, `~/.claude/skills/tableflipper` is a symlink to this repository. With it, `/tableflipper` invokes the working copy and `/tableflipper:tableflipper` invokes the installed version of the plugin.

### Current development process

- The skill is developed empirically: it starts from a minimal skeleton, is applied in real projects, and an instruction is added only when the application shows that it is needed.
- The conventions are derived from authoritative sources and written into `SKILL.md`
- The current focus is on requirements, following the book Software Requirements (Wiegers & Beatty), starting with the user requirements (use cases).

The skill is currently applied in the following projects:

- weibeld/lithuanian-bakery

### TODO

The following items are to be resolved soon:

- arc42 with C4 example: <https://github.com/bitsmuggler/arc42-c4-software-architecture-documentation-example>
- Research about agentic software engineering
  - Possible characterisation of human-agent split of responsibilities: agent as analyst (what and how), human as strategist (why)
  - See the iSAQB AGENTA module on <https://public.isaqb.org/#_agenta> (curriculum only), seems to be the field in which Tableflipper operates
  - SDLC with agents
    - <https://www.workingsoftware.dev/the-new-software-development-lifecycle-sdlc-from-vibe-coding-to-agentic-engineering/>
    - <https://www.kaggle.com/whitepaper-the-new-SDLC-with-vibe-coding>
    - <https://www.fellow.gmbh/>
