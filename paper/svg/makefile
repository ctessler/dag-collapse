#
# Scaled Vector Graphics Makefile by Corey Tessler (corey.tessler@wayne.edu)
#
SVGS = $(wildcard *.svg)
EPS = $(wildcard *.eps)
PDFS = $(patsubst %.svg,%.pdf_tex,$(SVGS))
PDFS += $(patsubst %.eps,%.pdf,$(EPS))

all: $(PDFS)

%.pdf: %.eps
	epstopdf $^

%.pdf_tex: %.svg
	inkscape $^ -z -D --export-latex --export-pdf=$(^:.svg=.pdf)

clean:
	rm -rf *.pdf *.pdf_tex
