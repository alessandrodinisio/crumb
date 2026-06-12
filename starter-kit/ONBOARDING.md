# Onboarding — Crumb

## Filosofia

- I file `AGENTS.md` sono le briciole: documentazione operativa pushata su git, cross-tool
- La cartella `.kiro/` contiene solo l'enforcement (hook) e il protocollo — non duplica contenuto

## Setup rapido

1. Copia `.kiro/` di questo starter-kit nella root del tuo progetto
2. Assicurati di avere un `AGENTS.md` nella root del progetto
3. Esegui `/crumb-init` per generare AGENTS.md figli nelle sottocartelle

## Struttura risultante

```
progetto/
├── AGENTS.md                         ← root (pushato, cross-tool)
├── src/
│   └── AGENTS.md                     ← regole area src (pushato)
├── scripts/
│   └── AGENTS.md                     ← regole area scripts (pushato)
└── .kiro/
    ├── hooks/
    │   ├── crumb-update-after-task.kiro.hook
    │   ├── crumb-closeout.kiro.hook
    │   └── crumb-manual-refresh.kiro.hook
    ├── skills/
    │   ├── crumb-init.md
    │   ├── crumb-refresh.md
    │   └── crumb-closeout.md
    └── steering/
        └── crumb-protocol.md
```

## Come funziona

### Cross-tool: funziona ovunque
- **Kiro**: steering punta agli AGENTS.md + hook enforcano l'aggiornamento
- **Claude Code**: legge AGENTS.md root automaticamente a inizio sessione
- **Codex**: legge AGENTS.md root automaticamente per ogni task

### Hook Kiro (solo enforcement, zero overhead in sessione)
- **postTaskExecution** → dopo un task completato, verifica se gli AGENTS.md vanno aggiornati
- **agentStop** → fallback per sessioni libere senza spec task
- **userTriggered** → bottone manuale per forzare un refresh

### Comandi on-demand

| Comando | Quando |
|---------|--------|
| `/crumb-init` | Bootstrap iniziale: genera albero AGENTS.md |
| `/crumb-refresh` | Manutenzione: rigenera indici, rimuovi stale |
| `/crumb-closeout` | Pre-PR: verifica tutto allineato |

## Quando creare un nuovo AGENTS.md figlio

Crea `<cartella>/AGENTS.md` quando l'area ha ALMENO 2 di:
- Scopo distinto
- Tecnologia diversa
- Build/test propri
- Pattern architetturali specifici
- Configurazione propria

Altrimenti, il root AGENTS.md copre.
