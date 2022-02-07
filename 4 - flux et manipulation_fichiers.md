# Manipulation des fichiers et des dossiers

* ``man``: Affiche le manuel d'une commande
* ``cd``: Changer de répertoire de travail
* ``cp``: Permet de copier un fichier/répertoire
* ``ls``: Lister le contenu d'un répertoire
* ``mkdir``: Créer un répertoire
* ``tree``: Affichier l'arborescence d'un répertoire
* ``mv``: Déplacer un fichier/répertoire
* ``rm``: Supprimer un fichier
* ``rmdir``: Supprimer un répertoire
* ``touch``: Créer un fichier
* ``echo``: Afficher en sortie standard l'argument de la commande
* ``cat``: Afficher en sortie standard le contenu d'un fichier
* ``pwd``: Afficher le nom du répertoire de travail courant
* ``which``: Afficher l’emplacement d’une commande.
* ``head``: afficher le début d’un fichier (par défaut, les 10 premières lignes).
* ``tail``: Afficher la fin d’un fichier (par défaut, les 10 dernière ligne


## Les flux 

Chaque application lancée en Bash a les flux d'entrée/sortie : 

* L'entrée standard, qui permet d'envoyer des données au programme : ``stdin``
* La sortie standard, qui est utilisée pour afficher les résultats d'un programme : ``stdout``
* La sortie standard des erreurs, qui permet d'afficher les messages correspondant aux erreurs survenues lors de l'exécution du programme : ``stderr```

**Par défaut les deux flux de sortie sont envoyés sur le terminal de l'utilisateur (écran) et l'entrée prend ses données depuis le clavier.**

Les trois flux standards peuvent être redirigés vers d'autres sources autres que le clavier ou l'écran. Par exemple, on peut ordonner à un processus de diriger sa sortie standard vers un fichier. Pour cela, les numéros des descripteurs de flux sont utilisés. Les outils pour réaliser ces redirections sont les suivants :

* ``>`` redirige le flux de sortie de la commande pour la placer dans un fichier. Par défaut, si rien n'est précisé, le flux redirigé est la sortie standard. *``>`` est équivalent à ``1>``. Pour rediriger la sortie d'erreur standard, on utilise ``2>``*.

    *script.sh*
    ```bash
        #!/bin/bash
        echo "Salut"
    ```

    ```bash
        $ ./script.sh > log
        $ cat log
        $ ./toto.sh
        bash: ./toto.sh: Aucun fichier ou dossier de ce type
        $ ./toto.sh 2> log
        $ cat log
        bash: ./toto.sh: Aucun fichier ou dossier de ce type
    ```

* ``<`` redirige le flux d'entrée de la commande pour la prendre dans un fichier

* ``>>`` redirige le flux de sortie de la commande pour l’ajouter à la fin d’un fichier existant.

     *test.txt*
     ```txt
        Bonjour à tous
     ```

     ```bash 
        $ echo "Au revoir" >> test.txt
        $ cat test.txt
        Bonjour à tous
        Au revoir
     ```

### Le cat tautologique

La commande cat recopie l'entrée standard sur la sortie standard. Pour quitter cette commande, utiliser la combinaison de touches CTRL D.
Par défaut, cat prend ses données en entrée ligne par ligne. Ce qui explique qu'à chaque fois que l'on tape entrée, les caractères inscrits sur l'entrée standard via le clavier sont recopiés sur la sortie standard. Cette commande peut prendre un fichier comme entrée standard.

On peut utiliser cat pour créer un fichier texte rapidement, en utilisant la redirection de la sortie standard vers un fichier : 

```bash 
    $ cat > journal
    > Bonjour Antoine
    > Ça va ?
    $ cat journal
    Bonjour Antoine
    Ça va ?
```

Souvent, dans les scripts bash, on utilise l'astuce suivante pour créer un fichier texte dynamiquement : 

```bash 
    $ cat <<FIN > fichier
    > Hey
    > ça Va 
    > moi oui 
    > FIN
    $ cat fichier 
    Hey
    ça Va 
    moi oui 
```

**Pour ajouter du contenu à un fichier, il suffit d'utiliser ``>>``.**

```bash 
    $ cat <<FIN >> fichier
    > Au top 
    > FIN
    $ cat fichier 
    Hey
    ça Va 
    moi oui 
    Au top
```

## Concaténation dans un fichier

*fichier1.txt*
```txt 
    Bonjour à tous
```
*fichier2.txt*
```txt
    Vous allez bien ?
```
```bash
    $ cat fichier2.txt >> fichier1.txt
    $ cat fichier1.txt
    Bonjour à tous
    Vous allez bien ?
```
*Avec une sortie d'erreur*
```bash
    $ cat fichier_introuvable 2>> fichier1.txt
    $ cat fichier1.txt
    Bonjour à tous
    Vous allez bien ?
    cat: fichier_introuvable: No such file or directory
```

## Les pipes

Les pipes permettent de rediriger la sortie standard d'une commande vers l'entrée standard d'une autre commande.

```bash 
    commande1 | commande2
```

ou pour connecter en plus la sortie d'erreur de la commande1 sur l'entrée de la commande2:

```bash 
    commande1 |& commande2
```

Exemple : 

```bash
    $ ls | grep *.sh
```
*Cette commande liste tous les fichiers d'un répertoire et ne selectionne que les fichiers ayant comme extension .sh*




