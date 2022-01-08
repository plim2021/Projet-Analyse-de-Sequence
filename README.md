# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
#include "utils.h"

void traduction() {
#include "utils.h"

void traduction() {

    // Procédure qui demande à l utilisateur de fournir un fichier contenant une séquence ARN
    // et qui la séquence ARN en séquence protéique suivant le code génétique

    // L utilisateur entre le nom du fichier 
    char path_input[30];
    get_path_from_user(path_input);

    // Extraction de la séquence dans la variable arn
    char arn[SIZE];
    extract_sequence(path_input, arn);


    char prot[SIZE]; // Stockage de la séquence protéique
    char path_output[]= "seq_prot.fasta"; // Nom du nouveau fichier
    int taille_arn = strlen(arn) ; //on stocke dans une variable la taille de notre chaîne de caractère
    int j=0; // indice permettant d écrire la séquence protéique

    // Lecture des codons : on avance de 3 nucléotides à la fois

    for (int i=0 ; i<taille_arn ; i=i+3) { 

        // Premier nucléotide : U

        if(arn[i] == 'U'){

            // Deuxième nucléotide :   
            // UC

            if(arn[i+1] == 'C') {

                    // Troisième nucléotide :

                    if (arn[i+2] == 'A' || arn[i+2] == 'U' || arn[i+2] == 'G' || arn[i+2] == 'C') {
                        prot[j] ='S'; //Serine (UCA, UCG, UCU, UCC)
                    }
                    else {
                        prot[j] = '~'; //si on ne trouve pas d acide aminé correspondant
                    }
            
            }

            // UU

            else if (arn[i+1] == 'U') {

                // Troisième nucléotide :
                    
                if (arn[i+2] == 'C' || arn[i+2] == 'U') {
                    prot[j] ='F'; // Phenylalaline (UUU, UUC)
                }
                
                else if (arn[i+2] == 'A' || arn[i+2] == 'G') {
                    prot[j] ='L'; //Leucine (UUA, UUG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
            
            }

            //UA

            else if (arn[i+1] == 'A') {

                // Troisième nucléotide :

                if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='*'; //STOP (UAA, UAG)

                }
                else if (arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='Y'; //Tyrosine (UAU, UAC)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                    
            }

            //UG

            else if (arn[i+1] == 'G') {

                // Troisième nucléotide :
                    
                if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='C';//Cystéine (UGU, UGC)
                }
                else if(arn[i+2] == 'A'){
                    prot[j] ='*' ; //STOP (UGA)
                }
                    
                else if (arn[i+2] == 'G'){
                    prot[j] ='W'; //Tryptophane (UGG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }

            }
            // Si le deuxième nucléotide lu n est pas reconnu

            else {
                prot[j] = 'x';
            }
                
        } 

        // Premier nucléotide : G

        else if(arn[i] == 'G') {

            // Deuxième nucléotide :   
            // GC

            if(arn[i+1] == 'C'){

                // Troisième nucléotide :
                
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='A'; //Alanine (GCU, GCA, GCC, GCG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                
            }

            // GG

            else if(arn[i+1] == 'G'){

                // Troisième nucléotide :
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='G'; //Glycine (GGG, GGA, GGC, GGU)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                    
            }
            
            // GA

            else if (arn[i+1] == 'A'){

                // Troisième nucléotide :
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'G' ){
                    prot[j] ='Q';//Glutamine (GAA, GAG)
                }
                    
                else if (arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='D'; //Acide aspartique (GAC, GAU)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }

            }

            // GU

            else if (arn[i+1] == 'U'){

                // Troisième nucléotide :
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='V';//Valine (GUA, GUG, GUC, GUG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
            }

            // Si le deuxième nucléotide lu n est pas reconnu
            else {
                prot[j] = 'x';
            }

        }

        // Premier nucléotide : A
        
        else if(arn[i] == 'A'){

            // Deuxième nucléotide                
            // AA

            if(arn[i+1] == 'A'){
                    
                // Troisième nucléotide :

                if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='D'; // Acide aspartatique (AAC ou AAU)
                }

                else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='K'; // Lysine  (AAA ou AAG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                
            }

            //AC

            else if(arn[i+1] == 'C'){

                // Troisième nucléotide :
            
                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='F'; // Thréonine (ACA ou ACG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                    
            }

            //AU
            
            else if(arn[i+1] == 'U'){

                // Troisième nucléotide :
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='I'; //isoleucine (AUA ou AUC)
                }

                else if (arn[i+2]=='G'){
                    prot[j] ='M'; //Methionine (AUG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
            }

            //AG

            else if(arn[i+1] == 'G'){

                // Troisième nucléotide :

                if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='R'; //Arginine (AGG ou AGA)
                }

                else if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='S'; //Serine (AGC ou AGU)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                    
            }

            // Si le deuxième nucléotide lu n est pas reconnu

            else {
                prot[j] = 'x'; 
            }
                
        }

        // Premier nucléotide : C

        else if (arn[i] == 'C'){
            
            // Deuxième nucléotide
            // CU

            if(arn[i+1] == 'U'){

                // Troisième nucléotide :

                if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                    prot[j] ='L'; //Leucine (CUU, CUA, CUC, CUG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                    
            }

            // CC

            else if(arn[i+1] == 'C'){

                // Troisième nucléotide :
                    
                if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                    prot[j] ='P'; //Proline (CCA, CCC, CCU, CCG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                    
            }

            // CG

            else if(arn[i+1] == 'G'){

                // Troisième nucléotide :

                if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                    prot[j] ='R'; //Arginine (CGA, CGC, CGU, CGG)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                
            }

            // CA
            else if(arn[i+1] == 'A'){
                
                // Troisième nucléotide :

                if(arn[i+2] == 'U' || arn[i+2] == 'C') {
                    prot[j] ='H'; //Histidine (CAU, CAC)
                }
                    
                else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                    prot[j] ='Q'; //Glutamine (CAG, CAA)
                }
                else {
                    prot[j] ='~'; //si on ne trouve pas d acide aminé correspondant
                }
                
            }

            // Si le deuxième nucléotide lu n est pas reconnu
            else {
                prot[j] = 'x'; 
            }
            
        } 
        // Si le premier nucléotide lu n est pas reconnu 

        else {
            prot[j] = 'x';
        }

        j++;
    }

    // Terminaison de la séquence protéique
    taille_arn= strlen(prot);
    prot[taille_arn]= '\0'; //pour ajouter à la fin de la chaîne de caractère de fin de chaîne

    // Sauvegarde de la séquence protéique
    save_sequence(path_output, prot);
    
}   
