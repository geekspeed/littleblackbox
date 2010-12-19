CC=gcc
OPTS=-static -Wall
OPENSSL=openssl
LIBPCAP=libpcap
SQLITE=sqlite
LDFLAGS=-lsqlite3 -lssl -lcrypto -lpcap -ldl -lpthread
INC=-I./$(OPENSSL)/include -I./$(LIBPCAP)/include -I./$(SQLITE)/include
LIB=-L$(OPENSSL)/lib -L$(LIBPCAP)/lib -L$(SQLITE)/lib
TARGET=littleblackbox

$(TARGET): littleblackbox.o
	$(CC) $(OPTS) main.c -o ../bin/$(TARGET) *.o $(INC) $(LIB) $(LDFLAGS) 

littleblackbox.o: $(SQLITE) common.o sql.o certs.o network.o
	$(CC) $(OPTS) $(INC) -c littleblackbox.c

common.o: $(OPENSSL)
	$(CC) $(OPTS) $(INC) -c common.c

network.o: $(OPENSSL) $(LIBPCAP)
	$(CC) $(OPTS) $(INC) -c network.c

certs.o: $(OPENSSL)
	$(CC) $(OPTS) $(INC) -c certs.c

sql.o: $(SQLITE)
	$(CC) $(OPTS) $(INC) -c sql.c

$(OPENSSL):
	(mkdir $(OPENSSL) && tar -zxvf openssl*.tar.gz --directory=$(OPENSSL))
	(cd $(OPENSSL)/openssl* && ./config --prefix=$(shell pwd)/$(OPENSSL) && make && make install)

$(LIBPCAP):
	(mkdir $(LIBPCAP) && tar -zxvf libpcap*.tar.gz --directory=$(LIBPCAP))
	(cd $(LIBPCAP)/libpcap* && ./configure --prefix=$(shell pwd)/$(LIBPCAP) && make && make install)

$(SQLITE):
	(mkdir $(SQLITE) && tar -zxvf sqlite*.tar.gz --directory=$(SQLITE))
	(cd $(SQLITE)/sqlite* && ./configure --prefix=$(shell pwd)/$(SQLITE) && make && make install)

install:
	cp $(TARGET) ../bin/$(TARGET)

clean:
	rm -f *.o

distclean: clean
	rm -rf $(OPENSSL) $(LIBPCAP) $(SQLITE)
