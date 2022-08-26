# Clase 04

## GIT RESET
Tengo que elegir de la lista de commits los que quiero incluir en el reset. Para ellos tengo que seleccionar el inmediato inferior. 
### SOFT
Lo que hace es borrar los commits seleccionados y colocarme la información de esos commits en la zona del staging area

```sh
git reset --soft <hash>
git reset --soft 98d52e4
```

### MIXED
Lo que hace es borrar los commits seleccionados y colocarme la información de esos commits en el working directory

```sh
git reset --mixed <hash>
git reset --mixed 98d52e4
```

### HARD (Cuidado)
Es destructivo: Lo que hace es borrar los commits seleccionados y descartar la información que ellos tienen.

```sh
git reset --hard <hash>
git reset --hard 98d52e4
```

# GIST
Compartir código, pasar snippet a otras personas o información que quiero compartir.

<https://gist.github.com/>

Secretos => Solo la persona que tienen link puede verlo. No son privados
Publicos => Se van indexar en los motores de búsqueda

Pueden tener varios archivos y sus revisiones.

# GIT PAGES
Me permite alojar un sitio, estaticos. Aplicaciones React, Vue, Angular.
Hosting gratuito.

Hay que activar las GitHub Pages... 

Settings > Pages...

<https://<cuenta-github>.github.io/<repositorio>/>
<https://mlapeducacionit.github.io/proyecto-web/>

Respositorio con nombre especial
Actomaticamente este repositorio tiene activo GitHub

mlapeducacionit.github.io

## NETLIFY

<https://www.netlify.com/>


## APUNTADORES

### Aputandores estáticos

* RAMAS
* TAGS
* STASH

### Aputandores dinamicos

* HEAD


## TAGS

> Para crear un tag
```sh
git tag <nombre-tag> 
```

> Para ver los tags
```sh
git tag
```

> Para ver más info sobre un tag en particular
```sh
git tag <nombre-tag>
```