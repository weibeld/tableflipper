# Tableflipper

Tableflipper is a Claude Code skill that makes Claude follow a fixed set of conventions for the requirements, architecture, and development work in a software project: which documents exist, where they are stored, and which formats and notation they use.

> Note: this project is still WIP and does not cover all of these areas (requirements, architecture, and development) yet.

Tableflipper is distributed as a Claude Code plugin that contains a single skill.

## Usage

Installation:

```
claude plugin install tableflipper --marketplace weibeld/claude-marketplace
```

Update:

```
claude plugin update tableflipper@weibeld
```

Invocation:

```
/tableflipper:tableflipper
```

> Note: if no other local command with the same name exists, the short form `/tableflipper` can also be used.
