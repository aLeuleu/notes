# Git - la HEAD

**Dans Git, la tête (HEAD) est un pointeur qui pointe vers le commit le plus récent dans la branche actuellement active.** En d'autres termes, la tête représente l'état actuel du code dans votre dépôt local.

La tête est un pointeur spécial qui est toujours présent dans un dépôt Git, quelle que soit la branche sur laquelle vous travaillez. **Vous pouvez penser à la tête comme étant le commit "courant" sur lequel vous travaillez.**

![image](https://blog.git-init.com/content/images/2021/08/HEAD.001.png)

à gauche, la HEAD pointe sur main, et donc vos fichiers seront à jour avec le dernier commit.
à droite, la HEAD ne pointe plus sur une branche, on dit qu'elle est detached. Et vos fichiers seront modifiés en conséquence !.. 



Vous pouvez voir quelle branche est actuellement sélectionnée en utilisant la commande `git branch`. Vous pouvez également voir quel commit est actuellement pointé par la tête en utilisant la commande `git log`.

Il est important de noter que *la tête n'est pas un commit en soi*, mais plutôt un pointeur vers un commit. Cela signifie qu'il est possible de changer la tête pour pointer vers un autre commit, ce qui peut être utile lorsque vous voulez revenir en arrière dans l'historique de votre dépôt ou annuler des modifications. Vous pouvez utiliser la commande `git checkout` pour changer la tête pour pointer vers un autre commit.

# Git - Le rebase interactif
Le rebase interactif dans Git est une fonctionnalité qui vous permet de **modifier l'historique des commits dans votre dépôt.** Cela peut être utile lorsque vous voulez regrouper plusieurs commits en un seul, supprimer des commits indésirables, ou simplement modifier l'ordre des commits.

`git rebase -i <commit>` ouvre un éditeur de texte avec une liste de tous les commits après le commit spécifié.
![image](https://about.gitlab.com/images/blogimages/how-to-keep-your-git-history-clean-with-interactive-rebase/editor-window-start-ir@2x.png)
Vous pouvez alors modifier cette liste en supprimant les commits que vous ne souhaitez pas inclure dans le rebase, en modifiant l'ordre des commits, ou en regroupant plusieurs commits en un seul en utilisant la commande squash. Une fois que vous avez terminé de modifier la liste, enregistrez et fermez l'éditeur de texte, et Git exécutera le rebase en fonction des modifications que vous avez apportées.

Le rebase interactif peut être un peu déroutant au début, mais il peut être très utile une fois que vous l'avez compris. C'est un outil puissant qui vous permet de modifier l'historique des commits dans votre dépôt de manière flexible et contrôlée. Il est important de noter que le rebase interactif modifie l'historique des commits de votre dépôt, de sorte qu'il est recommandé de ne pas l'utiliser sur des branches partagées avec d'autres collaborateurs sans leur consentement.
 
 Voici les options disponibles pour `git rebase -i <commit>` (en general, on désigne `<commit>` avec des reference relatives : `HEAD~3` (ou `HEAD^^^`))  
 ```sh
 # Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```
 
# Git - Les branches "remote"

Les branches "remote" dans Git sont des branches qui sont partagées par plusieurs utilisateurs sur un dépôt distant. Lorsque vous travaillez en collaboration sur un projet avec Git, il est courant d'avoir plusieurs branches locales sur votre ordinateur, mais il est également important de synchroniser ces branches avec celles des autres collaborateurs sur le dépôt distant. C'est là que les branches remote entrent en jeu.

Si la branche principale s'apelle "main" et que vous venez de mettre à jour votre depot local en faisant un `git pull`, vous verrez (en faisant git log --graph) qu'il existe une branche origin/main.

Cette branche reflete la branche "remote"

Donc si vous etes en avance d'1 commit par rapport a `origin/main`, c'est que vous devrez faire `push` votre commit.

En revanche, si votre `origin/main` possede 1 commit d'avance sur vous... eh bien faites un `git pull` pour etre a jour avec les derniers changement !

# Git - Submodules

## 1) pourquoi on ne fait pas git clone sur git clone ? 

Pour travailler sur un nouveau projet (ex un gros projet 42) qui dépend d'un autre projet (ex la libft), on peut faire :

```sh
git clone <url_gros_projet> MonGrosProjet
cd MonGrosProjet
git clone <url_libft> libft
 	↓ 
MonGrosProjet
├── libft
│   ├── ...
│   ├── ...
│   ├── ...
├── ...
├── ...
└── ...
```

On peut maintenir la libft à jour depuis ce repos  


<span style="color:red">
⚠️Mais attention La libft ne sera pas push avec le projet !
</span>


```sh
gaa && gcmsg -m 'asdf' && gp
 	↓ 
MonGrosProjet
├── libft\ <- ce dossier est completement vide
├── ...
├── ...
└── ...
```
<span style="color:red">
Alors comment faire ?
</span>

![image](https://media.tenor.com/Gc7Crn1EBVgAAAAC/steve-carell-sad.gif) <br>
<br>
<br>

## 2) Les "git submodules" : plus tricky, mais mieux 


Les submodules sont **la** solution : <br>



Pour maintenir la libft à jour : <br>

```sh
git pull --recurse-submodules
git push --recurse-submodules
```

<span style="color:green">
Et en prime, la libft sera bien push avec le projet. ✅
</span>

![image](https://media.tenor.com/mUR6IIN2CnEAAAAC/wow-surprised.gif) <br>

Mais ....
Pour bien cloner le projet, il sera necessaire de faire : 
```
git clone --recursive
```
Pensez-y ! ..

"*Oui mais la mouli ne rajoutera pas ce flag toute seule ?*"

Sans blagues Sherlock.
Mais tqt, tu peux facilement transformer ton submodules en simple directory : 

```
git --version #make sure git is >= V1.8.5 !
mv yoursubmodule yoursubmodule_tmp
git submodule deinit yourSubmodule
git rm yourSubmodule
mv yoursubmodule_tmp yoursubmodule
git add yoursubmodule
```
(à faire juste avant de push, évidemment)

"*si j'ai fail mon projet et que je dois le retry, comment remettre le submodules ? *"

```
rm yourdirectory
git submodule add <remote_url> <destination_folder>
```

Facile non ? 
