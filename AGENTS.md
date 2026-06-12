# Crumb

- Crumb è un protocollo di documentazione operativa basato su file AGENTS.md
- L'agente segue le briciole (AGENTS.md) per orientarsi nel progetto
- Ispirato da DOX (Agent Zero), adattato per approccio ibrido cross-tool

## Contratto Fondamentale

- I file AGENTS.md sono contratti di lavoro vincolanti per i rispettivi sottoalberi
- Ogni area deve restare comprensibile dall'AGENTS.md più vicino + tutti i genitori

## Leggere Prima di Modificare

1. Leggi l'AGENTS.md root
2. Identifica ogni file o cartella che prevedi di toccare
3. Percorri dal root fino a ogni percorso target
4. Leggi ogni AGENTS.md trovato lungo ciascun percorso
5. Se un genitore elenca un figlio il cui ambito contiene il percorso, leggi quel figlio
6. Usa l'AGENTS.md più vicino come contratto locale
7. Se conflitto: il documento più vicino controlla i dettagli locali, ma nessun figlio può indebolire il protocollo

## Aggiornare Dopo la Modifica

Aggiorna l'AGENTS.md più vicino quando una modifica riguarda:
- scopo, ambito, proprietà o responsabilità
- struttura durevole, contratti, workflow o regole operative
- input/output, permessi, vincoli, effetti collaterali
- preferenze utente
- creazione/eliminazione/spostamento di AGENTS.md

## Struttura dei Figli

Ordine sezioni:
- Scopo
- Proprietà
- Contratti Locali
- Linee Guida di Lavoro
- Verifica
- Indice Figli

## Stile

- Conciso, aggiornato, operativo
- Contratti stabili, non diari
- Regole generali nel genitore, dettagli concreti nei figli
- Elimina testo stale immediatamente

## Chiusura

1. Ricontrolla i percorsi modificati
2. Aggiorna AGENTS.md coinvolti
3. Aggiorna ogni Indice Figli
4. Rimuovi testo stale

## Preferenze Utente

- Lingua: italiano
- Approccio ibrido: AGENTS.md cross-tool + hook Kiro per enforcement
- Hook leggeri: scattano a fine task, mai ad ogni singolo file write

## Indice Figli

| Area | Path | Descrizione |
|------|------|-------------|
| Starter Kit | starter-kit/AGENTS.md | Kit installazione per Kiro (hook, skill, steering puntatore) |
