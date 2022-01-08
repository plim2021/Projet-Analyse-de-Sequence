# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 
# define SIZE 10000

```ruby

#include "utils.h"
#define SIZE 10000

void recherchetaillemax() {

    char path_input[30];
    
    get_path_from_user(path_input);

    //appel la fonction qui va extraire la séquence et la mettre dans un tableau
    char seq[SIZE];
    extract_sequence(path_input, seq);

    char nom_fichier[] = "seq_codante_max.fasta";
    // Calcul de la taille de la séquence entière
    int taille_seq_entiere = strlen(seq);

    // Variables stockeuses de la séquence codante la plus longue et de sa taille
    char seqcod_max[SIZE];
    seqcod_max[0]='Z'; // flag qui permet de savoir si on a trouvé une séquence codante
    int taille_seqcod_max = 0;

    int i = 0; // indice qui parcourt la séquence entière
    int n ; // indice qui parcourt la nouvelle séquence codante trouvée 

    // Parcours pour chaque séquence codante trouvée
    int taille_seqcod; // indice qui parcourt la séquence codante, variable qui compte sa longueur
    char seq_cod[SIZE]; // variable qui stocke la séquence codante trouvée


    //  trouve le brin complémentaire
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

    //anti sera une copie de seq_antisens
    char anti2[SIZE]; 

    //On copie seq_antisens dans anti2
    for ( i = 0 ; i < taille_seq_entiere ; i++ ){

        anti2[i] = seq_antisens[i] ; 

    }

    //On inverse la seq_antisens ( pour ne pas avoir à lire à l envers )
    for ( i = 1 ; i < taille_seq_entiere ; i++ ){

        seq_antisens[i - 1 ] = anti2[taille_seq_entiere-i] ;

    }
    
    //Boucle qui cherche une fois la seq cod max
    //Dans cod et anti sens 
    for ( int y = 0 ; y < 1 ; y++ ){

        //2ème tour
        if ( y == 1 ){

            //On remplace Seq par l anti sens
            for ( i = 0 ; i < taille_seq_entiere ; i++ ){
                seq[i] = seq_antisens[i] ; 
            }
        }

        //On parcours la séquence ( seq[] ) avec i 
        for ( i = 0 ; i < taille_seq_entiere ; i++ ){

            //On découvre une nouvelle seq cod
            if ( seq[i] == 'A' && seq[i+1] == 'T' && seq[i+2] == 'G' ) {

                //On init une nouvelle seq_cod
                taille_seqcod = 0; //Init taille seq_cod

                //On parcours le début du nouveau seq cod 
                for ( int c = i+3 ; c < taille_seq_entiere ; c++ ) {
                    
                    //Si fin de seq_cod
                    if ( ( seq[c] == 'T' && seq[c+1] == 'A' && seq[c+2] == 'A' ) || \
                        (seq[c] == 'T' && seq[c+1] == 'G' && seq[c+2] == 'A' ) || \
                        (seq[c] == 'T' && seq[c+1] == 'A' && seq[c+2] == 'G') ){

                        //Si la taille de ce seq
                        if ( taille_seqcod_max < taille_seqcod ){

                            //Si taille divisible par 3
                            if (taille_seqcod % 3 == 0) {

                                //Alors taille max = taille seq
                                taille_seqcod_max = taille_seqcod;

                                //Si la seq condante max provient de l anti sens
                                if ( y == 1 ){

                                    /*Alors on remplit la seqcod_max à l envers car on lit 
                                    l'anti sens à l'envers donc on le remet à l endroit !*/
                                    for ( n = 1 ; n < taille_seqcod ; n++ ){

                                        seqcod_max[ n - 1 ] = seq_cod[ taille_seqcod - n ];

                                    }

                                } else {

                                    //On remplit Seq Max avec le nouveau Seq
                                    for ( n = 0 ; n < taille_seqcod ; n++ ){

                                        seqcod_max[n]= seq_cod[n];

                                    }

                                }

                            }

                        }

                        // On brise la condition du For ( pour éviter qu il continue de compter )
                        c = taille_seq_entiere ;

                    } 

                    //On remplit Séquence codante avec la séquence
                    seq_cod[taille_seqcod] = seq[c]; //c parcours du début de notre nouvelle seq sur la seq  jusqu a la fin de la nouvelle seq 

                    //Sinon c est pas la fin du Seq donc on augmente la taille !                
                    taille_seqcod++;

                }
            }
        }
    }


    // Si aucune séquence codante n a été trouvée
    if (seqcod_max[0] == 'Z') {
        
        FILE* f= fopen("seq_codante_max.fasta", "w");
        if (!f) {
            printf("L'ouverture du fichier a échoué \n");
            exit(EXIT_FAILURE);
        }
        fprintf(f,"\n La taille de la séquence codante maximale est : %d \n", taille_seqcod_max );
        fclose(f); 
    
    } else { // Si une séquence codante a été trouvée

        // On sauvegarde la séquence codante
        save_sequence( nom_fichier, seqcod_max);
        // On sauvegarde la taille de la séquence codante 
        FILE* f= fopen("seq_codante_max.fasta", "a");
            if (!f) {
                printf("L'ouverture du fichier a échoué \n");
                exit(EXIT_FAILURE);
            }
            fprintf(f,"\n La taille de la séquence codante maximale est : %d", taille_seqcod_max);
        fclose(f);
    }
}
```
