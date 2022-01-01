# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
void score(char* seq1[], char * seq2[]){

    //appel de la fonction qu'on va modifier pour demander à l'utilisateur le nom de ses 2 fichiers
    
    // il faut verifier que les séquences soient bien de taille identique

    int taille_seq1, taille_seq2 = 0 ;
    int i, j =0;
    int identite = 0;
    
    
    //on parcourt notre séquence tant qu'on n'a pas d'espace
    //et on compte afin d'avoir la taille de notre sequence

    
    while(seq1[i] != " ") {
        taille_seq1 ++;
        i++;
    }

    while(seq2[j] != " ") {
        taille_seq2 ++;
        j++;
    }
    

    //on vérifie que nos séquences sont égales

    
    if (taille_seq1 == taille_seq2){
        
        //on parcourt nos deux séquences
        //afin de voir si elles sont identiques

        
        for(i=0; i<taille_seq1; i++){
                
            //si elles sont identiques au même indice on rajoute +1 
            //au nb d'identité

            if(seq1[i] == seq2[i]){
                identite++;

            }
        }
        
        //j'ai oublié comment on crée un tableau je verrais plus tard
        //ici on crée un tableau de caractère pour ressoritr que les nt ou aa identiques

        char id[identite];

        for(j=0; j<taille_seq1; i++){
            if (seq1[i] == seq2[i]){
                id[i]= seq1[i];

            }
        }
    

        score_id = identite/taille_seq1 ; 
        //on affiche les messages
        printf("Identité de sequence : %d/%d, soit %1lf \n", identite, taille_seq1, score_id);
        printf("seq1 %s \n", seq1[taille_seq1]);
        printf("seq2 %s \n", seq2[taille_seq2]);
        printf("-id- %s \n",id[identite] );
    


    }
    
    else {
        printf("IMPOSSIBLE : les séquences ne sont pas de taille identique ");
    }
    

}
```