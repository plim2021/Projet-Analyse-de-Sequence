# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

#ifndef PROJET_YANCLAPAU_H 
#define PROJET_YANCLAPAU_H

#include <stdio.h>
#include <stdlib.h>

```
// Structure
typedef struct AcideAmine {
    int polarite ; 
    char nom ;
} AcideAmine ;
```

```
// Fonctions 
void affichage_menu (){
    // fonction permettant d'afficher le menu des commandes proposées
    printf("---Menu---\n");
    printf("1. Recherche de la séquence codante de taille maximale\n");
    printf("2. Transcription d'une séquence d'ADN en séquence ARN\n");
    printf("3. Traduction d'une séquence codante en séquence protéique\n");
    printf("4. Calcul du score d'identité entre deux séquences\n");
    printf("5. Calcul du score de similarité de polarité entre deux séquences protéiques\n");
    printf("6. Recherce d'une séquence consensus à partir d'un alignement muliple\n");
    printf("7. Recherche de la plus grande sous-chaîne de polarité commune à 2 séquences protéiques\n");
    
}
```

#endif
