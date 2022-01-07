# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1

```ruby
#include <stdio.h>
#include <string.h>

#include "module2.h"
#include "utils.h"
```

```ruby
void transcription() {

    char path_input[30];
    //appel la fonction qui demande à lutilisateur le nom de son fichier
    get_path_from_user(path_input);

    char sequence[10000];

    //appel la fonction qui va extraire la séquence et la mettre dans un tableau
    extract_sequence(path_input, sequence);

    int taille_adn = strlen(sequence); // stocke la taille de la séquence
    char arn[taille_adn +1]; // stocke la séquence ARN
    char nom_fichier[]= "sequence_arn.fasta";

    // condition codon initiation ATG et la taille est divisible par 3
    if ( taille_adn % 3 == 0 && ( strncmp("ATG",sequence,3) == 0 ))  {
    
        for (int j=0 ; j<taille_adn ; j++) {
            // si on a une Thymine on remplace par une Uracile
            if (sequence[j] == 'T') {
                arn[j] = 'U';
            } else {
                arn[j]=sequence[j];
            }
        }
        arn[taille_adn]='\0';
    } else {
        printf("Vérifiez que la séquence commence par un codon d'initiation et qu'elle soit divisible par 3. \n");
        printf("Rentrez de nouveau un fichier. \n");
        transcription();
    }
    // appel la fonction qui écrit dans un fichier
    save_sequence(nom_fichier, arn);
    
}
```
