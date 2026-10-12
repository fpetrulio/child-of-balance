# Child of Balance

Campagna D&D 5e (regole 2014) ambientata nei Forgotten Realms. Eos, figlio impossibile nato dall'unione di Lathander e Shar, torna al mondo come neonato; due culti clandestini e assolutisti ne cercano il potere. I PG ne diventano i custodi.

Repository locale sincronizzato da Google Drive il 12 ottobre 2026. Punto di ingresso: [`docs/00-project-management/project-index.md`](docs/00-project-management/project-index.md).

## Stato del progetto

Fase di **pre-produzione narrativa**. Nessun capitolo è ancora approvato oltre l'incipit (nascita e fuga dal santuario druidico). Vedi [Narrative Roadmap](docs/00-project-management/narrative-roadmap.md) per i decision gate da chiudere prima di scrivere contenuto giocabile. Si procede **un gate alla volta**: **Gate A** (regole del potere di Eos) prima, poi **Gate B** (limiti all'intervento divino — candidato: il Patto degli Avatar di Ao).

## Struttura del repository

```
docs/                       Contenuto narrativo canonico — fonte di verità, indipendente dalle presentazioni
├── 00-project-management/  Project Index, Technical Specification, Narrative Roadmap, archivio changelog
├── 01-campaign-design/     Campaign Bible, Story Outline, Characters & Factions, archi narrativi, workshop
└── 02-sessions/            Session Log (eventi realmente giocati, non pianificazione)

latex/manual/                Motore LaTeX + scheletro completo dell'avventura (main.tex, capitoli, interludi, appendici) — vedi README dedicato
foundry/child-of-balance/    Scheletro del modulo Foundry (da popolare dopo il Gate A/F della roadmap)
assets/                      Mappe, token/creature, handout, audio, concept art — vuoto, da popolare
archive/                     Bozze superate e materiale di riferimento — vuoto, da popolare
```

## Pipeline (da Technical Specification)

| Piattaforma | Ruolo |
|---|---|
| **Claude Code** (questa sessione) | Decisioni creative e tecniche — sostituisce ChatGPT dal 12/10/2026 |
| Google Drive | Solo archivio storico e asset grezzi pre-ottimizzazione |
| **Questo repository** | Markdown canonico, sorgenti LaTeX, script, release |
| LaTeX | PDF del manuale GM, appendici, handout giocatori |
| Foundry VTT (The Forge) | Modulo giocabile — target v14.365, dnd5e 5.3.3, Plutonium (verificare versione al Gate F/G: repo rinominato `plutonium-next`) |

Principio architetturale: una sola versione approvata per ogni contenuto. Il Markdown in `docs/` è la fonte; LaTeX e Foundry sono output derivati, non copie parallele da editare a mano.

## Build del manuale (LaTeX)

```sh
cd latex/manual
make        # richiede una distribuzione TeX Live con i pacchetti elencati in packages.txt
```

`latex/manual/` è già strutturata come un'avventura D&D standard: `main.tex` + Introduzione + 4 capitoli + 3 interludi (downtime) + 4 appendici (nuove creature, oggetti magici, mappe/handout, PNG/fazioni) — vedi [`latex/manual/README.md`](latex/manual/README.md) per i dettagli. Ogni file è per ora uno scheletro con un box editoriale che segnala a quale gate della roadmap è legato: nessun contenuto narrativo è stato scritto lì per primo, verrà adattato da `docs/` quando un capitolo sarà approvato.

## Convenzioni editoriali

Ogni documento in `docs/` distingue:

- **CONFERMATO** — deciso esplicitamente dall'autore/GM
- **IPOTESI** — proposta non approvata
- **SCARTATO** — proposta respinta
- **DA DEFINIRE** — questione aperta senza soluzione

Non promuovere un'IPOTESI a canone senza un aggiornamento esplicito della Campaign Bible. I segreti da GM non vanno copiati in materiali destinati ai giocatori.
