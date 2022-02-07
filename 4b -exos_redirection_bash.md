
1. Exécutez la commande cat sans arguments, puis tapez quelques mots et terminez-la normalement. Que constatez-vous ?

2. Exécutez la commande wc sans arguments, puis tapez quelques mots et terminez-la normalement. Que constatez-vous ?

3. Utilisez la commande cat pour afficher le contenu du fichier /etc/hosts de deux manières : en passant le nom du fichier en argument, puis en utilisant une redirection.

4. Utilisez la commande wc pour compter le nombre de lignes du fichier /etc/passwd de deux manières : en passant le nom du fichier en argument, puis en utilisant une redirection. Que constatez-vous ?

5. Utilisez la commande cat pour écrire quelques mots dans le fichier /tmp/ficcat.

6. Utilisez la commande cat sans argument pour copier le fichier /tmp/ficcat en /tmp/ficcat2.

7. Utilisez la commande cat pour ajouter quelques mots au fichier /tmp/ficcat existant.

8. Utilisez la commande cat pour concaténer le contenu des fichiers /tmp/ficcat et /etc/hosts dans le fichier /tmp/ficcat3.

9. Allez dans le répertoire /etc et redirigez la sortie de la commande ls dans le fichier /tmp/ls.out. Que contient ce fichier ?

10. Utilisez la commande wc sans argument pour compter le nombre de lignes contenues dans le fichier /tmp/ls.out.

11. Combien y a-t-il de fichiers dans le répertoire /etc ? Supprimez le fichier /tmp/ls.out.

12. Sans utiliser de fichier intermédiaire, comptez de nouveau le nombre de fichiers présents dans le répertoire /etc.

13. En employant un tube (ou "pipe"), comptez de nouveau le nombre de fichiers présents dans le répertoire /etc, tout en écrivant le résultat de la commande ls dans le fichier /tmp/ls.out.

14. Exécutez la commande ls /etc/passwd glop et notez son résultat.

15. Exécutez la commande ls /etc/passwd glop en redirigeant les sorties dans le fichier /tmp/ls.out et les messages d’erreur dans le fichier /tmp/ls.err.

16. Exécutez la commande ls /etc/passwd glop en redirigeant les sorties dans le fichier /tmp/ls.out et en supprimant les messages d’erreur.

17. Exécutez la commande ls /etc/passwd glop en redirigeant les sorties et les messages d’erreur dans le fichier /tmp/ls.out.

Indices

5. Redirigez la sortie de la commande avec le caractère >.

6. Redirigez l’entrée de la commande avec le caractère < et la sortie avec le caractère >.

7. Redirigez la sortie de la commande avec les caractères >>.

8. Redirigez la sortie de la commande avec le caractère >.

10. Redirigez l’entrée de la commande avec le caractère <.

12. Utilisez un tube (ou "pipe") : caractère |.

13. Utilisez la commande tee pour générer une sortie intermédiaire.

15. Redirigez la sortie de la commande avec le caractère >, et l’erreur avec les caractères 2>.

16. Redirigez les messages d’erreur de la commande dans le fichier spécial /dev/null.

17. Redirigez les messages d’erreur de la commande au même endroit que la sortie avec les caractères 2>&1.