# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

#include "projet.h"

```ruby
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
// définition des acides aminés
AcideAmine Cysteine;
Cysteine.nom ='C';
Cysteine.polarite=0;

AcideAmine Tyrosine;
Tyrosine.nom='Y';
Tyrosine.polarite=0;

AcideAmine Threonine;
Threonine.nom='T';
Threonine.polarite=0;

AcideAmine Serine;
Serine.nom='S';
Serine.polarite=0;

AcideAmine Asparagine;
Asparagine.nom='N';
Asparagine.polarite=0;

AcideAmine Glutamine;
Glutamine.nom='Q';
Glutamine.polarite=0;

AcideAmine Histidine;
Histidine.nom = 'H';
Histidine.polarite=0;

AcideAmine Lysine;
Lysine.nom='K';
Lysine.polarite=0;

AcideAmine Arginine:
Arginine.nom='R';
Arginine.polarite=0;

AcideAmine Aspartate;
Aspartate.nom='D';
Aspartate.polarite=0;

AcideAmine Glutamate;
Glutamate.nom='E';
Glutamate.polarite=0;

AcideAmine Phenylalanine;
Phenylalanine.nom='F';
Phenylalanine.polarite=1;

AcideAmine Alanine;
Alanine.nom='A';
Alanine.polarite=1;

Acide Leucine;
Leucine.nom='L';
Leucine.polarite=1;

AcideAmine Isoleucine;
Isoleucine.nom='I';
Isoleucine.polarite=1;

AcideAmine Methionine;
Methionine.nom='M';
Methionine.polarite=1;

AcideAmine Tryptophane;
Tryptophane.nom='W';
Tryptophane.polarite=1;

AcideAmine Proline;
Proline.nom='P';
Proline.polarite=1;

AcideAmine Glycine;
Glycine.nom='G';
Glycine.polarite=1;

AcideAmine Valine;
Valine.nom='V';
Valine.polarite=1;
```

```ruby
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
            printf(">> Vous avez choisi : Recherche de la séquence codante de taille maximale.\n");
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
        default:
            printf(">> Veuillez choisir une option.\n";
            break;
    }
    return 0;
}
```
