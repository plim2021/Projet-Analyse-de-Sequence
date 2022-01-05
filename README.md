# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
void get_path_from_user(char * path_input){
//Procédure qui va permettre à notre utilisateur de donner le nom du fichier

    printf("Entrez le nom de votre fichier" :);
    scanf("%30s", path_input);
              
}
```

```ruby
void extract_sequence(const char* path_input, char* sequence){
//Procédure qui extrait la sequence dans le fichier FASTA et la met dans un tableau de séquence
  
    char ligne[81]; //stock les lignes de 80 caractères, on rajoute 1 pour le caractère spécial '\0'
    int i=0; //indice pour pouvoir incrémenter nos valeurs dans notre tableau qui contiendra la séquence
    int j=0; //indice pour com

    FILE * f= fopen(path_input, "r"); //On ouvre le fichier
        if (!f) {
            printf("L'ouverture du fichier a échoué. \n");
            exit(EXIT_FAILURE);
        }

    
    while (fgets(ligne, 81, f)) {
        //tant quon arrive pas à la fin de la ligne et à la fin de la chaîne de caractère on continue de remplir notre ligne
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
//Procédure qui va enregistrer une nouvelle séquence dans un nouveau fichier

    int i=0;

    //on ouvre le fichier
    FILE* fsave= fopen(path_output, "w");
        if (!f) {
            print("L'ouverture du fichier a échoué \n");
            exit(EXIT_FAILURE);

        }
    
    //tant quon ne rencontre pas le caracère spéciale qui indique la fin dune chaîne de caractère on stock la séquence
    while (sequence[i] != '\0') {
        fputc(sequence[i], fsave);
        i++; //on compte le nombre de caractère 80 

        // si la ligne est égale à 80 on retourne à la ligne pour respecter le format FASTA
        if (i%80 == 0) {
            fprintf(fsave, "\n");
        }

    }
    fclose(fsave);


}
```
