PROJ = planches

help:
	echo "clean,pdflatex,debug,fast,show,full,fullbib"

clean:
	touch debuglog
	\rm debuglog
	cp $(PROJ).tex bak_$(PROJ).tex
	mkdir hunhun
	mv $(PROJ).tex hunhun/$(PROJ).tex
	touch $(PROJ).toto
	\rm $(PROJ).*
	mv hunhun/$(PROJ).tex $(PROJ).tex 
	rmdir hunhun        

pdflatex: 
	pdflatex $(PROJ).tex

debug:
	make clean
	touch debuglog
	\rm debuglog
	make pdflatex > debuglog &
	watch tail -n 30 debuglog

fast:
	make pdflatex | grep [Ww]arning

show:
	make fast
	acroread $(PROJ).pdf &

full:
	make clean
	make pdflatex > /dev/null 
	make pdflatex > /dev/null
	acroread $(PROJ).pdf &

fullbib:
	make clean
	make pdflatex 
	bibtex $(PROJ)
	make pdflatex
	make pdflatex
	acroread $(PROJ).pdf &

#pdf: $(PROJ).tex *.tex
#	pdflatex $(PROJ).tex
#	bibtex $(PROJ)
#	pdflatex $(PROJ).tex 
#	acroread $(PROJ).pdf

#ps: $(PROJ).dvi
#	dvips -t letter $(PROJ).dvi
