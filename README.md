# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

#include "utils.h"
#include "module1.h"
#include "module2.h"
#include "module3.h"
#include "module4.h"
#include "module5.h"

```ruby
int main (int argc, char *argv[]){

    // Affichage du menu 
    affichage_menu();

    // Choix de l'utilisateur
    int choix;
    printf(CYN ">> Quel est votre choix ? Tapez le numéro de la commande désirée, par exemple : 1.\n"RESET);
    scanf("%d", &choix);
    printf("\n");

    switch(choix){
        case 1: 
            printf(BLU">> Vous avez choisi : Recherche de la séquence codante de taille maximale.\n"RESET);
            recherchetaillemax();
            break;
        case 2:
            printf(BLU">> Vous avez choisi : Transcription d'une séquence d'ADN en séquence ARN.\n"RESET);
            transcription();
            break;
        case 3:
            printf(BLU">> Vous avez choisi : Traduction d'une séquence codante en séquence protéique.\n"RESET);
            traduction();
            break;
        case 4:
            printf(BLU">> Vous avez choisi : Calcul du score d'identité entre deux séquences.\n"RESET);
            score();
            break;
        case 5:
            printf(BLU">> Vous avez choisi : Calcul du score de similarité de polarité entre deux séquences protéiques.\n"RESET);
            score_polarite();
            break;
        case 6:
            printf(BLU">> Vous avez choisi : Recherce d'une séquence consensus à partir d'un alignement muliple.\n"RESET);
            printf(">> Le module 6 n'est pas disponible :(. \n");
            break;
        case 7:
            printf(">> Vous avez choisi : Recherche de la plus grande sous-chaîne de polarité commune à 2 séquences protéiques.\n");
            printf(">> Le module 7 n'est pas disponible :(. \n");
            break;
        default:
            printf(">> Veuillez choisir une option.\n");
            break;
    }
    return 0;
}
```
