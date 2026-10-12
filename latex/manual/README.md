# LaTeX manual — Child of Balance

Motore copiato da [`fpetrulio/DnD_Campaigns`](https://github.com/fpetrulio/DnD_Campaigns), cartella "Ritorno a Bloodstone" (12 ottobre 2026): `dndbook.cls`, `dnd.sty`, `dndcore.def`, `dndoptions.clo`, `lib/`, `bin/`, `Makefile`, `packages.txt`.

Non ancora presenti (volutamente): `main.tex` e i capitoli (`Capitolo*.tex`). Nessun contenuto narrativo è approvato in forma giocabile — vedi [Narrative Roadmap, Gate F](../../docs/00-project-management/narrative-roadmap.md#6-gate-f--primo-vertical-slice-giocabile). Il testo canonico vive in `docs/01-campaign-design/` come Markdown; quando un capitolo è approvato, va adattato qui in `.tex`, non scritto qui per primo (principio architetturale: una sola fonte approvata, Markdown → LaTeX).

Per impaginare un capitolo quando pronto, seguire il pattern di `main.tex`/`Introduzione.tex`/`Capitolo1.tex` nell'originale `Ritorno a Bloodstone` come riferimento di struttura (non copiarne il contenuto, solo l'impalcatura `\documentclass{dndbook}` + `\input{}`).

Build: `make` da questa cartella (richiede TeX Live, pacchetti in `packages.txt`).
