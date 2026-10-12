---
description: Chiude la sessione di lavoro su Child of Balance — aggiorna changelog, Project Index, e fa commit+push
---

Esegui il protocollo di fine sessione per il progetto Child of Balance:

1. **Rivedi la conversazione** da quando è iniziata la sessione (o da dopo l'ultimo `/wrapup`) e identifica: decisioni CONFERMATE, proposte scartate, nuove IPOTESI, tensioni risolte o aperte.

2. **Aggiorna il changelog**: in `docs/00-project-management/session-archive/`, se esiste già una sezione per la data odierna continuala con nuove voci CL-NNN (numerazione progressiva, non riusare ID esistenti); altrimenti crea un nuovo file `YYYY-MM-DD-changelog-handoff.md` seguendo il formato di `2026-10-09-changelog-handoff.md`. Ogni voce: stato, decisione, razionale breve.

3. **Aggiorna i documenti toccati**: se una decisione modifica un'affermazione in Campaign Bible, Story Outline, Characters & Factions, o uno degli archi narrativi, aggiorna quel documento con una nota che referenzia il nuovo DEC-/CL-ID — non sovrascrivere la cronologia precedente, aggiungi.

4. **Aggiorna il Project Index** (`docs/00-project-management/project-index.md`): la sezione "Situazione corrente" e la "Cronologia documentale" (§8) con una riga per oggi.

5. **Verifica la Narrative Roadmap**: se un gate è stato chiuso o è avanzato, aggiorna il suo stato lì.

6. **Commit e push**: `git add -A`, commit con messaggio che riassume le decisioni della sessione (referenziando i DEC-/CL-ID toccati), poi `git push`.

7. **Riporta un riepilogo breve** all'utente: cosa è stato deciso, cosa resta apertO, qual è il prossimo gate/passo secondo la Narrative Roadmap.

Non promuovere a canone nulla che non sia stato esplicitamente confermato in questa sessione.
