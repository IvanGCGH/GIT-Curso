# Clase 03

## GIT MERGE

### 3 tipos de merge

* Fastfodward (No genera conflictos). El merge se hace automatico, sin intervencion del usuario.

* Recursiva (No genera conflicto). El merge se hace en forma automatica. No hay coliciones de cambios.

* Manual (Genera conflictos). Ocurre cuando hay modificaciones en la misma linea de codigo.


## Detener proceso de MERGE
Cuando se encuentran conflictos puedo detener el merge

```sh
git merge --abort
``` 


## Servicios en la nube para compartir repositorios

* GitHub: <https://github.com/>

* BitBucket: 

* GitLab: <https://about.gitlab.com/>

## GIT FETCH
Me trae y actualiza toda la metadata de git. **(.git)**

``` sh
git fetch --all
```

## GIT PULL
Me trae la info del GitHub a mi local

``` sh
git pull <remoto> <rama-local>
git pull origin ivan
git pull origin dev
```

## GIT BRANCH (Continuación)

Para listar tpda la informacion de las ramas tanto locales como remotas

``` sh
git branch -a
```

Verbose: Mostrarme mas detalle de las ramas. En el estado que esta las ramas y su ultimo commit.

``` sh
git branch -av
```

## Cheatsheet

<https://education.github.com/git-cheat-sheet-education.pdf>

## GIT ALIAS

Me permite escribir comandos por medio de una palabra clave

Creo un alias:

``` sh
git config --global alias.palabraclave "comando a abreviar"
git config --global alias.ll "log --oneline --decorate --all --graph"
git config --global alias.set "config --global"
git config --global alias.s "status"
```

Borro un alias:

``` sh
git config --global --unset alias.palabraclave
git config --global --unset alias.set
```

Veo los alias:

``` sh
git config --get-regexp palabra alias
```

Para ver mi configuración de GIT:

``` sh
git config --get-regexp user # Configuración de usuario (username, mail)
git config --list
```

## GIT AMEND

Este corrije siempre el ultimo commit realizado. Tambien permite agregar elementos a un ultimo commit. Luego de tipear este comando nos manda a nuestro editor por defecto, nos pide un mensaje, lo guardamos con la combinacion de Ctrl + O y luego para salir Ctrl + X

``` sh
git commit --amend # Me abre el editor que configuré por defecto
```
