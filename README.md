# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
void score(){

    printf("Entrez le nom de fichier de la séquence à comparer\n");
    
    get_path_from_user(char *path_input);
    extract_sequence(const char* path_input, char* seq1);
    
    printf("Entrez le nom du fichier de la deuxième séquence à comparer\n");
    
    get_path_from_user(char *path_input);
    extract_sequence(const char* path_input, char* seq2);
    

    int taille_seq1 = strlen(seq1); // taille de la séquence 1
    int taille_seq2 = strlen(seq2); // taille de la séquence 2

    //on vérifie que nos séquences sont de taiille identique

    if (taille_seq1 == taille_seq2){
        
        int i; //parcourt les sequences
        int identite = 0; //nb éléments identiques
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
    
    

        double score_id = (identite/taille_seq1) *100 ; //calcule le score didentité

        //on affiche les messages
        printf("Identité de sequence : %d/%d, soit %.1lf \n", identite, taille_seq1, score_id);
        printf("seq1 %s \n", &seq1[taille_seq1]);
        printf("seq2 %s \n", &seq2[taille_seq2]);
        printf("-id- %s \n", id[identite]);
    


    }
    
    else {
        printf("IMPOSSIBLE : les séquences ne sont pas de taille identique ");
    }
    

}
```