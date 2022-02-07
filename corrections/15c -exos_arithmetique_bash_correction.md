1. 

Après création du fichier 06max, cela donne :

[tux]$ cat 06max  
#!/bin/bash 
# on sort si le nombre d'arguments est différent de 2 
[ $# -ne 2 ] && exit 1 
# recherche du nombre le plus grand 
[ "$1" -ge "$2" ] && echo $1 || echo $2 

2.
[tux]$ chmod u+x 06max  
[tux]$ 06max 12 
[tux]$ echo $? 
1 
[tux]$ 06max 12 34 
34 
[tux]$ 06max 12 6  
12 
[tux]$ 06max 12 12    
12 
[tux]$ 06max 12 " 34" 
34 

3.
Après création du fichier 07min, cela donne :

[tux]$ cat 07min  
#!/bin/bash 
# on sort si le nombre d'arguments est différent de 2 
(( $# != 2 )) && exit 1 
# recherche du nombre le plus petit 
(( "$1" <= "$2" )) && echo $1 || echo $2 

4.
[tux]$ chmod u+x 07min  
[tux]$ 07min 12 
[tux]$ echo $? 
1 
[tux]$ 07min 12 34 
12 
[tux]$ 07min 12 6  
6 
[tux]$ 07min 12 12 
12 
[tux]$ 07min 12 " 34" 
12 

5.
Après création du fichier 08div, cela donne :

[tux]$ cat 08div  
#!/bin/bash 
# on sort si le nombre d'arguments est différent de 2 
(( $# != 2 )) && exit 1 
# on sort si le second paramètre positionnel est égal à 0 
(( "$2" == 0 )) && exit 2 
# affichage du résultat de l'opération 
echo $(( $1 / $2 )) 

6.
[tux]8 chmod u+x 08div 
[tux]$ 08div 12  
[tux]$ echo $? 
1 
[tux]$ 08div 12 0 
[tux]$ echo $? 
2 
[tux]$ 08div 12 2 
6 
[tux]$ 08div 12 5 
2 
[tux]$ 08div 12 14 
0 