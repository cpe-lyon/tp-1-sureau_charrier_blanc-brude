# CR TP1


## Exercice 1 : OK

## Exercice 2 :


### Manuel 


_1. A l’aide du manuel, identifiez le rôle de la commande which_

On rentre : man which
Commande which : permet de localiser une commande/fichier/chemin.
Renvoie
0 si tout est trouvé et exécutable
1 si une commande spécifiée n'est pas exécutable ou n'existe pas
2 si une option non valable est spécifiée


_2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher
le terme option dans la page de manuel de which ?_

/terme

_3. Comment quitte-t-on le manuel ?_

On appuie sur la touche q dans la console.

_4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la
première page de la section 6 ; de quoi parle cette section ?_

man 6 intro
Description des jeux et logiciels installés sur le système

### Navigation dans l’arborescence des fichiers


_1. allez dans le dossier /var/log_

cd /var/log

_2. remontez dans le dossier parent (/var) en utilisant un chemin relatif_

cd /var

_3. retournez dans le dossier personnel_

cd

_4. revenez au dossier précédent (/var) sans utiliser de chemin_

cd ..

_5. essayez d’accéder au dossier /root ; que se passe-t-il ?_

Cd /root ou sudo cd/root ne fonctionne pas car on est pas en administrateur root. On est simple utilisateur de base. Pour contourner : sudo su

_6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez_

cf 5.

_7. à partir de votre dossier personnel, créez l’arborescence suivante :_

On utilise mkdir pour créer les dossiers et touch pour créer les fichiers voulus.

_8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis
Dossier1 ; que se passe-t-il ?_

Pour supprimer Fichier1, on a un message d'erreur car nous ne sommes pas au bon endroit dans l'arborescence.
Pour supprimer Dossier1, on a un message d'erreur car rm est destiné à supprimer des fichiers et non des dossiers.

_9. quelle commande permet de supprimer un dossier ?_

On utilise rmdir.

_10. que se passe-t-il quand on applique cette commande à Dossier2 ?_

Erreur car Dossier2 n'est pas vide. On peut contourner cela avec la commande : rm -rf.

_11. comment supprimer en une seule commande Dossier2 et son contenu ?_

rm -rf


### Commandes importantes


_1. Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ?_

Commande pour afficher l'heure : date

_2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire
sur les fichiers commençant par un point ?_

ls permet d'afficher les dossiers non cachés
la permet d'afficher tous les dossier meme cachés
Ce sont les fichiers cachés.

_3. Où se situe le programme ls ?_

localisation ls : which ls ; La commande se situe dans usr/bin/ls

_4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande._

Pas d'entrée manuel pour la commande ll

alias ll= 'ls -alF' et donc on a des infos dans le manuel


_5. Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ?_

ls /bin

_6. Que fait la commande ls .. ?_

Cela liste tous les fichiers et dossiers du repertoire courant.

_7. Quelle commande donne le chemin complet du dossier courant ?_

pwd

_8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?_

Echo 'yo' plop > permet d'écrire 'yo' dans un fichier plop créé dans la session.
Si on réitère la commande, cela écrase ce qui a été écrit  avant.

_9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?_

Echo 'yo' plop >>permet d'ajouter 'yo' à la suite de ce qu'on a déjà écrit

_10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents._

file nous permet de connaître le type d'un fichier.

_11. Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier
avec la commande ln toto titi. Modifiez à présent le contenu de toto et affichez le contenu de titi :
qu’observe-t-on ? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi ?_

Supprimer le fichier toto supprime l'acces au fichier, mais le titi (le lien vers toto) n'est pas supprimé donc on peut toujours avoir accès au contenu de toto : cat titi.

_12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le
contenu de titi ; quelle conséquence pour tutu ? Et inversement ? Supprimez le fichier titi ; quelle
conséquence cela a-t-il sur tutu ?_

Si on supprime le fichier vers lequel point un lien symbolique, le lien est alors cassé et il ne peut plus avoir accès au contenu du fichier supprimé.

_13. Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et
reprendre le défilement à l’écran ?_

Ctrl +S interrompt le defilement
Ctrl +Q reprends le defilement

_14. Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les
lignes 10 à 20._

head -n affiche les n premieres lignes.
tail -n 	affiche les n dernieres lignes.

Pour afficher les lignes 10 à 20 de syslog : head -20 syslog | tail -10 
(permet de selectionnerles 20 premieres lignes puis de prendr les 10 dernieres parmi ces 20)


_15. Que fait la commande dmesg | less ?

dmesg : print or control the kernel ring buffer : permet d'examiner et de controler le buffer noyau

dmesg | less :  affiche la mémoire tampon de message du noyau

_16. Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’afficher la page
de manuel de ce fichier ?_



_17. Affichez seulement la première colonne triée par ordre alphabétique inverse_

Afficher la premiere colonne de passwd : cut -c1
cut -c1 passwd | sort -d (tri par ordre alphabétique : d comme dictionnaire).
cut -c1 passwd | sort -d | sort -r (r comme reverse donc ordre alphabétique inverse).

_18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement les utilisateurs connectés) ?_

Pour afficher les personnes ayant un compte sur la machine, on peut utiliser la commande who.

_19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?_

En utilisant la commande man -k conversion, on a acces aux pages du manuel qui comportent le mot 'conversion'.

_20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine_

Find  / -name passwd : permet de chercher tous les fichiers se nommant passwd.

_21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier
~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null_

_22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu
précédemment_

On utilise : grep ll .bashrc

_23. Utilisez la commande locate pour trouver le fichier history.log._

Apres installation de mlocate on utilise la commande : locate history.log
/var/log/apt/history.log

_24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?_


## Exercice 3. Découverte de l’éditeur de texte nano : OK

## Exercice 4. Personnalisation du shell

_1. Commencez par créer une copie de ce fichier, que vous appellerez .bashrc_bak_

On utilise la commande suivante: cp ~/.bashrc .bashrc_bak

_2. Editez le fichier .bashrc avec nano et décommentez la ligne force_color_prompt=yes pour activer
la couleur. Enregistrez le fichier et quittez nano._

OK

_3.  Le fichier .bashrc est lu au démarrage du shell ; pour le recharger, il faudrait donc se déconnecter
puis se reconnecter ; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite
de commande devrait immédiatement passer en couleurs._

On utilise la commande source .bashrc pour éviter de se déconnecter et se reconnecter pour pouvoir afficher les couleurs dans l'invite de commande.

_4.  Les couleurs par défauts (surtout celle du dossier courant) ne sont pas très visibles. Dans .bashrc,
cherchez les lignes commençant par PS1= ; elles indiquent la mise en forme de l’invite de commande
(selon que l’on est en couleurs ou non)._

OK

_La page suivante vous donne les différents codes couleurs possibles : https://misc.flogisoft.com/
bash/tip_colors_and_formatting
Modifiez l’invite de commande pour qu’elle s’affiche sous la forme suivante :
[heure] - user@host:chemin_courant$
où l’heure est affichée en violet et entre crochets, et le chemin du dossier courant en cyan_

OK
