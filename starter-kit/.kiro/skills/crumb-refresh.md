---
name: crumb-refresh
description: Rigenera gli indici nei file AGENTS.md, verifica testo stale, rimuove contraddizioni.
---

# crumb-refresh — Manutenzione albero Crumb

Verifica la salute dell'albero AGENTS.md, rigenera indici, segnala/rimuove informazioni stale.

## Quando usarla

- Periodicamente (ogni ~10 sessioni)
- Dopo refactoring significativi
- Quando si sospetta drift tra documentazione e codice

## Procedura

### 1. Inventario

Trova tutti i file AGENTS.md nel progetto:
```bash
find . -name "AGENTS.md" -not -path "./.git/*"
```

### 2. Verifica coverage

Per ogni AGENTS.md figlio:

| Check | Azione se FAIL |
|-------|----------------|
| La cartella ha ancora file? | Segnala "AGENTS.md orfano" |
| Le regole corrispondono al codice? | Aggiorna |
| Sezioni vuote da tempo? | Rimuovi placeholder o popola |
| Indice Figli completo? | Aggiorna |

### 3. Consistenza

- Nessuna regola duplicata tra root e figli
- Nessun conflitto non esplicito
- Ogni AGENTS.md figlio è nell'Indice del genitore

### 4. Rigenera Indice Root

Riscrivi la tabella "Indice Figli" nel root AGENTS.md con i dati attuali.

### 5. Pulizia

- Rimuovi riferimenti a file/classi che non esistono più
- Rimuovi avvisi per rischi passati
- Rimuovi TODO completati

### 6. Report

```markdown
## Crumb Refresh Report

- AGENTS.md trovati: N
- Aggiornati: N (lista)
- Stale rimosso: N occorrenze
- Suggerimenti: ...
```
