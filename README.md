# Projet-Analyse-de-Sequence
projet noté – Logiciel d’analyse de séquences - Mini Informatique 1 

```ruby
char* get_path_from_user(){
        int good = 0;
    char* char_fichier;

        char str[50];

        while ( good == 0 ){
        printf("Entrer le nom du fichier : ");
                scanf("%[^\n]%*c", str);
                printf(".%s.\n", str);
        
        char_fichier = readFile( str );

                if ( char_fichier != NULL ){ // On peut lire et écrire dans le fichier
                        good = 1 ;
                }
                else {
                        // On affiche un message d'erreur si on veut
                        printf("Impossible d'ouvrir le fichier : ");
            puts( str );
                }
        }

        return str ;
}
```

void extract_sequence(const char* path_input, char* sequence){
  
}

void save_sequence(const char* path_output, char* sequence)
