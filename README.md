# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

#include "projet.h"

/* ***************************************************************************
*   Transcription d'une seq ADN en seq ARN  *
****************************************************************************/
void transcription(*adn) {
    // calculer la taille pour la condition divisible par 3
    int taille_adn = 0;
    int i = 0;
    while (adn[i] != " ") {
         taille_adn ++;
         i ++;
     }
    // condition codon initiation ATG et la taille est divisible par 3
    if (adn[0] == "A" && adn[1] == "T" && adn[0] == "G" && taille_adn % 3 == 0) {
        for (int j = 0; j < taille_adn; j++) {
            if (adn[j] == "T") {
                // si on a une Thymine on remplace par une Uracile
                adn[j] = "U";
            }
        }
    }
    // appel la fonction qui écrit dans un fichier
    save_sequence(chemin,*adn)
    FILE* fichier = NULL;
    <citation nom="Exécution"></citation>
    fichier = fopen("seq_ARN.txt", "w");
    if (fichier != NULL) {
        fputs(*adn, fichier);
        fclose(fichier);
    }
    return 0;
}
