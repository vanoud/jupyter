1.
Après création du fichier 09mult, cela donne :

[tux]$ cat 09mult  
#!/bin/bash 
# saisie des nombres 
echo "Entrez le premier opérande :" ; read num1 
echo "Entrez le second opérande  :" ; read num2 
# affichage du résultat de l'opération 
echo $(( num1 * num2 )) 

2.
[tux]$ chmod u+x 09mult  
[tux]$ 09mult  
Entrez le premier opérande : 
12 
Entrez le second opérande  : 
3 
36 