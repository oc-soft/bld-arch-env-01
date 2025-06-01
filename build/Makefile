top_srcdir = ..
abs_top_srcdir = $(abspath $(top_srcdir))

LATEX = lualatex
KSEWHICH = kpsewhich
TEXINPUTS = $(abs_top_srcdir)//:$(DEFAULT_TEXINPUTS)
DEFAULT_TEXINPUTS := $(shell kpsewhich -var-value=TEXINPUTS)
PDF_FILES = arch-install-pre-1.pdf \
	arch-install-note-1.pdf 

SUBDIRS = img
vpath %.tex $(top_srcdir) 
vpath %.pdf ./ ./img/

all: pdf-doc


pdf-doc: create-pdf 
	cp $(PDF_FILES) $(top_srcdir)

create-pdf: img-pdf $(PDF_FILES) 

arch-install-pre-1.pdf : arch-install-pre-1.tex arch-install-1.tex hw-img.pdf
arch-install-note-1.pdf : arch-install-note-1.tex arch-install-1.tex

clean:
	rm -f *.pdf *.out *.log *.log *.aux *.snm *.nav *.toc

img-pdf:
	cd img && $(MAKE) $(MFLAGS) 

.PHONY: all clean create-pdf pdf-doc
.SUFFIXES: .tex .pdf

.tex.pdf:
	@res=0; \
	for idx in seq 2; do \
		TEXINPUTS=$(TEXINPUTS) $(LATEX) $<; \
		res=$$?; \
		if [ $$res -ne 0 ]; then \
			break; \
		fi \
	done; \
	exit $$res
# vi: se ts=4 sw=4 noet:
