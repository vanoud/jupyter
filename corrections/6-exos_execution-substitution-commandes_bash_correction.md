
1.
[tux]$ type cd vi find 
cd est une primitive du shell
vi est /usr/bin/vi
find est /usr/bin/find

Dans cet exemple, la commande cd est une commande interne du shell Bash, vi et find sont des commandes externes du shell dont le chemin absolu est /usr/bin/find.

2.
[tux]$ whereis grep ls fdisk       
grep: /bin/grep /usr/share/man/man1p/grep.1p.gz /usr/share/man/man1/grep.1.gz 
ls: /bin/ls /usr/share/man/man1p/ls.1p.gz /usr/share/man/man1/ls.1.gz 
fdisk: /sbin/fdisk /usr/share/man/man8/fdisk.8.gz 

3.
[tux]$ ps -e --no-heading | wc -l  
64 

4.
[tux]$ echo "il y a actuellement $(ps -e --no-heading | wc -l) processus" 
il y a actuellement 65 processus 
[tux]$ echo "il y a actuellement `ps -e --no-heading | wc -l` processus"  
il y a actuellement 65 processus 

5.
[tux]$ alias nbps='echo "il y a actuellement $(ps -e --no-heading | wc -l) processus"' 
[tux]$ nbps 
il y a actuellement 65 processus 