1.
Après création du fichier 04fichier, cela donne :

[tux]$ cat 04fichier  
#!/bin/bash 
# on sort si le nom passé en premier paramètre positionnel n'est pas un fichier 
[ -e "$1" ] || exit 1 
# type de fichier 
[ -f "$1" ] && echo "$1 est un fichier standard" \ 
           || echo "$1 n'est pas un fichier standard" 
[ -d "$1" ] && echo "$1 est un répertoire" \ 
           || echo "$1 n'est pas un répertoire" 
# droits 
[ -r "$1" ] && echo "droit de lecture activé" 
[ -w "$1" ] && echo "droit d'écriture activé" 
[ -x "$1" ] && echo "droit d'exécution activé 
# contenu 
[ -s "$1" ] && echo "$1 contient des données" \ 
           || echo "$1 ne contient pas de données" 

2.
[tux]$ chmod u+x 04fichier 
[tux]$ 04fichier /glop 
[tux]$ echo $? 
1 
[tux]$ 04fichier /etc/hosts 
/etc/hosts est un fichier standard 
/etc/hosts n'est pas un répertoire 
droit de lecture activé 
/etc/hosts contient des données 
[tux]$ 04fichier /bin/ls    
/bin/ls est un fichier standard 
/bin/ls n'est pas un répertoire 
droit de lecture activé 
droit d'exécution activé 
/bin/ls contient des données 
[tux]$ 04fichier /home   
/home n'est pas un fichier standard 
/home est un répertoire 
droit de lecture activé 
droit d'exécution activé 
/home contient des données 