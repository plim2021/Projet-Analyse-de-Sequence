# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

#include "projet.h"

```
// Pour colorer l'affichage dans le terminal:
#define RED   "\x1B[31m"
#define GRN   "\x1B[32m"
#define YEL   "\x1B[33m"
#define BLU   "\x1B[34m"
#define MAG   "\x1B[35m"
#define CYN   "\x1B[36m"
#define WHT   "\x1B[37m"
#define RESET "\x1B[0m"
```

```
int main (int argc, char *argv[]){

    // Affichage du menu 
    affichage_menu();

    // Choix de l'utilisateur
    int choix;
    printf("Quel est votre choix ? Tapez le numéro de la commande désirée, par exemple : 1 \n");
    scanf("%d", &choix);
    printf("\n");

    switch(choix){
        case 1: 
            printf(">> Vous avez choisi : Recherche de la séquncce codante de taille maximale.\n");
            break;
        case 2:
            printf(">> Vous avez choisi : Transcription d'une séquence d'ADN en séquence ARN.\n");
            break;
        case 3:
            printf(">> Vous avez choisi : Traduction d'une séquence codante en séquence protéique.\n");
            break;
        case 4:
            printf(">> Vous avez choisi : Calcul du score d'identité entre deux séquences.\n");
            break;
        case 5:
            printf(">> Vous avez choisi : Calcul du score de similarité de polarité entre deux séquences protéiques.\n");
            break;
        case 6:
            printf(">> Vous avez choisi : Recherce d'une séquence consensus à partir d'un alignement muliple.\n");
            break;
        case 7:
            printf(">> Vous avez choisi : Recherche de la plus grande sous-chaîne de polarité commune à 2 séquences protéiques.\n");
            break; 
    }
    return 0;
}
```
