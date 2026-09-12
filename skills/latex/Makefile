# Template build file for the IAsLab PDG thesis LaTeX project.
#
# Copy this Makefile (and .latexmkrc) into the actual LaTeX project folder
# once it exists. It drives latexmk, which handles the pdflatex/bibtex
# rerun dance automatically (needed for cross-references, ToC, and the
# APA/natbib bibliography to converge).
#
# All generated files land in OUTDIR, never in the source tree — per the
# repo-wide rule in ../../CLAUDE.md. Adjust OUTDIR if this project ends up
# nested deeper/shallower than one level under the repo root.

MAIN    = main
OUTDIR  = ../compiled-output/latex-build

.PHONY: all build watch clean open

all: build

build:
	mkdir -p $(OUTDIR)
	latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=$(OUTDIR) $(MAIN).tex

# Recompile automatically on save (needs a PDF viewer that auto-reloads).
watch:
	mkdir -p $(OUTDIR)
	latexmk -pdf -interaction=nonstopmode -pvc -outdir=$(OUTDIR) $(MAIN).tex

clean:
	latexmk -C -outdir=$(OUTDIR) $(MAIN).tex 2>/dev/null || true
	rm -rf $(OUTDIR)

open:
	xdg-open $(OUTDIR)/$(MAIN).pdf 2>/dev/null || open $(OUTDIR)/$(MAIN).pdf
