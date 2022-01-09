# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 



```ruby
#include <stdio.h>
#include <string.h>

#include "module6.h"
#include "utils.h"
#define SIZE 10000

void frequence(){

    //Tab de ligne et de caractère
    char adn[1001][30];

    char path_input[30];
    
    get_path_from_user(path_input);

    char seq[SIZE];
    extract_sequence(path_input, seq);

    char result[30];

    //Init les var
    int ligne_index = 0 ;
    int caratere_index = 0 ;

    //On va remplire adn avec seq 
    //On parcours i de 0 à taille de Seq
    for ( int i = 0 ; i < strlen(seq) ; i++ ){

        //Si il y a un saut de ligne
        if ( seq[i] == '\n' ){
            //ligne++
            ligne_index++;
            //Et donc on commence au caractère 0 de cette nouvelle ligne
            caratere_index = 0 ; 

        } else {
            //Sinon on remplit le tab adn 
            adn[ligne_index][caratere_index] = seq[i];
            caratere_index++;
        }
    }

    int recurrence[4]; //chaque case corespond a une lettre g , c, t, a 
    recurrence[0] = 0 ; //g
    recurrence[1] = 0 ; //c
    recurrence[2] = 0 ; //t
    recurrence[3] = 0 ; //a

    //on parcours le tab à deux dimensions avec donc deux boucles
    //Parcours les caractères
    for ( int p = 0 ; p < 30 ; p++ ){

        //Init a chaque changement de colonnes
        recurrence[0] = 0 ; //g
        recurrence[1] = 0 ; //c
        recurrence[2] = 0 ; //t
        recurrence[3] = 0 ; //a

        //On parcours les lignes
        for ( int u = 0 ; u < ligne_index ; u++ ){

            //On compte les reccurences des lettres ligne par ligne
            if ( adn[u][p] == 'G'){
                recurrence[0]++;
            } else if ( adn[u][p] == 'C'){
                recurrence[1]++;
            } else if ( adn[u][p] == 'T'){
                recurrence[2]++;
            } else if ( adn[u][p] == 'A'){
                recurrence[3]++;
            }
        }

        //max recurrence
        int max = 0 ;
        for ( int r = 0 ; r < 4 ; r++ ){
            if ( recurrence[max] < recurrence[r] ){
                max = r ;
            }
        }

        //produit en croix pour les %
        double pourcentage = (recurrence[max] / ligne_index)*100 ;

        if ( pourcentage == 100 ){
            if ( max == 0 ){
                result[p] = 'G' ;
            } else if ( max == 1 ){
                result[p] = 'C' ;
            } else if ( max == 2 ){
                result[p] = 'T' ;
            } else if ( max == 3 ){
                result[p] = 'A' ;
            }
        } else if ( pourcentage >= 80 ){
            result[p] = '*' ;
        } else ( pourcentage >= 60 ){
            result[p] = '-' ;
        }

    }

    char nomfichier[30];
    nom_fichier = "test.txt"
    save_sequence( nom_fichier, result);

    
}
```
