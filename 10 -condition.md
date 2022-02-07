# Les conditions 

## If 

Le type de condition le plus courant est le if, qui signifie « si ».

```bash
#! /bin/bash
    if [ test ]
    then
        echo "C'est vrai"
    else
        echo "C'est faux"
    fi
```

## Elif 

Il existe aussi le mot cléelif, abréviation de « else if », qui signifie « sinon si ».

```bash 
#! /bin/bash
    if [ test ]
    then
        echo "Le premier test a été vérifié"
    elif [ autre_test ]
    then
        echo "Le second test a été vérifié"
    elif [ encore_autre_test ]
    then
        echo "Le troisième test a été vérifié"
    else
        echo "Aucun des tests précédents n'a été vérifié"
    fi
```

## Les tests 

Trois types de test bash éxistent : 

* Des tests sur des chaînes de caractères.
* Des tests sur des nombres.
* Ses tests sur des fichiers.

### Voici la liste des opérateurs de conditions : 

#### test chaine de caractère

* ``[-n chaîne]`` Retourne vrai si la chaîne de caractères n’est pas vide.
* ``[-z chaîne]`` Retourne vrai si la chaîne de caractères est vide.
* ``[ chaîne1 = chaîne2 ]`` Retourne vrai si les deux chaînes de caractères sont égales
* ``[ chaîne1 != chaîne2 ]`` Retourne vrai si les deux chaînes de caractères sont différentes.

#### test arithmétique

* ``[valeur1 -eq valeur2]`` Retourne vrai si les deux valeurs arithmétiques sont égales (equal).
* ``[valeur1 -ne valeur2]`` Retourne vrai si les deux valeurs arithmétiques sont inégales (not equal).
* ``[valeur1 -lt valeur2]`` Retourne vrai si valeur1 est strictement inférieure à valeur2 (lowerthan).
* ``[valeur1 -le valeur2]`` Retourne vrai si valeur1 est inférieure ou égale à valeur2 (loweror equal).
* ``[valeur1 -gt valeur2]`` Retourne vrai si valeur1 est strictement supérieure à valeur2 (greaterthan).
* ``[valeur1 -ge valeur2]`` Retourne vrai si valeur1 est supérieure ou égale à valeur2 (greateror equal).

#### test sur des fichiers

* ``[ -f <nom> ] `` Retourne vrai si le fichier est de type standard (file)
* ``[ -d <nom> ] `` Retourne vrai si le fichier est de type répertoire (directory)
* ``[ -r <nom> ] `` Retourne vrai si l’utilisateur possède le droit de lire le fichier (read) 
* ``[ -w <nom> ] `` Retourne vrai si l’utilisateur possède le droit de modifier le fichier (write).
* ``[ -x <nom> ] `` Retourne vrai si l’utilisateur possède le droit d’exécuter le fichier (ou de le traverser dans le cas d’un répertoire) (execute).
* ``[ -e <fichier> ] `` Retourne vrai si le fichier existe (exist).
* ``[ -s fichier ] `` Retourne vrai si le fichier n’est pas vide (size).
* ``[<fichier1> -nt <fichier2>] `` Retourne vrai si fichier 1 est plus récent que fichier2(newerthan).
* ``[ <fichier1> -ot <fichier2> ] `` Retourne vrai si fichier 1 est plus ancien que fichier2(olderthan).
* ``[ <fichier1> -ef <fichier2> ] `` Retourne vrai si fichier 1 est identique à fichier2(equalfile), c’est-à-dire que ces deux fichiers possèdent le même inode.

#### Les opérateurs logiques 

* ``!`` : Retourne vrai si l’expression est fausse, et inversement
* ``expression1 -a expression2`` :  -a (and) représente le "et logique" entre expression1 et expression2
```bash 
    #!/bin/bash
    if [ $1 = 'chien' -a $i -ge 5  ]
    then
        echo "ça marche"
    else
        echo "ça marche pas"
    fi
```

*Il existe une autre manière de l'écrire :*

```bash 
    #!/bin/bash
    if [ $1 = 'chien' ] && [ $i -ge 5  ]
    then
        echo "ça marche"
    else
        echo "ça marche pas"
    fi
```

* ``expression1 -o expression2`` -o (or) représente le "ou logique" entre expression1 et expression2
```bash 
    #!/bin/bash
    if [ $1 = 'chien' -o $i -ge 5  ]
    then
        echo "ça marche"
    else
        echo "ça marche pas"
    fi
```

*Il existe une autre manière de l'écrire :*

```bash 
    #!/bin/bash
    if [ $1 = 'chien' ] || [ $i -ge 5  ]
    then
        echo "ça marche"
    else
        echo "ça marche pas"
    fi
```

## Case

Le rôle decaseest de tester la valeur d'une même variable, mais de manière plus concise et lisible.

```bash
    case $variable in 
        "val1") 
            <TRAITEMENT>
            ;;
        "val2") 
            <TRAITEMENT>
            ;;
        *) 
            <TRAITEMENT>
            ;;
    esac
```

##### Exemple : 

```bash 
    #!/bin/bash
    case $1 in 
        "--run" | "-r")
            echo "Je démarre le programme"
            ;;
        "--stop" | "-s")
            echo "J'arrête le programme"
            ;;
        "--delete" | "-d")
            echo "Je supprime le programme"
            ;;
        "--help" | "-h")
            echo "J'affiche les commandes disponibles"
            ;;
        *) 
            echo "Commande inconnu"
            ;;
    esac
```


## Différence entre [ ] et [[ ]]

* `[` est une commande et est soumise aux mêmes règles que toutes les autres commandes que le shell exécute.
* `[[` est un mot-clé, pas une commande, cependant, le shell le traite spécialement et il fonctionne selon des règles très différentes.