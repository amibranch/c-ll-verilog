CC = g++
BISON = bison
FLEX = flex
INCLUDE = .
CFLAGS = -I$(INCLUDE) -lLLVM-16 `llvm-config --cppflags` `llvm-config --ldflags` -std=c++17 # -Wall
BISONFLAGS = -d -v --report-file=bisonreport.output
BISONSRCS = parser.y
FLEXSRCS = scanner.l
ALLSRCS = parser.c scanner.c SymbolTable.cc Type.cc 

TARGETBISON = parser.c
TARGETFLEX = scanner.c
TARGETALL = parser

bison: $(TARGETBISON)
$(TARGETBISON): $(BISONSRCS)
	$(BISON) -o $(TARGETBISON) $(BISONSRCS) $(BISONFLAGS)

flex: $(TARGETFLEX)
$(TARGETFLEX): $(FLEXSRCS)
	$(FLEX) -o $(TARGETFLEX) $(FLEXSRCS)

all: $(TARGETALL)
$(TARGETALL): $(ALLSRCS)
	$(CC) $(CFLAGS) $(INCLUDES) $(ALLSRCS) -o $(TARGETALL)

clean:
	$(RM) $(TARGETBISON) $(TARGETFLEX) $(TARGETALL) *.output
