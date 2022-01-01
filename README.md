*Taille_max

void recherchetaillemax (*nomfichier) {

  extraxt_sequence(chemin,*seq);
  // variable de toute la sequence nucléotidique stockée
  char seq ;
  // variables stockeuses de la séquence codante la plus longue et de sa taille
  char seqcod_max ;
  int taille_seqcod_max = 0;
  // boucle parcourant toute la séquence. 10 000 car on considère que la taille max de la séquence en nucléotide est de 10 000.
  for (int i = 0; i < 10000; i++) {
    // on entre si on trouve un codon ATG
    if (seq[i] == "A" && seq[i+1] == "T" && seq[i+2] == "G") {
      // variable compteur de la sequence codante
      int k = 0;
      int j = i;
      int taille_seqcod = 0;
      // tant qu'on à pas de condon TAA, TAG, TGA. On stock dans une variable toute la séquence codante en comptant sa longueur
      while (seq[j] <> "T" && seq[j+1] <> "A" && seq[j+2] <> "A" or seq[j] <> "T" && seq[j+1] <> "G" && seq[j+2] <> "A" or seq[j] <> "T" && seq[j+1] <> "A" && seq[j+2] <> "G") {
        seqcod[k]== seq[j];
        taille_seqcod ++;
        j ++;
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
  }
  // taille de la séquence
  int taille_seq = 0;
    int i = 0;
    while (adn[i] != " ") {
         taille_adn ++;
         i ++;
     }
  //  trouve le brin complémentaire
  int i = 0;
  char seq_ADN;
  while (i<taille_seq) {
    if (seq[i]=='A') {
      seq_ADN[i]=='T');
    }
    if (seq[i]=='T') {
      seq_ADN[i]=='A');
    }
    if (seq[i]=='G') {
      seq_ADN[i]=='C');
    }
    if (seq[i]=='C') {
      seq_ADN[i]=='G');
    }
    l++;
  }
  for (int i = 0; i < 10000; i++) {
    // on entre si on trouve un codon ATG
    if (seq_ADN[i] == "A" && seq_ADN[i+1] == "T" && seq_ADN[i+2] == "G") {
      // variable compteur de la sequence codante
      int k = 0;
      int j = i;
      int taille_seqcod = 0;
      // tant qu'on à pas de condon TAA, TAG, TGA. On stock dans une variable toute la séquence codante en comptant sa longueur
      while (seq_ADN[j] <> "T" && seq_ADN[j+1] <> "A" && seq_ADN[j+2] <> "A" or seq_ADN[j] <> "T" && seq_ADN[j+1] <> "G" && seq_ADN[j+2] <> "A" or seq_ADN[j] <> "T" && seq_ADN[j+1] <> "A" && seq_ADN[j+2] <> "G") {
        seqcod[k]== seq_ADN[j];
        taille_seqcod ++;
        j ++;
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
  }
  save_sequence(chemin,*seqcod_max)
  return 0
 
}
