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

Il représente l'ajout de toutes choses faite depuis le 16 janvier, les différents commit qui a pu avoir 

Comment voit-on sur quelle branche on est actuellement ?

Nathan@Nothing MINGW64 ~/OneDrive/Cour/Informatique/Linux/git (fonctionnalite2)

mais aussi dans git graph la partie qui est en gras veut dire que on est la

VALIDATION PROF04