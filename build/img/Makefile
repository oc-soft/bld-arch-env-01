top_srcdir = ../..
srcdir = $(top_srcdir)/img
abs_top_srcdir = $(abspath $(top_srcdir))
abs_srcdir = $(abspath $(srcdir))

LATEX = lualatex
KPSEWHICH = kpsewhich
TEXINPUTS = $(abs_srcdir)//:$(abs_top_srcdir):$(DEFAULT_TEXINPUTS)
DEFAULT_TEXINPUTS := $(shell kpsewhich -var-value=TEXINPUTS)
PDF_FILES = hw-img.pdf \
	screen-img.pdf \
	hw-os.pdf \
	storage-part.pdf \
	linux-fs.pdf \
	lvm.pdf \
	lvm-usecase.pdf \
	hw-fm-sw.pdf \
	ipxe-http-page.pdf \
	archlinux-logo-dark-scalable.pdf \
	aiopcwa-internal-1.pdf \
	sw-requirement.pdf \
	sw-requirement-res-1.pdf \
	sw-requirement-res-2.pdf \
	sw-requirement-res-3.pdf \
	sw-requirement-res-4.pdf
 
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

linux_fs_pdf_SOURCES = \
	linux-fs.tex

lvm_pdf_SOURCES = \
	lvm.tex

lvm_uscase_pdf_SOURCES = \
	lvm-usecase.tex 
	

hw_fm_sw_pdf_SOURCES = \
	hw-fm-sw.tex \
	custom-color-def.tex	

ipxe_http_page_pdf_SOURCES = \
	ipxe-http-page.tex \
	ipxe-http-page.png

archlinux_logo_dark_scalable_pdf_SOURCES = \
	archlinux-logo-dark-scalable.svg \

aiopcwa_internal_1_pdf_SOURCES = \
	aiopcwa-internal-1.jpg

sw_requirement_pdf_SOURCES = \
	sw-requirement.tex \
	sw-requirement-res-1.pdf

sw_requirement_res_1_pdf_SOURCES = \
	sw-requirement-res-1.tex

sw_requirement_res_2_pdf_SOURCES = \
	sw-requirement-res-2.tex

sw_requirement_res_3_pdf_SOURCES = \
	sw-requirement-res-3.tex

sw_requirement_res_4_pdf_SOURCES = \
	sw-requirement-res-4.tex


vpath %.tex $(srcdir) $(top_srcdir)
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

linux-fs.pdf : $(linux_fs_pdf_SOURCES)

lvm.pdf : $(lvm_pdf_SOURCES)

lvm-usecase.pdf : $(lvm_usecase_pdf_SOURCES)

hw-fm-sw.pdf : $(hw_fm_sw_pdf_SOURCES)

ipxe-http-page.pdf : $(ipxe_http_page_pdf_SOURCES)

archlinux-logo-dark-scalable.pdf : $(archlinux_logo_dark_scalable_pdf_SOURCES)

aiopcwa-internal-1.pdf : $(aiopcwa_internal_1_pdf_SOURCES)

sw-requirement.pdf: $(sw_requirement_pdf_SOURCES) 

sw-requirement-res-1.tex: $(sw_requirement_res_1_pdf_SOURCES)

sw-requirement-res-2.tex: $(sw_requirement_res_2_pdf_SOURCES)

sw-requirement-res-3.tex: $(sw_requirement_res_3_pdf_SOURCES)

sw-requirement-res-4.tex: $(sw_requirement_res_4_pdf_SOURCES)

.PHONY: all clean create-pdf pdf-doc
.SUFFIXES: .jpg .svg .tex .pdf

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

.svg.pdf:
	rsvg-convert -o $(@F) $<

.jpg.pdf:
	magick convert $< $@ 

# vi: se ts=4 sw=4 noet:
