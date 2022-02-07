1.
Après création du fichier 02varspec, cela donne :

[tux]$ cat 02varspec  
#!/bin/bash 
echo "mon nom est            : $0" 
echo "mon PID est            : $$" 
echo "le PID de mon père est : $PPID" 
[tux]$ chmod u+x 02varspec 

2.
[tux]$ echo $$ 
2885 
[tux]$ bash 02varspec  
mon nom est            : 02varspec 
mon PID est            : 4386 
le PID de mon père est : 2885 
[tux]$ 02varspec  
mon nom est            : /home/tux/bin/02varspec 
mon PID est            : 4388 
le PID de mon père est : 2885 
[tux]$ ./02varspec  
mon nom est            : -bash 
mon PID est            : 2885 
le PID de mon père est : 2884 
On constate bien que lors du troisième appel avec la commande . (point), le script shell 02varspec est interprété par le shell courant.

3.
[tux]$ cp 02varspec 03param 
[tux]$ chmod u+x 03param  
[tux]$ vi 03param 
#!/bin/bash 
echo "mon nom est            : $0" 
echo "mon PID est            : $$" 
echo "le PID de mon père est : $PPID" 
echo "nombre de paramètres   : $#" 
echo "param. positionnels    : \$1=$1 \$2=$2 \$3=$3" 

4.
[tux]$ 03param a b c d 
mon nom est            : /home/tux/bin/03param 
mon PID est            : 4666 
le PID de mon père est : 2885 
nombre de paramètres   : 4 
param. positionnels    : $1=a $2=b $3=c 
[tux]$ 03param "a b" c d 
mon nom est            : /home/tux/bin/03param 
mon PID est            : 4668 
le PID de mon père est : 2885 
nombre de paramètres   : 3 
param. positionnels    : $1=a b $2=c $3=d 
[tux]$ 03param a b c\ d   
mon nom est            : /home/tux/bin/03param 
mon PID est            : 4670 
le PID de mon père est : 2885 
nombre de paramètres   : 3 
param. positionnels    : $1=a $2=b $3=c d 
[tux]$ 03param a 'b c' d  
mon nom est            : /home/tux/bin/03param 
mon PID est            : 4672 
le PID de mon père est : 2885 
nombre de paramètres   : 3 
param. positionnels    : $1=a $2=b c $3=d 

5.
Après modification du script 03param, cela donne :

[tux]$ cat 03param  
#!/bin/bash 
echo "mon nom est            : $0" 
echo "mon PID est            : $$" 
echo "le PID de mon père est : $PPID" 
echo "nombre de paramètres   : $#" 
echo "param. positionnels    : \$1=$1 \$2=$2 \$3=$3" 
echo "décalage des paramètres positionnels" ; shift 2 
echo "param. positionnels    : \$1=$1 \$2=$2 \$3=$3" 
[tux]$ 03param a b c d 
mon nom est            : /home/tux/bin/03param 
mon PID est            : 4751 
le PID de mon père est : 2885 
nombre de paramètres   : 4 
param. positionnels    : $1=a $2=b $3=c 
décalage des paramètres positionnels 
param. positionnels    : $1=c $2=d $3= 

6.
Après modification du script 03param, cela donne :

[tux]$ cat 03param  
#!/bin/bash 
echo "mon nom est            : $0" 
echo "mon PID est            : $$" 
echo "le PID de mon père est : $PPID" 
echo "nombre de paramètres   : $#" 
echo "tous les paramètres    : $*" 
echo "param. positionnels    : \$1=$1 \$2=$2 \$3=$3 \${11}=${11}" 
echo "décalage des paramètres positionnels" ; shift 2 
echo "tous les paramètres    : $@" 
echo "param. positionnels    : \$1=$1 \$2=$2 \$3=$3 \${11}=${11}" 
[tux]$ 03param a b c d e f g h i j k l m o 
mon nom est            : /home/tux/bin/03param 
mon PID est            : 4812 
le PID de mon père est : 2885 
nombre de paramètres   : 14 
tous les paramètres    : a b c d e f g h i j k l m o 
param. positionnels    : $1=a $2=b $3=c ${11}=k 
décalage des paramètres positionnels 
tous les paramètres    : c d e f g h i j k l m o 
param. positionnels    : $1=c $2=d $3=e ${11}=m 