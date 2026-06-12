<p align="center">
  <img src="./banner.png" alt="Crumb" width="100%">
</p>

## Crumb — Briciole per agenti AI

Come Pollicino lasciava sassolini per ritrovare la strada, Crumb lascia file `AGENTS.md` nell'albero del progetto perché l'agente AI non si perda.

Funziona con **qualsiasi agente**: Kiro, Claude Code, Codex, OpenCode.

## Come funziona

L'agente segue una gerarchia di file `AGENTS.md`:

- `AGENTS.md` nella root → regole progetto-wide e indice aree
- `AGENTS.md` nelle sottocartelle → regole locali specifiche
- Prima di modificare un'area → segue le briciole (legge gli AGENTS.md lungo il percorso)
- Dopo modifiche significative → ri-posiziona le briciole (aggiorna gli AGENTS.md)

## Uso base (qualsiasi tool)

1. Copia `AGENTS.md` nella root del tuo progetto
2. Dì all'agente: `Inizializza l'albero Crumb per questo progetto.`

Nessuna installazione, nessuna dipendenza. Solo Markdown.

## Uso con Kiro (enforcement via hook)

Per aggiungere enforcement automatico:

1. Copia `starter-kit/.kiro/` nella root del tuo progetto
2. Esegui `/crumb-init`

Gli hook garantiscono che gli AGENTS.md vengano aggiornati a fine task — senza overhead durante il lavoro.

## Struttura starter-kit

```
starter-kit/.kiro/
├── hooks/
│   ├── crumb-update-after-task.kiro.hook   ← postTaskExecution
│   ├── crumb-closeout.kiro.hook            ← agentStop (fallback)
│   └── crumb-manual-refresh.kiro.hook      ← userTriggered
├── skills/
│   ├── crumb-init.md                       ← Genera albero AGENTS.md
│   ├── crumb-refresh.md                    ← Rigenera indici, rimuovi stale
│   └── crumb-closeout.md                   ← Verifica pre-PR
└── steering/
    └── crumb-protocol.md                   ← Puntatore: "segui AGENTS.md"
```

## Vantaggi

- **AGENTS.md pushati su git** — documentazione viva, condivisa, versionata
- **Cross-tool** — funziona su Kiro, Claude Code, Codex senza adattamenti
- **Zero duplicazione** — `.kiro/` ha solo hook e puntatori, non contenuto
- **Enforcement leggero** — hook scattano solo a fine task, mai ad ogni write

## Crediti

Ispirato da [DOX](https://github.com/agent0ai/dox) di [Agent Zero](https://www.agent-zero.ai/).

---

🇬🇧 [Read in English](./README.md)
