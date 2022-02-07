
Corrigé Redirections et tubes

1.

[tux]$ cat 
voici 
voici 
quelques 
quelques 
mots 
mots 

La séquence de touches [Ctrl]-D permet de terminer une commande utilisant le clavier comme entrée standard.

La commande cat retourne les lignes saisies en entrée (sans redirection, l’entrée standard est le clavier) sur sa sortie (sans redirection, la sortie standard est l’écran).

2.

[tux]$ wc 
voici quelques 
mots 
     2       3      20 
De nouveau, la séquence de touches [Ctrl]-D permet de terminer la commande normalement ; la séquence de touches [Ctrl]-C permettant d’arrêter l’exécution du processus ne produit pas le même effet (annulation de la commande, donc pas de statistiques en résultat).

La commande wc produit des statistiques sur les données reçues en entrée, elle indique dans l'ordre : le nombre de lignes, le nombre de mots puis le nombre de caractères (sans redirection, l’entrée standard est le clavier).

3.

[tux]$ cat /etc/hosts 
# Do not remove the following line, or various programs 
# that require network functionality will fail. 
127.0.0.1               localhost.localdomain localhost 

[tux]$ cat < /etc/hosts 
# Do not remove the following line, or various programs 
# that require network functionality will fail. 
127.0.0.1               localhost.localdomain localhost 

Le résultat est le même, la commande cat redirige tout le flux qu'elle reçoit en résultat

4.

[tux]$ wc -l /etc/passwd 
45 /etc/passwd 

[tux]$ wc -l < /etc/passwd 
45 

L'option -l permet d'afficher le nombre de lignes
Dans le second cas, le nom de fichier n’est pas passé en argument de la commande wc (c’est une redirection). La commande ne connaît donc pas le fichier, elle ne se contente que de traiter les données reçues sur son entrée ; par conséquent, le nom du fichier /etc/passwd n’est pas affiché.

5.

[tux]$ cat > /tmp/ficcat 
voici quelques 
mots 

[tux]$ cat /tmp/ficcat  
voici quelques 
mots 

6.

[tux]$ cat < /tmp/ficcat > /tmp/ficcat2 
[tux]$ cat /tmp/ficcat2 
voici quelques 
mots 

7.

[tux]$ cat >> /tmp/ficcat 
encore quelques 
mots supplémentaires 
[tux]$ cat /tmp/ficcat 
voici quelques 
mots 
encore quelques 
mots supplémentaires 

8.

[tux]$ cat /tmp/ficcat /etc/hosts > /tmp/ficcat3 
[tux]$ cat /tmp/ficcat3 
voici quelques 
mots 
encore quelques 
mots supplémentaires 
# Do not remove the following line, or various programs 
# that require network functionality will fail. 
127.0.0.1               localhost.localdomain localhost 

9.

[tux]$ cd /etc  
[tux]$ ls > /tmp/ls.out 
[tux]$ cat /tmp/ls.out  
a2ps.cfg 
a2ps-site.cfg 
acpi 
adjtime 
alchemist 
... 
Le fichier généré contient le nom de chaque fichier présent dans le répertoire /etc sur une ligne distincte.

10.

[tux]$ wc -l < /tmp/ls.out 
220 
Le nombre de fichiers présents dans le répertoire /etc est le résultat de la commande précédente, soit 220 dans l’exemple.

11.

[tux]$ rm /tmp/ls.out 

12.

[tux]$ ls /etc | wc -l 
220 

13.

[tux]$ ls /etc | tee /tmp/ls.out | wc -l 
220 
[tux]$ cat /tmp/ls.out  
a2ps.cfg 
a2ps-site.cfg 
acpi 
adjtime 
alchemist 
... 

14.

[tux]$ ls /etc/passwd glop 
ls: glop: Aucun fichier ou répertoire de ce type 
/etc/passwd 

15.

[tux]$ ls /etc/passwd glop > /tmp/ls.out 2> /tmp/ls.err 
[tux]$ cat /tmp/ls.out  
/etc/passwd 
[tux]$ cat /tmp/ls.err  
ls: glop: Aucun fichier ou répertoire de ce type 

16.

[tux]$ ls /etc/passwd glop > /tmp/ls.out 2> /dev/null   
[tux]$ cat /tmp/ls.out  
/etc/passwd 

17.

[tux]$ ls /etc/passwd glop > /tmp/ls.out 2>&1         
[tux]$ cat /tmp/ls.out                        
ls: glop: Aucun fichier ou répertoire de ce type 
/etc/passwd 