# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
void traduction () {

    // appel de la fonction qui va permettre à lutilisateur dentrer le nom de son fichier

    get_path_from_user(char *path_input);

    extract_sequence(const char* path_input, char* arn);

    FILE* fichier = NULL;
    fichier = fopen("seq_Prot.txt", "w");
    if (fichier != NULL) {
        int taille_arn = strlen(arn) ; //on stock dans une varaible la taille de notre chaîne de caractère
        int i; //parcourt le tableau de caractère 

        for(i=0; i<taille_arn; i+3){ // on avance de 3 en 3 pour les codons

            //on commence par le nt U
            if(arn[i] == 'U'){
                    
                //puis le deuxième nt du codon -> C
                    
                if(arn[i+1] == 'C'){

                        //on termine avec le troisième nt du codon
                        if(arn[i+2] == 'A' || arn[i+2] == 'U' || arn[i+2] == 'G' || arn[i+2] == 'C'){
                            frpintf("S"); //Serine (UCA, UCG, UCU, UCC)
                        }
                        else {
                            fprintf("~"); //Si on ne trouve pas d aa correspondante
                        }
                
                }

                //UU
                else if(arn[i+1] == 'U'){
                        
                    if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("F"); // Phenylalaline (UUU, UUC)
                        }
                    
                    else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                        fprintf("L"); //Leucine (UUA, UUG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                
                }
                //UA
                else if(arn[i+1] == 'A'){
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                        fprintf("*"); //STOP (UAA, UAG)

                    }
                    else if (arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("Y"); //Tyrosine (UAU, UAC)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                        
                }
                //UG
                else{
                        
                    if( arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("C");//Cystéine (UGU, UGC)
                    }
                    else if(arn[i+2] == 'A'){
                       fprintf("*") ; //STOP (UGA)
                    }
                        
                    else if (arn[i+2]) == 'G'{
                        fprintf("W"); //Tryptophane (UGG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }

                }
                    
            }  
            //G
            else if(arn[i] == 'G'){

                //GC
                if(arn[i+1] == 'C'){
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("A"); //Alanine (GCU, GCA, GCC, GCG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                    
                }
                //GG
                else if(arn[i+1] == 'G'){
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("G"); //Glycine (GGG, GGA, GGC, GGU)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                        
                }
                //GA
                else if (arn[i+1] == 'A'){
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' ){
                        fprintf("Q");//Glutamine (GAA, GAG)
                    }
                        
                    else if (arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("D"); //acide aspartique (GAC, GAU)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }

                }
                //GU
                else{
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("V");//Valine (GUA, GUG, GUC, GUG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                }
            }
            //A
            else if(arn[i] == 'A'){
                    
                //AA
                if(arn[i+1] == 'A'){
                        
                    if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("D"); // Acide aspartatique (AAC ou AAU)
                    }

                    else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                        fprintf("K"); // Lysine  (AAA ou AAG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                    
                }
                //AC
                else if(arn[i+1] == 'C'){
                
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("F"); // Thréonine (ACA ou ACG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                        
                }
                //AU
                else if(arn[i+1] == 'U'){
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("I"); //isoleucine (AUA ou AUC)
                    }

                    else if (arn[i+2]=='G'){
                        fprintf("M"); //Methionine (AUG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                }

                //AG
                else{

                    if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                        fprintf("R"); //Arginine (AGG ou AGA)
                    }

                    else if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("S"); //Serine (AGC ou AGU)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                        
                }
                    
            }
            // C
            else{
                
                //CU
                if(arn[i+1] == 'U'){

                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("L"); //Leucine (CUU, CUA, CUC, CUG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                        
                }
                //CC
                else if(arn[i+1] == 'C'){
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                        fprintf("P"); //Proline (CCA, CCC, CCU, CCG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                        
                }
                //CG
                else if(arn[i+1] == 'G'){          
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                        fprintf("R"); //Arginine (CGA, CGC, CGU, CGG)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                    
                }
                //CA
                else{
                    
                    if(arn[i+2] == 'U' || arn[i+2] == 'C') {
                        fprintf("H"); //Histidine (CAU, CAC)
                    }
                        
                    else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                        fprintf("Q"); //Glutamine (CAG, CAA)
                    }
                    else {
                        fprintf("~"); //Si on ne trouve pas d aa correspondante
                    }
                    
                }
                
            }
        }
        
    } 
    fclose(fichier);
    
}   