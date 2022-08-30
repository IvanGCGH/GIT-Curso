# Minuta GIT 24/08 - Clase 03

## RAMAS: 

### ¿Para que sirven?

Nos permiten trabajar realizando pruebas que no influyan directamente en la rama principal

### Repaso sobre algunos comandos:

* git diff => En el working directory compara el estado actual con el último commit. Cuando hacemos un git diff desde una rama padre (por ejemplo 'master') a una rama hija (por ejemplo 'gitmerge') se comparan las diferencias existentes de una rama en relación a la otra. Para hacer esto nos paramos en una rama principal (en este caso 'master') y teniendo en cuenta también a la otra rama a comparar se escribe por consola:

```sh
git diff rama_a_comparar
git diff gitmerge
```

* git commit -am "mensaje" => Este comando añade a los archivos al area de confirmación y a su vez los confirma, por lo que no es necesario hacer un 'git add' antes. Cabe resaltar que para que este comando funcione los archivos deben estar en seguimiento o unmodified.

```sh
git commit -am "mensaje"
git commit -am "inicializando proyecto"
```

* git help -a => muestra por consola la documentación de GIT que nos puede ser de mucha ayuda para recordar, experimentar e implementar nuevos comandos.  

```sh
git help -a
```

## GIT MERGE: 

Crea una rama 'gitmerge' y se traslada a la misma => git switch -c gitmerge

Pone los archivos en seguimiento con git add .

Confirma los cambios con git commit -m 'mensaje'

git switch -  => vas saltando de una rama a la otra

### Tenemos 3 tipos de merge:

#### Fastfodward => No genera conflictos. El merge se hace automático por lo que el usuario no interviene.

#### Recursiva => No genera conflictos. El merge se hace de manera automática. No hay colisiones de cambios.

#### Manual => Genera conflicto. Ocurre cuando hay modificaciones en las mismas líneas de código, es decir, cuando hay superposición entre líneas y GIT no va a saber qué información quiero guardar.

## Detener el proceso de merge

Los conflictos que se producen influyen 'físicamente' en el archivo, con quiere decir que paso el archivo a un formato .txt, .docx, etc, este archivo va a contener el texto que escribe GIT cuando encuentra un archivo en el código. Un ejemplo es el siguiente:

```sh
<<<<<<< HEAD

bloque de código de la rama donde queremos traer los cambios

=======

bloque de código de la rama a fusionar

>>>>>>> gitmerge
```

El HEAD hace referencia al nodo de cabecera o dicho de otra forma a la rima donde estemos parados actualmente, en este caso estoy parado en la rama MASTER (principal). Luego viene el bloque de código que le corresponde a la rama donde estamos parados. Después vienen los iguales que indican la separación del bloque de código de la rama principal con el bloque de código de la rama a fusionar, es decir, aquella rama de donde nos queremos traer la información, en este caso es la rama 'gitmerge'.
Estos conflictos generalmente se dan porque en ambas ramas hay código en el mismo número de línea de código.

* En el caso de que nosotros hagamos un 'git merge' de una rama y no estamos seguros de integrar el codigo que esta contiene, podemos hacer un 'git merge --abort' y cancelar la fusión de la rama hija con la rama padre  

* En el caso de que si estemos seguros y por lo tanto hayamos sacado las referencias que nos da GIT, el conflicto ya se encuentra resuelto y nos quedaría de la siguiente manera:

```sh

bloque de código de la rama donde queremos traer los cambios


bloque de código de la rama a fusionar

```

Como resultado ya nos encontramos listos para hacer un commit de esto y 'cerrar' la etapa de merge. 

Después de realizar el commit de esta información el profesor implementó un nuevo comando:

```sh
git log --oneline --decorate --graph --all
```

Este comando va a devolver toda la información sobre el repositorio y va a mostrar por consola las conexiones entre ramas de una manera más dinámica.

## GIT PAGES:

El profesor realiza un proyecto colaborativo de prueba que consiste en que cada integrante cree su propia rama y agregue en el documento HTML principal un elemento <p> que tenga contenga algo aleatorio escrito por cada integrante. Es decir que van a ver tantos elementos <p> como cantidad de colaboradores en el proyecto. Algo importante es que para agregar colaboradores a un repositorio de GitHub se realiza desde allí enviando una invitación solamente a través de correo electrónico y el destinatario tendrá que aceptar dicha invitación para unirse al proyecto. 

Lo primero que se hace es inicializar el proyecto público en GitHub, luego se inicializa en la bash de git con los siguientes comandos:

```sh
git remote add origin (ruta)
git remote add origin https://github.com/mlapeducacionit/proyecto-colab-pescar.git
```

y

```sh
git add origin -u master
```

Pero en nuestro caso como el que creó el repositorio fue el profesor solo basta con clonarlo para trabajar en nuestro entorno local con:

```sh
git clone (ruta)
git clone https://github.com/mlapeducacionit/proyecto-colab-pescar.git
```

Lo que hace el profesor localmente es crear las ramas correspondientes a cada colaborador y una base de código que después vamos a modificar. Por lo tanto para subir estas ramas al repositorio remoto de GitHub se ejecuta desde la bash de GIT:

```sh
git push origin <rama1> <rama2> <rama3> <etc>
git push origin ivan maxi mauro hernan geronimo angie alison
```

Una vez hecho esto ya se encuentran agregadas las ramas locales al repositorio remoto.

Ahora lo que sigue es clonar el proyecto pero antes se crea una carpeta denominada "nombreColaborador-proj-collab" o bien por ejemplo "ivan-proj-collab". Ahora si podemos clonar el repositorio, para ello primero en la GIT BASH nos situamos en la carpeta a donde queremos que se clone el repositorio y ejecutamos el siguiente comando:

```sh
git clone <url> .
```

Este punto al final del comando indica que se quiere descomprimir la carpeta del repositorio y no crear una nueva con los archivos dentro.

Pasamos a trabajar con las ramas. Primero las visualizamos a todas con:

```sh
git branch -a
```

Si se quiere ver aún más información acerca de las ramas:

```sh
git branch -av
```

Las ramas de color verde son las que ya se encuentran descargadas y las de color rojo son las que no se estan descargadas.

Para descargar o pasar a una rama:

```sh
git switch <rama>
git switch maxi
```

Nos traemos la información de master hacia la rama correspondiente para trabajar en el código:

```sh
git merge maxi
```

En consecuencia, cada colaborador comienza a modificar el documento HTML agregándole su toque personal. El resultado es el siguiente:

```sh
<body>
    <h1>Proyecto Colaborativo</h1>

    <p>"Lo que ustedes quieran" by @Pandiimau</p>

    <p>Alison</p>

    <p>Ivan: aprendiendo GIT</p>

    <p>Angie</p>

    <p>Hernan</p>

    <p>Geronimo, me siento hacker :)</p>

    <p>Maxi</p>
</body>
```

Una vez que se agregaron y se confirmaron los cambios lo que queda es subir el código al repositorio remoto, siempre haciendo referencia a la rama específica que nosotros queremos subir, en este caso puede ser:

```sh
git push -u origin <rama-local>
git push -u origin maxi
```

Luego de que cada colaborador haya hecho un push de su rama al repositorio remoto lo que sigue es actualizar toda la información al repositorio remoto (en el caso del profesor que es el dueño del proyecto). Para traer toda la metadata:

```sh
git fetch -all
```

Este comando te descarga la metadata pero sin agregarla directamente al repositorio local. Simplemente la trae para visualizarla y trabajar en ella.

Para actualizar la información de la rama local con la que tiene la remota nos dirigimos a dicha rama local:

```sh
git switch <rama-local>
git switch maxi
```

Y ejecutamos el comando pull (trabaja con información desde el repositorio remoto al local):

```sh
git pull origin <rama-local>
git pull origin maxi 
```

Como la información nos parece correcta la fusionamos con la rama principal (master) haciendo un merge a la rama hija (podría ser la rama 'maxi'), así que cuando estemos parados en la rama principal escribimos:

```sh
git merge maxi
```

## GIT ALIAS:

Los alias se usan para acortar la escritura de aquellos comandos que sean algo extensos por medio de una palabra clave.

### Para crear un alias:

```sh
git config --global alias.nombre "comando-a-ejecutar"
git config --global alias.lon "log --oneline"
git config --global alias.ll "log --oneline --decorate --graph --all"
```

### Para borrar un alias:

```sh
git config --global --unset <nombre-del-alias>
git config --global --unset alias.set
```

### Para buscar la lista de alias disponibles:

```sh
git config --get-regexp alias
```

## GIT AMEND:

Utilizado para corregir el último commit hecho. También permite agregar elementos o código a un último commit. Antes que todo agregamos los archivos al área de confirmación con "git add .". Ahora sí podemos ejecutar el próximo comando:

```sh
git commit --amend
```

Al efectuar el anterior comando se va a abrir una pequeña interfaz donde vamos a escribir el mensaje que reemplazará al anterior. Luego de escribir dicho mensaje apretamos la combinación de ctrl + o para guardar cambios y ctrl + x para salirnos del editor.

Un punto importante que hay que tener en cuenta es que git --amend cambia el hash del commit anterior por uno nuevo por lo que pueden surgir problemas de referencia. Si estamos seguros de hacer este cambio hacemos:

```sh
git push --force
```

## Cheatsheet de ayuda con comandos de GIT:

<https://education.github.com/git-cheat-sheet-education.pdf>
