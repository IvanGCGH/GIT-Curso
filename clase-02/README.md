# Clase 02

## .gitignore
Permite ignorar archivos que no quiero formen parte del repositorio de git.
Normalmente se crear en la raíz del proyecto

> Creo el archivo

```sh
touch .gitignore
```

## GIT REMOTE
Nos permite agregar al repositorio local un repositorio remoto

> Agregar un repositorio remoto al local

```sh
git remote add <alias> <url>
git remote add origin git remote add origin https://github.com/mlapeducacionit/61094-git.git
```

> Borra el repositorio remoto

```sh
git remote rm <alias> 
git remote rm origin 
```

> Borra el repositorio remoto

```sh
git remote rename <alias-original> <alias-nuevo> 
git remote rename origin pepito
```

## GIT CLONE
Nos sirve para hacer una copia exacta del repositorio y su metada (.git)

```sh
git clone <url> # Me va a clonar el repo dentro de una carpeta con el nombre del repo
git clone <url> . # Se clona en la carpeta actual, sin crear ninguna carpeta extra 
```

## GIT BRANCHES (RAMAS)
Son bifurcaciones en el tiempo para por ejemplo poder trabajar en funcioanlidades que aún no están del todo probadas

> Ver ramas

```sh
git branch
```

> Crear ramas

>> Me crear la rama y no cambia a esa rama

```sh
git branch <nombre-rama-nueva>
git branch dev
```

> Para borrar una rama

```sh
git branch -d <nombre-rama>
git branch -d dev-2
```

> Para forzar el borrado. Esto ocurre cuando tengo información en la rama que no está fusionada.

```sh
git branch -D <nombre-rama>
git branch -D dev-2
```

## GIT SWITCH 
Me permite cambiar entre ramas

> Cambiar de rama

```sh
git switch <nombre-rama>
git switch dev
```

> Me la crea y se mueve a esa rama

```sh
git switch -c <nombre-rama-nueva>
git switch -c dev-2
```

## GIT MERGE (FUSIONAR RAMAS)
Me permite unificar cambios de diferentes ramas. Funsionar el contenido que tengan las ramas.

**IMPORTANTE:** Tengo en la rama destino. O sea por ejemplo. Si quiero traerme los cambios que tengo en **dev** a **master**. Tengo que estar posicionado en la rama **master**.

```sh
git switch master
git merge dev
```

## AYUDA DE GIT
Me permite ver la ayuda detallada de cada sub-comando

```sh
git <nombre-subcomando> --help
git commit --help
git switch --help
git branch --help
```

