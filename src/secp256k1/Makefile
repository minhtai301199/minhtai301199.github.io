
CC = gcc
CXX = @CXX@
AS = gcc
LD = gcc
CPP = gcc
CFLAGS = -m64 -g -O2 -I/usr/local/include -DARCH_LITTLE_ENDIAN=1 -DPREFER_FLOCK -Wall -fno-omit-frame-pointer --param allow-store-data-races=0 -Wno-deprecated-declarations -Wformat-extra-args -Wunused-but-set-variable -std=gnu89 -Wdate-time -D_POSIX_SOURCE -D_GNU_SOURCE -D_XOPEN_SOURCE=600  -Wno-unused-function
ASFLAGS = -m64  -DARCH_LITTLE_ENDIAN=1 -c 
LDFLAGS = -m64  -L/usr/local/lib -L/lib64  -lssl -lcrypto
YASM = /usr/bin/yasm
AR = ar
FIND = /usr/bin/find
RM = /bin/rm -f

IN = secp256k1.o

all: secp256k1.a
default: secp256k1.a

secp256k1.o: secp256k1.c
	$(CC) -DHAVE_CONFIG_H $(CFLAGS) -c secp256k1.c -o secp256k1.o

.PHONY: subdirs $(SUBDIRS)

subdirs: $(SUBDIRS)

$(SUBDIRS):
	$(MAKE) -C $@ all

secp256k1.a: $(SUBDIRS) secp256k1.o
	$(AR) -rs $@ $(IN)

clean:
	$(FIND) . -name \*.a -exec $(RM) {} \;
	$(FIND) . -name \*.o -exec $(RM) {} \;

distclean: clean
	$(RM) Makefile
