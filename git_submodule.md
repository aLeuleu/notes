# Git - Dépendances

## Just gcl en fait! 

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
## Git submodules ? 

Les submodules sont la solution si l'on veut dépendre d'une dépandance **d'une manière statique !!** <br>

<span style="color:red">
⚠️On ne peut pas maintenir la libft à jour de cette manière  !
</span>.


<span style="color:green">
La libft sera push avec le projet.
</span>.
