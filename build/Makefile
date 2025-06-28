top_srcdir = ..
abs_top_srcdir = $(abspath $(top_srcdir))

LATEX = lualatex
UPLATEX = uplatex
DVIPDFM = dvipdfmx
KPSEWHICH = kpsewhich
TEXINPUTS = $(abs_top_srcdir)//:$(DEFAULT_TEXINPUTS)
DEFAULT_TEXINPUTS := $(shell kpsewhich -var-value=TEXINPUTS)
PDF_FILES = arch-install-pre-1.pdf \
	arch-install-note-1.pdf \
	movie-resources.pdf

DVI_FILES = \
	movie-resources.dvi

arch_install_common_SOURCES = \
	arch-install-common-1.tex \
	arch-install-1.tex \
	custom-color-def.tex \
	hw-img.pdf \
	hw-fm-sw.pdf \
	ipxe-http-page.pdf
	
arch_install_pre_SOURCES = $(arch_install_common_SOURCES) \
	arch-install-pre-1.tex

arch_install_note_SOURCES = $(arch_install_common_SOURCES) \
	arch-install-note-1.tex

movie_resources_SOURCES = \
	movie-resources.tex \
	custom-color-def.tex \
	archlinux-logo-dark-scalable.pdf \
	hw-img.pdf \
	aiopcwa-internal-1.pdf
	

SUBDIRS = img
vpath %.tex $(top_srcdir) 
vpath %.pdf ./ ./img/

all: pdf-doc


pdf-doc: create-pdf 
	cp $(PDF_FILES) $(top_srcdir)


create-pdf: img-pdf $(PDF_FILES) 

create-pdf: img-pdf $(DVI_FILES)

arch-install-pre-1.pdf : $(arch_install_pre_SOURCES)
arch-install-note-1.pdf : $(arch_install_note_SOURCES)
movie-resources.pdf: movie-resources.dvi
movie-resources.dvi: $(movie_resources_SOURCES)

clean:
	rm -f *.pdf *.out *.log *.log *.aux *.snm *.nav *.toc

img-pdf:
	cd img && $(MAKE) $(MFLAGS) 

.PHONY: all clean create-pdf create-dvi pdf-doc
.SUFFIXES: .tex .pdf .dvi

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

.tex.dvi:
	@res=0; \
	for idx in seq 2; do \
		TEXINPUTS=$(TEXINPUTS) $(UPLATEX) -kanji=utf8 -no-guess-input-enc $<; \
		res=$$?; \
		if [ $$res -ne 0 ]; then \
			break; \
		fi \
	done; \
	exit $$res

.dvi.pdf:
	TEXINPUTS=$(TEXINPUTS) $(DVIPDFM) $<

# vi: se ts=4 sw=4 noet:
