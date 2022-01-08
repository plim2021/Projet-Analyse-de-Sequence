# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <limits.h>
#include <string.h>

```ruby
// Constante

#define SIZE 10000 // taille maximale des séquences

// Affichage coloré

#define RED   "\x1B[31m" // pour les messages d'erreur
#define ORA   "\x1B[32m" // pour le menu
#define YEL   "\x1B[33m"
#define BLU   "\x1B[34m" // pour les messages
#define MAG   "\x1B[35m" 
#define CYN   "\x1B[36m" // pour les instructions
#define WHT   "\x1B[37m"
#define RESET "\x1B[0m"
```

```ruby
// Fonction qui affiche le menu des modules

void affichage_menu ();

// Fonctions dans utils.c

void get_path_from_user(char * path_input);

void extract_sequence(const char* path_input, char* sequence);

void save_sequence(const char* path_output, char* sequence);
```
