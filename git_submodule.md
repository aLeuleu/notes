# Git - Dépendances

## 1)Juste gcl en fait! 

Pour travailler sur un nouveau projet (ex un gros projet 42) qui dépend d'un autre projet (ex la libft) :

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

<span style="color:green">
On peut maintenir la libft à jour depuis ce repos  
</span>.


<span style="color:red">
⚠️La libft ne sera pas push avec le projet !
</span>.


```sh
gaa && gcmsg -m 'update' && gp
 	↓ 
MonGrosProjet
├── libft\
├── ...
├── ...
└── ...
```

<br>
<br>

## Et les "git submodules", bonne ou mauvaise idée ? 

Les submodules sont la solution si l'on veut dépendre d'une dépandance **d'une manière statique !!** <br>

<span style="color:red">
⚠️On ne peut pas maintenir la libft à jour de cette manière  ! <br>
Mais on peut la tenir à jour grâce à : 
</span> <br>

```sh
git pull --recurse-submodules
```


<span style="color:green">
La libft sera push avec le projet.
</span>.
