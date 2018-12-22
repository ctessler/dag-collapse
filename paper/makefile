#
# LateX makefile by Corey Tessler (corey.tessler@wayne.edu)
#
.PHONY: all svg plot tex
BASE=$(shell basename ${PWD})

TOP=$(BASE).pdf

BIBS=$(wildcard *.bib)
TEX=$(wilcdard *.tex)
PDFS=$(TOP)
VER=$(shell git rev-parse --short HEAD)

all: $(TOP)
	mv tex/main.pdf $(TOP)
	cp $(TOP) $(TOP:.pdf=-$(VER).pdf)

$(TOP): tex
	$(MAKE) -C tex $(opt)

#
# tex/ directory
#  add the svg or plot directories once files are placed there
#  tex: svg plot
tex:

# svg/ directory
#    SVG files that must be *made* before they are included in the paper.
svg:
	$(MAKE) -C svg $(opt)
# plot/ directory
#    PLOTs that must be *made* before they are included in the paper
plot:
	$(MAKE) -C plot $(opt)

clean: opt=clean
clean: svg plot tex
clean:
	-rm -f $(BASE)*.pdf
