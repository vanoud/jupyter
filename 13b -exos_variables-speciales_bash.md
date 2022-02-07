
1. Dans votre répertoire bin, créez le script shell 02varspec qui effectue les opérations suivantes :

- Afficher le nom du script shell

- Afficher le PID du script shell.

- Afficher le PID du processus père.

Chaque affichage doit être précédé d’un énoncé (par exemple pour le nom du script : mon nom est : "nom du script shell").

Puis modifiez les droits du fichier de façon à l’instancier par son nom.

2. Affichez le PID de votre shell courant, puis exécutez le script 02varspec des trois manières suivantes :

- bash 02varspec

- 02varspec

./02Varspec

Les résultats sont-ils ceux attendus ?

3. Copiez le script 02varspec en 03param et modifiez ce dernier de façon à :

- afficher le nombre d’arguments passés sur la ligne de commandes,

- afficher les trois premiers paramètres positionnels.

4. Testez votre script shell 03param avec les arguments suivants :

- a b c d

- "a b" c d

- a b c\ d

- a ’b c’ d

5. Ajoutez les opérations suivantes dans le script 03param :

- Décaler les paramètres positionnels de deux rangs.

- Afficher de nouveau les trois premiers paramètres positionnels.

- Testez de nouveau le script avec les arguments suivants :

- a b c d

6. Modifiez le script 03param comme suit :

Afficher le onzième paramètre positionnel en plus des trois premiers.

Afficher l’ensemble des paramètres positionnels avant et après le décalage avec la commande shift.

Testez le script avec les arguments suivants :

a b c d e f g h i j k l m o

Indices

1. Utilisez respectivement les variables $0, $$ et PPID pour obtenir le nom, le PID, et le PID du père du script shell.

Utilisez la commande chmod pour modifier les droits du fichier.

3. Le nombre de paramètres positionnels est contenu dans la variable spéciale $# ; les paramètres positionnels sont quant à eux contenus dans les variables $1, $2, $3...

5. Utilisez la commande shift.

6. Utilisez la syntaxe ${} pour référencer le onzième paramètre positionnel.

Les variables spéciales $* et $@ contiennent, toutes les deux, l’ensemble des paramètres positionnels passés sur la ligne de commandes.