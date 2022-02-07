# Les fonctions

* Une fonction peut être placée n'importe où dans le script, au début comme à la fin, avant comme après son appel.
* Les variables qu'une fonction utilise sont globales par défaut, cela signifie qu'elles sont les mêmes hors et à l'intérieur d'une fonction
* Les fonctions, au même titre qu'un script entier, utilisent les variables spéciales.

## Ecrire une première fonction 

*Création du fichier bash*

```bash 
    $ mkdir hello.sh
    $ chmod +x hello.sh
```

*Edition de nnotre fichier*

```bash 
    function hello {
        echo 'Bonjour'
    }

    hello
```

*Exécution du fichier*

```bash 
    $ ./hello.sh
    bonjour
```

## Passer des paramètre dans une fonction 


*1er exemple:*

```bash 
    function hello {
        echo "Bonjour $1"
    }

    hello "antoine"
```

*Exécution du fichier*

```bash 
    $ ./hello.sh
    bonjour antoine
```

*2éme exemple:*

```bash 
    function hello {
        echo "Bonjour $1, tu as $2 ans"
    }

    hello "antoine" "34"
```

*Exécution du fichier*

```bash 
    $ ./hello.sh
    bonjour antoine, tu as 34 ans
```

## Les variables locales

Comme dit précédemment, les variables par défaut sont globales dans les fonctions, cela se vérifie de la façon suivante :

```bash 
    function ecrire {
        echo "Dans la fonction \$var1 vaut $var1"
        var1="B"
    }
    var1="A"
    echo "Avant la fonction \$var1 vaut $var1"
    ecrire
    echo "Après la fonction \$var1 vaut $var1"
```

*Exécution du fichier*

```bash 
    $ ./ecrire.sh
    Avant la fonction $var1 vaut A
    Dans la fonction $var1 vaut A
    Après la fonction $var1 vaut B
```

**Si on définie et initialise la variable hors de la fonction (en dehors des accolades), la valeur sera la même si on l'appelle (afficher son contenu par exemple avec "echo") dans la fonction qu'à l'extérieur de celle-ci. De la même façon, si on modifie cette variable dans la fonction, la modification est valable pour tout le reste du script après l'appel de la fonction**

Pour définir une variable comme locale (valable uniquement pour l'intérieur de la fonction), on utilisera le terme "local" avant la définition de la fonction comme suivant : 


```bash 
    function ecrire {
        echo "Dans la fonction avant la redéfinition local \$var1 vaut $var1"
        local var1="B"
        echo "Dans la fonction après la redéfinition local \$var1 vaut $var1"
    }
    var1="A"
    echo "Avant la fonction \$var1 vaut $var1"
    ecrire
    echo "Après la fonction \$var1 vaut $var1"
```

*Exécution du fichier*

```bash 
    $ ./ecrire.sh
    Avant la fonction $var1 vaut A
    Dans la fonction avant la redéfinition local $var1 vaut A
    Dans la fonction après la redéfinition local $var1 vaut B
    Après la fonction $var1 vaut A
```