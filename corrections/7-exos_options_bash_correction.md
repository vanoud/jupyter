1.
[tux]$ set -o 
allexport       off 
braceexpand     on 
emacs           on 
errexit         off 
errtrace        off 
functrace       off 
hashall         on 
histexpand      on 
history         on 
ignoreeof       off 
interactive-comments    on 
keyword         off 
monitor         on 
noclobber       off 
noexec          off 
noglob          off 
nolog           off 
notify          off 
nounset         off 
onecmd          off 
physical        off 
pipefail        off 
posix           off 
privileged      off 
verbose         off 
vi              off 
xtrace          off 

2.
[tux]$ PS4="DEBOGAGE>>> " 

3.
[tux]$ set -o xtrace 
Ou :

[tux]$ set -x 

4.
[tux]$ cd /etc ; ls -d X* 
DEBOGAGE>>> cd /etc 
DEBOGAGE>>> ls --color=tty -d X11 
X11 
L’option xtrace affiche l’interprétation shell (alias, caractères génériques...) de chaque commande en utilisant l’invite définie dans la variable PS4.

5.
[tux]$ set +o xtrace 
Ou :

[tux]$ set +x 