CC=gcc
RC=windres
LINK=dllwrap
CXXFLAGS= -c -O3
SBFLAGS= -Wl,--enable-stdcall-fixup
IMPLIB=libcrypto.a
IMPOBJ=stdc.o
LINKOBJ=fileio.o lzssdec.o modxmlparser.o r2sapi.o r2sapi.res
BIN=r2sapi.dll


all:$(BIN)

clean:
	del $(BIN) $(LINKOBJ)

cleanobj:
	del $(LINKOBJ)

$(BIN):$(LINKOBJ)
	$(LINK) -s -o $(BIN) $(LINKOBJ) $(IMPOBJ) $(IMPLIB) --def r2sapi.def --output-lib libr2sapi.a

fileio.o:../r2pak/fileio.cpp
	$(CC) ../r2pak/fileio.cpp $(CXXFLAGS) -D_USRDLL

lzssdec.o:../r2pak/lzssdec.cpp
	$(CC) ../r2pak/lzssdec.cpp $(CXXFLAGS) -D_USRDLL

modxmlparser.o:../../../modxmlparser.cpp
	$(CC) ../../../modxmlparser.cpp $(CXXFLAGS)

r2sapi.o:r2sapi.cpp
	$(CC) r2sapi.cpp $(CXXFLAGS)

r2sapi.res:r2sapi.rc
	$(RC) r2sapi.rc -o r2sapi.res -O coff
