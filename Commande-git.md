Ouvrir un terminal (terminal Git Bash à privilégier)

Créer, en ligne de commande, un répertoire tp-git

mkdir tp-git

Se déplacer dans le répertoire

cd tp-git/

Vérifier qu’on est dans le bon répertoire en affichant le chemin du répertoire courant

pwd

Initialiser un dépôt Git

$ cd C/Users/Nathan/Onedrive/Cour/Informatique/Linux/git

git init

Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s’assurer que le répertoire .git à été créé

ls -a

Ouvrir ce répertoire sous VS Code

Exécuter git status et copier/coller la sortie

***********
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md

nothing added to commit but untracked files present (use "git add" to track)
*************

Créer le fichier fichier1.md avec un contenu quelconque et l’enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)

touch fichier1.md
nano fichier1.md
Hello World
CTRL X

Attention, il s’agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.
Créer le fichier fichier2.md avec un contenu quelconque et l’enregistrer

touch fichier2.md
nano fichier2.md
No Hello World
CTRL X

Exécuter git status et copier/coller la sortie

***********************
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md
        fichier1.md
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)
***********************

Ajouter fichier1.md à l’index de Git (zone de Staging)

git add fichier1.md

Exécuter git status et copier/coller la sortie

*********************
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md
        fichier2.md
*********************

Créer un commit avec pour message : “Ajout de fichier1.md”

git commit -m "Ajout fichier1.md"

VALIDATION PROF01

Exécuter git status et copier/coller la sortie

*********************
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)
*********************

Modifier fichier1.md et enregistrer

nano fichier1.md
Juice Boys
CTRL X

Exécuter git status et copier/coller la sortie

************************
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md
        fichier2.md

no changes added to commit (use "git add" and/or "git commit -a")
************************

Ajouter fichier1.md et fichier2.md à la zone de Staging

git add fichier1.md fichier2.md

Créer un commit “Ajout de fichier2.md et modification de fichier1.md”

git commit -m "Ajout de fichier2.md et modification de fichier1.md"

Exécuter git status et copier/coller la sortie

**********************
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Commande-git.md

nothing added to commit but untracked files present (use "git add" to track)
**********************

Copier/coller l’ID des deux premiers commits (utiliser log) :

ID commit 1 : 101a98ccd86abcd3113acad580870b57568c8bb8
ID commit 2 : efdd5a0b2cd37f00b1c278d40c6976c7579524b0 
Que signifie qu’un fichier est “tracked” ou “untracked“ ?

Sa veut dire qu'il sont déjà passer dans la page de staying 

Pourquoi doit-on passer les fichiers par la zone de Staging (l’index) avant de les committer ?

Pour pouvoir qu'il comprennent qu'il va devoir envoyer ces fichier la qui sont dans cette Staying a commit est pas des autres 

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
Committer : “Modification fichier1 pour fonctionnalité 3”

Comment utiliser Git Graph pour qu’il nous montre les différences entre l’ancienne version de fichier1.md et la version courante que l’on vient de committer ?

On vois un nouveaux point pour la branch et le fichier et dedans avec le message du commit

Repartir sur master, et modifier fichier1.md en y ajoutant aussi une ligne (différente de celle qu’on a ajoutée sur l’autre branche) ; ajouter à l’index et commit

nano fichier1.md
Bodyyyy Holaaa

Tenter de fusionner la branche fonctionnalite3 avec master

git merge foncionnalite3

Que se passe-t-il et pourquoi ?

il y'a un conflit le fichier fichier1 et modifier donc il peut pas commit

Lancer un git status

On branch master
Your branch is up to date with 'origin/master'.

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        modified:   Commande-git.md

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   fichier1.md


Que doit-on faire si on veut annuler la fusion en cours ? (ne pas lancer la commande)

git merge --abort

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

nano fichier1.md

NB : parfois, plusieurs fichiers sont en conflit ; le processus est identique, il faut juste résoudre les conflits sur tous les fichiers

NB : les conflits de fusion sont fréquents lorsqu’on travaille en collaboration (plusieurs personnes vont travailler sur le même fichier pour remplir deux fonctionnalités différentes)

Les branches créées n’ont plus de raison d’exister

non

Elles avaient pour but de créer une déviation afin de travailler sur des fonctionnalités individuelles, sans interférer avec le travail des autres, avant de les fusionner dans la branche d’intégration
On va vouloir nettoyer le dépôt en les supprimant
Cela ne va bien sûr pas supprimer tous les commits qui y sont associés
Attention cependant d’éviter en général de supprimer une branche qui n’a pas encore été intégrée à la branche d’intégration, sauf on souhaite vraiment abandonner le développement de cette branche
Ne pas réutiliser une branche qui a déjà été intégrée pour démarrer une nouvelle piste : toujours utiliser une nouvelle branche
Nouvelle tâche ? => nouvelle branche à partir d’un commit de la branche d’intégration (en général le plus récent)
Tâche terminée ? => fusion dans la branche d’intégration et suppression de la branche
Supprimer les trois branches fonctionnalitex (attention : on ne peut pas supprimer une branche sur laquelle on est)

git branch -d (nom de la branche)

VALIDATION PROF05
=======

Faire un fork du dépôt https://github.com/rose-line/sio1-2024-java-grpb (pas par commande Git, c’est sur l’interface GitHub)

Cloner localement votre fork (ne pas cloner le dépôt original)

Quelle est la différence entre un fork et un clonage ?
Indiquer dans quelles circonstances on voudrait forker et/ou cloner un dépôt
Modifier le fichier README.md à la racine du dépôt en ajoutant une ligne quelconque

On veut maintenant envoyer cette modification vers le dépôt distant

Il faut d’abord faire un add/commit local
Puis utiliser la commande qui « pousse » les modifs sur le dépôt GitHub (push)
Vérifier directement sur GitHub que le push a bien fonctionné
Trouver la commande qui affiche le nom du ou des dépôt(s) distant(s) relié(s) avec le dépôt local : cela permet de savoir si le dépôt courant est synchronisé avec un dépôt en ligne ou non

On va faire un merge en local puis push :

Créer une branche locale bugfix1, se déplacer dessus, créer un nouveau fichier ok.java à la racine du dépôt
Ajouter ok.java à l’index et faire un commit
Retourner sur master, créer le fichier ajout.java, ajouter à l’index et committer
Fusionner la branche bugfix1 dans la branche master
Afficher le log des commits ; noter les emplacements des trois branches différentes, en local et en remote
Faire un push
Refaire un affichage du log ; origin/master a bougé : que représente cette branche ?
Étudier le résultat sur GitHub, en examinant commits et branches (bouton drop-down sur la page du dépôt pour voir les branches) : qu’est-ce qui est différent de la version locale ?

Le bug est corrigé et intégré ; que doit-on faire de la branche bugfix1 maintenant ?

VALIDATION PROF06

Supposons que l’on veuille effectivement publier sur le remote une branche sur laquelle on travaille (pour sauvegarde ou pour que d’autres puissent l’utiliser)

Créer une nouvelle branche partage
Aller sur la branche
Ajouter un fichier partage.md
L’inclure dans l’index
Faire un commit
Push
Que se passe-t-il ?
Exécuter la bonne commande pour sauvegarder la branche sur le remote
Vérifier sur GitHub que la branche apparaît bien
La branche partage n’a pas été fusionnée avant le push ; on va utiliser un autre moyen offert par GitHub pour fusionner une branche en remote : la Pull Request

La Pull Request est très utilisée en collaboration : elle permet à l’intégrateur du projet d’examiner les demandes de merge au niveau du remote avant de les accepter (ou non)
Sur GitHub, cliquer sur le bouton Compare & pull request, qui apparaît directement sur la page du dépôt depuis le dernier push qui a ajouté la branche (voir ci-dessus).

À gauche, la branche d’intégration (« base », qui reçoit le merge) ; à droite, la branche à fusionner (« compare »)

On doit fusionner partage dans master
Attention, il faut bien choisir le repo de base qui est sur votre propre compte (pas le compte du dépôt d’origine que vous avez forké)
On peut ajouter d’autres informations : titre et commentaire de la pull request, et même upload de fichiers annexes, liens éventuels… Également, on peut ajouter des labels pour étiquetter la pull request et lui affecter un reviewer, qui va officiellement être en charge
Valider en cliquant sur le bouton Create pull request
La page résultante informe sur les branches source et cible, sur les commits concernés, les fichiers qui ont été modifiés…

On peut aussi y démarrer une conversation notamment entre l’émetteur de la pull request et l’intégrateur

On voit que l’intégrateur (possesseur du compte cible) peut accepter la pull request en cliquant sur le bouton Merge pull request (ou refuser en cliquant sur Close pull request).

En discutant de la pull request, on se rend compte que certaines choses devraient être modifiées

Repartir en local pour effectuer une modification sur partage.md et ajouter precision.md
Commit des deux modifs
Push
Observer la pull request : que s’est-il passé ?
Finalement, faire le merge sur la page de la pull request
Noter que l’interface nous propose alors de supprimer la branche devenue inutile ; supprimer la branche
Dans un contexte de travail en collaboration sur un même dépôt, donner un workflow (façon de travailler) possible qui va permettre à tous les intervenants de viser des ajouts à la branche d’intégration, d’en discuter, et ceci sans danger pour la branche d’intégration, avant que finalement l’intégrateur (probablement propriétaire du dépot) accepte les changements.

VALIDATION PROF07

