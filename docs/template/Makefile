PAPER=ae
TEX = $(wildcard *.tex)
#BIB = references.bib
#FIGS = $(wildcard figures/*.pdf figures/*.png figures/*.eps)

all: paper
default: paper

#	bibtex $(PAPER)
#	pdflatex $(PAPER).tex </dev/null >/dev/null
#	pdflatex $(PAPER).tex </dev/null
paper: $(TEX)
	pdflatex $(PAPER).tex </dev/null
	pdflatex $(PAPER).tex </dev/null >/dev/null
	@/bin/echo ""
	@/bin/echo "++++++++++++++++++++++++++++++++++++++++++++++++++++++++++"
	@/bin/echo "               ++++ ANY UNDEFINED REFERENCES ++++"
	-@grep -i undef $(PAPER).log || echo "No undefined references."
	@/bin/echo "                 ++++ ANY EMPTY REFERENCES ++++"
	-@egrep -i -n -e 'cite{ *}' -e 'ref{ *}' $(TEX) $(FIGS) || echo "No empty references."
	@/bin/echo "++++++++++++++++++++++++++++++++++++++++++++++++++++++++++"
	@/bin/echo ""

tidy:
	rm -f $(PAPER).aux $(PAPER).bbl $(PAPER).blg $(PAPER).brf $(PAPER).btx $(PAPER).log $(PAPER).out

clean: tidy
	rm -f *.aux *.bbl *.blg *.log *.out $(PAPER).pdf *~
