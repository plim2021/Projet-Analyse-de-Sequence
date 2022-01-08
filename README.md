# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

#include "utils.h"

```ruby
void affichage_menu (){

    // Procédure qui affiche le menu des modules
    printf(ORA "---MENU---\n");
    printf("1. Recherche de la séquence codante de taille maximale\n");
    printf("2. Transcription d'une séquence d'ADN en séquence ARN\n");
    printf("3. Traduction d'une séquence codante en séquence protéique\n");
    printf("4. Calcul du score d'identité entre deux séquences\n");
    printf("5. Calcul du score de similarité de polarité entre deux séquences protéiques\n");
    printf("6. Recherce d'une séquence consensus à partir d'un alignement muliple\n");
    printf("7. Recherche de la plus grande sous-chaîne de polarité commune à 2 séquences protéiques\n"RESET);
    printf("\n");
    
}
```

```ruby
void get_path_from_user(char * path_input){
    
    //Procédure qui va permettre à notre utilisateur de fournir le nom du fichier

    printf("Entrez le nom de votre fichier" :);
    scanf("%30s", path_input);
              
}
```

```ruby
void extract_sequence(const char* path_input, char* sequence){
    
    //Procédure qui extrait la sequence dans le fichier FASTA et la met dans un tableau de séquence
  
    char ligne[81]; //stocke les lignes de 80 caractères, on rajoute 1 pour le caractère spécial '\0'
    int i=0; //indice pour pouvoir incrémenter nos valeurs dans notre tableau qui contiendra la séquence
    int j=0; //indice

    FILE * f= fopen(path_input, "r"); //On ouvre le fichier
        if (!f) {
            printf("L'ouverture du fichier a échoué. \n");
            exit(EXIT_FAILURE);
        }

    
    while (fgets(ligne, 81, f)) {
        //tant qu'on arrive pas à la fin de la ligne et à la fin de la chaîne de caractère on continue de remplir notre ligne
        while(ligne[j] != '\n' && ligne[j] != '\0') {
            sequence[i] = ligne[j]; //on ajoute nos caractères dans notre nouveau tableau
            i++; 
            j++;//on ajoute +1 pour avancer 
        }
    
    sequence[i] = '\0'; //on ajoute le caractère spéciale pour indiquer la fin de la chaîne de caractère
    }
    fclose(f); //on ferme le fichier


}
```

```ruby
void save_sequence(const char* path_output, char* sequence) {

    // Procédure qui va enregistrer une nouvelle séquence dans un nouveau fichier

    int i=0; //indice qui parcourt séquence et qui indique le retour à la ligne

    // Ouverture du fichier
    FILE* fsave= fopen(path_output, "w");
    if (!fsave) {
        printf(RED "> L'ouverture du fichier a échoué \n" RESET);
        exit(EXIT_FAILURE);
    }
    
    // Tant quon ne rencontre pas le caracère spéciale qui indique la fin dune chaîne de caractère on stock la séquence
    while (sequence[i] != '\0') {
    
        fputc(sequence[i], fsave);
        i++; //on compte le nombre de caractère 80 

        // Respect du format FASTA : retour à la ligne au bout de 80 caractères
        if (i%80 == 0) {
            fprintf(fsave, "\n");
        }

    }
    
    fclose(fsave);

}
```
