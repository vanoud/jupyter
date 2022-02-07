1.

$sudo adduser tux

Appuyez sur les touches [Ctrl]-[Alt]-[F3], puis :

localhost login: tux
Password: <le mot de passe n'apparaît pas> 
[tux]$ 

2.

[tux]$ set | less
BASH=/bin/bash 
BASH_ARGC=() 
BASH_ARGV=() 
BASH_LINENO=() 
BASH_SOURCE=() 
... 

3.

[tux]$ var1=abc 
[tux]$ set | less
BASH=/bin/bash 
BASH_ARGC=() 
BASH_ARGV=() 
BASH_LINENO=() 
BASH_SOURCE=() 
... 
var1=abc 

4.

[tux]$ echo $var1 
abc 

5.

[tux]$ echo $var2 
L’appel d’un nom de variable non défini ne génère aucune erreur ; le shell se contente de le remplacer par une chaîne vide.

6.

[tux]$ echo $HOME 
/home/tux 
La variable HOME contient le chemin complet du répertoire personnel de l’utilisateur actuellement connecté.

7.

[tux]$ HOME=/tmp 
[tux]$ pwd 
/home/tux 
[tux]$ cd 
[tux]$ pwd 
/tmp 

8.

[tux]$ LANG=C 
[tux]$ man bash 
Ce qui affiche :

BASH(1)                                                                BASH(1) 
 
NAME 
      bash - GNU Bourne-Again SHell 
 
SYNOPSIS 
      bash [options] [file] 
 
COPYRIGHT 
      Bash is Copyright (C) 1989-2004 by the Free Software Foundation, Inc. 
 
DESCRIPTION 
      Bash  is  an  sh-compatible  command language interpreter that executes 
      commands read from the standard input or from a file.  Bash also incor- 
      porates useful features from the Korn and C shells (ksh and csh). 
 
      Bash  is  intended  to be a conformant implementation of the IEEE POSIX 
      Shell and Tools specification (IEEE Working Group 1003.2). 
 
OPTIONS 
      In addition to the single-character shell  options  documented  in  the 
      description  of  the set builtin command, bash interprets the following 
      options when it is invoked: 
: 
C’est la langue C ANSI internationale (anglais) qui est désormais utilisée.

9.

La séquence de touches permettant de rechercher la chaîne de caractères "PROMPTING" est /PROMPTING, puis [Entr] ; cela donne :

PROMPTING 
      When executing interactively, bash displays the primary prompt PS1 when 
      it is ready to read a command, and the secondary  prompt  PS2  when  it 
      needs  more  input  to  complete  a  command.  Bash allows these prompt 
      strings to be customized by inserting  a  number  of  backslash-escaped 
      special characters that are decoded as follows: 
             \a     an ASCII bell character (07) 
             \d     the  date  in "Weekday Month Date" format (e.g., "Tue May 
                    26") 
             \D{format} 
                    the format is passed to strftime(3)  and  the  result  is 
                    inserted  into the prompt string; an empty format results 
                    in a locale-specific time representation.  The braces are 
                    required 
             \e     an ASCII escape character (033) 
             \h     the hostname up to the first '.' 
             \H     the hostname 
             \j     the number of jobs currently managed by the shell 
             \l     the basename of the shell's terminal device name 
             \n     newline 
             \r     carriage return 
             \s     the  name  of  the shell, the basename of $0 (the portion 
                    following the final slash) 
: 
Une fois sorti de la page de manuel avec la touche q :

[tux]$ PS1='[\d - \H]$ ' 
[Mon Jul 08 - localhost.localdomain]$ 

10.

[Sun Jun 19 - localhost.localdomain]$ exit 
Puis :

localhost login: tux
Password: <le mot de passe n'apparaît pas> 
[tux]$ set | less
BASH=/bin/bash 
BASH_ARGC=() 
BASH_ARGV=() 
BASH_LINENO=() 
BASH_SOURCE=() 
... 
[tux]$ echo $var1 
 
[tux]$ echo $HOME 
/home/tux 
[tux]$ echo $LANG 
fr_FR.UTF-8 
[tux]$ echo $PS1 
[tux]$ 

11.

[tux]$ var3=Bond 
[tux]$ echo $var3 
Bond 

12.

[tux]$ echo $var3, James $var3. 
Bond, James Bond. 

13.

[tux]$ echo ${var3}ir 
Bondir 

14.

[tux]$ var4=lun 
[tux]$ var5=di 
[tux]$ var6=$var4$var5 
[tux]$ echo $var6 
lundi 

15.

[tux]$ set | less
BASH=/bin/bash 
BASH_ARGC=() 
BASH_ARGV=() 
BASH_LINENO=() 
BASH_SOURCE=() 
... 
var3=Bond 
var4=lun 
var5=di 
var6=lundi 
[tux]$ unset var4 var5 var6 
[tux]$ set | less
BASH=/bin/bash 
BASH_ARGC=() 
BASH_ARGV=() 
BASH_LINENO=() 
BASH_SOURCE=() 
... 
var3=Bond 

16.

[tux]$ echo $var3 
Bond 
[tux]$ bash 
[tux]$ echo $var3 
 
[tux]$ exit 
exit 
[tux]$ echo $var3 
Bond 

17.

[tux]$ export var3 
[tux]$ echo $var3 
Bond 
[tux]$ bash 
[tux]$ echo $var3 
Bond 
[tux]$ exit 
exit 
[tux]$ echo $var3 
Bond 