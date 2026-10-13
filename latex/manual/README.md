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

**Compilazione verificata il 12/10/2026** — `main.pdf` si genera correttamente (15 pagine). Setup usato su questa macchina (macOS Intel, nessun TeX preesistente, nessun accesso sudo disponibile):

```sh
# Installazione TeX Live minimale, tutta in home, senza sudo
mkdir -p ~/texlive-setup && cd ~/texlive-setup
curl -fsSL -o install-tl-unx.tar.gz https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
tar -xzf install-tl-unx.tar.gz && cd install-tl-20*
cat > ../texlive-local.profile << 'EOF'
selected_scheme scheme-infraonly
TEXDIR ~/texlive-local
TEXMFCONFIG ~/.texlive-local/texmf-config
TEXMFHOME ~/texmf
TEXMFLOCAL ~/texlive-local/texmf-local
TEXMFSYSCONFIG ~/texlive-local/texmf-config
TEXMFSYSVAR ~/texlive-local/texmf-var
TEXMFVAR ~/.texlive-local/texmf-var
option_doc 0
option_src 0
EOF
./install-tl --profile=../texlive-local.profile --no-interaction

# Ad ogni sessione di shell:
export PATH="$HOME/texlive-local/bin/universal-darwin:$PATH"   # darwin su Linux: bin/x86_64-linux

# Installare i pacchetti di packages.txt UNO ALLA VOLTA (un batch con tutti insieme
# annulla l'intera transazione se anche un solo pacchetto non risolve da un mirror):
for p in dvips graphics graphics-def latex latex-bin latexmk xetex $(grep -v '^#' packages.txt | sed 's/#.*//' | grep -v '^[[:space:]]*$'); do
  tlmgr install --repository https://texlive.info/CTAN/systems/texlive/tlnet "$p"
done
```

Stranezze incontrate (`packages.txt` risale al 2019, alcuni nomi sono cambiati su CTAN):
- `ifluatex`/`ifxetex` non esistono più come pacchetti separati → sono nel bundle **`iftex`**.
- `etex` (nome nel messaggio d'errore) → il pacchetto vero è **`etex-pkg`** (già in `packages.txt`, ma se manca va installato per nome esatto).
- `bookman`/`times`/altri font PostScript "standard" → vengono da **`psnfss`** (già in elenco), non da un pacchetto con lo stesso nome del font.
- `sttools` (fornisce `stfloats.sty`) è risultato intermittente sul mirror `texlive.info` — se fallisce, riprovare o usare un mirror diverso (`mirror.ctan.org`, `ctan.math.illinois.edu`).
- Il mirror generico `mirror.ctan.org` a volte risolve verso repliche con catalogo disallineato ("remote database... seems older") — se capita, puntare esplicitamente a `https://texlive.info/CTAN/systems/texlive/tlnet`.

**Risolto (12/10/2026)**: l'avviso `Package pgfkeys Error: I do not know the key '/tcb/\NoValue'` che compariva una volta per ogni box `DndComment` era causato da `\begin{DndComment}{Titolo}` senza l'argomento opzionale `[...]` — il marcatore interno `-NoValue-` di xparse per l'argomento omesso finiva passato al parser di chiavi di `tcolorbox`. Fix: usare sempre `\begin{DndComment}[]{Titolo}` con le quadre esplicite anche se vuote (già applicato in tutti i capitoli/appendici esistenti).

**Risolto (12/10/2026)**: testo giustificato invece di ragged-right — il template ha già un'opzione di classe `justified` (vedi `dndoptions.clo`), basta passarla: `\documentclass[...,justified]{dndbook}` (già impostata in `main.tex`).

## Convenzioni per quando si scrive contenuto vero

- `\chapter{}` per ogni capitolo/interludio/appendice; `\section{}`/`\subsection{}` per le sezioni interne.
- `DndReadAloud` per i testi da leggere ad alta voce ai giocatori (terza persona, mai "voi", sotto le 100 parole/4 frasi -- vedi guida ufficiale D&D Beyond "Let's Design an Adventure: Boxed Text"); `DndSidebar`/`DndComment` per approfondimenti ed note editoriali (non breakable il primo, breakable il secondo).
- `DndItemHeader` per gli oggetti magici; `DndSpellHeader` per incantesimi homebrew. **Corretto (13/10/2026)**: `DndArea`/`DndSubArea` menzionati qui in precedenza NON esistono nel template -- per zone di mappa numerate usare `\subsection*{Zona N --- Nome}` (vedi `Capitolo1.tex`). Per gli statblocchi, nessun esempio del box `DndMonster` completo è sopravvissuto dal template originale: usare formattazione semplice (`\textbf`/`\textit` manuali, vedi `AppendiceA.tex`) finché qualcuno non investe il tempo di decifrare `lib/dndmonster.sty`. **Attenzione**: `dndmonster.sty` ridefinisce `\hline` (lo rompe fuori da un vero statblock) -- non usarlo nelle tabelle normali, va bene ometterlo o usare `\\[2pt]` per lo spazio dopo l'intestazione.
- **Stile wiki per ogni voce di background** (luoghi, culti, PNG, mostri custom) **-- standard del progetto, non solo per questo capitolo** (richiesta esplicita dell'autore, 13/10/2026): paragrafo d'apertura (chi/cosa/dove), poi una sezione **Storia** in prosa discorsiva e connessa -- mai un elenco puntato di eventi con sole date -- cosi' il GM può rispondere a tono alle domande dei giocatori invece di recitare fatti frammentati (modello: voci organizzative della Forgotten Realms Wiki). Dove rilevante, una o più **tabelle delle conoscenze dei PG**, una per abilità pertinente (Storia, Religione, Arcana, Natura... separate, non una prova combinata), con DC calibrate sulla reale difficoltà dell'informazione (vedi `AppendiceD.tex`, box "Come calibrare le DC di conoscenza": scala 5-30+, i segreti quasi impossibili restano DC 28-30+, raggiungibili solo da expertise eccezionale).
- Non promuovere un'IPOTESI a testo definitivo qui: scrivi un capitolo `.tex` solo dopo che il contenuto corrispondente è CONFERMATO in `docs/`.
