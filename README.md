<p align="center">
  <img src="./banner.png" alt="Crumb" width="100%">
</p>

## Crumb — Breadcrumbs for AI agents

Like Hansel leaving pebbles to find the way home, Crumb leaves `AGENTS.md` files across your project tree so AI agents never get lost.

Works with **any agent**: Kiro, Claude Code, Codex, OpenCode.

## How it works

The agent follows a hierarchy of `AGENTS.md` files:

- `AGENTS.md` at the root → project-wide rules and area index
- `AGENTS.md` in subfolders → area-specific local rules
- Before modifying an area → follows the crumbs (reads AGENTS.md files along the path)
- After significant changes → repositions the crumbs (updates the affected AGENTS.md files)

## Basic usage (any tool)

1. Copy `AGENTS.md` into your project root
2. Tell your agent: `Initialize the Crumb tree for this project.`

No installation, no dependencies. Just Markdown.

## Usage with Kiro (hook enforcement)

To add automatic enforcement:

1. Copy `starter-kit/.kiro/` into your project root
2. Run `/crumb-init`

Hooks ensure AGENTS.md files get updated at task boundaries — zero overhead during work.

## Starter kit structure

```
starter-kit/.kiro/
├── hooks/
│   ├── crumb-update-after-task.kiro.hook   ← postTaskExecution
│   ├── crumb-closeout.kiro.hook            ← agentStop (fallback)
│   └── crumb-manual-refresh.kiro.hook      ← userTriggered
├── skills/
│   ├── crumb-init.md                       ← Generate AGENTS.md tree
│   ├── crumb-refresh.md                    ← Regenerate indexes, remove stale
│   └── crumb-closeout.md                   ← Pre-PR verification
└── steering/
    └── crumb-protocol.md                   ← Pointer: "follow AGENTS.md"
```

## Advantages

- **AGENTS.md pushed to git** — living documentation, shared, versioned
- **Cross-tool** — works on Kiro, Claude Code, Codex without adaptation
- **Zero duplication** — `.kiro/` only has hooks and pointers, not content
- **Lightweight enforcement** — hooks fire only at task end, never per file write

## Credits

Inspired by [DOX](https://github.com/agent0ai/dox) by [Agent Zero](https://www.agent-zero.ai/).

---

🇮🇹 [Leggi in italiano](./README.it.md)
