# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby

#include "module2.h"
#include "utils.h"

void transcription() {

    // Procédure qui demande à l utilisateur de fournir une séquence ADN codante 
    // et qui écrit dans un nouveau fichier la transcription de cette séquence

    // L utilisateur entre le nom du fichier
    char path_input[30];
    get_path_from_user(path_input);

    // Extraction de la séquence dans la variable séquence
    char sequence[10000];
    extract_sequence(path_input, sequence);


    int taille_adn = strlen(sequence); // stocke la taille de la séquence
    char arn[taille_adn +1]; // stocke la séquence ARN
    char nom_fichier[]= "sequence_arn.fasta";

    // Conditions : présence du codon d initiation et la taille de séquence est divisible par 3
    if ( taille_adn % 3 == 0 && (strncmp("ATG",sequence,3)==0) )  {
    
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
        
        printf(RED " ERREUR : Vérifiez que la séquence commence par un codon d initiation et qu'elle soit divisible par 3.\n");
        printf("\n");

        // On redemande à l utilisateur de rentrer un autre fichier 
        transcription();

    }
    
    // Sauvegarde de la séquence ARN
    save_sequence(nom_fichier, arn);
}
```
