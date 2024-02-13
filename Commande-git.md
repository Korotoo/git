Ouvrir un terminal (terminal Git Bash à privilégier)

Créer, en ligne de commande, un répertoire tp-git

mkdir tp-git

Se déplacer dans le répertoire

Vérifier qu’on est dans le bon répertoire en affichant le chemin du répertoire courant

Initialiser un dépôt Git

Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s’assurer que le répertoire .git à été créé

Ouvrir ce répertoire sous VS Code

Exécuter git status et copier/coller la sortie

Créer le fichier fichier1.md avec un contenu quelconque et l’enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)

Attention, il s’agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.
Créer le fichier fichier2.md avec un contenu quelconque et l’enregistrer

Exécuter git status et copier/coller la sortie

Ajouter fichier1.md à l’index de Git (zone de Staging)

Exécuter git status et copier/coller la sortie

Créer un commit avec pour message : “Ajout de fichier1.md”

VALIDATION PROF01

Exécuter git status et copier/coller la sortie

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md

nothing added to commit but untracked files present (use "git add" to track)

Modifier fichier1.md et enregistrer

Ajout de Heyyyyyy

Exécuter git status et copier/coller la sortie

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md

no changes added to commit (use "git add" and/or "git commit -a")

Ajouter fichier1.md et fichier2.md à la zone de Staging

$ git add fichier1.md fichier2.md
warning: in the working copy of 'fichier1.md', LF will be replaced by CRLF the next time Git touches it

Créer un commit “Ajout de fichier2.md et modification de fichier1.md”

git commit -m "Ajout de texte fichier1"
[master 9cb5bb9] Ajout de texte fichier1
 1 file changed, 1 insertion(+)

Exécuter git status et copier/coller la sortie

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md

nothing added to commit but untracked files present (use "git add" to track)

Copier/coller l’ID des deux premiers commits (utiliser log) :

ID commit 1 : efdd5a0b2cd37f00b1c278d40c6976c7579524b0
ID commit 2 : 9cb5bb97e64adc1fc4fa91ebd6bef47a77dfb1ab
Que signifie qu’un fichier est “tracked” ou “untracked“ ?

tracked veut dire que en gros même après un commit il continue d'être suivie et untracked l'inverse il ne donne plus d'informationa propos des fichiers 

Pourquoi doit-on passer les fichiers par la zone de Staging (l’index) avant de les committer ?

Pour dire que il va passer le commit ces une préparation pour passer au commit 



VALIDATION PROF02



Créer une branche fonctionnalite1

git branch fonctionnalite1

Lister les branches

git branch

Se déplacer sur la branche fonctionnalite1

git switch fonctionnalite1

Lister les branches

git branch 

Que représente l’étoile à côté des noms des branches ?

Sa veut dire que on est dans cette branche 

Créer un nouveau fichier fichier3.md

touch fichier3.md

Modifier le fichier fichier2.md

nano fichier2.md

Comment utiliser VS Code pour qu’il nous montre les différences entre l’ancienne version de fichier2.md et la version courante que l’on vient d’éditer ?

git diff

Committer ces deux modifications : “Fonctionnalité 1 - première phase”

git add fichier2.md fichier3.md
git commit -m “Fonctionnalité 1 - première phase”

Créer un nouveau fichier fichier4.md

touch fichier4.md 

Modifier de nouveau le fichier fichier2.md

nano fichier2.md
Ajout okok
 
Committer ces deux modifications : “Fonctionnalité 1 - terminée”

git add fichier2.md fichier4.md
git commit -m "Fonctionnalité 1 - terminée"


VALIDATION PROF03


Afficher la liste des fichiers du répertoire

ls

Se déplacer sur la branche master

git switch master

Afficher la liste des fichiers du répertoire

<<<<<<< HEAD
ls

Pourquoi les deux sorties sont-elles différentes ? Les fichiers ont-ils disparus ?

car ce n'ai pas la même branch, oui fichier 3 et 4 il sont sur une autre branche

Créer une nouvelle branche fonctionnalite2

git branch focntionnalite2

Cette branche ne va pas avoir toutes les données incluses dans fonctionnalite1. Pourquoi ?

Car quant j'ai crée la branche fonctionnalite2 je l'ai crée sur master donc il ne peut plus voir les modifs

Qu’aurait-il fallu faire si on avait souhaité démarrer la branche fonctionnalite2 en intégrant les modifications récentes de fonctionnalite1 ?

git add commande-git.md
git commit -m "maj"
git checkout fonctionnalite2

Se déplacer sur la nouvelle branche fonctionnalite2

git switch fonctionnalite2

Créer un nouveau fichier fichier5.md

touch fichier et fichier5

Faire un commit intégrant cette ajout : “Ajout fichier5.md”

git add fichier5.md
git commit -m "Ajout de fichier5.md"

Entrer la commande git log --oneline --decorate --graph --all pour visualiser, sur le terminal, le graphe des commits sur toutes les branches

$ git log --oneline --decorate --graph --all
* 7b80f04 (HEAD -> fonctionnalite2, origin/fonctionnalite2) modified
* 93359a5 Ajout de fichier5
* 7877af5 maj
| * 7b6522b (fonctionnalite1) Newfile
| * 701e6e9 (origin/fonctionnalite1) modified
| * b56a8bc Add commande
| * 80c83c5 Fonctionnalite 1 terminee
| * 82fbde7 Fonctionnalite 1 - premiere phase
|/
* 9cb5bb9 (master, bois) Ajout de texte fichier1
* efdd5a0 Ajout de fichier2.md et modification de fichier1.md
* 101a98c Ajout fichier1.md

Noter la « déviation » entre les deux branches, à partir de la branche master (schématisée sous forme de traits)
l’option --all permet de visualiser toutes les branches, pas seulement celle sur laquelle on est
l’option --oneline affiche les commits sur une seule ligne
l’option --graph affiche le log sous forme de graphe
(utilisez si besoin les touches haut/bas pour naviguer dans la sortie de cette commande et Q pour quitter)
Installer l’extension VS Code Git Graph et visualiser le graphe actuel des commits à l’aide de cette extension

Sur cette représentation, que représente les points ?
<<<<<<< HEAD

Il représente l'ajout de toutes choses faite depuis le 16 janvier, les différents commit qui a pu avoir 

Comment voit-on sur quelle branche on est actuellement ?

Nathan@Nothing MINGW64 ~/OneDrive/Cour/Informatique/Linux/git (fonctionnalite2)

mais aussi dans git graph la partie qui est en gras veut dire que on est la


VALIDATION PROF04


On considère que la branche originale (master ou main) est la branche d’intégration, c’est-à-dire celle qui va contenir l’historique de toutes les modifications développées au fur et à mesure dans les branches annexes

Se déplacer sur la branche master

git switch master

Noter le changement dans l’onglet Git Graph

nous somme revenue sur la branch master et sa fait que il y rien dessus

On va maintenant intégrer la branche fonctionnalite1, qui est terminée, dans la branche d’intégration (ça s’appelle une fusion, ou un merge) : fusionner avec la branche fonctionnalite1

git merge fonctionnalite1

$ git merge fonctionnalite1
Auto-merging Commande-git.md
CONFLICT (add/add): Merge conflict in Commande-git.md
Automatic merge failed; fix conflicts and then commit the result.

Noter le changement dans l’onglet Git Graph. Que signifie la mention Fast-forward indiquée par la sortie de la commande ?

la branche fonctionnalite1 a rejoint la branche master

On veut maintenant fusionner fonctionnalite2 dans la branche d’intégration (master). Effectuer cette fusion.

git merge fonctionnalite2

Noter le changement dans l’onglet Git Graph. Que signifie la mention Merge made by the … strategy indiquée par la sortie de la commande ?

Quelle est la différence fondamentale avec la fusion précédente ?

?

Créer une nouvelle branche fonctionnalite3, se déplacer dessus, et modifier le fichier fichier1.md en y ajoutant une ligne de texte. Committer : “Modification fichier1 pour fonctionnalité 3”

git branch fonctionnalité3
nano fichier1

Comment utiliser Git Graph pour qu’il nous montre les différences entre l’ancienne version de fichier1.md et la version courante que l’on vient de committer ?
Repartir sur master, et modifier fichier1.md en y ajoutant aussi une ligne (différente de celle qu’on a ajoutée sur l’autre branche) ; ajouter à l’index et commit

Tenter de fusionner la branche fonctionnalite3 avec master

Que se passe-t-il et pourquoi ?
Lancer un git status

Que doit-on faire si on veut annuler la fusion en cours ? (ne pas lancer la commande)
On veut résoudre le conflit. Plusieurs possibilités :

Conserver uniquement les modifications faites dans fonctionnalite3
Conserver uniquement les modifications faites dans master
Conserver les deux modifications
Supprimer les deux modifications ou remanier sensiblement le fichier pour les intégrer correctement
Git nous laisse totalement la main et ne va pas essayer d’imposer l’un de ces choix pour nous, ni nous assister dans l’application automatique de l’un d’entre eux : il faut examiner le(s) fichier(s) en conflit et éditer nous-mêmes

Ouvrir le fichier en question sous VS Code

La chaîne <<<<<<<<<< marque le début du conflit
La chaîne >>>>>>>>>> marque la fin du conflit
La chaîne ========== sépare les deux versions
Éditer le fichier pour faire en sorte d’intégrer les deux modifications ; à la fin de l’édition :

Il ne doit plus y avoir de marques quelconques en dehors des ajouts fonctionnels originaux, c’est-à-dire pas de <<<<<<<<<<, ni de mentions de nom de branche, etc. : vous rendez le fichier tel qu’il doit apparaître dans le commit de fusion, avec les conflits résolus manuellement
Sauvegarder
Ajouter les modification à l’index et committer

NB : parfois, plusieurs fichiers sont en conflit ; le processus est identique, il faut juste résoudre les conflits sur tous les fichiers

NB : les conflits de fusion sont fréquents lorsqu’on travaille en collaboration (plusieurs personnes vont travailler sur le même fichier pour remplir deux fonctionnalités différentes)

Les branches créées n’ont plus de raison d’exister

Elles avaient pour but de créer une déviation afin de travailler sur des fonctionnalités individuelles, sans interférer avec le travail des autres, avant de les fusionner dans la branche d’intégration
On va vouloir nettoyer le dépôt en les supprimant
Cela ne va bien sûr pas supprimer tous les commits qui y sont associés
Attention cependant d’éviter en général de supprimer une branche qui n’a pas encore été intégrée à la branche d’intégration, sauf on souhaite vraiment abandonner le développement de cette branche
Ne pas réutiliser une branche qui a déjà été intégrée pour démarrer une nouvelle piste : toujours utiliser une nouvelle branche
Nouvelle tâche ? => nouvelle branche à partir d’un commit de la branche d’intégration (en général le plus récent)
Tâche terminée ? => fusion dans la branche d’intégration et suppression de la branche
Supprimer les trois branches fonctionnalitex (attention : on ne peut pas supprimer une branche sur laquelle on est)

VALIDATION PROF05
=======

