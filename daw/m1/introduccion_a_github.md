---
title: Introduccion a Github
program: DAW
module: M1
layout: main
---

# Introducción a Github

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Configurar Github
* Crear repositorios remotos
* Enviar código local al repositorio remoto
* Bajar cambios del repositorio remoto al repositorio local

Este tutorial está basado en el [Introducción a Git](/daw/m1/introduccion_a_git). Si no has hecho ese tutorial, te recomendamos completarlo primero.

### II. Usando Github

**Github** es una plataforma de colaboración para desarrolladores de software que utiliza Git. Además de la funcionalidad de Git, Github permite la organización del desarrollo de software a través de un sistema de manejo de *issues*, controles de acceso y colaboración, y hosting remoto de repositorios.

> La mascota de Github es un gato con ocho tentáculos llamado [Octocat](https://octodex.github.com/). Seguramente lo has visto en *stickers* en las laptops de muchos desarrolladores de software.

#### Paso 1: Abre tu Cuenta de Github

Visita Github [aquí](https://github.com) y sigue las instrucciones para abrir tu cuenta. Hay opciones de pago si quieres tener repositorios privados. Esto no es necesario por el momento. Escoge la opción **gratis**.

#### Paso 2: Crea un Repositorio Remoto

En Github, una vez que entras al sistema usando tu usuario y password, verás en la esquina superior derecha la foto de tu perfil. Al lado de tu perfil, del lado izquierdo, verás este signo `+`. Da click ahí, y selecciona la opción de `New repository`.

Si seguiste las instrucciones, Github te redireccionará a la página donde puedes crear un nuevo repositorio.

Ahí, introduce el nombre del *repo* `git-intro`, una descripción (esto es opcional), y escoge que tu repositorio sea público. Después de hacer esto, da click en el botón de `Create repository`.

#### Paso 3: Agrega el *Remote* de Github a tu *Repo* Local

En la página de Github de tu repo, da click en el botón de `https` y copia el url. Este deberá seguir un formato similar a este `https://github.com/<nombre de usuario>/git-intro.git`.

Una vez hecho esto, en tu terminal asegúrate de estar en el directorio `git-intro` en tu computadora. Este directorio contiene el *repo* con tu código.

Para agregar el repositorio remoto o *remote* a tu repositorio local, ejecuta el siguiente comando en tu terminal:

```bash
$ git remote add origin <url de tu repo>
```

Ahora tienes un *remote* llamado *origin* en tu repositorio local a donde puedes mandar el código de tu proyecto. Para ver la lista de *remotes* disponibles en tu *repo* ejecuta este comando en tu terminal:

```bash
$ git remote
origin
```

> Puedes agregar varios *remotes* a tu repositorio local con diferentes nombres. Por convención, los desarrolladores de software llaman al repositorio remoto principal *origin*.

### III. Manda tu Código a Github

Una vez que tienes el *origin remote* listo en tu repositorio local, puedes mandar tu código a tu repositorio remoto. Para hacer esto ejecuta el siguiente comando en tu terminal:

```bash
$ git push origin master
Username for 'https://github.com': <tu username>
Password for 'https://<username>@github.com': <tu password>
Counting objects: 9, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (9/9), 730 bytes | 730.00 KiB/s, done.
Total 9 (delta 0), reused 0 (delta 0)
To https://github.com/<username>/git-intro.git
 * [new branch]      master -> master
```

Ahora visita la página de tu repositorio remoto en Github y recarga la página. Ahora verás que tu código está ahí.

### IV. Descarga tu Código de Github

Ya que tienes tu código en tu repositorio remoto, vamos a hacer un cambio en tu código desde Github para que veas el proceso de descargar código remoto.

Para hacer esto, haz click en el nombre del archivo llamado `archivo.txt`. Una vez en que veas los contenidos de tu archivo, haz click en el ícono de lápiz que se encuenta en la parte superior derecha. Esto te va a llevar a un editor de texto. Agrega el nombre de tu escuela en la primaria, y en la parte de abajo de la página, da click en el botón de `Commit changes`. Esto creará un *commit* con los cambios de tu archivo en el *master branch* en tu repositorio remoto.

> Modificar tu código en la página de Github no es recomendable. Aunque la funcionalidad existe, esto te impide utilizar las herramientas locales de tu ambiente de desarrollo para checar la sintaxis del código y hacer las pruebas necesarias.

Ya que modificaste el código en tu repositorio remoto, en tu terminal ejecuta el siguiente comando:

```bash
$ git pull origin master
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/novohispano/git-intro
 * branch            master     -> FETCH_HEAD
   d1facae..c0620e8  master     -> origin/master
Updating d1facae..c0620e8
Fast-forward
 archivo.txt | 1 +
 1 file changed, 1 insertion(+)
```

Ahora, ve los cambios en tu archivo local llamado `archivo.txt` ejecutando el siguiente comando en tu terminal:

```bash
$ atom archivo.txt
```

Como puedes ver, los cambios han sido incorporados a tu código.

> Hasta ahora hemos utilizado `HTTPS` ([Hyper Text Transfer Protocol Secure](https://en.wikipedia.org/wiki/HTTPS)) para conectarnos con Github. Este protocolo de transferencia permite la transmisión de datos de modo seguro mediante una conexión encriptada con `TLS` (o su predecesor `SSL`). Sin embargo, también te puedes conectar directamente con Github usando `SSH` ([Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell)), lo que te permite hacer *remote login* en Github para transmitir tu código. Puedes aprender más sobre este sistema de transferencia y como configurarlo [aquí](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).
