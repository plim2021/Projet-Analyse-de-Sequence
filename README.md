# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby

#include "module4.h"
#include "utils.h"

void score(){

    printf("Entrez le nom de fichier de la séquence à comparer\n");

    char path_input1[30];
    char seq1[1000];
    
    get_path_from_user(path_input1);
    extract_sequence(path_input1, seq1);
    printf("\n");
    
    printf("Entrez le nom du fichier de la deuxième séquence à comparer\n");
    
    char path_input2[30];
    char seq2[1000];
    
    get_path_from_user(path_input2);
    extract_sequence(path_input2, seq2);
    printf("\n");
    

    int taille_seq1 = strlen(seq1); // taille de la séquence 1
    int taille_seq2 = strlen(seq2); // taille de la séquence 2

    //on vérifie que nos séquences sont de taille identique

    if (taille_seq1 == taille_seq2){
        
        int i; //parcourt les sequences
        double identite = 0; //nb éléments identiques
        char id[taille_seq1+1]; // stock le résultat, on met +1 pour stocker le caractère spéciale '\0' 

        //on parcourt nos deux séquences afin de voir si elles sont identiques

        for(i=0; i<taille_seq1; i++){
                
            //si elles sont identiques au même indice on rajoute +1 
            //au nb d identité

            if(seq1[i] == seq2[i]){
                identite++;
                id[i]= seq1[i];
        
            }
            else{
                id[i]='-';

            }
        }
        id[i]='\0';

        // Calcul du score didentité
        float score_id=0;
        score_id = (identite/taille_seq1)*100 ;

        //on affiche les messages
        printf("Identité de sequence : %.0lf/%d, soit %.1lf \n", identite, taille_seq1, score_id);
        printf("seq1 %s \n", seq1);
        printf("seq2 %s \n", seq2);
        printf("-id- %s \n", id);

    }
    
    else {
        printf("IMPOSSIBLE : les séquences ne sont pas de taille identique ");
    }
    

}
```
