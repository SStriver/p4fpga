P4FILE=p4src/simple_router.p4
CONNECTALFLAGS += -D PARSER=Parser
CONNECTALFLAGS += -D DEPARSER=Deparser
CONNECTALFLAGS += -D MATCHTABLE=Control
CONNECTALFLAGS += -D TYPEDEF=StructDefines
CONNECTALFLAGS += -D NUM_RXCHAN=1
CONNECTALFLAGS += -D NUM_TXCHAN=1
CONNECTALFLAGS += -D NUM_HOSTCHAN=1
CONNECTALFLAGS += -D STREAM
CONNECTALFLAGS += -m matchtable_model.cpp

CONNECTALFLAGS += --bsvpath=generatedbsv
#CPPFILES = $(P4FPGADIR)/cpp/main.cpp $(SONICDIR)/sw/lpcap.c app_init.cpp
CPPFILES = main.cpp $(SONICDIR)/sw/lpcap.c app_init.cpp

build:
	p4fpga -o generatedbsv --p4-14 -v --top4 Evaluator -Tfcontrol:1,fparser:1,table:1 $(P4FILE)

compile:
	make build.bluesim -j8

run-thru:
	(cd bluesim; ./bin/ubuntu.exe -p ../${T} -r ${R} -n ${N})

include ../Makefile.common
BSVFILES += generatedbsv/ConnectalTypes.bsv
BSVFILES += $(SONICDIR)/hw/bsv/DbgDefs.bsv
