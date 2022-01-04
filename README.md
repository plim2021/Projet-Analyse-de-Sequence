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
                        
                
                }

                //UU
                else if(arn[i+1] == 'U'){
                        
                    if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("F"); // Phenylalaline (UUU, UUC)
                        }
                    
                    else if (arn[i+2] == 'A' || arn[i+2] == 'G'){
                        fprintf("L"); //Leucine (UUA, UUG)
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
                        
                }
                //UG
                else{
                        
                    if( arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("C");//Cystéine (UGU, UGC)
                    }
                    else if(arn[i+2] == 'A'){
                       fprintf("*") ; //STOP (UGA)
                    }
                        
                    else{
                        fprintf("W"); //Tryptophane (UGG)
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
                    
                }
                //GG
                else if(arn[i+1] == 'G'){
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("G"); //Glycine (GGG, GGA, GGC, GGU)
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

                }
                //GU
                else{
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("V");//Valine (GUA, GUG, GUC, GUG)
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
                    
                }
                //AC
                else if(arn[i+1] == 'C'){
                
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("F"); // Thréonine (ACA ou ACG)
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
                }

                //AG
                else{

                    if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                        fprintf("R"); //Arginine (AGG ou AGA)
                    }

                    else (arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("S"); //Serine (AGC ou AGU)
                    }
                        
                }
                    
            }
            // C
            else{

                if(arn[i+1] == 'U'){

                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        fprintf("L"); //Leucine (CUU, CUA, CUC, CUG)
                    }
                        
                }
                //CC
                else if(arn[i+1] == 'C'){
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                        fprintf("P"); //Proline (CCA, CCC, CCU, CCG)
                    }
                        
                }
                //CG
                else if(arn[i+1] == 'G'){          
                        
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                        fprintf("R"); //Arginine (CGA, CGC, CGU, CGG)
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
                    
                }
                
            }
        }
        
    } 
    fclose(fichier);
    
}   