1. Allez dans le répertoire /etc.

2. Listez tous les fichiers dont le nom commence par la lettre "r". Le résultat de la commande est-il bien celui attendu ?

3. Listez de nouveau tous les fichiers dont le nom commence par la lettre "r" sans afficher le contenu des répertoires correspondants.

4. Affichez tous les fichiers dont le nom contient la chaîne de caractères "rc".

5. Affichez tous les fichiers dont le nom comporte trois caractères.

6. Affichez tous les fichiers dont le nom commence par la chaîne de caractères "rc", suivie d’un caractère quelconque, et se terminant par la chaîne de caractère ".d".

7. Affichez les fichiers dont les noms sont rc2.d, rc3.d, et rc4.d.

8. Affichez tous les fichiers dont le nom ne commence pas par les lettres "a", "b" et "c".

9. Affichez tous les fichiers dont le nom commence par une lettre majuscule.

10. Listez tous les fichiers dont le nom se termine par la chaîne de caractères "conf" ou "config".

11. Listez tous les fichiers dont le nom :

- commence par une minuscule,

- suivie d’un nombre quelconque de caractères,

- suivis de la lettre "a", puis obligatoirement d’un autre caractère,

- suivi de l’extension ".conf" ou ".config".

>Indices

2. Utilisez le caractère générique *.

3. Utilisez la commande ls avec l’option adéquate.

5. Utilisez le caractère générique ?.

7. Utilisez les caractères génériques [].

9. Utilisez la classe de caractères [:upper:]. Il est aussi possible d’utiliser le motif [A - Z], mais il faut dans ce cas s’assurer du comportement de Bash qui dépend de la langue utilisée pour distinguer les majuscules des minuscules ; pour avoir un comportement standard, le plus simple est de définir la variable LC_ALL à C (POSIX) avec la commande export LC_ALL = C.

10. Utilisez les caractères génériques {}.

11. Utilisez tous les caractères génériques vus précédemment et la classe de caractères [:lower:].