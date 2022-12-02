# Git submodule

Pour travailler sur un nouveau projet (ex un gros projet 42) qui depend d'un autre projet (ex la libft) :

```sh
git clone <url_gros_projet> MonGrosProjet
cd MonGrosProjet
git clone <url_libft> libft
```
```
MonGrosProjet
├── libft
│   ├── ...
│   ├── ...
│   ├── ...
├── ...
├── ...
└── ...
```

| Avantages | Inconvenients |
| ----------- | ----------- |
|On peut maintenir la libft à jour depuis ce repos| ⚠️La libft ne sera pas push avec le projet !|
|||

```sh
gaa && gcmsg -m 'update' && gp
```

```
MonGrosProjet
├── libft\
├── ...
├── ...
└── ...
```
