---
name: crumb-closeout
description: Verifica manuale che tutti gli AGENTS.md siano allineati dopo un blocco di lavoro.
---

# crumb-closeout — Verifica allineamento AGENTS.md

Passaggio Crumb completo: verifica che tutti gli AGENTS.md impattati dal lavoro recente siano aggiornati.

## Quando usarla

- Dopo un blocco di lavoro significativo
- Prima di un merge/PR
- Quando l'hook automatico non basta (lavoro multi-sessione)

## Procedura

### 1. Identifica modifiche recenti

```bash
git diff --name-only HEAD~5
```

### 2. Mappa file → AGENTS.md

Per ogni file modificato, risali l'albero fino a trovare l'AGENTS.md più vicino.

### 3. Verifica ogni AGENTS.md impattato

| Aspetto | Se obsoleto |
|---------|-------------|
| Scopo | Aggiorna |
| Tecnologie | Aggiorna |
| Contratti locali | Aggiorna/Rimuovi |
| Linee guida | Aggiorna |
| Verifica | Aggiorna |
| Indice Figli | Aggiorna |

### 4. Report

```markdown
## Crumb Closeout Report

- File modificati: N
- AGENTS.md verificati: N
- Aggiornamenti fatti: N

| AGENTS.md | Status | Azione |
|-----------|--------|--------|
| ./AGENTS.md | OK | — |
| src/AGENTS.md | Aggiornato | Sezione "Verifica" |
```
