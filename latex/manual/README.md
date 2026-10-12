# LaTeX manual — Child of Balance

Questa cartella **è** la root dell'avventura: non è un sotto-progetto di un repository multi-campagna. Motore copiato da [`fpetrulio/DnD_Campaigns`](https://github.com/fpetrulio/DnD_Campaigns), cartella "Ritorno a Bloodstone" (12 ottobre 2026): `dndbook.cls`, `dnd.sty`, `dndcore.def`, `dndoptions.clo`, `lib/`, `bin/`, `Makefile`, `packages.txt`, `.editorconfig`, `LICENSE` (MIT, Evan Bergeron 2017 — nessuna restrizione).

**Pulizia 12/10/2026**: rimossi dal motore originale gli strumenti pensati per un repository multi-campagna/multi-collaboratore e non applicabili qui — `bin/bump-version` (versioning del template stesso), `package.json`/`package-lock.json` (lint `eclint` senza `.editorconfig` reale, ora sostituito da uno vero), target `lint` del Makefile, e tutta la parte del README originale su bacheca Trello, branch-per-capitolo e review via Acrobat (gestione multi-collaboratore — qui lavoriamo io e l'autore via `/wrapup`, vedi `CLAUDE.md` nella root del repository).

## Struttura

```
main.tex              Frontespizio, sommario, \include di tutto il resto
Introduzione.tex      Background dell'avventura, guida all'avventura, riassunto
Capitolo1.tex         Capitolo 1
Interludio1.tex       Downtime 1
Capitolo2.tex         Capitolo 2
Interludio2.tex       Downtime 2
Capitolo3.tex         Capitolo 3
Interludio3.tex       Downtime 3
Capitolo4.tex         Capitolo 4
AppendiceA.tex        Nuove creature (statblocchi originali)
AppendiceB.tex        Oggetti magici (incluse le Impronte di Eos)
AppendiceC.tex        Mappe e handout
AppendiceD.tex        PNG e fazioni
```

Struttura standard di un'avventura D&D pubblicata (setup/background, sinossi, capitoli, appendici per mostri/oggetti/mappe/PNG), allineata ai 4 capitoli + 3 downtime già decisi (DEC-0018/0019). Tutti i file esistono già come **scheletro**: ogni capitolo contiene solo un box `DndComment` che segnala cosa manca e a quale gate della [Narrative Roadmap](../../docs/00-project-management/narrative-roadmap.md) è legato — nessun contenuto narrativo è stato scritto qui per primo (principio architetturale: il canone vive in `docs/01-campaign-design/` come Markdown, il `.tex` è output derivato quando un capitolo è approvato, non la sua prima stesura).

## Installazione e avvio di LaTeX

Se sei nuovo a LaTeX:

1. Scarica la distribuzione [MiKTeX](https://miktex.org/download) (o, su macOS/Linux, [TeX Live](https://www.tug.org/texlive/) — vedi anche `bin/install-texlive` e `bin/install-packages packages.txt` per un'installazione minimale automatizzata).
2. Scarica l'editor [TeXstudio](https://www.texstudio.org/).
3. Apri `main.tex` in TeXstudio ed esegui "Compila e Visualizza" (doppia freccia verde). **Nota bene**: va sempre compilato `main.tex`, non i singoli capitoli, per una corretta impaginazione.
4. Per approfondire la sintassi LaTeX: [L'Arte di LaTeX](http://www.lorenzopantieri.net/LaTeX_files/ArteLaTeX.pdf) (guida in italiano).

In alternativa, da riga di comando: `make` in questa cartella (richiede `latexmk` e i pacchetti elencati in `packages.txt`).

**Non ancora testato in questa sessione**: nessuna distribuzione TeX è installata sulla macchina usata per questa revisione, quindi lo scheletro sopra non è stato compilato localmente. La sintassi segue esattamente i pattern verificati in `main.tex`/`Introduzione.tex`/`AppendixA.tex` di "Ritorno a Bloodstone" — verificalo con una compilazione reale alla prima occasione.

## Convenzioni per quando si scrive contenuto vero

- `\chapter{}` per ogni capitolo/interludio/appendice; `\section{}`/`\subsection{}` per le sezioni interne.
- `DndReadAloud` per i testi da leggere ad alta voce ai giocatori; `DndSidebar`/`DndComment` per approfondimenti ed note editoriali (non breakable il primo, breakable il secondo).
- `DndMonster` per gli statblocchi (vedi esempio completo nel `main.tex` del template originale); `DndItemHeader` per gli oggetti magici; `DndSpellHeader` per incantesimi homebrew; `DndArea`/`DndSubArea` per regioni di mappa numerate.
- Non promuovere un'IPOTESI a testo definitivo qui: scrivi un capitolo `.tex` solo dopo che il contenuto corrispondente è CONFERMATO in `docs/`.
