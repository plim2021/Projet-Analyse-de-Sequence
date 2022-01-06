# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby

void recherchetaillemax () {

    
    printf("Entrez le nom de votre fichier \n" );
    get_path_from_user(&path_input);

    //appel la fonction qui va extraire la séquence et la mettre dans un tableau
    char seq[];
    extract_sequence(&path_input, &seq);

    char nom_fichier = "seq_codante_max.txt";
    // Calcul de la taille de la séquence entière
    int taille_seq_entiere = strlen(seq);

    // Variables stockeuses de la séquence codante la plus longue et de sa taille
    char seqcod_max ;
    int taille_seqcod_max = 0;

    int i = 0; // indice qui parcourt la séquence entière

    // Parcours pour chaque séquence codante trouvée
    int k, taille_seqcod ; // indice qui parcourt la séquence codante, variable qui compte sa longueur
    char seq_cod[]; // variable qui stocke la séquence codante trouvée
    int j; // indice qui parcourt la séquence codante trouvée

    //  trouve le brin complémentaire
    int l = 0; // indice qui parcourt la séquence entière
    char seq_antisens; // variable qui stocke la séquence entière antisens
    while (l<taille_seq) {
        if (seq[l]=='A') {
            seq_antisens[l]='T';
        }
        if (seq[l]=='T') {
            seq_antisens[l]='A';
        }
        if (seq[l]=='G') {
            seq_antisens[l]='C';
        }
        if (seq[l]=='C') {
            seq_antisens[l]='G';
        }
        l++;
    }

    // Boucle parcourant toute la séquence entière
    while (i < taille_seq_entiere) {

        // on entre si on trouve un codon ATG
        if (seq[i] == "A" && seq[i+1] == "T" && seq[i+2] == "G") {

            // variable compteur de la sequence codante
            k = 0;
            taille_seqcod = 0;
            j=i; // on choisit de commencer par l indice i pour stocker le codon start dans seq_cod

            // tant qu on à pas de condon TAA, TAG, TGA. On stocke dans une variable toute la séquence codante en comptant sa longueur
            while (seq[j] <> "T" && seq[j+1] <> "A" && seq[j+2] <> "A" \
            || seq[j] <> "T" && seq[j+1] <> "G" && seq[j+2] <> "A" \
            || seq[j] <> "T" && seq[j+1] <> "A" && seq[j+2] <> "G") {
                seq_cod[k]= seq[i]; // on écrit le nucléotide seq[i] dans seq_cod[k]
                taille_seqcod++; // la taille de la séquence codante augmente de 1
                j++; // on continue de parcourir la séquence
                k++;
            }

            // si la longueur de la séquence est divisible par 3
            if (taille_seqcod % 3 = 0) {
            // et si la longueur de la séquence trouvée est plus grande que la séquence trouvée précédement on remplace la taille et le contenu de la séq codante max dans les variables stockeuses
                if (taille_seqcod > taille_seqcod_max) {
                    taille_seqcod_max == taille_seqcod;
                    seqcod_max == seqcod;
                }
            }
        }
        i++;
    }
    
    int m = strlen(seq); // indice qui parcourt le brin antisens

    // Boucle parcourant toute la séquence entière antisens
    while (m<>0){
        // on entre si on trouve un codon ATG
        if (seq[m] == "A" && seq[m-1] == "T" && seq[m-2] == "G") {

            // variable compteur de la sequence codante
            k = 0;
            taille_seqcod = 0;
            j=m; // on choisit de commencer par l indice i pour stocker le codon start dans seq_cod

            while (seq[j] <> "T" && seq[j-1] <> "A" && seq[j-2] <> "A" \
            || seq[j] <> "T" && seq[j-1] <> "G" && seq[j-2] <> "A" \
            || seq[j] <> "T" && seq[j-1] <> "A" && seq[j-2] <> "G") {
                seq_cod[k]= seq[m]; // on écrit le nucléotide seq[m] dans seq_cod[k]
                taille_seqcod++; 
                j++; 
                k++;
            }

            if (taille_seqcod % 3 = 0) {

                if (taille_seqcod > taille_seqcod_max) {
                    taille_seqcod_max == taille_seqcod;
                    seqcod_max == seqcod;
                }
            }
        }
        m--; // on parcourt le brin à l envers
    }
    save_sequence( nom_fichier, &seqcod_max);
}
