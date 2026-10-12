# Technical Specification — Child of Balance

Versione iniziale 0.1 — 9 ottobre 2026

## 1. Ambiente target

- Hosting primario: The Forge.
- Foundry Virtual Tabletop: v14 Stable 7, build 365 — versione indicata dal GM.
- Sistema Dungeons & Dragons Fifth Edition (dnd5e): 5.3.3 — confermato dal GM.
- Plutonium: 2.18.1-v14 — versione indicata dal GM.
- Regole di gioco della campagna: D&D 5e 2014.

Qualsiasi upgrade deve essere verificato rispetto alle versioni di Foundry, del sistema e dei moduli installati.

## 2. Ruoli delle piattaforme

- ChatGPT: interfaccia primaria per decisioni creative e progettuali.
- Google Drive: memoria documentale, bozze, appunti, file originali e asset master.
- GitHub: codice, Markdown canonico approvato, template/sorgenti LaTeX, script e release.
- LaTeX: PDF del manuale GM, appendici e player handout.
- Foundry su The Forge: modulo giocabile con journal, scene, asset e contenuti importabili.

## 3. Principi architetturali

- Una sola versione approvata di ciascun contenuto; nessuna modifica parallela non riconciliata tra Drive e GitHub.
- Contenuti narrativi strutturati e indipendenti dalle presentazioni; output LaTeX e Foundry generati o adattati da tali contenuti.
- Asset raw conservati in Drive; asset approvati e ottimizzati distribuiti nel modulo con percorsi locali al package.
- Scene, muri, luci, token e configurazioni VTT sono dati specifici di Foundry e possono richiedere editing nell'applicazione.
- UUID di creature importate con Plutonium non assunti stabili tra mondi; usare mapping/logiche di riferimento configurabili.
- Plutonium deve restare opzionale per il modulo, ove possibile.

## 4. Compatibilità e dipendenze

- Target iniziale di sviluppo: Foundry 14.365 con dnd5e 5.3.3.
- Compatibilità runtime del nostro modulo: NON ANCORA TESTATA su The Forge.
- Plutonium può importare mostri standard nel mondo del GM. Il nostro modulo distribuirà solo contenuti pubblicabili e originali/appropriatamente licenziati.
- Per le release pubbliche rispettare licenze di template, testo, stat block, mappe, illustrazioni e audio.

## 5. Pubblicazione e test

- Prototipo locale v0.1.1 già preparato nella conversazione, ma installazione e test su The Forge in sospeso.
- Futuro repository dedicato e pubblico: **questo repository locale**, da collegare a GitHub dopo analisi template (vedi sezione 7).
- Obiettivo build: PDF dal template LaTeX; ZIP installabile Foundry; module.json con versioni minime e URL validi; GitHub Releases.
- Per repository privati, gli URL di installazione non sono automaticamente accessibili. Con repository pubblico, i release artifact possono essere esposti tramite URL stabili.
- Test minimi: manifest valido, attivazione, macro/prototipo, creazione journal e scena, accesso ai media, import Adventure Compendium, isolamento spoiler.

## 6. Sicurezza editoriale e licenze

- Tenere distinti materiali Player e Game Master.
- Non redistribuire automaticamente contenuti proprietari importati con Plutonium; usare fonti autorizzate e licenze applicabili.
- Rivedere il diritto d'uso del template LaTeX prima della pubblicazione pubblica.
- Confermare con il GM operazioni distruttive, pubblicazione e cambiamenti di ampia portata.

## 7. Stato implementazione

- Drive: struttura e documenti base inizializzati.
- **GitHub: repository locale impostato il 12 ottobre 2026 (`~/DnD/child-of-balance`), sincronizzato come git repo; remoto GitHub non ancora creato/collegato.**
- **LaTeX: motore del template `fpetrulio/DnD_Campaigns` (cartella "Ritorno a Bloodstone") copiato in `latex/manual/` — dndbook.cls, dnd.sty, lib/, bin/, Makefile. Nessun capitolo scritto: non esiste ancora materiale narrativo approvato da impaginare.**
- **Foundry: nessuno scheletro di modulo creato finché non sono definite le regole minime (vedi Narrative Roadmap, Gate A/F). Il prototipo ZIP v0.1.1 menzionato in chat precedente non è recuperabile da Drive né da questo archivio.**
- The Forge: test effettivo non ancora eseguito.

## 8. Log di sincronizzazione locale

- 2026-10-12 — Cartella Drive "Child of Balance" esplorata e sincronizzata in questo repository locale. Tutti i documenti di `01 — Campaign Design`, `00 — Project Management` e `02 — Sessions` convertiti in Markdown. Le cartelle `03 — Assets`, `04 — Publications` e `99 — Archive` erano vuote su Drive al momento della sincronizzazione — replicate come scheletro locale (`assets/`, `foundry/`, `archive/`) pronto a ricevere contenuto.
