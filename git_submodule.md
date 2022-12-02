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

On peut maintenir la libft à jour depuis ce repos  


<span style="color:red">
⚠️La libft ne sera pas push avec le projet !
</span>.


```sh
gaa && gcmsg -m 'asdf' && gp
 	↓ 
MonGrosProjet
├── libft\
├── ...
├── ...
└── ...
```

<br>
<br>

## 2) Les "git submodules" : plus tricky, mais mieux 

Les submodules sont la solution si l'on veut dépendre d'une dépandance **d'une manière statique !!** <br>



Pour maintenir la libft à jour : <br>
Mais on peut la tenir à jour grâce à : 

```sh
git pull --recurse-submodules
git push --recurse-submodules
```


<span style="color:green">
La libft sera bien push avec le projet.
</span>.
