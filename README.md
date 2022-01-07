# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
#include "utils.h"

void traduction() {

    // appel de la fonction qui va permettre à lutilisateur dentrer le nom de son fichier

    char path_input[30];
    printf("Entrez le nom de votre fichier : ");
    get_path_from_user(path_input);

    char arn[1000];

    extract_sequence(path_input, arn);

    char path_output[]= "seq_prot.fasta";
    char prot[1000];

    
    int taille_arn = strlen(arn) ; //on stocke dans une varaible la taille de notre chaîne de caractère
    int i; // indice parcourant la séquence ARN
    int j=0; // indice permettant d écrire la séquence protéique

    for(i=0; i<taille_arn; i=i+3){ // on avance de 3 en 3 pour la lecture des codons

        //on commence par le nt U
        if(arn[i] == 'U'){
                
            //puis le deuxième nt du codon -> C
                
            if(arn[i+1] == 'C'){

                    //on termine avec le troisième nt du codon
                    if(arn[i+2] == 'A' || arn[i+2] == 'U' || arn[i+2] == 'G' || arn[i+2] == 'C'){
                        prot[j] ='S'; //Serine (UCA, UCG, UCU, UCC)
                    }
                    else {
                        prot[j] = '~'; //Si on ne trouve pas d aa correspondante
                    }
            
            }

            //UU
            else if(arn[i+1] == 'U'){
                    
                if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='F'; // Phenylalaline (UUU, UUC)
                }
                
                else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='L'; //Leucine (UUA, UUG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
            
            }
            //UA
            else if(arn[i+1] == 'A'){
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='*'; //STOP (UAA, UAG)

                }
                else if (arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='Y'; //Tyrosine (UAU, UAC)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                    
            }
            //UG
            else{
                    
                if( arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='C';//Cystéine (UGU, UGC)
                }
                else if(arn[i+2] == 'A'){
                    prot[j] ='*' ; //STOP (UGA)
                }
                    
                else if (arn[i+2] == 'G'){
                    prot[j] ='W'; //Tryptophane (UGG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }

            }
                
        }  
        //G
        else if(arn[i] == 'G'){

            //GC
            if(arn[i+1] == 'C'){
                
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='A'; //Alanine (GCU, GCA, GCC, GCG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                
            }
            //GG
            else if(arn[i+1] == 'G'){
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='G'; //Glycine (GGG, GGA, GGC, GGU)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                    
            }
            //GA
            else if (arn[i+1] == 'A'){
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'G' ){
                    prot[j] ='Q';//Glutamine (GAA, GAG)
                }
                    
                else if (arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='D'; //acide aspartique (GAC, GAU)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }

            }
            //GU
            else{
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='V';//Valine (GUA, GUG, GUC, GUG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
            }
        }
        //A
        else if(arn[i] == 'A'){
                
            //AA
            if(arn[i+1] == 'A'){
                    
                if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='D'; // Acide aspartatique (AAC ou AAU)
                }

                else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='K'; // Lysine  (AAA ou AAG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                
            }
            //AC
            else if(arn[i+1] == 'C'){
            
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='F'; // Thréonine (ACA ou ACG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                    
            }
            //AU
            else if(arn[i+1] == 'U'){
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='I'; //isoleucine (AUA ou AUC)
                }

                else if (arn[i+2]=='G'){
                    prot[j] ='M'; //Methionine (AUG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
            }

            //AG
            else{

                if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='R'; //Arginine (AGG ou AGA)
                }

                else if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='S'; //Serine (AGC ou AGU)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                    
            }
                
        }
        // C
        else{
            
            //CU
            if(arn[i+1] == 'U'){

                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='L'; //Leucine (CUU, CUA, CUC, CUG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                    
            }
            //CC
            else if(arn[i+1] == 'C'){
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                    prot[j] ='P'; //Proline (CCA, CCC, CCU, CCG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                    
            }
            //CG
            else if(arn[i+1] == 'G'){          
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                    prot[j] ='R'; //Arginine (CGA, CGC, CGU, CGG)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                
            }
            //CA
            else{
                
                if(arn[i+2] == 'U' || arn[i+2] == 'C') {
                    prot[j] ='H'; //Histidine (CAU, CAC)
                }
                    
                else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='Q'; //Glutamine (CAG, CAA)
                }
                else {
                    prot[j] ='~'; //Si on ne trouve pas d aa correspondante
                }
                
            }
            
        }
        j++; 
    }
    taille_arn= strlen(prot);
    prot[taille_arn]= '\0'; //pour ajouter à la fin de la chaîne de caractère de fin de chaîne

    save_sequence(path_output, prot);
    
}   
