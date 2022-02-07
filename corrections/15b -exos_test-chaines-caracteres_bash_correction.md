1.
Après création du fichier 05chaine, cela donne :

[tux]$ cat 05chaine  
#!/bin/bash 
# on sort si un des deux arguments est une chaîne de caractères nulle 
[ -z "$1" -o -z "$2" ] && exit 1 
# égalité 
[ "$1" = "$2" ] && echo "la chaîne '$1' est égale à '$2'" \ 
               || echo "la chaîne '$1' est différente de '$2'" 

2.
[tux]$ chmod u+x 05chaine 
[tux]$ 05chaine abc "" 
[tux]$ echo $?         
1 
[tux]$ 05chaine "" abc 
[tux]$ echo $?         
1 
[tux]$ 05chaine "" ""  
[tux]$ echo $?        
1 
[tux]$ 05chaine abc abc 
la chaîne 'abc' est égale à 'abc' 
[tux]$ 05chaine abc ABC 
la chaîne 'abc' est différente de 'ABC' 
[tux]$ 05chaine abc "abc " 
la chaîne 'abc' est différente de 'abc ' 