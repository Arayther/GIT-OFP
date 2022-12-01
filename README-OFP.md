 
<h1 style="text-align: center;">Commande Git</h1>

 ![LogoMontoute](https://www.cjoint.com/doc/22_12/LLbnfAjI0Ec_Frame-1-3-.png)

## Démarrer une zone de travail

 `git clone` (Cloner un dépôt dans un nouveau répertoire)

`git init` (Créez un référentiel Git vide ou réinitialisez-en un existant)

## Travailler sur le changement en cours 

`git add` (Ajouter le contenu du fichier à l'index)

`git add --all` (ajouter tout les fichier a l'index)

`git mv` (Déplacer ou renommer un fichier, un répertoire ou un lien symbolique)

`git restore` (Restaurer les fichiers de l'arborescence de travail)

`git rm` (Supprimer des fichiers de l'arborescence de travail et de l'index)

## Examiner l'histoire et l'état


`git bisect` (Utilisez la recherche binaire pour trouver le commit qui a introduit un bogue)

`git diff` (Afficher les changements entre les commits, le commit et l'arborescence de travail, etc.)

`git grep` (Imprimer des lignes correspondant à un motif)

`git log` (Afficher les journaux de validation)

`git show` (Afficher différents types d'objets)

`git status` (Afficher l'état de l'arborescence de travail)

## Grandir, marquer et peaufiner votre histoire commune

`git branch` (Répertorier, créer ou supprimer des succursales)

`git commit` (Enregistrer les modifications dans le référentiel)

`git merge` (Joindre deux ou plusieurs historiques de développement ensemble)

`git rebase` (Réappliquez les commits au-dessus d'un autre conseil de base)

`git reset` (Réinitialiser HEAD actuel à l'état spécifié)

`git switch` (Changer de succursale)

`git tag` (Créer, répertorier, supprimer ou vérifier un objet tag signé avec GPG)


## Collaborer (voir aussi : workflows d'aide git)

`git fetch` (Télécharger des objets et des références à partir d'un autre référentiel)

`git pull` (Récupérer et intégrer à un autre référentiel ou à une branche locale)

`git push` (Mettre à jour les références distantes avec les objets associés)






_____________________________________________________________________________________________________________________






# Ajout



`git commit -m` (enregistrer dans depot sans passer par VIM ex: `git commit -m 'ajout du fichier test.txt'`)

`rm` (supprime le ficher du depot mais le garde en memoire au contraire de git rm)

`git rm --cached` (abbandone le suivi du fichier uniquement)

`echo 'texte a ajouter' >> nomdufichier.txt,etc` (ajouter du texte dans le fichier choisi)

`cat nomdufichier.txt,etc` (affiche le contenu du fichier)

`git reset HEAD nomdufichier.text,etc` (supprimer le fichier dans sa version actuelle de l'index, mais garde le suivi)

creer un fichier **.gitignore** permet en ecrivant le nom du fichier/dossier de l'exclure du suivi, **on peut par exemple ecrire** `*txt` **dans le fichier pour exclure tout les fichier txt du suivie**

`git mv ancien-nom-fichier.txt,etc nouveau-nom-fichier.txt,etc` permet de renommer un fichier directement depuis git



`git log` (consulter l'historique des modification git) **La commande git log supporte également de nombreuses options.** Certaines vont pouvoir être très utiles par exemple les options `-p`, `--pretty`, `--since` ou `--author`.
Utiliser `git log -p` permet d’afficher explicitement les différences introduites entre chaque validation .L’option `--pretty` permet, avec sa valeur **oneline**, d’afficher chaque commit sur une seule ligne ce qui peut faciliter la lecture dans le cas où de nombreux commits ont été réalisés. **source online format pro**


L’option `--since` permet de n’afficher que **les modifications depuis une certaine date** (on peut lui fournir différents formats de date comme **2.weeks** ou **2019-10-10** par exemple). **source online format pro**

L’option `--author` permet de n’afficher que les commits d’un auteur en particulier.



`git restore nomdufichier.txt,etc` (restaure la derniere version du fhichier enregistrer dans git)

`git branch nomvoulu` (creer une nouvelle branche)

`git checkout nomdelabranche` (basculé sur la branhe voulue)

`git branch -D nomdelabranche` (supprimer la branche)

 on a une branche test qui pointe sur un commit **commitN+1** et une branche *master* qui pointe sur un commit **commitN**. **commitN** est l’ancêtre direct de **commitN+1** et il n’y a donc pas de problème de divergence.

Pour fusionner nos deux branches, on va se placer sur *master* avec une commande `git checkout` puis taper une commande `git merge` avec le nom de la branche qu’on souhaite fusionner avec *master*.
Dans ce cas, “fusionner” nos deux branches revient finalement à faire avancer *master* au niveau du commit pointé par *test*. C’est exactement ce que fait Git et c’est ce qu’on appelle un “fast forward” (avance rapide).
Il ne nous reste alors plus qu’à effacer notre branche *test*. On peut faire cela en utilisant la commande `git branch -d`. **source online format pro**

`git merge nomdelabranche` (fusionner les branches)

`git branch -d nomdelabranche` (supprimer la branche)

Plutôt que d’effectuer une fusion à trois sources, on va pouvoir **rebaser** les modifications validées dans **commitN+1** dans notre branche *master*. On utilise la commande `git rebase` pour récupérer les modifications validées sur une branche et les rejouer sur une autre **source online format pro**

# GIT HUB

Pour **cloner** un dépôt distant, nous allons pouvoir utiliser la commande `git clone`. Une fois que vous disposez d’un dépôt distant cloné localement,vous pouvez utiliser la commande `git remote` pour afficher la liste des serveurs distants des dépôts

`git clone [URL] [nomdurepository]` (permet de cloner un depot git hub sur sur un depot (dossier) vierge)

Le nom donné par défaut par Git à un serveur à partir duquel on a effectué un clonage est **origin**.
 On peut également utiliser `git remote -v` pour afficher les URLs stockées
Pour définir un nom personnalisé pour un dépôt distant, on peut utiliser la commande `git remote add` suivi du nom choisi suivi de l’URL du dépôt.
Pour renommer ensuite notre référence, on pourra utiliser `git remote rename [ancien-nom] [nouveau-nom]`. **source online format pro**

La commande `git fetch [nom-distant]` va nous permettre de récupérer toutes les données d’un dépôt distant qu’on ne possède pas déjà.
Cela permet de récupérer les ajouts du projet distant et d’avoir une version à jour du projet. **source online format pro**

Notez que fetch tire les données dans votre **dépôt local** mais sous sa propre branche ce qui signifie que ces données ne sont pas fusionnées avec vos autres travaux et que votre copie de travail n’est pas modifiée. 
**Il faudra donc fusionner explicitement les données tirées par fetch par la suite**  **source online format pro**

on peut également utiliser `git pull` qui va récupérer les données d’une branche distante et les fusionner automatiquement dans notre branche locale

Une fois qu’on a terminé nos modifications localement, on va les pousser vers le dépôt distant. On utilise pour cela la commande `git push [nom-distant] [nom-de-branche]`. 
Si on souhaite par exemple pousser les modifications faites sur notre branche *master* vers le serveur origin, on écrira `git push origin master`. **source online format pro**

Pour obtenir des informations sur un dépôt distant, on peut utiliser la commande `git remote show [nom-du-depot]`.

Pour retirer un dépôt distant, on utilisera la commande `git remote rm [nom-du-depot]`.


**DEPOT=PROJET** 

Pour copier un dépôt (repository) GitHub sur nos machines, il suffit d’utiliser l’option “clone URL” de GitHub pour récupérer le lien du repo, puis d’utiliser la commande `git clone [URL]` dans notre console **source online format pro**

On peut également utiliser l’option “fork” de GitHub. **Un fork est une copie d’un dépôt distant qui nous permet d’effectuer des modifications sans affecter le projet original**. **source online format pro**



# Commande de base



`cd` (aller dans un dossier exemple: `cd dektop/projet-gip`)

`touch nomdufichier.txt,etc` (creer un fichier)

`echo 'texte' >> nomduficher.txt,etc` (permet d'ecrire dans le fichier)

`cat nomdufichier.txt,etc` ( permet de voir ce qui est ecrit dans le fichier)

`mkdir nomdudossier` (creer un dossier)

`pwd` (savoir ou l'on ce trouve sur le PC)
