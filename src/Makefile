CC = gcc
CFLAGS += -O2 -Wall -Wno-strict-aliasing
# CFLAGS += -ggdb
CFLAGS += -I../libamievent -I../libamievent/libc-jss -I../pdu
LDFLAGS = -lev -lm

OBJ += ../libamievent/libc-jss/ini/ini.o
OBJ += ../libamievent/libc-jss/netsocket.o
OBJ += ../libamievent/libc-jss/logger.o
OBJ += ../libamievent/libc-jss/misc.o
OBJ += ../libamievent/ami.o
OBJ += pdu/charset.o
OBJ += pdu/compat.o
OBJ += pdu/pdu.o
OBJ += option.o
OBJ += conf.o
OBJ += pnv.o
OBJ += verbose.o
PROGS=sms phone_number_validator pnv_json

# take version from GIT
GIT_VERSION = $(shell sh -c 'git describe --abbrev=6 --dirty --always --tags')
CFLAGS += -DVERSION=\"$(GIT_VERSION)\"

.PHONY: all
all: $(patsubst %, %.o, $(PROGS)) $(OBJ) $(PROGS)

%: %.o $(OBJ)
	gcc $(CFLAGS) -o $@ $< $(OBJ) $(LDFLAGS)

clean:
	rm -f *.o $(OBJ) $(PROGS)

