# Starter Kit Crumb per Kiro

## Scopo

Kit di installazione che aggiunge enforcement automatico (hook Kiro) al protocollo Crumb basato su AGENTS.md. Non contiene la documentazione del progetto — quella vive nei file AGENTS.md nel repo.

## Proprietà

- Tecnologie: Kiro (hook, steering, skill)
- Compatibilità: funziona in parallelo con Claude Code, Codex, OpenCode

## Contratti Locali

- `.kiro/hooks/` — enforcement automatico (postTaskExecution, agentStop, userTriggered)
- `.kiro/skills/` — comandi on-demand (`/crumb-init`, `/crumb-refresh`, `/crumb-closeout`)
- `.kiro/steering/crumb-protocol.md` — puntatore che dice a Kiro "segui i file AGENTS.md"
- I file `.kiro/` NON contengono regole di progetto — sono solo meccanismo

## Linee Guida di Lavoro

- Non duplicare mai contenuto tra `.kiro/` e AGENTS.md
- Gli hook devono restare leggeri (nessun preToolUse per singolo file)
- Le skill devono operare sui file AGENTS.md, non creare/modificare steering

## Verifica

- Dopo modifica agli hook: verificare che il JSON sia valido
- Dopo modifica alle skill: verificare coerenza con il protocollo Crumb (root AGENTS.md)

## Indice Figli

Nessun sotto-AGENTS.md — lo starter-kit è piccolo e gestito da questo file.
