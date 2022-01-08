# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 


```ruby
#include "utils.h"
#include "module1.h"
```

```ruby
void recherchetaillemax() {

    // Procédure qui demande à l'utilisateur de fournir une séquence ADN au format FASTA
    // et qui recherche la séquence codante de taille maximale pour le brin sens et antisens

    // L'utilisateur entre le nom du fichier

    char path_input[30];
    get_path_from_user(path_input);

    // Extraction de la séquence
    char seq[SIZE];
    extract_sequence(path_input, seq);
    char nom_fichier[] = "seq_codante_max.fasta";

    // Calcul de la taille de la séquence entière
    int taille_seq_entiere = strlen(seq);

    // Variables stockeuses de la séquence codante la plus longue et de sa taille
    char seqcod_max[SIZE];
    seqcod_max[0]='Z'; // flag qui permet de savoir si on a trouvé une séquence codante
    int taille_seqcod_max = 0;

    // Indices
    int i = 0; // indice qui parcourt la séquence entière
    int n ; // indice qui parcourt la nouvelle séquence codante trouvée
    int c ; // indice qui parcourt la séquence codante trouvée 

    // Parcours pour chaque séquence codante trouvée
    int taille_seqcod; // indice qui parcourt la séquence codante, variable qui compte sa longueur
    char seq_cod[SIZE]; // variable qui stocke la séquence codante trouvée


    // Brin complémentaire

    int l = 0; // indice qui parcourt la séquence entière
    char seq_antisens[SIZE]; // variable qui stocke la séquence entière antisens

    while (l<taille_seq_entiere) {
        if (seq[l]=='A') {
            seq_antisens[l]='T';
        }
        if (seq[l]=='T') {
            seq_antisens[l]='A';
        }
        if (seq[l]=='G') {
            seq_antisens[l]='C';
        }
        if (seq[l]=='C') {
            seq_antisens[l]='G';
        }
        l++;
    }

    char anti2[SIZE]; //copie de seq_antisens

    // On copie seq_antisens dans anti2
    for ( i = 0 ; i < taille_seq_entiere ; i++ ){
        anti2[i] = seq_antisens[i] ; 
    }

    //On inverse la seq_antisens ( pour ne pas avoir à lire à l'envers )
    for ( i = 1 ; i < taille_seq_entiere ; i++ ){
        seq_antisens[i - 1] = anti2[taille_seq_entiere-i] ;
    }

    
    // Boucle qui cherche les séquences codantes dans le brin sens et antisens inversé 
    
    for ( i = 0 ; i < taille_seq_entiere ; i++ ){

        // On parcourt le brin sens

        // Codon d'initiation trouvé 

        if ( seq[i] == 'A' && seq[i+1] == 'T' && seq[i+2] == 'G' ) {

            // La taille de la séquence est initialisée à 0
            taille_seqcod = 0; 

            //On parcourt la nouvelle séquence trouvée 
            for (c = i; c < taille_seq_entiere ; c++ ) {


                // Si on trouve un codon stop 
                if ((seq[c] == 'T' && seq[c+1] == 'A' && seq[c+2] == 'A' ) || \
                    (seq[c] == 'T' && seq[c+1] == 'G' && seq[c+2] == 'A' ) || \
                    (seq[c] == 'T' && seq[c+1] == 'A' && seq[c+2] == 'G')) {
                        
                    // Ecriture du codon stop
                    seq_cod[taille_seqcod]=seq[c];
                    seq_cod[taille_seqcod+1]=seq[c+1];
                    seq_cod[taille_seqcod+2]=seq[c+2];

                    // Codon stop : taille + 3 
                    taille_seqcod= taille_seqcod+3;

                    // Si la séquence est la plus longue et divisible par 3

                    if (taille_seqcod_max < taille_seqcod) {

                        if (taille_seqcod % 3 == 0) {

                            // Taille de la séquence la plus longue = taille de la séquence codante trouvée
                            taille_seqcod_max = taille_seqcod;

                            //On remplit Seq Max avec le nouveau Seq
                            for (n = 0 ; n < taille_seqcod ; n++ ){

                                seqcod_max[n]= seq_cod[n];

                            }
                        }
                    }
                    
                    // On brise la condition du For ( pour éviter qu'il continue de compter )
                    c = taille_seq_entiere ;

                }
                //On remplit Séquence codante avec la séquence
                seq_cod[taille_seqcod] = seq[c]; //c parcours du début de notre nouvelle seq sur la seq  jusqu'a la fin de la nouvelle seq 
                // Si le codon n'a pas été trouvé, on augmente la taille de la séquence codante 
                taille_seqcod++;
            }

        }

        // On parcourt le brin antisens inversé
        if (seq_antisens[i] == 'A' && seq_antisens[i+1] == 'T' && seq_antisens[i+2] == 'G' ) {

            // La taille de la séquence est initialisée à 0
            taille_seqcod = 0; 

            //On parcourt la nouvelle séquence trouvée 
            for ( c = i; c < taille_seq_entiere ; c++ ) {

            // Si on trouve un codon stop ou fin de séquence

                if ((seq_antisens[c] == 'T' && seq_antisens[c+1] == 'A' && seq_antisens[c+2] == 'A' ) || \
                    (seq_antisens[c] == 'T' && seq_antisens[c+1] == 'A' && seq_antisens[c+2] == 'G' ) || \
                    (seq_antisens[c] == 'T' && seq_antisens[c+1] == 'G' && seq_antisens[c+2] == 'A' )){
                    
                    // Ecriture du codon stop
                    seq_cod[taille_seqcod]=seq_antisens[c];
                    seq_cod[taille_seqcod+1]=seq_antisens[c+1];
                    seq_cod[taille_seqcod+2]=seq_antisens[c+2];

                    // Codon stop : taille + 3 
                    taille_seqcod= taille_seqcod+3;

                    // Si la séquence est la plus longue et si elle est codante

                    if (taille_seqcod_max < taille_seqcod) {

                        if (taille_seqcod % 3 == 0) {

                            // Taille de la séquence la plus longue = taille de la séquence codante trouvée
                            taille_seqcod_max = taille_seqcod;

                            // Si la seq condante max provient de l'anti sens, on la remet dans le bon sens

                            for ( n = 1 ; n < taille_seqcod+1 ; n++ ){

                                seqcod_max[n-1] = seq_cod[taille_seqcod-n];

                            }
                        }
                    }

                    // On brise la condition du For ( pour éviter qu'il continue de compter )
                    c = taille_seq_entiere ;

                }
            

                //On remplit Séquence codante avec la séquence
                seq_cod[taille_seqcod] = seq_antisens[c]; //c parcours du début de notre nouvelle seq sur la seq  jusqu'a la fin de la nouvelle seq 
                // Si le codon n'a pas été trouvé, on augmente la taille de la séquence codante 
                taille_seqcod++;
            }
        }
    }
    
    
    // Si aucune séquence codante n a été trouvée
    if (seqcod_max[0] == 'Z') {
        
        FILE* f= fopen("seq_codante_max.fasta", "w");
        if (!f) {
            printf(RED "L'ouverture du fichier a échoué \n" RESET);
            exit(EXIT_FAILURE);
        }
        fprintf(f,RED "\n Aucune séquence codante n'a été trouvée. \n" RESET);
        fclose(f); 
    
    } else { // Si une séquence codante a été trouvée

        // On sauvegarde la séquence codante
        save_sequence( nom_fichier, seqcod_max);

        // On sauvegarde la taille de la séquence codante 
        FILE* f= fopen("seq_codante_max.fasta", "a");
            if (!f) {
                printf(RED "L'ouverture du fichier a échoué \n" RESET);
                exit(EXIT_FAILURE);
            }
            fprintf(f, BLU "\n La taille de la séquence codante maximale est : %d" RESET, taille_seqcod_max);
        fclose(f);
    }
}
```
