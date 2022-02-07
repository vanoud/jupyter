# Getops

La commande interne getopts permet à un script d'anayser les options passées en argument d'un script bash. Pour getopts, une option est composée d'un caractère précédé du signe "+" ou "-".

Exemple : 

```bash 
    ls -l -a 
```

Comment utiliser `getops` : 

*script.sh*
```bash
    while getopts "abcd:e:" option
    do
            echo "getopts a trouvé l'option $option"
            case $option in
                    a)
                            echo "Exécution des commandes de l'option a"
                            echo "Indice de la prochaine option à traiter : $OPTIND"
                            ;;
                    b)
                            echo "Exécution des commandes de l'option b"
                            echo "Indice de la prochaine option à traiter : $OPTIND"
                            ;;
                    c)
                            echo "Exécution des commandes de l'option c"
                            echo "Indice de la prochaine option à traiter : $OPTIND"
                            ;;
                    d)
                            echo "Exécution des commandes de l'option d"
                            echo "Liste des arguments à traiter : $OPTARG"
                            echo "Indice de la prochaine option à traiter : $OPTIND"
                            ;;
                    e)
                            echo "Exécution des commandes de l'option e"
                            echo "Liste des arguments à traiter : $OPTARG"
                            echo "Indice de la prochaine option à traiter : $OPTIND"
                            ;;
            esac
    done
    echo "Analyse des options terminée"
    exit 0
```

* L'appel à la commande `getopts` récupère l'option suivante et retourne un code vrai tant qu'il reste des options à analyser.
* La liste des options utilisables avec ce script sont définies à la ligne 3 (`getopts "abcd:e:" option`). Il s'agit des options `-a, -b, -c, -d et -e.`
* Le caractère `":"` inscrit après les options `"d"` et `"e"` (getopts "abcd:e:" option)`indique que ces options doivent être suivies obligatoirement d'un argument.
* La variable `"option"` (getopts "abcd:e:" option) permet de récupérer la valeur de l'option en cours de traitement par la boucle while.
* La variable réservée `"$OPTIND"` contient l'indice de la prochaine option à traiter.
* La variable réservée `"$OPTARG"` contient l'argument associé à l'option.

## Option invalide 

Lorsque la commande getopts détecte une option invalide, la variable option est initialisée avec la caractère `"?"` et un message d'erreur est affiché à l'écran.
Les options suivantes sont analysées.


