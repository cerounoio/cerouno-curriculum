---
title: Introduccion a Git
program: DAW
module: M1
layout: main
---

# Introducción a Git

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Utilizar Git como sistema de control de versiones
* Crear un repositorio en un proyecto
* Usar *commits* para registrar los cambios en el código
* Crear y cambiar de *branches*
* Unir cambios en el código de otros *branches*

### II. Introducción

**Git** es un sistema de control de versiones (*VCS* por sus siglas en inglés) que nos permite llevar un registro de los cambios que se realizan en el código de un proyecto. Esto es bastante útil si queremos analizar la evolución del código, ver las contribuciones de los miembros de un equipo, e incluso, regresar a una versión anterior del proyecto de ser necesario.

Los desarrolladores que usan Git, guardan regularmente sus contribuciones al proyecto en versiones llamados *commits*. Estos commits permiten que muchos desarrolladores puedan trabajar en los mismos archivos al mismo tiempo sin necesidad de guardar múltiples versiones como *archivo_final*, *archivo_final_1*, *archivo_final_final*, etc.

> **Git** no es lo mismo que **Github**. **Git** es el sistema de control de versiones, mientras que **Github** es la plataforma en línea donde puedes guardar tu código.

Para aprender más sobre Git, puedes visitar la página oficial [aquí](https://git-scm.com/).

### III. Instalación

#### macOS / Ubuntu

Para instalar Git en **macOS** o **Ubuntu**, tienes que tener **Homebrew** instalado. Si no lo has hecho, sigue los pasos en este [tutorial](/daw/m1/preparacion_del_ambiente_de_desarrollo). Para verificar si Homebrew está instalado escribe este comando en la terminal y presiona `Enter`:

```shell
$ brew doctor
Your system is ready to brew.
```

Una vez de asegurarte que tienes Homebrew instalado, escribe el siguiente comando en la terminal y presiona `Enter`:

```shell
$ brew install git
==>  Downloading https://homebrew.bintray.com/bottles/git-2.14.3.high_sierra.bottle.tar.gz
########################################################### 100.0%
Configuring Git
```

Para asegurarte de que Git se haya instalado correctamente, escribe el siguiente comandoen la terminal y presiona `Enter`:

```shell
$ git
```

Si ves un texto describiendo las diferentes maneras de usar Git, has instalado Git exitosamente.

#### Windows

Para instalar Git en **Windows** tienes que descargar el paquete de instalación en [esta página](https://git-scm.com/download/win). Una vez descargado el archivo, ejecútalo y sigue los pasos en la pantalla.

### IV. Configuración

Antes de utilizar Git, debemos configurarlo con nuestra información personal. Esto le permite saber a otras personas quién está realizando los cambios en el código. Sustituye tu información en los siguientes comandos y presiona `Enter`:

```shell
$ git config --global user.name "Juan Pérez"
$ git config --global user.email "juan@example.com"
```

Tal vez notaste que usamos el *flag* `--global` en el comando que pusimos en la terminal. Esto hace que la configuracion de Git sea válida para todos los proyectos en los usemos Git.

### V. Creando un Repositorio

Para que podamos empezar a trabajar con Git, tienes que crear un directorio utilizando el siguiente comando en tu terminal:

```shell
$ mkdir git-intro
```

Esto crea un directorio en tu computadora donde podemos crear un repositorio. Ahora tenemos que entrar a ese directorio y crear un repositorio con el siguiente comando en tu terminal:

```shell
$ cd git-intro
$ git init
Initialized empty Git repository in /Users/username/other-folders/git-intro/.git/
```

Para Git, un **repositorio** es un directorio que contiene el código de tu proyecto. Al ejecutar el comando `git init`, Git crea un directorio oculto `.git` que mantiene un registro de los cambios que realizas en tu código. No te preocupes. La mayor parte del tiempo, no tendrás que interactuar con este directorio, pero es importante que sepas que existe.

Si quieres ver este directorio, ejecuta el siguiente comando para ver los archivos ocultos:

```shell
$ ls -a
.    ..   .git
```

### VI. Nuestro Primer *Commit*

Git lleva un registro de los cambios en tu código siguiendo los cambios que haces en los archivos y directorios en tu repositorio. Estos cambios son guardados en **commits** que les permiten a otras personas incorporar los cambios que realizaste fácilmente.

Vamos a crear un archivo de texto para demostrar esto. Executa el siguiente comando en tu terminal:

```shell
$ touch archivo.txt
```

Para asegurarte de haber creado el archivo, ejecuta el siguiente comando en tu terminal:

```shell
$ ls
archivo.txt
```

Ahora, ejecuta el siguiente comando en tu terminal para ver los cambios en tu repositorio.

```shell
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	archivo.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Lo que este mensaje dice es que estás en el *branch* `master`, que hay un archivo que se llama `archivo.txt` que no está siendo registrado por Git, y que no hay ningún cambio en el código pero que hay un archivo nuevo en el repositorio.

> Aunque hasta ahora hemos llamado al *repositorio* con su nombre completo, la gente normalmente le llama *repo*, utilizando la pronunciación en inglés. Es más corto y fácil de recordar.

Cuando creas un nuevo archivo en Git, este no se registra automáticamente, sino que tienes que agregarlo a tu repositorio de Git. Para hacer esto, puedes hacerlo de dos maneras, puedes agregarlo individualmente usando `git add <nombre del archivo>` o agregando todos los archivos que han cambiado en un solo comando usando `git add -A`.

En este caso, vamos a usar esta segunda opción. En tu terminal, ejecuta el siguiente comando:

```shell
$ git add -A
```

Para ver los cambios en el estatus de tu repositorio, ejecuta el siguiente comando en tu terminal:

```shell
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   archivo.txt
```

Aquí puedes ver que el mensaje de Git ha cambiado. Nos dice que estamos en el *branch* `master`, que estamos en el commit inicial, y que existen cambios listos para ser registrados en el repositorio (*Changes to be commited*). Además, nos dice que si queremos remover un archivo del registro de cambios, tenemos que ejectar el comando `git rm --cached <nombre del archivo>`.

En este caso, estamos listos para registrar los cambios con un mensaje que nos permita encontrarlo después en el historial de cambios.

Para hacer esto, ejectuta el siguiente comando en tu terminal:

```shell
$ git commit -m 'Mi primer commit'
[master (root-commit) 8402d71] Mi primer commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 archivo.txt
```

Este mensaje nos dice que nuestro primer *commit* (el registro de los cambios en el código de nuestro *repo*) ha sido registrado exitosamente en el *branch* master, que éste ha cambiado un archivo, y que esto no ha borrado ni creado líneas nuevas en el archivo.

Si deseas ver el historial de cambios, puedes hacerlo ejecutando el siguiente comando:

```shell
$ git log
commit 8402d712bc7789f3fe59968cf9657c9499138d2f (HEAD -> master)
Author: Jorge Téllez <jorge@example.com>
Date:   Tue Oct 24 12:14:21 2017 -0500

    Mi primer commit
```

Aquí puedes ver el número de registro del *commit* o *SHA* (*Secure Hash Algorithm*, también llamado *hash*), el autor de los cambios, la fecha y el mensaje con el que fue creado. Esto, sin embargo, es mucha información cuando quieres ver varios commits.

Para ver una versión condensado del historial de registro de cambios, puedes ejecutar el siguiente comando:

```
$ git log --oneline
8402d71 (HEAD -> master) Mi primer commit
```

#### Ejercicio

Para asegurarnos de haber comprendido los contenidos de la lección hasta ahora, vamos a realizar el siguiente ejercicio:

1. Abre el archivo `archivo.txt` en tu terminal ejecutando `atom .`.
2. Escribe tu nombre completo y guarda el archivo con `CMD + S`.
3. Muestra el estatus de tu repositorio en la terminal.
3. Agrega los cambios en tu repositorio a Git.
4. Guarda los cambios en un commit.
5. Muestra el historial de cambios en tu terminal.

### VII. Manejando los *Branches*

En Git, puedes tener varias copias con diferentes versiones de tu código llamadas *branches*. Cada *branch* representa una línea de desarrollo que te permite realizar cambios al código sin afectar la copia maestra o el branch *master*.

> Es una buena práctica mantener el **master branch** sin cambios y libre de *bugs*. Antes de desarrollar una nueva funcionalidad es recomendable crear un *branch* nuevo y realizar los cambios ahí.

Cuando trabajas usando Git, el *workflow* de desarrollo sigue este proceso:

1. Creamos un nuevo *branch* basado en una funcionalidad que queremos agregar.
2. Nos cambiamos al *branch* que creamos.
3. Hacemos cambios, los agregamos a Git y los registramos en un *commit*.
4. Nos cambiamos al *branch* `master`.
5. Unimos los cambios del otro *branch* a `master`.

Ahora vamos a practicar este *workflow*.

#### Paso 1: Crea un Nuevo *Branch*

Primero, tenemos que asegurarnos de que estamos en el *branch* en el que queremos estar. Para hacer esto, ejecuta el siguiente comando:

```shell
$ git branch
* master
```

Este mensaje nos muestra que sólo tenemos el *master branch*, y que estamos en este *branch*.

Vamos a crear un nuevo *branch*. Para hacer esto, ejecuta el siguiente comando:

```shell
$ git branch nuevo
```

Ahora, si ejecutas el comando `git branch` de nuevo, podrás ver que hay un nuevo *branch* llamado `nuevo` en tu terminal.

```shell
$ git branch
* master
  nuevo
```

El asterisco al lado de *master* en esta lista, nos dice qué *branch* estamos en el *master branch* en este momento.

#### Paso 2: Cambia de *Branch*

Para cambiar de *branch* de *master* a *nuevo*, ejecuta el siguiente comando en tu terminal:

```shell
$ git checkout nuevo
Switched to branch 'nuevo'
```

Ahora, vamos a verificar que estamos en el *branch* correcto. Para hacer esto, ejecuta el siguiente comando:

```shell
$ git branch
  master
* nuevo
```

En el mensaje en la terminal, puedes ver que el asterisco está al lado de *nuevo*, lo que nos indica que hemos cambiado exitosamente de *branch*.

#### Paso 3: Guarda Cambios en el Nuevo *Branch*

Una vez que estamos en el nuevo branch, abre el archivo `archivo.txt` ejecutando en el siguiente comando en la terminal:

```shell
$ atom .
```

Una vez que hayas seleccionado el archivo en *Atom*, escribe lo siguiente:

```text
Este es mi archivo.
```

Después guarda el archivo en *Atom* usando `CMD + S`.

Ahora vamos a ver los cambios en el archivo usando el comando `diff`. Para hacer esto, ejecuta en la terminal lo siguiente:

```shell
$ git diff
Jorge Téllez
+Este es mi archivo.
```

El símbolo `+` indica que es una línea nueva. Cuando removemos una línea de nuestro archivo, Git usa el símbolo de `-` en vez.

Una vez agregada esa línea nueva, vamos a registrar los cambios en un *commit* ejecutando el siguiente comando en tu terminal:

```shell
$ git add -A
$ git commit -m 'agrega nuevo texto'
```

> Es una buena práctica escribir los mensajes de tus *commits* de manera descriptiva empezando por un verbo de lo que hace ese *commit*. Por ejemplo: "implementa autenticación" o "agrega permisos de administrador a los usuarios".

Después de registrar los cambios en nuestro *commit*, vamos a cambiar de *branch* ejecutando el siguiente comando:

```shell
$ git checkout master
Switched to branch 'master'
```

Ahora, vamos a unir los cambios del branch *nuevo* con el branch *master* ejecutando el siguiente comando:

```shell
$ git merge nuevo
Updating b1bb327..d1facae
Fast-forward
 archivo.txt | 1 +
 1 file changed, 1 insertion(+)
```

Para verificar que nuestro *commit* esté ahí, ejecuta el siguiente comando en tu terminal:

```shell
$ git log --online
d1facae (HEAD -> master, nuevo) agrega nuevo texto
b1bb327 Mi segundo commit
8402d71 Mi primer commit
```

Como puedes ver, nuestro *commit* está en la lista de *commits* de nuestro repo en Git.

Por último, vamos a borrar el *branch* que creamos ejecutando el siguiente comando en tu terminal:

```bash
$ git branch -d 'nuevo'
Deleted branch nuevo (was d1facae).
```

> Existen dos maneras de borrar un *branch*. Uno es más segura que la otra. Si quieres borrar un *branch* sólo si los cambios de ese *branch* han sido unidos, usa este comando `git branch -d <nombre del branch>`. Si quieres borrar un *branch* sin importar si los cambios han sido unidos, usa este comando `git branch -D <nombre del branch`.

#### Ejercicio

Para asegurarnos de haber comprendido la incorporación de código de otros *branches*, vamos a realizar el siguiente ejercicio:

1. Crea un branch nuevo llamado `otro-branch`
2. Cambia de branch a `otro-branch`
3. Abre el archivo `archivo.txt` y agrega la ciudad dónde naciste.
4. Guarda el archivo, registra los cambios en un *commit* y escribe un mensaje descriptivo.
5. Cambia de branch a *master*.
6. Une (o *merge* en inglés) los cambios de `otro-branch` con `master`.
7. Lista los *commits* de tu repo y verfica que tu nuevo commit esta en la lista.
8. Una vez unidos los cambios de `otro-branch` con `master`, elimina `otro-branch`.

Si quieres aprender cómo usar Git con **Github**, ve este [tutorial](/daw/m1/introduccion_a_github).
