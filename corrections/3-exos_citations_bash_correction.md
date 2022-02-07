1.

[tux]$ echo a b     
a b 
[tux]$ echo a   b   
a b 
[tux]$ echo "a   b" 
a   b 
[tux]$ echo 'a   b'  
a   b 
[tux]$ echo a\ \ \ b 
a   b 
Les arguments de la commande echo (qui peuvent être séparés par plusieurs espaces) sont affichés sur la sortie, séparés par un seul espace.

 

Dans le cas des deux premières commandes (sans les caractères de citation ", ’ et \), les espaces font office de séparateurs d’arguments ; il y a donc deux arguments.

Pour les trois dernières commandes, la fonction de séparateur d’arguments des caractères espaces est désactivée par les caractères de citation ; il n’y a donc qu’un seul argument.

2.

[tux]$ cd / 
[tux]$ echo * 
bin boot dev etc home initrd lib lost+found media misc mnt net 
opt proc root sbin selinux srv sys tmp usr var 
La commande affiche tous les noms de fichiers présents dans le répertoire courant, car le caractère générique * est interprété par le shell (motif représentant tous les noms de fichiers du répertoire courant), puis les arguments ainsi générés sont affichés par la commande echo (chaque argument de la commande echo étant séparé en sortie par un espace).

3.

Il y a plusieurs manières d’afficher la chaîne de caractères "le caractère * est un caractère générique", suivant les caractères de citation employés :

[tux]$ echo "le caractère * est un caractère générique" 
le caractère * est un caractère générique 
[tux]$ echo 'le caractère * est un caractère générique'  
le caractère * est un caractère générique 
[tux]$ echo le caractère \* est un caractère générique   
le caractère * est un caractère générique 

4.

[tux]$ echo 'la variable référencée par $var3'  
la variable référencée par $var3 
[tux]$ echo la variable référencée par \$var3   
la variable référencée par $var3 
Les guillemets ne peuvent pas être employés ici car ils ne désactivent pas les caractères spéciaux $, ` et /.