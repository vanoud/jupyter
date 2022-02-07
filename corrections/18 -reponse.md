# Création de fichiers

```bash
 #!/bin/bash

# Écrire un script qui crée un dossier avec un nombre de fichiers.

# Si le nombre de fichier n'est pas donné en paramètre nommé, demander le nombre de fichier a créer.
# Si la destination du dossier n'est pas donnée en paramètre sa valeur par défaut serra un
# dossier exos sur bureau de l'utilisateur.

# Si le paramètre --help est donnée, afficher les options du script.

help="Création de fichiers dans un dossier: -n nombre de fichiers -p destination"

nb_fichiers=0
destination="/home/thomas/exos"

create_files() {
        for (( i=1 ; i<="$nb_fichiers"; i++));
        do
                touch "$destination/fichier-$i"
        done
}

check_path() {
        if [[ ! -e "$destination" ]];
        then
                mkdir -p "$destination"
        fi
}

while getopts 'n:p:h' options ;
do
        case "$options" in
                n)
                        nb_fichiers=$OPTARG
                        ;;
                p)
                        destination=$OPTARG
                        ;;
                h)
                        echo $help
                        break;;
        esac
done


check_path
create_files  
```

