# Makefile for GNUmake

SHELL = /bin/sh
MAKE  = gmake
LN    = /usr/bin/ln

THE_DIR = .
PS_DIR  = $(THE_DIR)
PDF_DIR = $(THE_DIR)
TEX_DIR = $(THE_DIR)
DVI_DIR = $(THE_DIR)

# name of LaTeX input file
MAIN = poster

all : printable 

printable : pdf

SUFFIXES : .tex .eps .ps .pdf .dvi 

.PHONY : all clean clean_all ps dvi \
         clean_dvi clean_ps clean_pdf \
         clean_tex_files

clean : clean_special clean_tex_files

clean_all : clean_special clean_tex_files \
	clean_ps clean_pdf clean_dvi

clean_special :
	find ./ -name "*~" -exec $(RM) \{\} \;
	find ./ -name "*.backup" -exec $(RM) \{\} \;
	find ./ -name "cifs*" -exec $(RM) \{\} \;
	find ./ -name "*.aux" -exec $(RM) \{\} \;

clean_ps : 	
	@$(RM) $(MAIN).ps

clean_pdf : 	
	@$(RM) $(MAIN).pdf

clean_dvi : 	
	@$(RM) $(MAIN).dvi

clean_tex_files : 
	@$(RM) $(MAIN).aux
	@$(RM) $(MAIN).bbl
	@$(RM) $(MAIN).blg
	@$(RM) $(MAIN).log
	@$(RM) $(MAIN).lof
	@$(RM) $(MAIN).lot
	@$(RM) $(MAIN).nav
	@$(RM) $(MAIN).out
	@$(RM) $(MAIN).snm
	@$(RM) $(MAIN).toc  

ps : $(MAIN).ps

pdf : $(MAIN).pdf

$(MAIN).ps : $(MAIN).dvi 
	dvips $< -o $(PS_DIR)/$(notdir $(@)) 

$(MAIN).pdf : clean_pdf
	pdflatex $(MAIN).tex
	pdflatex $(MAIN).tex

dvi : $(MAIN).dvi

$(MAIN).dvi :
	latex $(MAIN).tex
	latex $(MAIN).tex &&\
	dvips $*.dvi -o $@

# end
