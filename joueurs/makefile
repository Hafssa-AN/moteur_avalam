all: dep install

# Pour activer le mode debugage, il faut définir __DEBUG__
debug: DEBUG=-D'__DEBUG__'
debug: dep install

dep:
	cd ../libavalam; make
	cd ../libjoueur; make

LIB=-L../tournoi/lib
INC=-I../include

SRC=humain1.c humain2.c joueur1.c joueur2.c joueur3.c joueur4.c joueur5.c 9AvalamCorp.c
EXE=$(SRC:.c=.exe)
STATIC=$(SRC:.c=.static)

exe: $(EXE)
static: $(STATIC)

install: dep exe
	cp $(EXE) ../tournoi/bin

%.exe : %.c
	gcc $(DEBUG) $(LIB) $(INC) $< -o $@ -ljoueur -lpthread -lavalam

%.static : %.c
	gcc $(DEBUG) -static $(LIB) $(INC) $< -o $@ -ljoueur -lpthread -lavalam

clean: 
	rm -rf $(EXE) $(STATIC)
	cd ../tournoi/bin; rm -rf $(EXE) $(STATIC)

cleanall: clean
	cd ../libavalam; make clean
	cd ../libjoueur; make clean
