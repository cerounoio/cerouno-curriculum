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

Seguramente verás un largo mensaje de error, que dice que `Error: Cannot find module '../lib/Horse.js'`. Lo que esto nos quiere decir, es que no encuentra ningún archivo en esa ubicación. Vamos a arreglar esto.

En nuestra terminal ejecuta el siguiente comando:

```bash
$ touch lib/Horse.js
```

Ahora, en tu terminal, ejecuta el siguiente comando:

```bash
npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  0 passing (2ms)
```

Para nuestra primera prueba, tenemos que ver si el objeto `Horse` existe. Para hacer esto vamos a escribir lo siguiente en `HorseSpec.js`:

```js
const expect = require('chai').expect;
const Horse  = require('../lib/Horse.js');

describe('Horse', function(){
  // Aquí definimos la nueva prueba usando la función *it* que acepta
  // dos argumentos. El primero es el nombre de la prueba, y el segundo es
  // una función con la prueba en sí.
  it('creates a Horse object', function(){
    // Aquí creamos una nueva instancia de la clase *Horse* y la guardamos en
    // la variable *horse*
    var horse = new Horse();
    // Aquí decimos que esperamos que *horse* sea un *objeto*. Si esto es
    // cierto, nuestra prueba pasa.
    expect(horse).to.be.a('object');
  })
})
```

Una vez escrito esto, en tu terminal, ejecuta el siguiente comando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    1) creates a Horse object


  0 passing (6ms)
  1 failing

  1) Horse
       creates a Horse object:
     TypeError: Horse is not a constructor
      at Context.<anonymous> (test/HorseSpec.js:6:17)



npm ERR! Test failed.  See above for more details.
```

Lo que esto dice es que `Horse` no es una clase. Para resolver esto, tenemos que definirla en nuestro archivo. En tu archivo `Horse.js` vamos a escribir el siguiente código:

```js
class Horse {

}

module.exports = Horse;
```

Ahora, ejecuta en tu terminal el siguiente comando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object


  1 passing (8ms)

```

Cómo puedes ver, nuestra prueba está pasando ahora.

### IV. Describiendo Nuestra Funcionalidad

Ya que hicimos nuestra primera prueba, queremos que nuestra clase `Horse` tenga un atributo `breed` que indique su raza. En nuestro `HorseSpec.js` vamos a escribir esa prueba.

```js
const expect = require('chai').expect;
const Horse  = require('../lib/Horse.js');

describe('Horse', function(){
  it('creates a Horse object', function(){
    var horse = new Horse();

    expect(horse).to.be.a('object');
  })

  // Aquí estamos definiendo otra prueba
  it('creates a Horse with breed attribute', function(){
    // Aquí creamos un objeto *Horse* con el atributo *pura sangre*
    var horse = new Horse('pura sangre');

    // Aquí esperamos que el objeto *horse* tenga un atributo *breed*
    expect(horse).to.have.property('breed');
    // Aquí esperamos que el atributo *breed* sea igual a *pura sangre*
    expect(horse.breed).to.equal('pura sangre');
  }
})
```

Ahora, ejecuta en tu terminal el siguiente comando:

```bash
npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    1) creates a Horse with breed attribute


  1 passing (9ms)
  1 failing

  1) Horse
       creates a Horse with breed attribute:
     AssertionError: expected {} to have property 'breed'
```

Como puedes ver, Mocha te dice que nuestro `Horse` no tiene un atributo `breed`. Vamos a implementar esto en nuestro archivo `Horse.js`:

```js
class Horse {
  // Aquí definimos un constructor con un parámetro *breed*
  constructor(breed) {
    // Aqui mapeamos el parámetro *breed* al atributo *breed*
    this.breed = breed;
  }
}

module.exports = Horse;
```

Ya que hiciste eso, vuelve a correr tus pruebas. En tu terminal, ejecuta este comando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute


  2 passing (7ms)
```

Como puedes ver, nuestra nueva prueba está pasando.

#### Ejercicio

Vamos a agregar un atributo nuevo `name` a nuestra clase *Horse*.

1. En tu archivo `HorseSpec.js` crea una prueba nueva que nos permite verificar que nuestro `Horse` tiene un atributo `name`. Tu prueba también debe decirnos si el valor que le asignamos a este atributo es el correcto.
2. Corre tus pruebas con `npm test` y verifica que tu prueba está fallando.
3. Implementa la funcionalidad en tu clase `Horse`.
4. Corre tus pruebas con `npm test` y verifica que tu prueba está pasando.

### VI. Probando Comportamiento

Ahora vamos a agregar un poco más de funcionalidad a nuestra clase `Horse`. Queremos que cuando nuestro objeto `Horse` brinque tres veces nos diga que está cansado. Implementemos esto por partes.

Si terminaste el ejercicio anterior correctamente, tu archivo de pruebas `HorseSpec.js` se ve como esto:

```js
const expect = require('chai').expect;
const Horse  = require('../lib/Horse.js');

describe('Horse', function(){
  it('creates a Horse object', function(){
    var horse = new Horse();

    expect(horse).to.be.a('object');
  })

  it('creates a Horse with breed attribute', function(){
    var horse = new Horse('pura sangre');

    expect(horse).to.have.property('breed');
    expect(horse.breed).to.equal('pura sangre');
  })

  it('creates a Horse with name attribute', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('name');
    expect(horse.name).to.equal('Spirit');
  })
})
```

Y tu archivo `Horse.js` se ve como esto:

```js
class Horse {
  constructor(breed, name) {
    this.breed = breed;
    this.name  = name;
  }
}

module.exports = Horse;
```

Ahora vamos a agregar un atributo `tired` a nuestra clase `Horse` que nos permite saber si está cansado. Cuando un objeto `Horse` se crea, el valor del atributo `tired` será `false`.

Vamos a escribir una prueba para implementar esta funcionalidad en nuestro código. En tu archivo `HorseSpec.js` escribe lo siguiente:

```js
const expect = require('chai').expect;
const Horse  = require('../lib/Horse.js');

describe('Horse', function(){
  it('creates a Horse object', function(){
    var horse = new Horse();

    expect(horse).to.be.a('object');
  })

  it('creates a Horse with breed attribute', function(){
    var horse = new Horse('pura sangre');

    expect(horse).to.have.property('breed');
    expect(horse.breed).to.equal('pura sangre');
  })

  it('creates a Horse with name attribute', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('name');
    expect(horse.name).to.equal('Spirit');
  })
  // Aquí agregamos la siguiente prueba para probar si el atributo *tired*
  // existe
  it('knows that is not tired', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    // Aqui esperamos que el atributo *tired* exista
    expect(horse).to.have.property('tired');
    // Aquí esperamos que el valor del atributo *tired* sea igual a *false*
    expect(horse.tired).to.equal(false);
  })
})
```

Ahora corre tus pruebas en la terminal con el siguiente comando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    1) knows that is not tired


  3 passing (10ms)
  1 failing

  1) Horse
       knows that is not tired:
     AssertionError: expected { Object (breed, name) } to have property 'tired'
      at Context.<anonymous> (test/HorseSpec.js:28:27)



npm ERR! Test failed.  See above for more details.
```

Lo que este mensaje te dice es que el atributo `tired` no existe en tu clase `Horse`. Vamos a agregarlo en nuestra clase.

En tu archivo `Horse.js`, escribe el siguiente codigo:

```js
class Horse {
  constructor(breed, name) {
    this.breed = breed;
    this.name  = name;
    // Aquí agregamos un atributo *tired* y le asignamos el valor de *false*
    this.tired = false;
  }
}

module.exports = Horse;
```

Ahora si corres tus pruebas de nuevo verás que todas están pasando.

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    ✓ knows that is not tired


  4 passing (8ms)
```

Ya que nuestro objeto sabe si está cansado es hora de agregar un atributo ´jumps´ que nos permita llevar la cuenta de cuantos brincos lleva. Vamos a escribir una prueba en tu archivo `HorseSpec.js`:

```js
const expect = require('chai').expect;
const Horse  = require('../lib/Horse.js');

describe('Horse', function(){
  it('creates a Horse object', function(){
    var horse = new Horse();

    expect(horse).to.be.a('object');
  })

  it('creates a Horse with breed attribute', function(){
    var horse = new Horse('pura sangre');

    expect(horse).to.have.property('breed');
    expect(horse.breed).to.equal('pura sangre');
  })

  it('creates a Horse with name attribute', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('name');
    expect(horse.name).to.equal('Spirit');
  })

  it('knows that is not tired', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('tired');
    expect(horse.tired).to.equal(false);
  })

  // Aquí agregamos la nueva prueba para validar nuestro atributo *jumps*
  it('knows how many jumps it has', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    // Aquí esperamos que nuestro objeto *horse* tenga el atributo *jumps*
    expect(horse).to.have.property('jumps');
    // Aquí esperamos que el valor de nuestro atributo sea igual a 0
    expect(horse.jumps).to.equal(0);
  })
})
```

Ahora corre tus pruebas en la terminal con el siguiente comando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    ✓ knows that is not tired
    1) knows how many jumps it has


  4 passing (11ms)
  1 failing

  1) Horse
       knows how many jumps it has:
     AssertionError: expected { Object (breed, name, ...) } to have property 'jumps'
      at Context.<anonymous> (test/HorseSpec.js:35:27)



npm ERR! Test failed.  See above for more details.
```

Como en el caso anterior, nuestra prueba nos dice que `Horse` no tiene un atributo `jumps`. Vamos a implementar esto.

En tu archivo `Horse.js` escribe este código:

```js
class Horse {
  constructor(breed, name) {
    this.breed = breed;
    this.name  = name;
    this.tired = false;
    // Aquí agregamos un atributo *jumps* al que le asignamos un valor inicial de 0.
    this.jumps = 0;
  }
}

module.exports = Horse;
```

Corre tus pruebas de nuevo en la terminal, y verás que ahora están pasando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    ✓ knows that is not tired
    ✓ knows how many jumps it has


  5 passing (8ms)
```

Ya que tenemos esta funcionalidad implementada, vamos a crear un método `jump()` que nos permita agregar un salto al atributo `jumps`. En tu archivo `HorseSpec.js` vamos a escribir una prueba que refleje esta funcionalidad:

```js
const expect = require('chai').expect;
const Horse  = require('../lib/Horse.js');

describe('Horse', function(){
  it('creates a Horse object', function(){
    var horse = new Horse();

    expect(horse).to.be.a('object');
  })

  it('creates a Horse with breed attribute', function(){
    var horse = new Horse('pura sangre');

    expect(horse).to.have.property('breed');
    expect(horse.breed).to.equal('pura sangre');
  })

  it('creates a Horse with name attribute', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('name');
    expect(horse.name).to.equal('Spirit');
  })

  it('knows that is not tired', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('tired');
    expect(horse.tired).to.equal(false);
  })

  it('knows how many jumps it has', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('jumps');
    expect(horse.jumps).to.equal(0);
  })

  // Aquí estamos agregando una prueba adicional
  it('can jump', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    // Aquí estamos checando que el valor inicial de *jumps* sea 0
    expect(horse.jumps).to.equal(0);
    // Aquí estamos haciendo brincar a nuestro objeto usando el método *jump*
    horse.jump();
    // Aquí esperamos que el valor de *jumps* se haya incrementado por 1
    expect(horse.jumps).to.equal(1);
  })
})
```

Ahora, corremos las pruebas en nuestra terminal con el siguiente comando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    ✓ knows that is not tired
    ✓ knows how many jumps it has
    1) can jump


  5 passing (11ms)
  1 failing

  1) Horse
       can jump:
     TypeError: horse.jump is not a function
      at Context.<anonymous> (test/HorseSpec.js:43:11)



npm ERR! Test failed.  See above for more details.
```

Lo que este mensaje nos dice es que nuestro objeto no tiene un método llamado `jump()`. Para arreglar esta prueba, tenemos que implementar la funcionalidad. En nuestro archivo `Horse.js` escribe lo siguiente:

```js
class Horse {
  constructor(breed, name) {
    this.breed = breed;
    this.name  = name;
    this.tired = false;
    this.jumps = 0;
  }

  // Aquí agregamos la función *jump*
  jump(){
    // Aquí decimos que incremente el valor del atributo *jumps* más uno,
    // esto es equivalente a decir this.jumps = this.jumps + 1;
    this.jumps++;
  }
}

module.exports = Horse;
```

Ya que implementamos esta función, corre tus pruebas de nuevo en tu terminal ejecutando el siguiente comando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    ✓ knows that is not tired
    ✓ knows how many jumps it has
    ✓ can jump


  6 passing (11ms)
```

Como puedes ver nuestra prueba está pasando.

Por último, vamos a integrar todas las piezas que acabamos de desarrollar en una prueba de integración (o *integration test*) para asegurarnos de que el comportamiento de nuestro objeto es el correcto.

En tu archivo `HorseSpec.js` escribe la siguiente prueba:

```js
const expect = require('chai').expect;
const Horse  = require('../lib/Horse.js');

describe('Horse', function(){
  it('creates a Horse object', function(){
    var horse = new Horse();

    expect(horse).to.be.a('object');
  })

  it('creates a Horse with breed attribute', function(){
    var horse = new Horse('pura sangre');

    expect(horse).to.have.property('breed');
    expect(horse.breed).to.equal('pura sangre');
  })

  it('creates a Horse with name attribute', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('name');
    expect(horse.name).to.equal('Spirit');
  })

  it('knows that is not tired', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('tired');
    expect(horse.tired).to.equal(false);
  })

  it('knows how many jumps it has', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse).to.have.property('jumps');
    expect(horse.jumps).to.equal(0);
  })

  it('can jump', function(){
    var horse = new Horse('pura sangre', 'Spirit');

    expect(horse.jumps).to.equal(0);
    horse.jump();
    expect(horse.jumps).to.equal(1);
  })

  // Aquí agregamos la nueva prueba
  it('is tired after it jumps three times', function(){
    var horse = new Horse();

    // Aquí nos aseguramos de que nuestros valores iniciales están listos
    expect(horse.jumps).to.equal(0);
    expect(horse.tired).to.equal(false);

    // Aquí hacemos que nuestro objeto brinque una primera vez
    horse.jump();
    expect(horse.jumps).to.equal(1);
    expect(horse.tired).to.equal(false);

    // Aquí hacemos que nuestro objeto brinque una segunda vez
    horse.jump();
    expect(horse.jumps).to.equal(2);
    expect(horse.tired).to.equal(false);

    // Aquí hacemos que nuestro objeto brinque una tercera vez
    horse.jump();
    expect(horse.jumps).to.equal(3);
    // Aquí esperamos que el atributo tired cambie a true
    expect(horse.tired).to.equal(true);
  })
})
```

Ahora, en tu terminal, corre tus pruebas:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    ✓ knows that is not tired
    ✓ knows how many jumps it has
    ✓ can jump
    1) is tired after it jumps three times


  6 passing (12ms)
  1 failing

  1) Horse
       is tired after it jumps three times:

      AssertionError: expected false to equal true
      + expected - actual

      -false
      +true

      at Context.<anonymous> (test/HorseSpec.js:63:28)



npm ERR! Test failed.  See above for more details.

```

Lo que la prueba nos dice es que está fallando porque el valor del atributo `tired` es `false` en vez de `true`. Tenemos que implementar una funcionalidad en nuestra clase `Horse` que le diga a nuestro caballo que cambie el atributo `tired` de `false` a `true` después de haber brincado tres veces.

En tu archivo `Horse.js` escribe lo siguiente:

```js
class Horse {
  constructor(breed, name) {
    this.breed = breed;
    this.name  = name;
    this.tired = false;
    this.jumps = 0;
  }

  jump(){
    this.jumps++;
    // Aquí modificamos el método *jump* para que si el atributo *jumps* es
    // mayor o igual a 3, cambie el atributo *tired* a *true*.
    if(this.jumps >= 3){
      this.tired = true;
    }
  }
}

module.exports = Horse;
```

Ahora corre tus pruebas en la terminal de nuevo y verás que están pasando:

```bash
$ npm test

> introduccion-a-tdd@1.0.0 test /<tu directorio>/introduccion-a-tdd
> mocha --recursive ./test



  Horse
    ✓ creates a Horse object
    ✓ creates a Horse with breed attribute
    ✓ creates a Horse with name attribute
    ✓ knows that is not tired
    ✓ knows how many jumps it has
    ✓ can jump
    ✓ is tired after it jumps three times


  7 passing (12ms)
```

#### Ejercicio

Vamos a agregar un método `eat()` a nuestra clase `Horse`. Cuando el objeto `Horse` llame al método `eat()` cinco veces, nuestro caballo ya no tendrá hambre.

1. En `HorseSpec.js`, escribe una prueba para agregar un atributo `hungry` a la clase `Horse`. El valor inicial de este atributo es `true`. Corre tu prueba y verifica que está fallando.
2. Implementa la funcionalidad anterior en `Horse.js`, corre tus pruebas en la terminal, y verifica que tu prueba esté pasando.
3. En `HorseSpec.js`, escribe una prueba para agregar un atributo `meals` a la clase `Horse` que llevara la cuenta de las comidas que lleva el objeto. El valor inicial de este atributo es `0`. Corre tu prueba y verifica que está fallando.
4. Implementa la funcionalidad anterior en `Horse.js`, corre tus pruebas en la terminal, y verifica que tu prueba esté pasando.
5. En `HorseSpec.js`, escribe una prueba para agregar un método `eat()` que sumará uno al atributo `meals`. Corre tu prueba y verifica que está fallando.
6. Implementa la funcionalidad anterior en `Horse.js`, corre tus pruebas en la terminal, y verifica que tu prueba esté pasando.
7. Por último, en `HorseSpec.js`, escribe una prueba de integración que pruebe si el atributo `hungry` es `false` después de que el método `eat()` sea llamado cinco veces.
8. Implementa la funcionalidad anterior en `Horse.js`, corre tus pruebas en la terminal, y verifica que tu prueba esté pasando.

Ahora que ya sabes programar con la técnica de *TDD*, puedes practicar más completando estos ejercicios de [Criaturas Míticas](https://github.com/cerouno-examples/criaturas-miticas).
