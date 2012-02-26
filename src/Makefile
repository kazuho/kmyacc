# Makefile for KM-yacc

BIN = /usr/local/bin
PARLIB = /usr/local/lib

INSTALL = install

#CC = gcc

#CFLAGS = -g -Wall -O -DDEBUG '-DPARSERBASE="/proj/lang/kmyacc-4.1.2/kmyacc"'
CFLAGS = -Wall -O2 '-DPARSERBASE="$(PARLIB)/kmyacc"'


OBJS = yacc.o grammar.o token.o lalr.o misc.o genparser.o compress.o
PROGRAM = kmyacc

all: $(PROGRAM)

$(PROGRAM): $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o $(PROGRAM)

clean:
	rm -f core *.bak *.o *.obj *~ $(PROGRAM) tokentest

depend:
	./genhead yacc yacc.c
	./genhead grammar grammar.c
	./genhead lalr lalr.c
	./genhead token token.c
	./genhead misc misc.c
	./genhead genparser genparser.c
	./genhead compress compress.c
	./makedepend $(DEFS) *.c


TOBJS = tokentest.o token.o misc.o
tokentest: $(TOBJS)
	$(CC) $(CFLAGS) $(TOBJS) -o tokentest


install: $(PROGRAM)
	$(INSTALL) -s $(PROGRAM) $(BIN)
	$(INSTALL) kmyacc.c.parser $(PARLIB)
	$(INSTALL) kmyacc.java.parser $(PARLIB)
	$(INSTALL) kmyacc.js.parser $(PARLIB)
	$(INSTALL) kmyacc.pl.parser $(PARLIB)



# DO NOT DELETE THIS LINE -- make depend depends on it.
compress.o: compress.c config.h common.h token.h yacc.h misc.h \
 grammar.h lalr.h compress.h
genparser.o: genparser.c config.h common.h token.h yacc.h misc.h \
 grammar.h lalr.h compress.h genparser.h
grammar.o: grammar.c config.h common.h yacc.h misc.h token.h \
 genparser.h grammar.h
lalr.o: lalr.c config.h common.h yacc.h misc.h lalr.h grammar.h
misc.o: misc.c config.h common.h yacc.h misc.h
token.o: token.c config.h common.h yacc.h token.h misc.h
tokentest.o: tokentest.c token.h
yacc.o: yacc.c config.h common.h misc.h token.h grammar.h lalr.h \
 genparser.h yacc.h
