---
title: Preparacion del Ambiente de Desarrollo
program: DAW
module: M1
layout: main
---

# Preparación del Ambiente de Desarrollo

Cuándo eres desarrollador de software, nos referimos al **ambiente de desarrollo** (o *development environment* en inglés) al conjunto de herramientas en tu computadora que te permiten programar. Estas varían entre lenguajes de programación, sistemas operativos e incluso, entre compañías.

En este tutorial, vamos a aprender como instalar **Node.js**, la plataforma que nos permite ejecutar programas escritos en JavaScript. Además, vamos a instalar **Atom**, un editor de texto que nos permite escribir programas utilizando *syntax highlighting* y nos facilita la lectura de código.

Para instalar **Atom** simplemente visita [esta página](https://atom.io) y descarga la versión para tu sistema operativo.

Selecciona las instrucciones dependiendo de tu sistema operativo:

1. [macOS](#macOS)
2. [Ubuntu](#ubuntu)
3. [Windows](#windows)

### <a name='macOS'></a> macOS

Antes de instalar **Node.js**, tenemos que instalar dos aplicaciones, **XCode** y **Homebrew**.

#### Paso 1: Instalar XCode Command Line Tools

**XCode** es el software de desarrollo de Apple. Este software se utiliza para desarrollar aplicaciones en las plataformas de Apple como macOS, iOS, tvOS y watchOS. Sin embargo, aunque nosotros no vamos a utilizarlo para desarrollar aplicaciones de Apple, XCode incluye herramientas que nos permiten compilar los programas que desarrollemos en **Node.js** en tu computadora.

Afortunadamente, no necesitamos instalar todo XCode para tener estas herramientas. Para instalar solamente las herramientas de la línea de commando de XCode (*XCode Command Line Tools* en inglés), escribe este comando en la terminal y presiona `Enter`:

```bash
$ xcode-select --install
```

Después de hacer esto, te aparecerá un diálogo en tu computadora. Sigue las instrucciones en pantalla y espera a que el programa se termine de instalar.

#### Paso 2: Instalar Homebrew

**Hombrew** es un sistema para manejar paquetes en tu sistema operativo. Esto nos facilita la instalación de software de código abierto. Para installar Homebrew abre tu terminal, escribe el siguiente comando y presiona `Enter`:

```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Después de hacer esto, sigue las instrucciones en la pantalla de tu terminal.

#### Paso 3: Instalar NVM

Una vez instalado **Homebrew**, vamos a instalar **Node.js** usando **NVM** (por *Node Version Manager* por sus siglas en inglés). **NVM** nos permite administrar diferentes versiones de **Node.js** en nuestro sistema dependiendo de nuestro proyecto. Para instalarlo, escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.6/install.sh | bash
```

Después de hacer esto, tenemos que recargar la sesión de tu terminal. Para hacer esto, en tu terminal, escribe este comando y presiona `Enter`:

```bash
$ . ~/.bash_profile
```

Ahora vamos a verificar que **NVM** se haya instalado correctamente. Escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ nvm
```

Si ves una lista de comandos disponibles para **NVM**, la instalación ha funcionado.

#### Paso 4: Instalar **Node.js**

Ahora vamos a instalar **Node.js**. Primero hay que ver cuál es la última versión de **Node.js**. Para hacer esto, escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ nvm ls-remote
```

Una vez que ya encontraste la versión que deseas instalar, escribe el siguiente comando en tu terminal y presiona `Enter`. Cambia `<version>` por la versión que quieras instalar:

```bash
$ nvm install <version> --latest-npm
```

Para comprobar que hayas instalado todo correctamente, primero tenemos que recargar la sesión de la terminal. Para hacer esto escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ . ~/.bash_profile
```

Ahora, vamos a verificar que todo esté en orden. Escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ node -v
```

Esto imprime el número de versión de Node en la terminal. Si esto funciona, has instalado correctamente Node.

Por último, vamos a verificar que **NPM** se haya instalado correctamente. **NPM** es el sistema de Node que permite manejar dependencias (librerías externas programadas por otros desarrolladores que nos facilitan el trabajo). Escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ npm -v
```

Este comando imprime el número de versión de **NPM** en la terminal. Si esto funciona, **NPM** se ha instalado correctamente.


### <a name='ubuntu'></a> Ubuntu

Antes de instalar **Node.js**, tenemos que instalar **Ruby** y **Linuxbrew**.

#### Paso 1: Instalar Ruby

**Ruby** es un lenguaje de programación orientado a objetos. Para instalar este lenguaje, escribe este comando y presiona `Enter`:

```bash
$ sudo apt-get install build-essential curl git m4 ruby texinfo libbz2-dev libcurl4-openssl-dev libexpat-dev libncurses-dev zlib1g-dev
```

Después de hacer lo anterior, espera y selecciona `Y` cuando te lo pida la terminal.

Para confirmar que ese haya instalado correctamente, escribe este comando y presiona `Enter`:

```bash
$ ruby -v
```

#### Paso 2: Instalar Linuxbrew

**Linuxbrew** es una versión del sistema para manejo de paquetes desarrollado para macOS, Homebrew. Ubuntu tiene su propio sistema de manejo de paquetes llamado **APT**. Sin embargo, Linuxbrew hace que el manejor de paqueterías sea más fácil e intuitivo.

Para instalar Linuxbrew, escribe este comando y presiona `Enter`:

```bash
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/linuxbrew/go/install)"
```

Ahora, vamos a agregar los `paths` a tu perfil, para que Ubuntu sepa dónde encontrar los paquetes que instales a través de Linuxbrew. Para hacer esto, en tu terminal, escribe este comando y presiona `Enter`:

```bash
$ cd
$ atom .bashrc
```

Una vez que Atom haya abierto tu archivo de `.bashrc`, copia el siguiente texto y pégalo hasta abajo de tu archivo en una línea nueva.

```text
export PATH="$HOME/.linuxbrew/bin:$PATH"
export MANPATH="$HOME/.linuxbrew/share/man:$MANPATH"
export INFOPATH="$HOME/.linuxbrew/share/info:$INFOPATH"
```

Después de hacer esto tenemos que recargar la sesión de tu terminal. Para hacer esto, en tu terminal, escribe este comando y presiona `Enter`:

```bash
$ . ~/.bash_profile
```

#### Paso 3: Instalar NVM

Una vez instalado **Homebrew**, vamos a instalar **Node.js** usando **NVM** (por *Node Version Manager* por sus siglas en inglés). **NVM** nos permite administrar diferentes versiones de **Node.js** en nuestro sistema dependiendo de nuestro proyecto. Para instalarlo, escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.6/install.sh | bash
```

Después de hacer esto, tenemos que recargar la sesión de tu terminal. Para hacer esto, en tu terminal, escribe este comando y presiona `Enter`:

```bash
$ . ~/.bash_profile
```

Ahora vamos a verificar que **NVM** se haya instalado correctamente. Escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ nvm
```

Si ves una lista de comandos disponibles para **NVM**, la instalación ha funcionado.

#### Paso 4: Instalar **Node.js**

Ahora vamos a instalar **Node.js**. Primero hay que ver cuál es la última versión de **Node.js**. Para hacer esto, escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ nvm ls-remote
```

Una vez que ya encontraste la versión que deseas instalar, escribe el siguiente comando en tu terminal y presiona `Enter`. Cambia `<version>` por la versión que quieras instalar:

```bash
$ nvm install <version> --latest-npm
```

Para comprobar que hayas instalado todo correctamente, primero tenemos que recargar la sesión de la terminal. Para hacer esto escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ . ~/.bash_profile
```

Ahora, vamos a verificar que todo esté en orden. Escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ node -v
```

Esto imprime el número de versión de Node en la terminal. Si esto funciona, has instalado correctamente Node.

Por último, vamos a verificar que **NPM** se haya instalado correctamente. **NPM** es el sistema de Node que permite manejar dependencias (librerías externas programadas por otros desarrolladores que nos facilitan el trabajo). Escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
$ npm -v
```

Este comando imprime el número de versión de **NPM** en la terminal. Si esto funciona, **NPM** se ha instalado correctamente.

### <a name='windows'></a> Windows

Instalar **Node.js** es muy fácil. Ve a la [página de Node.js](https://nodejs.org/es/) y descarga el instalador de Windows. Una vez descargado el archivo, corre el instalador, y sigue las instrucciones en pantalla. Por último, reinicia tu computadora para que puedas usar Node.js.

Para verficar la instalación, abre el `Windows Command Prompt`, escribe la siguiente instrucción, y presiona `Enter`:

```bash
C:\> node -v
```

Esto imprime el número de versión de Node en la terminal. Si esto funciona, has instalado correctamente Node.

Por último, vamos a verificar que **NPM** se haya instalado correctamente. **NPM** es el sistema de Node que permite manejar dependencias (librerías externas programadas por otros desarrolladores que nos facilitan el trabajo). Escribe el siguiente comando en tu terminal y presiona `Enter`:

```bash
C:\> npm -v
```

Este comando imprime el número de versión de **NPM** en la terminal. Si esto funciona, **NPM** se ha instalado correctamente.

Para asegurarte de que **Node.js** siempre esté actualizado, asegúrate de visitar la [página de Node.js](https://nodejs.org/es/) y descarga el instalador con la última versión.
