#
# Plot Makefile by Corey Tessler (corey.tessler@wayne.edu)
#
PLOTS=$(wildcard *.plot)
TEXS=$(PLOTS:.plot=.tex)
PDFS=$(PLOTS:.plot=.pdf)

all: $(PDFS) | pdfs
	mkdir -p pdfs
	-rm -f *eps-converted*.pdf
	-cp *.pdf pdfs/.

pdfs:
	mkdir -p pdfs

%.tex : %.plot 
	gnuplot -e "set output '$@'" $<

%.pdf : %.tex
	latexmk -pdf $<

fetch:
	@echo "Must set DATADIR to fetch"
	test -n "$(DATADIR)"
	@echo "DATADIR is set to $(DATADIR)"
	rsync -av --progress $(DATADIR)/*.plot .
	rsync -av --progress $(DATADIR)/*.tex .
	mkdir -p data
	rsync -av --progress $(DATADIR)/*.dat data/.

unfetch: clean
	@echo "Removing all plots"
	-rm -f *.plot
	@echo "Removing all data"
	-rm -f data/*.dat
	@echo "Removing all tex"
	-rm -f *.tex

clean:
	-rm -f *.eps *.dvi *.aux *.log *.fls *.pdf *.fdb_latexmk
	-rm -rf pdfs
	@echo done
