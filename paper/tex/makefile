#
# tex makefile by Corey Tessler (corey.tessler@wayne.edu)
#
.PHONY: all
BASE=main
TOP=$(BASE).pdf

BIBS=$(wildcard *.bib)
TEX=$(wilcdard *.tex)
PDFS=$(TOP)
VER=$(shell git rev-parse --short HEAD)
TMP=aux

all: $(TOP)

$(TOP): export TEXINPUTS=../lipics-v2018-authors:
$(TOP): $(BASE).tex $(BIBS) | $(TMP)	# Bar says order only target
	pdflatex -output-directory=$(TMP) -output-format=pdf ./$<
	cp $(TMP)/$(TOP) .

$(TMP):
	mkdir -p $@

clean:
	-rm -rf *.bbl $(TOP) $(TMP)
