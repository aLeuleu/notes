# Git - Dépendances

## 1) git clone sur git clone ? 

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
├── libft\
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
