---
title: JavaScript Orientado a Objetos
program: DAW
module: M1
layout: main
---

# *JavaScript* Orientado a Objetos

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Entender el concepto de objetos en programación
* Entender clases y herencia
* Usar el principio de `Single-Responsibility` para diseñar sus objetos
* Organizar clases en diferentes archivos
* Llamar métodos en la clase *madre* usando super
* Usar objetos que se comuniquen entre sí

### II. Antecedentes

Los **objetos** son estructuras de datos que tienen **comportamiento**, también llamados *métodos*, y **estado**, también llamados *atributos*. Por ejemplo, si tienes un objeto *caballo*, éste tiene comportamientos como correr, brincar, comer, y estados como el número de patas, el color de pelo, si está dormido o despierto.

El mundo que conocemos está organizado en objetos. Cada persona, mascota, y vehículo podría ser un objeto en sí mismo, y cada uno de éstos interactúan todo el tiempo entre sí. Por ejemplo, si un dueño le dice a su perro que se siente, el perro escucha el comando, y reacciona ante esa instrucción. En programación, a estas interacciones entre objetos les llamamos **mensajes**.

> A pesar de que lenguajes como Java, C#, Python o Ruby popularizaron el concepto, la programación orientada a objetos se desarrolló en los 50s y 60s en el MIT. Para aprender más de este paradigma, haz click [aquí](https://en.wikipedia.org/wiki/Object-oriented_programming#History).

Los lenguajes orientados a objetos modernos tienen objetos que están organizados en **clases**. Una clase es como una fábrica que produce objetos. A cada uno de los objetos fabricados por una clase, les llamamos **instancia**. Por ejemplo, si tuviéramos una fábrica de galletas, la fábrica en sí sería una clase, mientras que cada galleta sería una instancia.

*JavaScript* es un lenguaje híbrido que sigue varios paradigmas. Por un lado puede usarse para crear aplicaciones orientadas a objetos, pero también tiene paradigmas funcionales. Es esta flexibilidad lo que lo convierte en un lenguaje versátil, pero también confuso.

### III. Nuestro Primer Objeto

Antes de crear nuestro primer objeto, vamos a crear un directorio para guardar nuestro código.

En la terminal, ejecuta el siguiente comando:

```bash
$ mkdir javascript-orientado-a-objetos
```

Una vez creado el directorio, vamos a crear un archivo que va a contener primer objeto `Animal.js`.

```bash
$ touch Animal.js
```

Ya que creaste tu archivo `Animal.js`, vamos a declarar nuestra clase `Animal`. En tu archivo, `Animal.js` escribe el siguiente código:

```js
class Animal {
  // El contenido de la clase va aquí.
}
```

Ya que tenemos nuestra clase, ahora vamos a utilizar un `constructor` para definir con que datos vamos a inicializar (es decir, *crear*) cada instancia. Lo que queremos hacer es que cuando creemos nuestro animal, podamos decir que de qué color es y cuántas patas tiene.

En tu archivo, `Animal.js` escribe el siguiente código:

```js
class Animal {
  // Este es el constructor que nos permite recibir crear una instancia con los atributos *color* y *legs*.
  constructor(color, legs) {
    // Aquí estamos mapeando los parámetros del constructor a los atributos del objeto.
    this.color = color;
    this.legs  = legs;
  }
}
```

Una vez que tenemos nuestra clase `Animal` lista, podemos crear una nueva instancia. En tu archivo, `Animal.js` escribe el siguiente código:

```js
class Animal {
  constructor(color, legs) {
    this.color = color;
    this.legs  = legs;
  }
}

// Aquí estamos declarando la variable *miAnimal* que va a guardar una instancia de la clase *Animal*. Esta instancia está recibiendo dos argumentos, *azul* y *4*, que va a guardar en sus atributos, *color* y *legs*, respectivamente.
var miAnimal = new Animal('azul', 4);

// Aquí estamos imprimiento los atributos de la instancia *miAnimal* junto con un mensaje.
console.log(`El color de mi animal es ${miAnimal.color}.`);
console.log(`Mi animal tiene ${miAnimal.legs} patas.`);
```

Ahora en tu terminal, corre tu programa:

```bash
$ node Animal.js
El color de mi animal es azul.
Mi animal tiene 4 patas.
```

Ya que pudimos crear una instancia y agregar atributos, ahora vamos a agregar un método `eat()` que tiene un parámetro `foof` e imprime el mensaje `"Estoy comiendo <comida>."`.

En tu archivo, `Animal.js` escribe el siguiente código:

```js
class Animal {
  constructor(color, legs) {
    this.color = color;
    this.legs  = legs;
  }
  // Aquí agregamos un método *eat()*, que acepta el parámetro *food*, y retorna un *string*.
  eat(food) {
    return `Estoy comiendo ${food}.`;
  }
}

var miAnimal = new Animal('azul', 4);

console.log(`El color de mi animal es ${miAnimal.color}.`);
console.log(`Mi animal tiene ${miAnimal.legs} patas.`);
// Aquí llamamos el método *eat()*, pasamos el argumento *pasto* e imprimimos el valor de retorno.
console.log(miAnimal.eat('pasto'));
```

Ahora, en tu terminal, corre tu programa:

```bash
$ node Animal.js
El color de mi animal es azul.
Mi animal tiene 4 patas.
Estoy comiendo pasto.
```

#### Ejercicio

Nuestra clase `Animal` actual funciona, pero puedes extender su comportamiento? En tu clase `Animal` haz lo siguiente:

1. Agrega un atributo adicional llamado `size` al constructor de la clase `Animal`. Este deberá aceptar un *string* que diga el tamaño.
2. Agrega un método llamado `jump()`, que acepte un parámetro llamado `place`, y que retorne un *string* que diga `Estoy brincando en <place>.`
3. Imprime un mensaje usando `console.log()` que diga `"Mi tamaño es <size>."`.
4. Imprime un mensaje usando `console.log()` que imprima el valor de retorno del método `jump()` con el argumento `pasto`.

### IV. Herencia

Una de las características de los lenguajes orientados a objetos es la capacidad de **heredar** la funcionalidad de una clase a otra. Por ejemplo, si tienes una clase `Animal`, puedes tener otras subclasses como `Dog`, `Cat` y `Pig` que pueden heredar la funcionalidad de la clase `Animal`.

Para practicar este concepto, vamos a crear una subclase `Dog` que herede su funcionalidad de la clase `Animal`. Para hacer esto, declaramos la subclase `Dog`, y usamos el *keyword* `extends` para especificar de dónde hereda la funcionalidad.

En tu archivo, `Animal.js` vamos a escribir este código:

```js
class Animal {
  constructor(color, legs, size) {
    this.color = color;
    this.legs  = legs;
    this.size  = size;
  }

  eat(food) {
    return `Estoy comiendo ${food}.`;
  }

  jump(place) {
    return `Estoy brincando en ${place}.`;
  }
}
// Aquí declaramos la subclase *Dog* y especificamos que ésta hereda su funcionalidad de *Animal* usando el keyword *extends*.
class Dog extends Animal {
}
// Aquí creamos una nueva instancia de la subclase *Dog* y guardamos su valor en la variable *myDog*.
var myDog = new Dog('café', 4);
// A pesar de que la subclase *Dog* está vacía, ésta hereda la funcionalidad de la clase *Animal*.
console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
```

Ahora, en tu terminal, corre tu programa:

```bash
$ node Animal.js
El color de mi animal es café.
Mi animal tiene 4 patas.
Estoy comiendo croquetas.
Estoy brincando en pasto.
```

Como pudiste ver en el ejemplo anterior, la subclase `Dog` hereda su funcionalidad completa de la clase `Animal`. Sin embargo, esto no quiere decir que no puedas agregar funcionalidad a la subclase. Para demostrar esto, vamos a crear un método `fetch()` en la subclase `Dog` con un parámetro `item` que acepte un argumento *string*.

```js
class Animal {
  constructor(color, legs, size) {
    this.color = color;
    this.legs  = legs;
    this.size  = size;
  }

  eat(food) {
    return `Estoy comiendo ${food}.`;
  }

  jump(place) {
    return `Estoy brincando en ${place}.`;
  }
}

class Dog extends Animal {
  // Aquí declaramos un nuevo método *fetch* con un parámetro item.
  fetch(item) {
    return `Estoy trayendo un ${item}.`;
  }
}

var myDog = new Dog('café', 4);

console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
// Aquí imprimimos el valor de retorno del método *fetch()*
console.log(myDog.fetch('hueso'));
```

Ahora corre tu programa en tu terminal:

```bash
$ node Animal.js
El color de mi animal es café.
Mi animal tiene 4 patas.
Estoy comiendo croquetas.
Estoy brincando en pasto.
Estoy trayendo un hueso.
```

Como puedes observar, a pesar de que el método *fetch()* no está definido en la clase `Animal`, podemos acceder a él dado que está definido en la subclase `Dog`.

Además, también podemos sustituir la funcionalidad de un método heredado de una clase. Para ejemplificar esto, vamos a definir otra implementación del método `jump()` en la subclase `Dog`. Esto va a sustituir la implementación de este método que heredamos de la clase `Animal`.

En tu archivo `Animal.js`, escribe el siguiente código:

```js
class Animal {
  constructor(color, legs, size) {
    this.color = color;
    this.legs  = legs;
    this.size  = size;
  }

  eat(food) {
    return `Estoy comiendo ${food}.`;
  }

  jump(place) {
    return `Estoy brincando en ${place}.`;
  }
}

class Dog extends Animal {
  fetch(item) {
    return `Estoy trayendo un ${item}.`;
  }
  // Aquí volvemos a denifir el método *jump*. Esto sustituye al método *jump* de la clase `Animal`
  jump() {
    return 'No quiero brincar.';
  }
}

var myDog = new Dog('café', 4);

console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
console.log(myDog.fetch('hueso'));
```

Ahora corre tu programa en la terminal:

```bash
$ node Animal.js
El color de mi animal es café.
Mi animal tiene 4 patas.
Estoy comiendo croquetas.
No quiero brincar.
Estoy trayendo un hueso.
```

Como puedes ver, el mensaje anterior de `"Estoy brincando en el pasto."` heredado del método `jump()` de la clase `Animal` fue sustituído por el mensaje `"No quiero brincar."` definido en el método `jump()` de la subclase `Dog`.

#### Ejercicio

Tenemos una subclase `Dog` que hereda la funcionalidad de la clase `Animal`. Sin embargo, la ventaja de usar el sistema de herencia es que podemos crear muchas subclases que hereden la misma funcionalidad.

En tu archivo `Animal.js`, implementa lo siguiente:

1. Crea una subclase `Cat` que herede su funcionalidad de `Animal`.
2. Crea una instancia de la clase `Cat` con argumentos de `color`, `legs` y `size`.
3. Guarda la instancia en una variable llamada `myCat`.
4. Implementa un método en la clase `Cat` que se llame `scratch()`, que regrese un string que diga `Te estoy rasguñando.`.
5. Reimplementa el método `eat()` en la clase `Cat` y haz que retorne un string que diga `Quiero atún`.
6. Imprime el valor de retorno del método `scratch()` de la instancia `myCat`.
7. Imprime el valor de retorno del método `eat()` de la instancia `myCat`.

### V. Organizando Nuestros Archivos

Si lograste terminar el ejercicio anterior, tu código seguramente se ve como esto:

```js
class Animal {
  constructor(color, legs, size) {
    this.color = color;
    this.legs  = legs;
    this.size  = size;
  }

  eat(food) {
    return `Estoy comiendo ${food}.`;
  }

  jump(place) {
    return `Estoy brincando en ${place}.`;
  }
}

class Dog extends Animal {
  fetch(item) {
    return `Estoy trayendo un ${item}.`;
  }

  jump() {
    return 'No quiero brincar.';
  }
}

class Cat extends Animal {
  scratch() {
    return 'Te estoy rasguñando.';
  }

  eat() {
    return 'Quiero atún.';
  }
}

var myDog = new Dog('café', 4);
console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
console.log(myDog.fetch('hueso'));

var myCat = new Cat('negro', 4, 'grande');
console.log(myCat.scratch());
console.log(myCat.eat());
```

Como puedes ver, nuestro archivo `Animal.js` se está volviendo demasiado grande. Es una buena práctica separar nuestras clases en diferentes archivos y nuestro implementación del programa en otro.

En tu terminal, crea tres archivos: `index.js`, `Dog.js` y `Cat.js` ejecutando el siguiente comando:

```bash
$ touch index.js Dog.js Cat.js
```

Una vez hecho esto, pon el código de tu clase `Dog` en el archivo `Dog.js`, el código de tu clase `Cat` en el archivo `Cat.js`, y la implementación de tu programa, en el archivo `index.js`.

Tus archivos deberán quedar organizados así:

`Animal.js`

```js
class Animal {
  constructor(color, legs, size) {
    this.color = color;
    this.legs  = legs;
    this.size  = size;
  }

  eat(food) {
    return `Estoy comiendo ${food}.`;
  }

  jump(place) {
    return `Estoy brincando en ${place}.`;
  }
}
```

`Dog.js`

```js
class Dog extends Animal {
  fetch(item) {
    return `Estoy trayendo un ${item}.`;
  }

  jump() {
    return 'No quiero brincar.';
  }
}
```

`Cat.js`

```js
class Cat extends Animal {
  scratch() {
    return 'Te estoy rasguñando.';
  }

  eat() {
    return 'Quiero atún.';
  }
}
```

`index.js`

```js
var myDog = new Dog('café', 4);
console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
console.log(myDog.fetch('hueso'));

var myCat = new Cat('negro', 4, 'grande');
console.log(myCat.scratch());
console.log(myCat.eat());
```

Una vez hecho esto, ejecuta tu programa corriendo el archivo `index.js` con este comando en tu terminal:

```bash
$ node index.js
/Users/Jorge/Dropbox/projects/examples/javascript-orientad-a-objetos/index.js:1
(function (exports, require, module, __filename, __dirname) { var myDog = new Dog('café', 4);
                                                                          ^

ReferenceError: Dog is not defined
    at Object.<anonymous> (/Users/Jorge/Dropbox/projects/examples/javascript-orientad-a-objetos/index.js:1:75)
    at Module._compile (module.js:612:30)
    at Object.Module._extensions..js (module.js:623:10)
    at Module.load (module.js:531:32)
    at tryModuleLoad (module.js:494:12)
    at Function.Module._load (module.js:486:3)
    at Function.Module.runMain (module.js:653:10)
    at startup (bootstrap_node.js:187:16)
    at bootstrap_node.js:608:3
```

Lo que sucede aquí es que nuestro programa no puede cargar las clases que se encuentran en otros archivos. Para arreglar esto tenemos que exportar las clases para que puedan ser leídas por otros archivos, e importar las clases en nuestro archivo `index.js`, para poder acceder a su funcionalidad.

Node nos permite exportar modulos que otros archivos o programas pueden utilizar. Para hacer esto usamos `module.exports` y especificamos la funcionalidad a exportar.

Al final tu archivo `Animal.js` escribe el siguiente código:

```js
class Animal {
  constructor(color, legs, size) {
    this.color = color;
    this.legs  = legs;
    this.size  = size;
  }

  eat(food) {
    return `Estoy comiendo ${food}.`;
  }

  jump(place) {
    return `Estoy brincando en ${place}.`;
  }
}
// Aquí le decimos a Node que estamos exportando la clase *Animal*
// para que otras partes de nuestro programa puedan usarla.
module.exports = Animal;
```

Repite el mismo proceso en los archivos `Dog.js` y `Cat.js`.

`Dog.js`

```js
class Dog extends Animal {
  fetch(item) {
    return `Estoy trayendo un ${item}.`;
  }

  jump() {
    return 'No quiero brincar.';
  }
}

// Aquí le decimos a Node que estamos exportando la clase *Dog*
// para que otras partes de nuestro programa puedan usarla.
module.exports = Dog;
```

`Cat.js`

```js
class Cat extends Animal {
  scratch() {
    return 'Te estoy rasguñando.';
  }

  eat() {
    return 'Quiero atún.';
  }
}

// Aquí le decimos a Node que estamos exportando la clase *Cat*
// para que otras partes de nuestro programa puedan usarla.
module.exports = Cat;
```

Ahora, corre tu programa en tu terminal con este comando:

```bash
$ node index.js
/Users/Jorge/Dropbox/projects/examples/javascript-orientad-a-objetos/index.js:4
var myDog = new Dog('café', 4);
            ^

ReferenceError: Dog is not defined
    at Object.<anonymous> (/Users/Jorge/Dropbox/projects/examples/javascript-orientad-a-objetos/index.js:4:13)
    at Module._compile (module.js:612:30)
    at Object.Module._extensions..js (module.js:623:10)
    at Module.load (module.js:531:32)
    at tryModuleLoad (module.js:494:12)
    at Function.Module._load (module.js:486:3)
    at Function.Module.runMain (module.js:653:10)
    at startup (bootstrap_node.js:187:16)
    at bootstrap_node.js:608:3
```

Lo que este mensaje nos dice es que la clase `Dog` no está definida. Esto se debe a que tenemos que importar esa clase en nuestro archivo `index.js`.

En tu archivo `index.js`, vamos a importar la clase `Dog` y la clase `Cat`:

```js
// Aquí importamos las clases *Dog* y *Cat, y las asignamos a las constantes *Dog* y *Cat*.
const Dog = require('./Dog.js');
const Cat = require('./Cat.js');

var myDog = new Dog('café', 4);
console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
console.log(myDog.fetch('hueso'));

var myCat = new Cat('negro', 4, 'grande');
console.log(myCat.scratch());
console.log(myCat.eat());
```

Ahora, corre tu programa en tu terminal:

```bash
$ node index.js
/Users/Jorge/Dropbox/projects/examples/javascript-orientad-a-objetos/Dog.js:3
class Dog extends Animal {
                  ^

ReferenceError: Animal is not defined
    at Object.<anonymous> (/Users/Jorge/Dropbox/projects/examples/javascript-orientad-a-objetos/Dog.js:3:19)
    at Module._compile (module.js:612:30)
    at Object.Module._extensions..js (module.js:623:10)
    at Module.load (module.js:531:32)
    at tryModuleLoad (module.js:494:12)
    at Function.Module._load (module.js:486:3)
    at Module.require (module.js:556:17)
    at require (internal/module.js:11:18)
    at Object.<anonymous> (/Users/Jorge/Dropbox/projects/examples/javascript-orientad-a-objetos/index.js:1:75)
    at Module._compile (module.js:612:30)
```

Esto nos dice que la clase `Animal` no está definida en la clase `Dog` cuando queremos heredar la funcionalidad de la clase `Animal`,

Vamos arreglar esto importando la clase `Animal` en las clases `Dog` y `Cat`.

`Dog.js`

```js
// Aquí importamos la clase *Animal*
const Animal = require('./Animal.js');

class Dog extends Animal {
  fetch(item) {
    return `Estoy trayendo un ${item}.`;
  }

  jump() {
    return 'No quiero brincar.';
  }
}

module.exports = Dog;
```

`Cat.js`

```js
// Aquí importamos la clase *Animal*
const Animal = require('./Animal.js');

class Cat extends Animal {
  scratch() {
    return 'Te estoy rasguñando.';
  }

  eat() {
    return 'Quiero atún.';
  }
}

module.exports = Cat;
```

Ahora, corre tu programa en tu terminal:

```bash
$ node index.js
El color de mi animal es café.
Mi animal tiene 4 patas.
Estoy comiendo croquetas.
No quiero brincar.
Estoy trayendo un hueso.
Te estoy rasguñando.
Quiero atún.
```

Ahora, todo funciona.

#### Ejercicio

Ya que hemos reorganizado nuestro programa, vamos a crear una clase llamada `Bird`. Para hacer esto, haz lo siguiente:

1. Crea un archivo `Bird.js`.
2. Define una clase `Bird` que herede su funcionalidad de la clase `Animal`.
3. Declara un método `fly()` en la clase `Bird` que retorne un *string* con el valor `Estoy volando.`
4. Crea una instancia de la clase Bird en tu programa en `index.js`, guárdala en una variable `myBird` e imprime el valor de retorno del método `fly()`.

### VI. Agregando Comportamiento

Hasta ahora hemos creado métodos en nuestros objetos que retornan *strings*. Vamos a hacer algo más complicado para que puedas entender como utilizamos los métodos.

Los métodos son funciones definidas dentro de objetos y especifican acciones que los objetos realizan. Por ejemplo, el objeto `Fish` puede tener un método `swim()` que contiene las instrucciones para que el objeto pueda nadar.

Para ejemplificar esto, vamos a crear un objeto `Pig`. Este objeto va a heredar los atributos iniciales de la clase `Animal` y un atributo adicional llamado `hungry`. Al crear un objeto `Pig`, este va a tener hambre, por lo que el valor de su atributo inicial `hungry` va a ser `true`. Cuando le digamos a `Pig` que coma, este valor va a ser `false`.

En tu terminal crea un archivo `Pig.js` ejecutando el siguiente comando:

```bash
$ touch Pig.js
```

Ahora abre el archivo `Pig.js` en tu editor, y escribe el siguiente código:

```js
const Animal = require('./Animal.js')

class Pig extends Animal {
  // Aquí redefinimos el constructor para poder agregar el atributo *hungry*
  constructor(color, legs, size) {
    this.color  = color;
    this.legs   = legs;
    this.size   = size;
    // Aquí creamos el nuevo atributo *hungry* con un valor inicial de *true*
    this.hungry = true;
  }

  // Aquí redefinimos el método *eat()* para poder agregar la instrucción que
  // cambia de valor el atributo hungry
  eat(food) {
    // Aquí cambiamos el valor del atributo *hungry* a *false*
    this.hungry = false;
    return `Estoy comiendo ${food}.`;
  }
}

module.exports = Pig;
```

Una vez implementado esto, en nuestro index.js, vamos a agregar el siguiente código:

```js
const Dog = require('./Dog.js');
const Cat = require('./Cat.js');
// Aquí agregamos la nueva clase *Pig* para poderla usar en nuestro programa
const Pig = require('./Pig.js');

var myDog = new Dog('café', 4);
console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
console.log(myDog.fetch('hueso'));

var myCat = new Cat('negro', 4, 'grande');
console.log(myCat.scratch());
console.log(myCat.eat());

// Aquí creamos un nuevo objeto *Pig*
var myPig = new Pig('rosa', 4, 'mediano');
// Aquí imprimimos el valor de *hungry* para ver su estado inicial
console.log(myPig.hungry);
// Aquí llamamos el método *eat()* y pasamos un argumento *maíz*
console.log(myPig.eat('maíz'));
// Aquí imprimimos el valor de *hungry* para ver el nuevo estado después de
// llamar a nuestro método *eat()*
console.log(myPig.hungry);
```

Ahora ejecuta el programa desde tu terminal:

```bash
$ node index.js
El color de mi animal es café.
Mi animal tiene 4 patas.
Estoy comiendo croquetas.
No quiero brincar.
Estoy trayendo un hueso.
Te estoy rasguñando.
Quiero atún.
true
Estoy comiendo maíz.
false
```

Por último podemos mejorar un poco nuestro código. Si te das cuenta, cuando redefinimos nuestro constructor en la clase `Pig`, realmente estamos reescribiendo el código del constructor de la clase `Animal`. Para evitar esto, podemos utilizar la función `super()`. Esta nos permite acceder a la funcionalidad de la clase madre, en este caso `Animal`, para evitar tener que reescribir el código.

En tu clase `Pig`, escribe lo siguiente:

```js
const Animal = require('./Animal.js')

class Pig extends Animal {
  constructor(color, legs, size) {
    // Aquí llamamos al constructor de la clase madre `Animal`
    super(color, legs, size);
    this.hungry = true;
  }

  eat(food) {
    this.hungry = false;
    // Aquí llamamos al método `eat()` de la clase madre `Animal`
    return super.eat(food);
  }
}

module.exports = Pig;
```

### VII. Interactuando Entre Objetos

Ahora, vamos a ver como dos objetos interactúan entre sí. En la programación orientada a objetos, dado que nuestro objetos encapsulan diferentes partes de nuestros programas, es normal que estos interactúen entre ellos.

Para ejemplificar lo anterior, vamos a agregar un objeto `Person` a nuestro programa. Este objeto tiene la responsabilidad de alimentar al objeto `Pig`. Primero, vamos a crear un archivo `Person.js` donde vamos a declarar nuestra clase `Person`. En tu terminal, ejecuta el siguiente comando:

```bash
$ touch Person.js
```

Ahora, vamos a declarar nuestra clase, declarar un método `feed()` que acepte un objeto `animal` y un *string* `food`.

El archivo `Person.js`, escribe el siguiente código:

```js

class Person {
  // Aquí definimos un método *feed()* que acepta un objeto *animal* y
  // un string *food*
  feed(animal, food) {
    // Aquí llamamos el método *eat()* en el objeto *animal* y le pasamos
    // el argumento *food*
    return animal.eat(food);
  }
}
// Aquí exportamos la clase *Person* para que otros archivos puedan usarla
module.exports = Person;
```

Una vez hecho esto, ahora vamos a modificar nuestro programa para que `Person` alimente a `Pig`.

En tu archivo `index.js` escribe el siguiente código:

```js
const Dog    = require('./Dog.js');
const Cat    = require('./Cat.js');
const Pig    = require('./Pig.js');
// Aquí estamos importando la clase *Person*
const Person = require('./Person.js');

var myDog = new Dog('café', 4);
console.log(`El color de mi animal es ${myDog.color}.`);
console.log(`Mi animal tiene ${myDog.legs} patas.`);
console.log(myDog.eat('croquetas'));
console.log(myDog.jump('pasto'));
console.log(myDog.fetch('hueso'));

var myCat = new Cat('negro', 4, 'grande');
console.log(myCat.scratch());
console.log(myCat.eat());

var myPig = new Pig('rosa', 4, 'mediano');
console.log(myPig.hungry);
console.log(myPig.eat('maíz'));
console.log(myPig.hungry);

// Aquí creamos un objeto *Person*
var myPerson = new Person();
// Aquí creamos otro objeto *Pig*
var myOtherPig = new Pig('café', 4, 'grande');
// Aquí imprimimos el valor inicial del atributo hungry de *Pig*
console.log(myOtherPig.hungry);
// Aquí llamamos el método *feed()* de la clase *Person* y le pasamos
// como argumentos el objeto *myOtherPig* y el string *alimento*
console.log(myPerson.feed(myOtherPig, 'alimento'));
// Aquí imprimos el valor del atributo *hungry* de *myOtherPig*
// y vemos que cambió
console.log(myOtherPig.hungry);
```

Ahora ejecuta tu programa en la terminal:

```bash
$ node index.js
El color de mi animal es café.
Mi animal tiene 4 patas.
Estoy comiendo croquetas.
No quiero brincar.
Estoy trayendo un hueso.
Te estoy rasguñando.
Quiero atún.
true
Estoy comiendo maíz.
false
true
Estoy comiendo alimento.
false
```

#### Ejercicio

Ya que sabes como crear clases e interactuar con ellas, vamos a hacer lo siguiente:

1. Agrega un atributo `thirsty` a la clase `Pig`. Cuando una instancia nueva de `Pig` se cree, el valor del atributo `thirsty` será `true`.
3. En la clase `Pig`, agrega un método `drink()` que cambie el atributo `thirsty` a `false` y que retorne un string que diga "Estoy tomando agua.".
4. En la clase `Person`, agrega un método `water()` que acepte un parámetro `animal` y que retorne el valor de `animal.drink()`.
5. En `index.js`, crea dos nuevas instancias de las clases `Person` y `Pig`.
6. Imprime el estado inicial del atributo `thirsty` de la nueva instancia de `Pig`.
7. Llama el método `water()` en la nueva instancia de `Person` y pasa la nueva instancia de `Pig` como argumento. Imprime el valor de retorno.
8. Imprime el estado del atributo `thirsdy` de la nueva instancia de `Pig` de nuevo. Este debió de haber cambiado de `true` a `false`.

Ahora ya sabes como programar usando objetos. Practica creando clases adicionales que se comuniquen entre sí. No olvides de compartir tu programa en Github.
