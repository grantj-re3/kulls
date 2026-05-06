# Your BASIC language source text-file should be $(APP).bas, e.g. kulls_vice.bas
APP     = kulls_vice
SRCDIR  = ../src

all: $(APP).d64

$(APP).prg: $(SRCDIR)/$(APP).bas
	@echo "Building $(APP).prg from $(SRCDIR)/$(APP).bas using the 'petcat' BASIC tokenizer"
	petcat -w2 -l 2001 -f -o $(APP).prg -- $(SRCDIR)/$(APP).bas

$(APP).d64: $(APP).prg
	@echo "Building $(APP).d64 from $(APP).prg using the 'c1541' disk-image utility"
	c1541 -format "kulldisk,01" d64 $(APP).d64 -attach $(APP).d64 -write $(APP).prg $(APP)

run: all
	xvic -default -memory 24k -8 $(APP).d64 -keybuf "poke43,1:poke44,32:poke8192,0:new\nload\"$(APP)\",8\npoke32000,peek(45):poke32001,peek(46)\nrun\n"

clean:
	rm -f $(APP).prg $(APP).d64

