1.
Appuyez sur les touches [Ctrl]-[Alt]-[F3], puis :

localhost login: tux 
Password: <le mot de passe n'apparaît pas> 
[tux]$ 

2.
[tux]$ cd 
[tux]$ mkdir bin 
[tux]$ cd bin 
[tux]$ pwd 
/home/tux/bin 

3.
[tux]$ cat > 01appel   
var="abc" 
echo "la variable \$var a pour valeur : $var" 
sleep 3 

4.
[tux]$ bash 01appel  
la variable $var a pour valeur : abc 
[tux]$ echo $var 
 
[tux]$ 
La variable var n’est pas définie dans l’environnement courant car le script 01appel s’est exécuté dans un shell fils.

5.
[tux]$ 01appel 
-bash: 01appel: command not found 
[tux]$ echo $PATH 
/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/usr/X11R6/bin 
[tux]$ ./01appel 
-bash: ./01appel: Permission non accordée 
Pour que le script shell puisse être invoqué de cette manière, il faut spécifier son chemin s’il n’est pas présent dans un des répertoires listés par la variable d’environnement PATH, et modifier ses droits pour le rendre exécutable.

6.
[tux]$ chmod u+x 01appel  
[tux]$ PATH=$PATH:/home/tux/bin 
[tux]$ echo $PATH 
/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/usr/X11R6/bin:/home/tux/bin 

7.
[tux]$ ./01appel  
la variable $var a pour valeur : abc 
[tux]$ echo $var 
 
[tux]$ 
Comme précédemment, la variable var n’est pas définie dans l’environnement courant car le script 01appel s’est exécuté dans un shell fils.

8.
Le shell appelé implicitement pour exécuter le script est le shell par défaut de l’utilisateur, soit le Bash sous Linux.

Après modification pour imposer le shell Bash comme interpréteur, cela donne :

[tux]$ cat 01appel  
#!/bin/bash 
var="abc" 
echo "la variable \$var a pour valeur : $var" 
sleep 3 

9.
[tux]$ . 01appel  
la variable $var a pour valeur : abc 
[tux]$ echo $var 
abc 
[tux]$ 
Cette fois-ci, le script 01appel a été interprété par le shell courant, comme si les commandes qu’il contient avaient été saisies à partir du clavier. La variable var est donc définie et contient la chaîne de caractères "abc".

10.
[tux]$ exec ./01appel 
la variable $var a pour valeur : abc 
À la fin du script 01appel, le shell appelant, qui a été remplacé par le script, se termine.