---
title: Introducción a TDD
program: DAW
module: M1
layout: main
---

# Introducción a *TDD*

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Desarrollar sus programas usando *TDD*
* Instalar Mocha y Chai en su proyecto
* Escribir sus pruebas usando estas librerías

### II. Antecedentes

**Test-Driven Development** (o *TDD*) es una técnica de programación que promueve el desarrollo de software en pequeños ciclos o iteraciones. Está técnica consiste en escribir un *test* (o *prueba* en español) antes de programar la funcionalidad para guiar al desarrollador de software. El objetivo es eliminar errores (o *bugs*) y sólo desarrollar la funcionalidad esperada y nada más.

El proceso de *TDD* sigue este ciclo:

1. El gerente de producto define una funcionalidad
2. El programador agrega una prueba que define esta funcionalidad
3. El programador corre todas las pruebas y ve si la nueva prueba falla
4. El programador escribe el código que hacer que la prueba pase
5. El programador corre todas las prubas y ve si la nueva prueba pasa
6. El programador mejora su implementación mediante *refactoring*
7. El ciclo se repite

Esta técnica fue reintroducida en el mundo de la programación en el 2003 por [Kent Beck](https://en.wikipedia.org/wiki/Kent_Beck). Beck es un promotor de las prácticas de desarrollo ágil e inventor de la metodología [Extreme Programming](https://en.wikipedia.org/wiki/Extreme_programming), la cuál busca mejorar el desarrollo de software respondiendo más rápido a las necesidades del cliente. Beck también desarrollo el *testing framework* de Java llamado [JUnit](https://en.wikipedia.org/wiki/JUnit).

### III. Instalando Mocha y Chai

Antes de empezar a escribir nuestras pruebas, tenemos que preparar nuestro proyecto. Primero vamos a crear un directorio `introduccion-a-tdd`. en tu terminal, ejecuta el siguiente comando:

```bash
$ mkdir introduccion-a-tdd
```

Una vez hecho esto, entra en el directorio, y crea un archivo `package.json` usando *NPM*. En tu terminal, ejecuta el siguiente comando:

```bash
$ cd introduccion-a-tdd && npm init -f
```

Ahora crea dos subdirectorios, `test` y `lib`. `test` es donde vamos a escribir las pruebas, mientras que `lib` es dónde vamos a escribir nuestro código. En tu terminal, ejecuta el siguiente comando:

```bash
$ mkdir lib test
```

Ya que tenemos la estructura de nuestro proyecto, ahora vamos a instalar **Mocha** y **Chai**. [Mocha](https://mochajs.org/) es un *test framework* de JavaScript, mientras que [Chai](http://chaijs.com/) nos permite tener una syntaxis más amigable para escribir nuestras prubas.

Para instalar Mocha globalmente, ejecuta el siguiente comando en tu terminal:

```bash
$ npm install --global mocha
```

Ahora, vamos a instalar Chai globalmente. En tu terminal, ejecuta el siguiente comando:

```bash
$ npm install --global chai
```

Esto nos va a permitir usar ambas librerías desde cualquier directorio en nuestra terminal.

Ya que hicimos esto, vamos a instalar Mocha y Chai en nuestro proyecto. Esto lo hacemos para que quien no tenga estas librerías pueda utilizarlas desde nuestro proyecto. En tu terminal, ejecuta el siguiente comando:

```bash
$ npm install -D mocha
```

Con el comando anterior estamos instalando Mocha en nuestro proyecto local como una dependencia de desarrollo. Es decir, esta dependencia estará disponible cuando alguien esté desarrollando software, pero no cuando nuestro proyecto esté funcionando en producción.

Ahora instala la siguiente dependencia, ejecutando el siguiente comando:

```bash
$ npm install -D chai
```

Ahora puedes ver que *NPM* creó un folder `node-modules` en el directorio de tu proyecto.

Por último, en nuestro archivo `package.json`, vamos a modificar el *test script*. Esto nos va a permitir ejecutar nuestros tests usando el comando `npm test` en nuestra terminal.

En tu `package.json`, cambia el *script* de `test` a lo siguiente:

```json
{
  "name": "introduccion-a-tdd",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "mocha --recursive ./test"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "chai": "^4.1.2",
    "mocha": "^4.0.1"
  }
}
```

Para verificar que todo esté bien, ejecuta este comando en tu terminal:

```bash
$ npm test
> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  0 passing (3ms)
```

### IV. Escribiendo Nuestra Primera Prueba

Para escribir nuestra primera prueba, vamos a crear un archivo `HorseSpec.js` en nuestro directorio `test`. Estas pruebas nos van a guiar en el desarrollo de nuestra clase `Horse`. Por convención, los nombres de los archivos de prueba siguen el nombre del objeto que están probando. Esto nos facilita enfocarnos en la funcionalidad que estamos desarrollando.

En tu terminal, ejecuta el siguiente comando:

```bash
$ touch test/HorseSpec.js
```

Ahora, abre el archivo `HorseSpec.js` en tu editor de texto, y vamos a escribir nuestra primera prueba:

```js
// Aquí cargamos Chai en nuestro archivo de pruebas
const expect = require('chai').expect;
// Aquí cargamos el archivo que va a tener nuestra funcionalidad,
// usamos los dos puntos para subir al siguiente nivel de directorio,
// y luego bajar a *lib*
const Horse  = require('../lib/Horse.js');
// Aquí usamos *describe* para especificar al usuario la funcionalidad que
// vamos a probar, en este caso la clase *Horse*
describe('Horse', function(){
// Aquí van nuestras pruebas
})
```

Una vez hecho esto, vamos a correr nuevamente nuestras pruebas. En tu terminal, ejecuta este comando:

```bash
$ npm test
```

Seguramente verás un largo mensaje de error, que dice que ''
