# Child of Balance — istruzioni di progetto

Campagna D&D 5e (regole 2014), Forgotten Realms. Leggi prima [`docs/00-project-management/project-index.md`](docs/00-project-management/project-index.md) — è il punto d'ingresso e riporta la situazione corrente.

## Protocollo editoriale

Ogni affermazione narrativa porta uno stato: **CONFERMATO** (deciso dall'autore/GM), **IPOTESI** (proposta non approvata), **SCARTATO** (respinta), **DA DEFINIRE**. Non promuovere mai un'IPOTESI a CONFERMATO senza una decisione esplicita dell'autore in questa sessione. Quando una decisione nuova supera una precedente, aggiungi una nota di aggiornamento — non riscrivere né eliminare la cronologia.

## Fonte unica del canone

Il testo narrativo canonico vive **solo** in `docs/` su questo repository. Google Drive è solo archivio storico e deposito di asset grezzi pre-ottimizzazione — non va più editato in parallelo (rischio di due versioni approvate divergenti). ChatGPT non è più usato per questo progetto (DEC-0022).

## Stile di lavoro dell'autore

- **Un decision gate alla volta** (vedi [Narrative Roadmap](docs/00-project-management/narrative-roadmap.md)), anche quando due gate sono tematicamente collegati. Non proporre di affrontarne due in parallelo nella stessa sessione.
- Lingua di lavoro: italiano.

## Lore e regole

Sistema D&D 5e **2014** (non la revisione 2024). Ambientazione Forgotten Realms con homebrew esplicito (vedi Campaign Bible per cosa è homebrew vs lore ufficiale). Prima di asserire un dettaglio di lore o una regola precisa (nome di piano, dominio di una divinità, testo esatto di un incantesimo, versione di un pacchetto Foundry/dnd5e/Plutonium), verifica con WebSearch se non sei sicuro al 100% — la memoria del modello può essere imprecisa su dettagli specifici, e le versioni dei tool Foundry cambiano nel tempo.

## Fine sessione

Quando l'autore chiude una sessione di lavoro su questo progetto, esegui `/wrapup` (vedi `.claude/commands/wrapup.md`) per aggiornare changelog, Project Index e fare commit+push.
