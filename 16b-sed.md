# Sed

Sed est un outil souvent mal connu des personnes récemment venues à l’informatique, et plus particulièrement au système Unix.

Cet utilitaire peut rendre de grands services au sein de scripts shell qui automatisent des tâches administratives, mais également pour manipuler des fichiers de texte, par exemple des pages HTML.

Le programme sed va agir sur les lignes d’un fichier de texte ou de son entrée standard, et fournir les résultats sur sa sortie standard. En conséquence, les instructions de manipulation doivent être fournies dans des fichiers de scripts indépendants, ou en ligne de commande. La syntaxe d’invocation est la suivante :

```bash
    $ sed -e ’liste_d_instructions’ fichier_à_traiter
```
ou 
```bash
    $ sed -f fichier_script fichier_à_traiter
```

* Si aucun fichier à traiter n’est indiqué, sed attend les données sur son entrée standard.
* Lorsqu’on fournit directement les commandes sur la ligne, grâce à l’option -e, il est préférable de les inclure entre apostrophes simples, en raison de l’usage fréquent des caractères $, *, ?, etc., susceptibles d’être interprétés par le shell.
* Une option importante est également disponible : -n, avec laquelle sed fonctionne en mode silencieux, c’est-à-dire qu’il ne copie une ligne de texte de l’entrée standard vers la sortie standard que si on le lui demande explicitement, et non pas automatiquement comme c’est le cas par défaut. Nous détaillerons cela ultérieurement.

## Fonctionnement de Sed

* Lecture d’une ligne sur le flux d’entrée (jusqu’à ce qu’il rencontre un caractère de saut de ligne).
* Traitement de cette ligne en la soumettant à toutes les commandes rencontrées dans le fichier script.
* Affichage de la ligne résultante sur la sortie standard, sauf si sed est invoqué avec l’option –n.
* Passage à la ligne suivante, et ainsi de suite jusqu’à la fin du flux d’entrée standard.


## Utilisation de sed

Tous d'abord nous allons créer un fichier texte : `text.txt`

```txt
    Bonjour,

    Ceci est un fichier de test.
    Ici la ligne numéro 4.

    # ceci pourrait être un commentaire
    Ici la ligne numéro 7.

    Au revoir
```

Nous allons faire nos premiers tests en affichant les résultats de sed dans la console.

```bash 
    $ sed '' test.txt
    Bonjour,

    Ceci est un fichier de test.
    Ici la ligne numéro 4.

    # ceci pourrait être un commentaire
    Ici la ligne numéro 7.

    Au revoir
```
sed lancé avec un script vide renvoie simplement le contenu du fichier.

## Adressage
#### Adressage par ligne 

Executez la commande `sed -e '4d; 7d' test.txt`

```bash 
    $ sed -e '4d; 7d' test.txt
    Bonjour,

    Ceci est un fichier de test.

    # ceci pourrait être un commentaire

    Au revoir
```

Ici, nous utilisons l'adressage par ligne. La commande `d (delete)` indique que l'on va supprimer la ligne.

**L'option `-e` permet de passer plusieurs commandes à la suite. Je pense que c'est une bonne habitude de l'ajouter de façon systématique.**

On peut aussi utiliser l'adressage par intervalle, comme ceci : `sed '4,7 d' test.txt`

```bash 
    $ sed '4,7 d' test.txt
    Bonjour,

    Ceci est un fichier de test.

    Au revoir
```

Cette commande va effacer toutes les lignes comprises entre la ligne 4 et la ligne 7.

```bash 
    sed -re '/^$/d' test.txt 
    Bonjour,
    Ceci est un fichier de test.
    Ici la ligne numéro 4.
    # ceci pourrait être un commentaire
    Ici la ligne numéro 7.
    Au revoir
```
Cette commande va effacer toutes les lignes vide.

#### Adressage par motif

On peut aussi utiliser des regex pour appliquer la commandes sur toutes les lignes ou le motif est trouvé.

```bash
    $ sed '/^#/d' test.txt
    Bonjour,

    Ceci est un fichier de test.
    Ici la ligne numéro 4.

    Ici la ligne numéro 7.

    Au revoir
```

`sed '/^#/ d' test.txt` supprimera toutes les lignes commençant par une dièse (le ^ est un métacaractère signifiant début de ligne).

On peut très bien aussi utiliser un adressage mixte, comme : 

```bash 
    $ sed '/^#/,7 d' test.txt
    Bonjour,

    Ceci est un fichier de test.
    Ici la ligne numéro 4.


    Au revoir
```

## Mode silencieux

Il existe une autre façon d'utiliser sed, particulièrement intéressante. C'est l'utilisation en mode "silencieux", c'est-à-dire que sed ne doit afficher par défaut aucune ligne. Seules les lignes intéressantes seront affichées, avec la commande p (print). Pour passer en mode "silencieux", il faut utiliser l'option sed `-n`

```bash 
    $ sed -n '/Ici/p' test.txt
    Ici la ligne numéro 4.
    Ici la ligne numéro 7.
```

## Substitution, translittération

### Substitution

sed permet de remplacer du texte avec des regex. On peut utiliser la syntaxe habituelle, ou la syntaxe étendue avec `sed -r`

La substitution s'écrit comme ceci : `s/motif/substitut/`

Par défaut, elle s'effectue sur la première occurrence du motif, sauf si on lui ajoute l'option g comme ceci : `s/motif/substitut/g`

On peut aussi choisir l'occurrence voulue, avec par exemple `s/motif/substitut/2` pour la deuxième occurrence.

Exemple : 

```bash 
    $ sed -re 's/^# *//' test1.txt 
    Bonjour,

    Ceci est un fichier de test.
    Ici la ligne numéro 4.

    ceci pourrait être un commentaire
    Ici la ligne numéro 7.

    Au revoir
```
Cette commande décommente les lignes commentées (commençant par une dièse), et supprime les espaces en début de ligne (le * est un métacaractère signifiant 0 ou plus).

```bash 
    $ sed -re 's/o/i/g' test.txt 
    Binjiur,

    Ceci est un fichier de test.
    Ici la ligne numéri 4.

    # ceci piurrait être un cimmentaire
    Ici la ligne numéri 7.

    Au reviir
```

Cette commande remplace tous les o par des i. 

```bash 
    $ sed -re 's/ //g' test.txt 
    Bonjour,

    Ceciestunfichierdetest.
    Icilalignenuméro4.

    #cecipourraitêtreuncommentaire
    Icilalignenuméro7.

    Aurevoir
```

Cette commande supprime tous les espaces

### Translittération

La translittération permet d'échanger certains caractères avec d'autres caractères.

On l'écrit comme ceci : `y/liste1/liste2/`

```bash 
    $ sed -re 'y/éèê/eee/' test.txt
    Bonjour,

    Ceci est un fichier de test.
    Ici la ligne numero 4.

    # ceci pourrait etre un commentaire
    Ici la ligne numero 7.

    Au revoir
```

Cette commande supprime les accents sur les e dans notre fichier test.txt.

## Commandes groupées

Sed permet de grouper les commandes avec des accolades. Cela permet de faire plus de choses dans une même commande.

```bash 
    $ sed -re 's/ //g;/^$/d' test.txt 
    Bonjour,
    Ceciestunfichierdetest.
    Icilalignenuméro4.
    #cecipourraitêtreuncommentaire
    Icilalignenuméro7.
    Aurevoir
```

Cette commande supprime les espaces et les lignes blanches


