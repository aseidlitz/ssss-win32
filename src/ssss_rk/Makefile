#all: ssss-split ssss-combine ssss.1 ssss.1.html
all: ssss-split ssss-combine
	
ssss-split: ssss.c
	gcc -W -Wall -O2 -I/usr/local/include -L/usr/local/lib randomkit.o -o ssss-split.exe ssss.c -lgmp
	strip ssss-split.exe

ssss-combine: ssss-split
	ln -f ssss-split.exe ssss-combine.exe


#ssss.1: ssss.manpage.xml
#	xmltoman ssss.manpage.xml > ssss.1

#ssss.1.html: ssss.manpage.xml
#	xmlmantohtml ssss.manpage.xml > ssss.1.html

clean:
	rm -rf ssss-split.exe ssss-combine.exe ssss.1 ssss.1.html
