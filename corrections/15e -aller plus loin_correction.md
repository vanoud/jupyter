1.
Après création du fichier 10compar, cela donne :

[tux]$ cat 10compar    
#!/bin/bash 
# on sort s'il n'y a pas d'argument 
(( $# == 0 )) && exit 1 
# initialisation des variables $min et $max 
min=$1 
max=$1 
shift 
# tant qu'il y a des arguments 
while (( $# > 1 )) 
do 
  max=$(06max $max $1) 
  min=$(07min $min $1) 
  # on traite l'argument suivant 
  shift 
done 
# affichage des résultats 
echo "nombre min : $min" 
echo "nombre max : $max" 

2.
[tux]$ 10compar   
[tux]$ echo $?    
1 
[tux]$ 10compar 1 
nombre min : 1 
nombre max : 1 
[tux]$ 10compar 1 2 
nombre min : 1 
nombre max : 2 
[tux]$ 10compar 1 2 3 
nombre min : 1 
nombre max : 3 
[tux]$ 10compar 3 5 2 6 1 8 7 
nombre min : 1 
nombre max : 8 