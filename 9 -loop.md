# Les boucles 

les boucles permettent de répéter autant de fois que nécessaire une partie du code.

## While (Tant que)

```bash 
    #! /bin/bash
    while [ test ]
    do
        echo 'Action en boucle'
    done
```
```bash
    #!/bin/bash
    nbr=0
    while ((nbr!=53))
    do
            echo -e "Saisir 53 : \c"
            read nbr
    done
    exit 0
```

## For

La boucle for permet de parcourir une liste de valeurs et de boucler autant de fois qu'il y a de valeurs.

```bash
    #! /bin/bash
    for variable in 'valeur1' 'valeur2' 'valeur3'
    do
        echo "La variable vaut $variable"
    done
```

On peu utiliser aussi des variables : 

```bash 
    #! /bin/bash
    liste_fichiers=`ls`
    for fichier in $liste_fichiers
    do
        echo "Fichier trouvé : $fichier"
    done
```

Utiliser une suite de nombre : 

```bash 
    #! /bin/bash
    for i in `seq 1 10`
    do
        echo $i
    done
```