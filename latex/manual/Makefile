.PHONY: all clean

LATEX ?= pdflatex

all: main.pdf

clean:
	latexmk -C

%.pdf: %.tex
	latexmk --interaction=nonstopmode --pdf --pdflatex=$(LATEX) $<
