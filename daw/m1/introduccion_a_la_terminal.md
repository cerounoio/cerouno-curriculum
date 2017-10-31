---
title: Introduccion a la Terminal
program: DAW
module: M1
layout: main
---

# Introducción a la Terminal

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Entender la importancia de la terminal
* Sentirse cómodos con la estructura de directorios y archivos
* Crear, copiar, mover y borrar archivos en la terminal

### II. ¿Por Qué es Importante usar la Terminal?

Si has crecido alrededor de computadoras es posible que nunca hayas escuchado sobre la *Terminal*. Las computadoras actuales tienen una interfaz gráfica (o *GUI* por sus siglas en inglés), que nos permiten interactuar con archivos, folders y otras funcionalidades con sólo arrastrar el *mouse*.

Sin embargo, para los desarrolladores de software, la *GUI* no es lo suficientemente rápida. El arrastrar el *mouse* y abrir ventanas es sumamente ineficiente cuando programas, ya que esto implica cambiar de contexto cada vez. Si estás desarrollando una funcionalidad en tu programa, esto puede hacer que pierdas tu *momentum*. Además, algunas de las herramientas que usarás como un desarrollador de software sólo pueden ser usadas a través de la terminal.

La terminal es intimidante al principio. No tiene gráficas, todo son bloques de texto, y no te da mucho *feedback*. Además al usarla, posiblemente te dé miedo borrar todo lo que está en tu computadora.

No te preocupes. No vas a descomponer tu computadora. Lo peor que puede pasar es que tengas que reinstalar tu sistema operativo. Pero, si intentas usar la terminal con frecuencia cada vez te sentirás más cómodo.

Vamos a empezar con algunas interacciones básicas usando nuestros archivos en la terminal. Estamos asumiendo que estás usando *macOS* para esta lección.

### III. Viendo Carpetas y Archivos

Cuando abres tu terminal, ésta normalmente te lleva a tu directorio raíz (*root*). Un directorio es una lista estructurada de archivos (*files*) y carpetas (*folders*) guardada en tu computadora.

Tu directorio raíz contiene usualmente las siguientes carpetas (si tu sistema operativo está en español probablemente los nombres estén en ese idioma):

```text
|- Applications
|- Documents
|- Desktop
|- Music
|- Pictures
```

Esto puede variar dependiendo de tu computadora y de los archivos y carpetas que hayas creado.

#### La Ubicación Actual

Muchas veces cuando estás trabajando en la terminal es posible que no sepas en qué directorio estés. Para resolver esto, usamos el comando `pwd` que significa *print working directory*. En tu terminal, desde el directorio raíz, escribe el siguiente comando y presiona `Enter`:

```bash
$ pwd
/Users/<nombre de usuario>
```

Ahora si te pierdes en tu terminal o confundes tu ubicación, puedes usar `pwd` para encontrar dónde estás.

> Un *directorio* no es lo mismo que una *carpeta*. Estrictamente, un *directorio* es una lista estructurada de *archivos* y *carpetas*, mientras que una *carpeta* es un *repositorio de archivos*.

#### Listando Carpetas y Archivos

En nuestro sistema operativo, nuestros archivos están organizados en listas de archivos y carpetas. Si pudieras representar esta estructura probablemente verías algo así:

```text
|-- directorio-en-primer-nivel
  |-- directorio-en-segundo-nivel
  |-- directorio-en-segundo-nivel
    |-- directorio-en-tercer-nivel
```

En la terminal, no contamos con un Finder que visualmente nos diga qué contiene un directorio pero tenemos comandos que nos permiten hacer esto. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls
```

El comando `ls` lista los carpetas y archivos del directorio vigente. Sin embargo, no podrás ver las carpetas y archivos que están dentro de otros directorios, ni los archivos o carpetas ocultos.

Para listar los contenidos ocultos, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls -a
```

Como puedes ver, ahora podemos ver una lista de archivos y carpetas que no veíamos antes. Si te fijas bien, podrás ver que sus nombres inician con un punto `.`. Tú puedes crear documentos y carpetas ocultas desde la terminal, si sus nombres empiezan con un punto.

Si buscas una lista más detallada de los contenidos de un directorio, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls -l
```

Al agregar la opción `-l`, obtienes un listado de carpetas y archivos que incluye información de cuando un archivo o carpeta fue modificado, qué permisos contiene, y el tamaño del archivo y carpeta, entre otros.

También puedes utilizar ambas opciones juntas y obtendrás una lista detallada que incluye archivos ocultos. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls -la
```

> La estructura de un **comando** en tu terminal se divide en diferentes argumentos. El primer argumento es el **nombre del comando**, el segundo argumento son las **opciones del comando** (normalmente están acompañadas de un `-`), y los argumentos siguientes son los **parámetros del comando**, los cuales dan información al comando o a las opciones para poder ejecutar la instrucción. Por ejemplo, en el comando `ls -l Downloads`, `ls` es el nombre del comando, `-l` es la opción del comando, y `Downloads` es el parámetro. En este caso, estamos listando los contenidos de la carpeta `Downloads` en formato de lista detallada.

### IV. Creando Directorios y Archivos

Los archivos de nuestro sistema operativo están organizados en una estructura jerárquica de datos dividida en directorios y subdirectorios, que a su vez tienen archivos y carpetas. Ahora, vamos a aprender cómo crear y eliminar directorios y archivos.

#### Creando Directorios

Para crear un directorio desde tu terminal usamos el comando `mkdir` (*make directory*) más el nombre de directorio que quieras crear. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ mkdir tutorial
```

Al ejecutar este comando, no obtienes ningún mensaje de la terminal. Sin embargo, si usas el comando `ls` para listar los contenidos de tu directorio, verás que el directorio `tutorial` está ahí.

```bash
$ ls
```

Ahora, vamos a borrar el directorio que acabamos de crear. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ rm -rf tutorial
```

En este caso estamos usando dos opciones del comando `rm`. La opción `r` (*recursive*) nos permite borrar directorios, incluyendo sus contenidos. La opción `f` nos permite borrar todos los contenidos del directorio sin necesidad de confirmar nuestra decisión en el proceso.

 > Cuando queremos borrar un directorio, siempre tenemos que usar la opción `r` para eliminar los contenidos del directorio. Esto se debe a que la estructura sistema operativo nos impide tener carpetas y archivos que no estén asociados a un directorio.

Ahora vamos a verificar que el directorio se ha borrado. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls
```

Como puedes ver, el directorio `tutorial` ya no existe.

#### Creando Archivos

Para crear un archivo desde tu terminal usamos el comando `touch` más el nombre del archivo que quieras crear, incluyendo la extensión. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ touch tutorial.js
```

Al ejecutar este comando, tampoco obtienes ningún mensaje de la terminal. Sin embargo, si usas el comando `ls` para listar los contenidos de tu directorio, verás que el archivo `tutorial.js` está ahí.

```bash
$ ls
```

Ahora, vamos a borrar el archivo que acabamos de crear. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ rm tutorial.js
```

A diferencia de cuando estamos borrando un directorio, en esta ocasión no necesitamos la opción `r`.

Para verificar que el archivo se ha borrado, en tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls
```

Como puedes ver, el archivo `tutorial.js` ya no existe.

#### Ejercicio

En tu terminal:

1. Crea un directorio llamado `ejercicio`.
2. Lista los contenidos de tu directorio actual para verificar que se haya creado.
3. Crea un archivo oculto llamado `.oculto` y lista los archivos ocultos para verificar que se haya creado.
4. Elimina el directorio `ejercicio`.
5. Elimina el archivo `.oculto`.
6. Lista los contenidos de nuevo en formato de lista, y verifica que el directorio `ejercicio` y que el archivo `.oculto`, no existan.

### V. Navegando la Estructura de Archivos

Para cambiar nuestra ubicación dentro de la estructura de archivos, usamos el comando `cd` (*change directory*) y el nombre del directorio a donde nos queremos mover.

Primero, vamos a crear un directorio para explorar este concepto. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ mkdir mi_directorio
```

Una vez hecho esto, lista los contenidos para verificar que tu directorio se haya creado. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls
```

Ahora, vamos a movernos dentro de ese directorio. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ cd mi_directorio
```

Si utilizas el comando `pwd` podrás ver que nuestra ubicación actual ha cambiado. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ pwd
/Users/<usuario>/mi_directorio
```

Podemos movernos entre directorios en dos direcciones: **hacia arriba** o **hacia abajo**. También podemos movernos hacia un **directorio previo** o hacia un **directorio anidado**.

Para regresar al nivel anterior, usamos el comando `cd` más el parámetro `..`. Esto le dice a nuestro sistema operativo, que queremos ir a un nivel superior.

En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ cd ..
```

Si utilizas el comando `pwd` podrás ver que ahora estamos en el nivel superior. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ pwd
/Users/<usuario>
```

#### Usando *Tab Completion*

Cuando no sabemos a qué directorio ir o no queremos escribir el nombre completo, podemos utilizar la funcionalidad de *tab completion*. Por ejemplo, si estás buscando cambiar de directorio, y estás escribiendo las primeras letras del directorio, al presional la tecla `tab`, la terminal autocompletará el resto del directorio al que quisieras llegar.

Ahora vamos a probar esta funcionalidad. En tu terminal, escribe el siguiente comando y presiona `tab`:

```bash
$ cd mi
```

Si todo funciona bien, verás como `mi` se autocompleto en `mi_directorio`, el nombre del directorio que creamos en el ejercicio anterior.

#### Cambiando de Ubicación a Subdirectorios

Si quieres cambiar a un directorio que está dentro de otro directorio Puedes continuar agregando subdirectorios con nuestro comando `cd`.

Por ejemplo, imagina que tenemos la siguiente estructura de archivos:

```text
|- mi_directorio
  |- mis_notas
    |- mis_comentarios
```

Si estamos en tu directorio raíz y quieres cambiar tu ubicación a `mis_comentarios` rápido, lo puedes hacer escribiendo `cd mi_directorio/mis_notas/mis_comentarios`.

Como puedes ver, cada subdirectorio está separado por una barra oblícua `/` (o *slash*).

Del mismo modo, si quieres retroceder múltiples directorios con un comando único, puedes usar dos puntos con un *slash* como separador. Por ejemplo, si utilizando la estructura anterior, si estás en el directorio `mis_comentarios`, y quieres ir a mi_directorio, entonces puedes escribir el comando `cd ../..`.

#### Regresando al Directorio Raíz

Por último, si quieres regresar rápidamente a tu directorio raíz, puedes usar hacerlo de la siguiente manera. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ cd ~
```

El símbolo `~` representa nuestro directorio raíz. Sin embargo, este símbolo no es necesario. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ cd
```

Ahora utiliza el comando `pwd` en tu terminal y verás que estás en tu directorio raíz.

#### Ejercicio

En tu terminal:

1. Crea un directorio llamado `ejercicio_1`
2. Cambia de directorio al directorio `ejercicio_1` y crea otro directorio `ejercicio_2`.
3. Cambia de directorio al directorio `ejercicio_2` usando *tab completion*.
4. Crea un archivo que se llame `ejercicio.js`.
5. Cambia de directorio al directorio raíz.
6. Elimina el directorio `ejercicio_1` y todos sus archivos y carpetas.

### VI. Copiando Directorios y Archivos

Para copiar un archivo o directorio usamos el comando `cp`. Para aprender a utilizar este comando, vamos a copiar el directorio `mi_directorio`. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ cp -r mi_directorio directorio_copia
```

Si utilizas el comando `ls` puedes ver que tanto `mi_directorio` como `directorio_copia` están listados en el directorio.

Como puedes observar, para copiar un directorio, usamos el comando `cp`, y la opción `r`, lo cuál le permite copiar los contenidos del directorio también. Además, el primer parámetro (en este caso **mi_directorio**) es el nombre del directorio que queremos copiar, y el segundo parámetro (**directorio_copia**), es el nombre de la copia que hicimos.

Para copiar archivos, el comando es prácticamente el mismo. Lo único que cambia es que no utilizamos la opción `r` dado que no es un directorio.

En tu terminal, vamos a crear un archivo. Escribe el siguiente comando y presiona `Enter`:

```bash
$ touch mi_archivo.js
```

Ahora, vamos a copiar el archivo `mi_archivo.js`. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ cp mi_archivo.js archivo_copia.js
```

Si utilizas el comando `ls` podrás ver a ambos archivos listados en tu directorio.

Ahora vamos a borrar el directorio copia y el archivo copia. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ rm -rf directorio_copia && rm -f archivo_copia.js
```

> Como puedes ver, hemos utilizado el símbolo `&&` para encadenar dos operaciones en la terminal. Este comando nos dice que si la ejecución del primer comando es exitosa, entonces podemos ejecutar el siguiente comando. Si la ejecución exitosa del primer comando no nos importa, entonces podemos utilizar el símbolo `;` en vez.

#### Ejercicio

En tu terminal:

1. Crea un archivo llamado `archivo_original.txt`.
2. Crea una copia de ese archivo y llámala `archivo_copia_1.txt`.
3. Vuelve a crear una copia de ese archivo y llámala `archivo_copia_2.txt`.
4. Ahora elimina los dos archivos usando `&&` para encadenar ambos comandos.

### VII. Moviendo Archivos y Directorios

Para mover un archivo usamos el comando `mv`. Vamos a mover el archivo `mi_archivo.js` dentro del directorio `mi_directorio`. Para hacer esto, escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ mv mi_archivo.js mi_directorio
```

Si ahora usas el comando `ls` para listar los contenidos de tu directorio, verás que el archvio `mi_archivo.js` no está en la lista. Para ver la ubicación del archivo, puedes listar los contenidos del directorio `mi_directorio` directamente desde tu carpeta actual.

En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ ls mi_directorio
mi_archivo.js
```

Como puedes observar, el comando `mv` sigue una sintaxis similar al comando `cp`. Para mover un archivo, tienes que escribir el comando `mv` seguido del nombre del archivo que quieres mover y la ubicación a dónde lo quieres mover.

Además de mover archivos y directorios, el comando `mv` también nos permite renombrar a los mismos. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ mv mi_directorio mi_nuevo_directorio
```
Si ahora usas el comando `ls` para listar los contenidos de tu directorio, verás que el directorio `mi_directorio` ahora se llama `mi_nuevo_directorio`.

Para terminar, vamos a borrar este directorio para no dejar rastro de nuestros experimentos en el sistema. En tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ rm -rf mi_nuevo_directorio
```

Por último, lista los contenidos de tu directorio con el comando `ls` y verás que el directorio fue borrado.

#### Ejercicio

En tu terminal:

1. Crea un archivo llamado `mi_archivo_original.txt`.
2. Crea una carpeta llamada `mi_directorio_orginal`.
3. Mueve el archivo `mi_archivo_original.txt` dento de la directorio `mi_directorio_orginal`.
4. Cambia el nombre del directorio `mi_directorio_original` a `mi_nuevo_directorio`.
5. Lista los contenidos del directorio `mi_nuevo_directorio`.
6. Elimina `mi_nuevo_directorio`.
