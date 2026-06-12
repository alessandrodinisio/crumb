# Protocollo Crumb

Questo progetto usa il protocollo Crumb per mantenere la documentazione allineata al codice.

## Fonte di verità

I file `AGENTS.md` sparsi nel progetto sono la documentazione operativa:
- `AGENTS.md` nella root → regole globali, indice aree
- `AGENTS.md` nelle sottocartelle → regole locali dell'area

## Regole per l'agente

1. **Prima di modificare un'area**: leggi l'AGENTS.md più vicino al file che stai toccando + tutti i genitori fino alla root
2. **Dopo un task completato**: se la modifica ha impattato scopo, struttura, contratti o regole di un'area → aggiorna l'AGENTS.md coinvolto
3. **Se non esiste un AGENTS.md per l'area**: segui le regole del root AGENTS.md
4. **Se trovi testo stale**: rimuovilo immediatamente

## Quando NON aggiornare

- Fix di una riga che non cambia comportamento
- Modifiche a file di dati/configurazione che non alterano la struttura
- Sessioni brevi di sola lettura/analisi
