# Grep 

Le logiciel grep est un outil indispensable tant pour l’administrateur système que pour le programmeur.

Il permet de parcourir des fichiers pour rechercher les lignes qui contiennent une expression rationnelle.

Voici sa syntaxe habituelle : ``grep [options] expression fichiers...``

## Les flags

* ``-E`` : les expressions régulières sont étendues ; par défaut, grep emploi des expressions rationnelles simples.
* ``-F`` : l’expression recherchée n’est pas une expression régulière mais une simple chaîne de caractères.
* ``-i`` : ignorer les différences entre majuscules et minuscules.
* ``-v`` : afficher les lignes qui ne contiennent pas l’expression rationnelle.
* `-o`: N'affiche que le résultat de l'expression régulière 

```bash 
    $ grep root /etc/passwd
    root:x:0:0:root:/root:/bin/bash
    operator:x:11:0:operator:/root:/sbin/nologin
```

# Les expressions régulières

* Les expressions régulières se révèlent un support essentiel pour un bon nombre d’utilitaires Unix.
* Elles sont à la base de l’outil grep, que nous allons étudier dans ce chapitre, mais elles servent aussi de fondement pour les langages Sed et Awk
* Dans les expressions rationnelles simples, ces métacaractères sont : ``^ $ . [ ] * \ | ? { } +``

*animaux.txt*
```txt
chien
chat
cheveaux
koala
dauphin
balaine
escargot
```

Exemple de recherche sur ce fichier texte : 

> ``^`` Début de ligne
```bash
    $ grep ^ch animaux.txt 
    chien 
    chat 
    cheveaux
```

> ``$`` Fin de ligne
```bash
    $ grep ot$ animaux.txt 
    escargot
```

> ``. (point)`` Un caractère quelconque de la chaine de caractère
```bash
    $ grep ch..n animaux.txt 
    chien
```

> ``[liste_de_caractères]`` Un caractère cité dans la liste
```bash
    $ grep [db]a animaux.txt
    dauphin
    balaine
```

> ``[^liste_de_caractères]`` Un caractère qui n'est pas cité dans la liste
```bash
    $ grep ch[^i] animaux.txt 
    chat 
    cheveaux
```

> ``[a-z]`` Caractères minuscules de a à z.

> ``[0-9]`` Chiffres de 0 à 9.

> ``[a-e0-9]`` Lettres de « a » à « e » ou chiffres de 0 à 9.

> ``[^0-9]`` Chaîne ne contenant PAS de chiffres.
```bash
    $ grep ch[a-e] animaux.txt 
    chat 
    cheveaux
```

> ``|`` Le caractère |, indique une alternative entre deux caractères.
```bash
    $ grep 'chi\|cha' animaux.txt
    chien
    chat
```

> ``e+`` « e » doit apparaître au moins 1 fois.
```bash
    $ grep 'e\+' animaux.txt
    chien 
    cheveaux
    balaine
    escargot
```

> ``e{2}`` e doit appraître exactement 2 fois (ee)

> ``e{1,3}`` e doit appraître de 1 à 3 fois

> ``e{1,}`` e doit appraître au moins 1 fois

## Compter le nombre d'occurence avec grep 

Vous pouvez ajoute `wc -l` à votre grep pour compter le nombre d'occurence : 

```bash 

    grep 'e\+' animaux.txt | wc -l
    4

```