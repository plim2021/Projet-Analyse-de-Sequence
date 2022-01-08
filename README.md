# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
CC = gcc
CFLAGS=-Wall

all : analyse

analyse : module1.o module2.o module3.o module4.o module5.o executable.o utils.o
	$(CC) module1.o module2.o module3.o module4.o module5.o executable.o utils.o -o analyse
	
utils.o : utils.c utils.h
	$(CC) -c utils.c $(CFLAGS)

module1.o : module1.c module1.h utils.o
	$(CC) -c module1.c $(CFLAGS)

module2.o : module2.c module2.h utils.o
	$(CC) -c module2.c $(CFLAGS)

module3.o : module3.c module3.h utils.o
	$(CC) -c module3.c $(CFLAGS)

module4.o : module4.c module4.h utils.o
	$(CC) -c module4.c $(CFLAGS)

module5.o : module5.c module5.h utils.o
	$(CC) -c module5.c $(CFLAGS)

executable.o : executable.c module1.h module2.h module3.h module4.h module5.h utils.o
	$(CC) -c executable.c $(FLAGS)

clean:
	rm -f *.o

mrproper: clean
	rm -f analyse
```
