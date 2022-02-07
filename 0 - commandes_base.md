# Les commandes linux de base

+ pwd
+ cd
+ ls
  + ls -R : dossier, sous dossiers et fichiers
  + ls -a : affiche les dossiers cachés
  + ls -al : informations détaillées
+ cat : liste le contenu d'un fichier sur la sortie standard. Permet par exemple la conversion d'un fichier de min en maj: ```cat nom_fichier | tr a-z A-Z```
+ cp: copie
+ mv: déplace
+ mkdir: création dossier
  + -p : permet de créer un nouveau répertoire entre deux existants
+ rmdir
+ rm
+ touch
+ locate: localise un fichier
  + -i: rend insensible à la casse
+ find: localise un fichier dans un répertoire donné
+ grep: recherche tout le texte d'un fichier donné
+ sudo
+ df: affiche un rapport sur l'utilisation de l'espae disque
+ du: affiche l'espace utilisé par un fichier ou dossier
  + -h: format
+ head: visualise les premières lignes d'un fichier texte
+ tail: affiche les 10 dernières lignes
+ diff: compare le contenu de 2 fichiers ligne par ligne
+ chmod: modifier les permissions de lecture, écriture, ...
+ chown: modifier le propriétaire du fichier
+ jobs: affiche les jobs et leur statut
+ wget: permet de télécharger du contenu sur internet
+ uname: affiche les informations du systeme
+ top: affiche les processus et les ressources utilisées 
+ history: afficher l'historique des commandes tapées
+ man: affiche le manuel d'une fonction
+ echo: déplacer des données dans un fichier ```echo Bonjour >> bonjour.txt``` (ajoute à la fin, > écrase tout)
+ zip, unzip
+ hostname: affiche le om de l'hote/réseau
  + -I : affiche l'ip du réseau