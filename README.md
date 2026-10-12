# Child of Balance

Campagna D&D 5e (regole 2014) ambientata nei Forgotten Realms. Eos, figlio impossibile nato dall'unione di Lathander e Shar, torna al mondo come neonato; due culti clandestini e assolutisti ne cercano il potere. I PG ne diventano i custodi.

Repository locale sincronizzato da Google Drive il 12 ottobre 2026. Punto di ingresso: [`docs/00-project-management/project-index.md`](docs/00-project-management/project-index.md).

## Stato del progetto

Fase di **pre-produzione narrativa**. Nessun capitolo è ancora approvato oltre l'incipit (nascita e fuga dal santuario druidico). Vedi [Narrative Roadmap](docs/00-project-management/narrative-roadmap.md) per i decision gate da chiudere prima di scrivere contenuto giocabile — in particolare il **Gate A** (regole del potere di Eos), prerequisito di tutto il resto.

## Struttura del repository

```
docs/                       Contenuto narrativo canonico — fonte di verità, indipendente dalle presentazioni
├── 00-project-management/  Project Index, Technical Specification, Narrative Roadmap, archivio changelog
├── 01-campaign-design/     Campaign Bible, Story Outline, Characters & Factions, archi narrativi, workshop
└── 02-sessions/            Session Log (eventi realmente giocati, non pianificazione)

latex/manual/                Motore del template LaTeX (da fpetrulio/DnD_Campaigns), pronto a ricevere capitoli
foundry/child-of-balance/    Scheletro del modulo Foundry (da popolare dopo il Gate A/F della roadmap)
assets/                      Mappe, token/creature, handout, audio, concept art — vuoto, da popolare
archive/                     Bozze superate e materiale di riferimento — vuoto, da popolare
```

## Pipeline (da Technical Specification)

| Piattaforma | Ruolo |
|---|---|
| ChatGPT | Decisioni creative e progettuali |
| Google Drive | Memoria documentale, bozze, asset master |
| **Questo repository** | Markdown canonico, sorgenti LaTeX, script, release |
| LaTeX | PDF del manuale GM, appendici, handout giocatori |
| Foundry VTT (The Forge) | Modulo giocabile — target v14.365, dnd5e 5.3.3, Plutonium 2.18.1-v14 |

Principio architetturale: una sola versione approvata per ogni contenuto. Il Markdown in `docs/` è la fonte; LaTeX e Foundry sono output derivati, non copie parallele da editare a mano.

## Build del manuale (LaTeX)

```sh
cd latex/manual
make        # richiede una distribuzione TeX Live con i pacchetti elencati in packages.txt
```

Nessun capitolo `.tex` esiste ancora: il motore (classe `dndbook.cls`, pacchetto `dnd.sty`) è pronto ma va scritto `main.tex` con i capitoli approvati una volta chiuso almeno il Gate F della roadmap (primo vertical slice giocabile).

## Convenzioni editoriali

Ogni documento in `docs/` distingue:

- **CONFERMATO** — deciso esplicitamente dall'autore/GM
- **IPOTESI** — proposta non approvata
- **SCARTATO** — proposta respinta
- **DA DEFINIRE** — questione aperta senza soluzione

Non promuovere un'IPOTESI a canone senza un aggiornamento esplicito della Campaign Bible. I segreti da GM non vanno copiati in materiali destinati ai giocatori.
