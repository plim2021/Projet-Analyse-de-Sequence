# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
void traduction ( char* arn) {

    // appel de la fonction qui va permettre à l'utilisateur d'entrer le nom de son fichier
    get_path_from_user();

    int taille_arn = 0 ;
    int i =i;
    
    
    while(arn[i] != " ") {
        taille_arn ++;
        i++;
    }
    
    
    // condition codon initiation AUG et la taille est divisible par 3
    if (arn[0] == "A" && arn[1] == "U" && arn[2] == "G" && taille_arn % 3 == i) {
        while(i<taille_arn) {

            //ici je dois dire que tu compte après avoir trouvé le codon d'initiation et tu compte de 3 en 3 
            // tu compte de la case i, i+1, i+2 puis tu recommences à la suite i, i+1, i+2 mais je vois pas trop
            
            // on commence par le premier nt du codon -> U
            ```
            if(arn[i] == 'U'){
                
                //puis le deuxième nt du codon -> C
                if(arn[i+i+1] == 'C'){

                    //on termine avec le troisième nt du codon
                    if(arn[i+i+2] == 'A' || arn[i+2] == 'U' || arn[i+2] == 'G' || arn[i+2] == 'C'){
                        return 'S'; //Serine (UCA, UCG, UCU, UCC)
                    }
            
                }
            }

                //UU
                else if(arn[i+1] == 'U'){
                    
                    if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'F'; // Phenylalaline (UUU, UUC)
                    }
                
                    else (arn[i+2] == 'A' || arn[i+2] == 'G'){
                        return 'L'; //Leucine (UUA, UUG)
                    }
            
                }
                //UA
                else if(arn[i+1] == 'A'){
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                        return '*'; //STOP (UAA, UAG)
                    }
            
                    else if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'Y'; //Tyrosine (UAU, UAC)
                    }
                    
                }
                //UG
                else{
                    
                    if( arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'C';//Cystéine (UGU, UGC)
                    }
                    else if(arn[i+2] == 'A'){
                        return '*'; //STOP (UGA)
                    
                    else{
                        return 'W'; //Tryptophane (UGG)
                    }

                }
                
            }
            //G
            else if(arn[i] == 'G'){

                //GC
                if(arn[i+1] == 'C'){
                
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'A'; //Alanine (GCU, GCA, GCC, GCG)
                    }
                
                }
                //GG
                else if(arn[i+1] == 'G'){
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'G'; //Glycine (GGG, GGA, GGC, GGU)
                    }
                    
                }
                //GA
                else if (arn[i+1] == 'A'){
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' ){
                        return 'Q';//Glutamine (GAA, GAG)
                    }
                    
                    else (arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'D'; //acide aspartique (GAC, GAU)
                    }

                }
                //GU
                else{
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'V';//Valine (GUA, GUG, GUC, GUG)
                    }
                }
            }
            //A
            else if(arn[i] == 'A'){
                
                //AA
                if(arn[i+1] == 'A'){
                    
                    if(arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'D'; // Acide aspartatique (AAC ou AAU)
                    }

                    else (arn[i+2] == 'A' || arn[i+2] == 'G'){
                        return 'K'; // Lysine  (AAA ou AAG)
                    }
                
                }
                //AC
                else if(arn[i+1] == 'C'){
            
                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'U'; // Thréonine (ACA ou ACG)
                    }
                    
                }
                //AU
                else if(arn[i+1] == 'U'){
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'I'; //isoleucine (AUA ou AUC)
                    }

                    else (arn[i+2]=='G'){
                        return 'M'; //Methionine (AUG)
                    }
                }

                //AG
                else{

                    if(arn[i+2] == 'A' || arn[i+2] == 'G'){
                        return 'R'; //Arginine (AGG ou AGA)
                    }

                    else (arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'S'; //Serine (AGC ou AGU)
                    }
                    
                }
                
            }
            // C
            else{

                if(arn[i+1] == 'U'){

                    if(arn[i+2] == 'A' || arn[i+2] == 'G' || arn[i+2] == 'C' || arn[i+2] == 'U'){
                        return 'L'; //Leucine (CUU, CUA, CUC, CUG)
                    }
                    
                }
                //CC
                else if(arn[i+1] == 'C'){
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                        return 'P'; //Proline (CCA, CCC, CCU, CCG)
                    }
                    
                }
                //CG
                else if(arn[i+1] == 'G'){          
                    
                    if(arn[i+2] == 'A' || arn[i+2] == 'C' || arn[i+2] == 'U' || arn[i+2] == 'G'){
                        return 'R'; //Arginine (CGA, CGC, CGU, CGG)
                    }
                
                }
                //CA
                else{
                
                    if(arn[i+2] == 'U' || arn[i+2] == 'C') {
                        return 'H'; //Histidine (CAU, CAC)
                    }
                    
                    else (arn[i+2] == 'A' || arn[i+2] == 'G'){
                        return 'Q'; //Glutamine (CAG, CAA)
                    }
                
                }
            
            }
        }
        i= i+3;
    } 
    // appel la fonction qui écrit dans un fichier
    save_sequence(path_output,*arn)
    FILE* fichier = NULL;
    <citation nom="Exécution"></citation>
    fichier = fopen("seq_proteique.txt", "w");
    if (fichier != NULL) {
        fputs(*arn, fichier);
        fclose(fichier);
    }
  
}
```