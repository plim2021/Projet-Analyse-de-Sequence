# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
#include <stdio.h>

void score_polarite(){
    // 1er fichier

    printf("Saisir le nom du 1er fichier \n");
    get_path_from_user(char* path_input);
    extract_sequence(const char* path_input, char* seq1);

    // 2eme fichier
    printf("Saisir le nom du 2e fichier \n");
    get_path_from_user(char* path_input);
    extract_sequence(const char* path_input, char* seq2);

    /*
    for (i=0; i<taille_seq; i++){
        //
        if AcideAmine
    */
    
    int i; // parcourt des deux séquences
    int taille_seq1 = strlen(seq1); // stocke la taille de la séquence 1
    int taille_seq2 = strlen(seq2); // stocke la taille de la séquence 2
    char id[taille_seq+1]; // séquence qui indique les zones respectant une similarité, +1 pour ajouter '\0'
    int score=0; // score qui compte le nombre daa similaires
    double score_similarite;
    
    if (taille_seq1 == taille_seq2) {
        for (i=0; i<taille_seq; i++){
            // si on a 1 aa hydrophobe dans la seq1 
            if (seq1[i] == 'F' || seq1[i] == 'A' || seq1[i] == 'L' || seq1[i] == 'I' \
            || seq1[i] == 'M' || seq1[i] == 'W' || seq1[i] == 'P' || seq1[i] == 'G' || seq1[i] == 'V') {
                // si on a 1 aa hydrophobe dans la seq2
                if (seq2[i] == 'F' || seq2[i] == 'A' || seq2[i] == 'L' || seq2[i] == 'I' \
                || seq2[i] == 'M' || seq2[i] == 'W' || seq2[i] == 'P' || seq2[i] == 'G' || seq2[i] == 'V') {

                    id[i] = '1'; // à cette position on a une zone hydrophobe
                    score++;
                }
                else {
                    id[i] ='-';
                }
            }
            // si on a 1 aa hydrophile dans la seq1
            if (seq1[i] == 'C' || seq1[i] == 'Y' || seq1[i] == 'T' || seq1[i] == 'S' \
            ||  seq1[i] == 'N' || seq1[i] == 'Q' || seq1[i] == 'H' || seq1[i] == 'K' \
            ||  seq1[i] == 'R' || seq1[i] == 'D' || seq1[i] == 'E' ||) {
                // si on a 1 aa hydrophile dans la seq2
                if (seq2[i] == 'C' || seq2[i] == 'Y' || seq2[i] == 'T' || seq2[i] == 'S' \
                ||  seq2[i] == 'N' || seq2[i] == 'Q' || seq2[i] == 'H' || seq2[i] == 'K' \
                ||  seq2[i] == 'R' || seq2[i] == 'D' || seq2[i] == 'E' ||) {

                    id[i] = '0'; // à cette position on a une zone hydrophile
                    score++;
                }
                else {
                    id[i] = '-';
                }
            }
        }
        score_similarite = (score/taille_seq1)*100;
        printf("Identité de séquence : %d / %d, soit %.1lf \n", score, taille_seq1, score_similarite);
        printf("0 : hydrophiles, 1 : hydrophobes, - : differents \n");
        printf("%s\n",&seq1);
        printf("%s\n",&seq2);
        printf("%s\n",id);

    }
}
    
```
