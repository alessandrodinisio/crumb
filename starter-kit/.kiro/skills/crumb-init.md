---
name: crumb-init
description: Scansiona il progetto e genera l'albero di AGENTS.md per area. Compatibile con Kiro, Claude Code, Codex.
---

# crumb-init — Inizializzazione albero Crumb

Scansiona ricorsivamente il progetto, identifica le aree con confini durevoli, e genera file AGENTS.md figli per ciascuna.

## Quando usarla

- Prima volta che si adotta Crumb in un progetto
- Dopo una ristrutturazione significativa
- Per aggiungere aree mancanti all'indice

## Procedura

### 1. Verifica root AGENTS.md

Se non esiste `AGENTS.md` nella root del progetto, crealo con il protocollo Crumb standard.

### 2. Scansione struttura

Scansiona ricorsivamente con profondità ≤ 3:
- Ignora: `.git/`, `node_modules/`, `target/`, `build/`, `dist/`, `.kiro/`, `__pycache__/`

### 3. Classificazione aree

Un confine durevole ha ALMENO 2 di:
- Scopo distinto dal progetto globale
- Tecnologia o linguaggio diverso
- Regole di build/test proprie
- Pattern architetturali specifici
- File di configurazione propri (pom.xml, package.json, Makefile)

Se < 2 → NON creare AGENTS.md, il root copre.

### 4. Generazione AGENTS.md figli

Per ogni area identificata, crea `<area>/AGENTS.md` con:

```markdown
# <Nome Area>

## Scopo
<1-2 frasi>

## Proprietà
- Tecnologie: ...
- Responsabile: ...

## Contratti Locali
<!-- Regole specifiche di questa area -->

## Linee Guida di Lavoro
<!-- Standard attuali — lascia vuoto se non definiti -->

## Verifica
<!-- Comandi build/test — lascia vuoto se non esistono -->

## Indice Figli
<!-- Sotto-aree con AGENTS.md proprio, se presenti -->
```

### 5. Aggiornamento indice root

Aggiorna la sezione "Indice Figli" nel root `AGENTS.md`:

```markdown
## Indice Figli

| Area | Path | Descrizione |
|------|------|-------------|
| src | src/AGENTS.md | Logica applicativa |
| scripts | scripts/AGENTS.md | Script di build e verifica |
```

### 6. Report

- Numero di aree identificate
- AGENTS.md creati (con path)
- Aree scartate e perché
- Suggerimenti per AGENTS.md futuri

## Regole

- NON creare AGENTS.md per aree < 5 file
- NON creare AGENTS.md vuoti senza regole specifiche
- Preferire meno AGENTS.md ben fatti a molti vuoti
- Massimo ~8 AGENTS.md per progetto
- I file AGENTS.md creati vanno committati su git
