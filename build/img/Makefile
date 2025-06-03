top_srcdir = ../..
srcdir = $(top_srcdir)/img
abs_top_srcdir = $(abspath $(top_srcdir))
abs_srcdir = $(abspath $(srcdir))

LATEX = lualatex
KSEWHICH = kpsewhich
TEXINPUTS = $(abs_srcdir)//:$(DEFAULT_TEXINPUTS)
DEFAULT_TEXINPUTS := $(shell kpsewhich -var-value=TEXINPUTS)
PDF_FILES = hw-img.pdf screen-img.pdf hw-os.pdf storage-part.pdf
VPATH = $(srcdir)

hw_img_pdf_SOURCES = \
	hw-img.tex \
	aiopcwa-front-1.jpg \
	aiopcwa-back-1.jpg \
	aiopcwa-internal-1.jpg \
	aiopcwa-insert-usb-0.jpg \
	aiopcwa-insert-usb-1.jpg \
	aiopcwa-insert-usb-2.jpg

screen_img_pdf_SOURCES = \
	screen-img.tex \
	bios-display-1.jpg	

hw_os_pdf_SOURCES = \
	hw-os.tex

storage_part_pdf_SOURCES = \
	storage-part.tex

vpath %.tex $(srcdir) 
vpath %.pdf ./

all: pdf-doc

pdf-doc: create-pdf
	cp $(PDF_FILES) $(srcdir)

create-pdf: $(PDF_FILES) 

clean:
	rm -f *.pdf *.out *.log *.log *.aux *.snm *.nav *.toc

hw-img.pdf : $(hw_img_pdf_SOURCES)

screen-img.pdf : $(screen_img_pdf_SOURCES)

hw-os.pdf : $(hw_os_pdf_SOURCES)

storage-part.pdf : $(storage_part_pdf_SOURCES)

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
