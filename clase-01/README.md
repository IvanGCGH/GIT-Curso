# Clase 01

## Primer paso

```sh
git config --global user.name "Nombre Apellido"
git config --global user.email "Email"
```
> Ejemplo

```sh
git config --global user.name "Maximiliano Príncipe"
git config --global user.email "mlapeducacionit@gmail.com"
```

## Por proyecto (Directorio o Carpeta)

### Repositorio GIT
Crea una carpeta oculta. Llamada **.git** 

```sh
git init
```

## AREAS DE GIT

> Working Directory (Carpeta o directorio del proyecto)

> Staging Area (El área de confirmación)

> Local Repo (La cajita donde tengo todas las fotos)

## Estados de los archivos

> Untracked: Git sabe que existe, pero no conoce su contenido, ni esta en el repo

> Modified: Git sabe que algo cambio del archivo. Compando Working Directory con el Local Repo

> Unmodified: Git sabe que no cambió el archivo. Respecto al Local Repo

> Staged: El archivo o archivos están en el staging area.

## GIT ADD
Confirmo archivos que quiero próximamente commitear.

```sh
git add . # con esto agrego todo al staging area
git add clase-01/README.md
```

## GIT COMMIT
Crear una foto de los archivos en el estado actual

```sh
git commit -m "Mensaje del Commit"
```

## GIT DIFF 

> Para ver diferencias entre el Working Directory y el Local Repo

```
git diff
```

## GIT LOG
Para salir del comando git log, tengo que presionar la tecla **q**

```sh
git log # Versión larga de la historia del repo
git log --oneline # Versión resumida
git log -1 # Listo cantidad de commits especificados
```
### GIT RESTORE
Me permite sacar archivos del area de staging.

```sh
git restore --staged <archivo>
git restore --staged css/styles.css
```

