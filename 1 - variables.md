# Les variables

* La programmation sous shell nécessite naturellement des variables pour stocker des informations temporaires, accéder à des paramètres, etc.
* Par défaut, les variables utilisées dans les scripts shell ne sont pas typées. (INT,BOOLEAN, FLOAT, DIC...)
* Le contenu d’une variable est considéré comme une chaîne de caractères, sauf si on indique explicitement qu’elle doit être traitée comme une variable entière qui peut être utilisée dans des calculs arithmétiques.
* À la différence des langages compilés habituels, une variable n’a pas à être déclarée explicitement. Dès qu’on lui affecte une valeur, elle commence à exister. Cette affectation prend la forme variable=valeur sans espaces autour du signe égal.

*Création d'une variable*

```bash 
    $ i=12
    $ echo $i
    12
```

```bash 
    $ variable="Bonjour Antoine"
    $ echo $variable
    Bonjour Antoine
```

**Le nom attribué à une variable peut contenir des lettres, des chiffres, ou le caractère souligné « _ ». Il ne doit toutefois pas commencer par un chiffre.**

## Les retours à la ligne 

Si vous voulez insérer des retours à la ligne, il faudra activer le paramètre ``-e`` et utiliser le symbole ``\n`` :

```bash 
    $ variable="Bonjour\nAntoine"
    $ echo -e $variable
    Bonjour 
    Antoine
```

## Les quotes 

Il est possible d'utiliser des quotes pour délimiter un paramètre contenant des espaces. Il existe trois types de quotes :

* les apostrophes ' ' (simples quotes)
* les guillemets " " (doubles quotes)
* les accents graves ` ` (back quotes)

#### Les simples quotes ' '

Avec de simples quotes, la variable n'est pas analysée et le ``$`` est affiché tel quel.

```bash 
    $ variable="Antoine Fissot"
    $ echo 'Bonjour $variable'
    Bonjour $variable
```

#### Les doubles quotes " "

Les doubles quotes demandent à bash d'analyser le contenu du message. S'il trouve des symboles spéciaux (comme des variables), il les interprète.

```bash 
    $ variable="Antoine Fissot"
    $ echo "Bonjour $variable"
    Bonjour Antoine Fissot
```

#### Les back quotes ``

Un peu particulières, les back quotes demandent à bash d'exécuter ce qui se trouve à l'intérieur.

```bash 
    $ variable=`pwd`
    $ echo "Vous êtes dans le dossier : $variable"
    Vous êtes dans le dossier : /root
```

La commande pwd a été exécutée et son contenu inséré dans la variable message ! Nous avons ensuite affiché le contenu de la variable.

## Vérifier si une variable est définie et non vide

La construction ``${variable:+valeur}`` renvoie la valeur fournie à droite du symbole ``:+`` si la variable est définie et non vide, sinon elle renvoie une chaîne vide.

```bash 
    $ variable="Antoine"
    $ echo ${variable:+1}
    1
    $ echo ${toto:+1}
    
    $
    $
```


## Connaitre la longueur d'une chaine d'une variable


```bash 
    $ variable=Antoine
    $ echo variable
    Antoine
    $ echo "La chaine contient ${#variable} caractères"
    La chaine contient 7 caractères
    $
```

## Extraction de sous-chaînes et recherche de motifs

Les shells récents offrent une possibilité d’extraction automatique de sous-chaînes de caractères au sein d’une variable. La version la plus simple s’appuie sur l’option ``:`` de l’opérateur ``${}``. Ainsi l’expression ``${variable:debut:longueur}``

```bash 
    $ variable=ABCDEFGHIJKLMNOPQRSTUVWXYZ
    $ echo ${variable:5:2}
    FG
    $ echo ${variable:20}
    UVWXYZ
    $
```

## Manipuler des chaines de caractères

Prenons en compte cette variable : 

```bash 
    $ variable="col1|col2|col3|col4|col5"
```
*Cette variable est constituée de 5 segments délimités par le caractère |*

#### Exclure le premier segment

`${variable#modele}`

* `modele` est une chaine de caractère incluant les caractères spéciaux : 
    * *, 
    * ?, 
    * [ ], 
    * ?(expression), 
    * +(expression), 
    * *(expression), 
    * @(expression), 
    * !(expression)
* Le caractère # signifie "Chaine la plus courte possible en partant de la gauche"

```bash 
    $ echo ${variable#*|}
```

#### Conserver le premier segment

`${variable%%modele}`

Les caractères `%%` signifient "Chaine la plus longue possible en partant de la droite"

```bash 
    $ echo ${variable%%|*}
```

#### Conserver le dernier segment

`${variable##modele}`

Les caractères `##` signifient "Chaine la plus longue possible en partant de la gauche"

```bash 
    $ echo ${variable##*|}
```

#### Exclure le dernier segment

`${variable%modele}`

Le caractère `%` signifie "Chaine la plus courte possible en partant de la droite"

```bash 
    $ echo ${variable%|*}
```

## Calcul arithmétique

Les calculs arithmétiques sont représentés par l’opérateur ``$((opérations))``. Il est déconseillé d’utiliser sa forme ancienne, ``$[opérations]``, car elle est considérée comme obsolète.

```bash 
    $ echo $((2 * (4 + (10/2)) - 1))
    17
    $ echo $((7 % 3))
    1
```

#### Utiliser une variable pour nos calculs

```bash 
    $ a=1
    $ b=2
    $ echo $(($a + $b))
    3
```

**Avec le mot clé ``let``**


```bash 
    $ let 'a = 1'
    $ let 'b = 2'
    $ let 'c = a + b'
    $ echo $c
    3 
```

La commande let est équivalente à ((expression))

## Demander une saisie : read 

Vous pouvez demander à l'utilisateur de saisir du texte avec la commande read. Ce texte sera immédiatement stocké dans une variable.

```bash 
    $ read variable
    $ echo "Bonjour $variable"
    antoine
    Bonjour antoine
```
*Notez que la première ligne correspond au texte que j'ai tapé au clavier.*

#### Affecter simultanément une valeur à plusieurs variables 

```bash 
    $ read nom prenom
    $ echo "Bonjour $nom $prenom"
    Fissot Antoine
    Bonjour Fissot Antoine
```

#### Flags

* ``-p`` : Afficher un message de prompt 

```bash 
    $ read -p 'Entrez votre prénom : ' prenom
    $ echo "Bonjour $prenom"
    Antoine
    Bonjour Antoine
```

* ``-n`` : Limiter le nombre de caractères

```bash 
    $ read -p 'Entrez votre login (5 caractères max): ' -n 5 login
    $ echo -e "\nBonjour $login"
    Entrez votre login (5 caractères max): Antoi
    Bonjour Antoine
```

* ``-t`` : Limiter le temps autorisé pour saisir un message (Valeur en seconde)

* ``-s`` : Ne pas afficher le texte saisi


## Les variables d'environnement

Actuellement, les variables que vous créez dans vos scripts bash n'existent que dans ces scripts.
Les variables d'environnement sont des variables que l'on peut utiliser dans n'importe quel programme. On parle aussi parfois de variables globales. Vous pouvez afficher toutes celles que vous avez actuellement en mémoire avec la commande ``env``

### Définir une variable global 

La commande ``export`` permet de propager une variable "au dela" du programme ou du terminal dans laquelle elle a été créé.

```bash 
    $ a=jesuisunevariable
    $ echo $a
    jesuisunevariable
    $ bash
    $ echo $a

    $ a=jesuisunevariable
    $ echo $a
    jesuisunevariable
    $ export a
    $ bash
    $ echo $a
    jesuisunevariable
    $
```

## Les variables des paramètres

Comme toutes les commandes, vos scripts bash peuvent eux aussi accepter des paramètres. Ainsi, on pourrait appeler notre script comme ceci :

```bash 
    $ ./script.sh param1 param2 param3
```

Par défault, quand on passe des paramètres à notre script bash, automatiquement bash crée des variables. Les voicis : 

* ``$#`` : contient le nombre de paramètres ;
* ``$0 ``: contient le nom du script exécuté (ici ./variables.sh) ;
* ``$1 ``: contient le premier paramètre ;
* ``$2 ``: contient le second paramètre ;
* … ;
* ``$9`` : contient le 9e paramètre.


```bash 
    #!/bin/bash

    echo "Vous avez executez le script : $0. Il contient $# paramètre(s)"
    echo "Voici le paramètre 2 : $2"
```

```bash 
    $ ./script.sh antoine fissot toto
    Vous avez executez le script : ./script.sh. Il contient 3 paramètre(s)
    Voici le paramètre 2 : fissot
```

**Utilisation de la commande ``shift`` :**

``shift`` permet de decaler les paramètres. Il est généralement utiliser dans les boucles avec des scripts comprennent beaucoups de paramètres. 

```bash 
    #!/bin/bash

    echo "Le paramètre 1 est $1"
    shift
    echo "Le paramètre 1 est maintenant $1" 
```
```bash 
    $ ./script.sh antoine fissot toto
    Le paramètre 1 est antoine
    Le paramètre 1 est maintenant fissot
```


## Les tableaux 

On peut définir des tableaux en bash : 

```bash 
    $ tab=('val1', 'val2', 'val3')
```

Puis acceder à un élément du tableau : 

```bash 
    $ echo ${tab[2]}
    val3
```

Vous pouvez aussi définir manuellement le contenu d'une case : 

```bash 
    $ tab[2]=val5
    $ echo ${tab[2]}
    val5
```

Pour affcher l'ensemble du contenu d'un tableau : 

```bash
    $ echo ${tab[*]}
    val1, val2, val5
```


