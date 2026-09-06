# Build file for the IAsLab PDG thesis document (copied from ../latex/Makefile,
# the module that owns this template — see ../latex/README.md). Drives
# latexmk, which handles the pdflatex/bibtex rerun dance automatically
# (needed for cross-references, ToC, and the APA/natbib bibliography to
# converge).
#
# All generated files land in OUTDIR, never in the source tree — per the
# repo-wide rule in ../CLAUDE.md.

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
