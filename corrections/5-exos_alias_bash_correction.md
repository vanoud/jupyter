1.

[tux]$ alias 
alias l.='ls -d .* --color=tty' 
alias ll='ls -l --color=tty' 
alias ls='ls --color=tty' 
alias vi='vim' 
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot 
--show-tilde' 

2.
[tux]$ alias ls='ls --color=tty' 

3.
Couleur par défaut du shell	    Fichier standard
Bleu	    Répertoire
Cyan	    Lien symbolique
Jaune	    Fichier FIFO et block.
Magenta 	Socket, fichier image (.jpg, .gif, .png, .tiff) et audio (.mp3, .ogg, .wav)
Rouge	    Archive (.tar, .zip, .deb, .rpm)
Vert	    Exécutable

4.
[tux]$ \ls 
... 
ou :

[tux]$ command ls 
... 
5.
[tux]$ alias cd..='cd ..' 
[tux]$ cd /usr/lib 
[tux]$ pwd 
/usr/lib 
[tux]$ cd.. 
[tux]$ pwd 
/usr 

6.
[tux]$ alias 
alias cd..='cd ..' 
alias l.='ls -d .* --color=tty' 
alias ll='ls -l --color=tty' 
alias ls='ls --color=tty' 
alias vi='vim' 
alias which='alias | /usr/bin/which --tty-only --read-alias 
--show-dot --show-tilde' 
[tux]$ unalias cd.. 
[tux]$ alias        
alias l.='ls -d .* --color=tty' 
alias ll='ls -l --color=tty' 
alias ls='ls --color=tty' 
alias vi='vim' 
alias which='alias | /usr/bin/which --tty-only --read-alias 
--show-dot --show-tilde' 
[tux]$ cd.. 
-bash: cd..: command not found