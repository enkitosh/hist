# test/Makefile
# testing for histogram 

## None of this is relevant, just wanted to get the initial commit up
SHELL=		/bin/sh
INSTALL=	/usr/local/lib
AR=			ar
AROPTS=		rcs
LIB=		hist

SRC=		hist.c
OBJ=		$(SRC:.c=.o)
VERSION=	0.0.1a
OPTS=		-DVERSION=\"$(VERSION)\" #-DNDEBUG

CC =		gcc
CFLAGS=		-std=c99 -pedantic-errors -g -Wall -Werror -O1 -Wstack-protector -fstack-protector-all

.SUFFIXES: .c .o

all: archive 

# Create an archive because shared libraries are slower/more difficult for me
# to conceptualize :P
archive: $(OBJ)
	$(AR) $(AROPTS) lib$(LIB).a $(OBJ)

.c.o:
	$(CC) -c $(OPTS) $(CFLAGS) $<


install:
	@echo installing executable to $(INSTALL)
	@${SUDO} cp $(LIB) $(INSTALL)

clean:
	@echo Removing object files
	@rm -f $(LIB) *.o $(.CURDIR)/*.BAK 

.PHONY: clean all
