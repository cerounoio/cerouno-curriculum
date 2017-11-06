---
title: Aplicaciones CLI
program: DAW
module: M1
layout: main
---

# Aplicaciones CLI

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Empezar un programa usando *npm*
* Crear aplicaciones con un *CLI*
* Utilizar la librería de *Readline* de *Node.js*
* Utilizar funciones para organizar el código
* Utilizar *Promises* y `async/await`

### II. ¿Qué es un *CLI*?

Si estás acostumbrado a utilizar una computadora, por lo general, utilizas tu *mouse* y tu teclado para interactuar con elementos gráficos en tu pantalla. Por ejemplo, si quieres abrir un programa o un archivo, haces click en un ícono y eso te permite acceder a la funcionalidad del programa. A este tipo de interfaces se les llama **interfaz gráfica** (*Graphic User Interface* en inglés).

Un *CLI* (*Command Line Interface*) es una interfaz que no tiene gráficos, por lo tanto, sólo puedes interactuar con tu programa mediante texto. En este tipo de interfaces, al iniciar el programa, este normalmente te muestra un mensaje de bienvenida, y te pide una instrucción de texto mediante un *prompt*. Una vez escrito el comando, uno presiona `Enter`, y el comando es analizado por la aplicación.

Tal vez las aplicaciones *CLI* te parezcan extrañas, pero antes todas las aplicaciones funcionaban así. Hojas de cálculo, procesadores de texto, e incluso juegos, utilizaban *CLIs* para interactuar con sus usuarios. De hecho, tu terminal sigue utilizando este tipo de interfaz.

### III. Preparando Nuestra Aplicación

La primera aplicación *CLI* que vamos a hacer es un programa que nos permite calcular el área de un rectángulo. Para eso vamos a utilizar un módulo de Node.js llamado **Readline**. Puedes aprender más de este módulo [aquí](https://nodejs.org/api/readline.html).

Para empezar nuestro proyecto, vamos a crear un directorio llamado `area-calculator` en el directorio donde guardes tus proyectos.

En tu terminal, ejecuta este comando:

```bash
$ mkdir area-calculator
```

Ahora cambia tu ubicación al directorio `area-calculator` que acabas de crear. En tu terminal, ejecuta este comando:

```bash
$ cd area-calculator
```

Una vez hecho esto, tenemos que crear un `package.json` dentro de nuestro directorio usando `npm`. Este archivo contiene información sobre nuestro proyecto, incluyendo el nombre, número de versión y dependencias (otro código del que depende nuestro programa para poder ejecutarse). Puedes aprender más sobre este archivo [aquí](https://docs.nodejitsu.com/articles/getting-started/npm/what-is-the-file-package-json/).

En tu terminal, ejecuta este comando:

```bash
$ npm init -f
```

Esto creará el archivo `package.json` con alguna información como el nombre del programa y el número de versión.

Ahora, vamos a crear un archivo `index.js`. Este archivo va a correr nuestro programa y cargar los archivos con nuestro código.

En tu terminal, ejecuta este comando:

```bash
$ touch index.js
```

Una vez hecho esto, vamos a abrir los archivos de nuestro proyecto en nuestro editor de texto para poder empezar a escribir nuesto programa. En tu terminal, ejecuta este comando:

```bash
$ atom .
```

Ya que tienes los archivos de tu proyecto abierto en tu editor, vamos a escribir nuestra primera línea de código. Selecciona el archivo `index.js` en tu editor de texto y escribe el siguiente código:

```js
console.log('¡Hola, Mundo!');
```

Ahora, en tu terminal, ejecuta el siguiente comando:

```bash
$ node index.js
¡Hola, Mundo!
```

### III. Instalando *Readline*

**Readline** es un módulo de Node que nos permite leer datos desde la terminal. Para incorporar este módulo a nuestro programa, tenemos que declarar una variable y asignarle como valor el modulo de *Readline*. Esto nos permite llamar este módulo y las funciones que éste contiene dentro de nuestro programa.

Para hacer esto, en nuestro archivo `index.js`, borra el código anterior y escribe el siguiente código:


```js
var readline = require('readline');
```

Ahora, para crear la `interfaz` de nuestro programa llamamos a la función `createInterface()` que está disponible en el módulo `readline`. Esta función del módulo `readline`, nos permite controlar el comportamiento de nuestro *CLI* como el dónde leer la información que el usuario introduce en la terminal, qué mensajes imprime en nuestra terminal y qué hacer con los datos que introduce usuario.

```js
var readline  = require('readline');
var interface = readline.createInterface();
```

Para configurar la interfaz de nuestra aplicación, tenemos que pasar un objeto `{}` como argumento a la función `createInterface()` . Este objeto tiene dos valores, `input` y `output`, que le dicen al módulo `readline` dónde leer las entradas de los usuarios (`input`), y dónde imprimir los mensajes para que el usuario los pueda leer (`output`).

> En programación, un `objeto` es una estructura de datos que tiene `comportamiento` y `estado`. Por ejemplo, el objeto `perro` tiene varios `comportamientos` como ladrar, correr, brincar; y varios `estados`, como grande, cuatro patas, color café, etc. Puedes aprender más de cómo JavaScript estructura los objetos [aquí](https://www.w3schools.com/js/js_objects.asp).

```js
var readline  = require('readline');
var interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});
```

Lo que estamos haciendo con esta configuración es decirle al módulo de `readline` que tome las entradas de datos de los usuarios de `process.stdin` y que muestre las salidas de mensajes en `process.stdout`. `process` en Node representa el proceso actual del programa que está corriendo.

### IV. Mostrando Nuestra Primera Pregunta

Una vez que ya tienes `readline` disponible en tu programa, y el `input` y `output` de tu *CLI* mapeada, ahora vamos a declarar una función `run` que contenga las instrucciones para correr nuestro programa.

En tu archivo `index.js`, escribe el siguiente código:

```js
var readline  = require('readline');
var interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});
// Aquí definimos la nueva función llamada run() con las instrucciones de nuestro programa.
function run() {
  console.log('** Bienvenido al Calculador de Área **');
}
// Aquí llamamos la función que definimos arriba.
run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
** Bienvenido al Calculador de Área **
```

Si todo salió bien, verás un mensaje que dice `** Bienvenido al Calculador de Área **` en tu terminal. Para salir del programa, presiona `Control` y `c` al mismo tiempo (también escrito como `CTRL + C`).

Una vez hecho esto, vamos a crear nuestra primera pregunta y guardar la información que recibimos del usuario en una variable. Para hacer esto, vamos a utilizar la función `question()` de `readline`. Esta función acepta dos argumentos, un mensaje y una función que le dice qué hacer con los datos que recibe del usuario.

```js
var readline  = require('readline');
var interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

function run() {
  // Aquí declaramos la variable y le asignamos un *string* vacío.
  var name = '';

  console.log('** Bienvenido al Calculador de Área **');
  // Aquí utilizamos la función *question()* para tomar el input del usuario,
  // regresamos el input del usuario y lo guardamos en una variable llamada *nombre*
  name = interface.question('¿Cuál es tu nombre?', function(name) {
    return name;
  })
  // Aquí imprimimos un mensaje de bienvenida para al ususario usando la variable *nombre*
  console.log(`¡Hola, ${name}!`);
}

run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
** Bienvenido al Calculador de Área **
¿Cuál es tu nombre?¡Hola, undefined!
```

Algo no funciona.

Primero, el texto de la pregunta y la respuesta del usuario están pegados. Esto se debe a que nos debemos indicarle a Node que tiene que crear una línea nueva al finalizar la pregunta. Para hacer esto, tenemos que agregar el caracter `\n` al final del mensaje.

En tu archivo `index.js`, escribe el siguiente código:

```js
var readline  = require('readline');
var interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

function run() {
  var name = '';

  console.log('** Bienvenido al Calculador de Área **');
  // Aquí ingresamos el caracter *\n* al final del mensaje para crear una nueva línea
  name = interface.question('¿Cuál es tu nombre?\n', function(name) {
    return name;
  })

  console.log(`¡Hola, ${name}!`);
}

run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
** Bienvenido al Calculador de Área **
¿Cuál es tu nombre?
¡Hola, undefined!
```

Hemos arreglado el primer problema. Pero, ¿por qué nos dice `¡Hola, undefined!` si hemos definido la variable `name` antes? Lo que sucede es que **Node.js** es una plataforma que permite procesar varias instrucciones a la vez sin esperar a que éstas terminen de ejecutarse.

En este caso, mientras que nuestro CLI espera a que le mandemos nuestra respuesta, Node sigue ejecutando el programa sin esperarnos. A este tipo de procesamiento se le llama *asynchronous I/O* o *non-blocking I/O*.

Por ejemplo, si estás cocinando un pastel, mientras el pastel está en el horno, tú puedes ir preparando el merengue para tenerlo listo cuando el pastel se termine de hornear. Esto te permite realizar varias tareas al mismo tiempo para ser más eficiente.

Puedes aprender más de este paradigma [aquí](https://en.wikipedia.org/wiki/Asynchronous_I/O).

Lo que tenemos que hacer ahora es decirle a Node que espere a que el usuario nos dé su respuesta antes de seguir ejecutando el programa. Para eso usamos una función especial llamada `Promise` que nos permite decirle a Node que espere utilizando la instrucción `await`.

`Promise` acepta una función con dos argumentos, `resolve` y `reject`. `resolve` le dice a nuestro programa que retornar si el `Promise` se ejecuta correctamente, mientras que `reject` le dice a nuestro programa que retornar si el `Promise` no termina de ejecutarse correctamente.

En tu archivo `index.js`, escribe el siguiente código:

```js
var readline  = require('readline');
var interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

function run() {
  var name = '';

  console.log('** Bienvenido al Calculador de Área **');

  // Aquí envolvemos la función que teníamos antes en un Promise, esto nos va a permitir
  // decirle a Node que nos espere a que esta instrucción termine de ejecutarse
  name = new Promise(function(resolve) {
    interface.question('¿Cuál es tu nombre?\n', function(name) {
      // Aquí cambiamos *return* por *resolve* para que el *Promise* regrese
      // los datos de entrada del usuario en caso de ejecutarse correctamente.
      resolve(name);
    })
  })

  console.log(`¡Hola, ${name}!`);
}

run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
** Bienvenido al Calculador de Área **
¿Cuál es tu nombre?
¡Hola, [object Promise]!
```

¿Por qué todavía no funciona nuestro programa? Nuestro programa todavía no funciona porque no le hemos dicho a Node que nuestra función `run()` es una función `asincrónica` que tiene instrucciones que dependen de otras instrucciones, y tampoco le hemos dicho a nuestro programa que tiene que esperar a que el `Promise` regrese los datos de entrada del usuario.

En tu archivo `index.js`, escribe el siguiente código:

```js
var readline  = require('readline');
var interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

// Con el keyword *async* le indicamos a Node que nuestra función *run()* contiene
// instrucciones que dependen de que otras instrucciones terminen de ejecutarse
async function run() {
  var name = '';

  console.log('** Bienvenido al Calculador de Área **');

  // Aquí usamos el keyword *await* para decirle a nuestro *Promise* que nos espere
  // a que el usuario introduzca su instrucción antes de seguir con la ejecución del programa
  name = await new Promise(function(resolve) {
    interface.question('¿Cuál es tu nombre?\n', function(name) {
      resolve(name);
    })
  })

  console.log(`¡Hola, ${name}!`);
}

run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
¿Cuál es tu nombre?
Ada
¡Hola, Ada!
```

Listo! Ahora nuestro programa funciona como esperábamos.

### V. *Refactoring*

Cuando eres un desarrollador de software profesional, después de terminar la implementación de una funcionalidad, debes mejorar tu código. Este proceso de mejora, sin cambiar la funcionalidad, se llama *Refactoring*.

Si ves nuestra implementación, podemos abstraer nuestro `Promise` en una función nueva para que sea más fácil de entender. Para hacer esto, primero vamos a declarar una función que se llame `requestName()`.

En tu archivo `index.js`, escribe el siguiente código:

```js
var readline  = require('readline');
var interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name = '';

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestName();
  console.log(`¡Hola, ${name}!`);
}

function requestName() {
  return new Promise(function(resolve) {
    interface.question('¿Cuál es tu nombre?\n', function(name) {
      resolve(name);
    })
  })
}

run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
¿Cuál es tu nombre?
Ada
¡Hola, Ada!
```

Antes de seguir con la implementación de nuestro programa, vamos a hacer otro cambio. Hasta ahora hemos usado variables para guardar datos en nuestro programa. Sin embargo, es una buena práctica usar `constantes` para guardar datos que no van a cambiar. Para declarar una constante, usamos el *keyword* `const`.

En nuestro programa, el modulo `readline` y la interfaz no van a cambiar. Por lo tanto, las variables `readline` e `interface` pueden ser constantes.

En tu archivo `index.js`, escribe el siguiente código:

```js
// Aquí cambiamos estas variables por constantes porque no vamos a cambiar su valor.
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name = '';

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestName();
  console.log(`¡Hola, ${name}!`);
}

function requestName() {
  return new Promise(function(resolve) {
    interface.question('¿Cuál es tu nombre?\n', function(name) {
      resolve(name);
    })
  })
}

run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
¿Cuál es tu nombre?
Ada
¡Hola, Ada!
```

Si todo salió bien, verás que la funcionalidad sigue siendo la misma.

#### Ejercicio

Ya que tenemos nuestro código más estructurado, ahora podemos agregar nuestra segunda pregunta.

En tu archivo `index.js`:

1. Declara una variable `base` que pueda guardar el valor de la base del rectángulo.
2. Declara una función `requestBase()`.
3. Dentro de tu función `resquestBase()` declara un `Promise` que, cuando termine su ejecución exitosamente, retorne los datos de entrada del usuario.
4. Asigna el valor del retorno de la función `requestBase()` a la variable `base`. No te olvides de decirle a Node que espere a que el usuario responda la pregunta antes de continuar la ejecución del programa.
5. Imprime un mensaje al usuario que diga `La base del rectángulo es <base>.`.
5. Asegúrate de que tu programa funciona corriéndolo en la terminal.

### VI. Agregando las Siguientes Preguntas

Si lograste completar el código anterior. Tu programa se verá de esta manera:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name = '';
  // Aquí está segunda variable que definimos en nuestro programa.
  var base = 0;

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestName();
  console.log(`¡Hola, ${name}!`);
  // Aquí está la función *requestBase() que llama a la segunda pregunta y la asignamos a la variable *base*
  base = await requestBase();
  // Aquí imprimimos un mensaje confirmando los datos de entrada del usuario
  console.log(`La base del rectángulo es ${base}.`);
}

function requestName() {
  return new Promise(function(resolve) {
    interface.question('¿Cuál es tu nombre?\n', function(name) {
      resolve(name);
    })
  })
}
// Esta es la implementación que llama a la segunda pregunta
function requestBase() {
  return new Promise(function(resolve) {
    interface.question('¿Cuál es la base del rectángulo?\n', function(base) {
      resolve(base);
    })
  })
}

run();
```

Cómo puedes ver, la función `requestName()` y `requestBase()` son iguales. Lo único que cambia es el mensaje, y el nombre del parámetro que retornamos.

Antes de seguir con la implementación de nuestro *CLI*. Vamos a crear una función llamada `requestInput()` que nos permita eliminar la repetición en nuestro código.

En tu archivo `index.js`, escribe el siguiente código:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name = '';
  var base = 0;

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestName();
  console.log(`¡Hola, ${name}!`);

  base = await requestBase();
  console.log(`La base del rectángulo es ${base}.`);
}

function requestName() {
  return new Promise(function(resolve) {
    interface.question('¿Cuál es tu nombre?\n', function(name) {
      resolve(name);
    })
  })
}

function requestBase() {
  return new Promise(function(resolve) {
    interface.question('¿Cuál es la base del rectángulo?\n', function(base) {
      resolve(base);
    })
  })
}
// Creamos una función que nos permite eliminar la repetición de *requestName()* y *requestBase()*
function requestInput(question) {
  return new Promise(function(resolve) {
    interface.question(question, function(input) {
      resolve(input);
    })
  })
}

run();
```

Ya que tenemos la función `requestInput()` en nuestro código, vamos a borrar las funciones `requestName()` y `requestBase()`.

En tu archivo `index.js`, escribe el siguiente código:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name = '';
  var base = 0;

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestName();
  console.log(`¡Hola, ${name}!`);

  base = await requestBase();
  console.log(`La base del rectángulo es ${base}.`);
}

function requestInput(question) {
  return new Promise(function(resolve) {
    interface.question(question, function(input) {
      resolve(input);
    })
  })
}

run();
```

Ahora, en tu terminal, ejecuta el siguiente comando para correr tu programa:

```bash
$ node index.js
** Bienvenido al Calculador de Área **
(node:28681) UnhandledPromiseRejectionWarning: Unhandled promise rejection (rejection id: 1): ReferenceError: requestName is not defined
(node:28681) [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.
```

Tenemos un problema. Hemos olvidado reemplazar las llamadas a las funciones viejas en nuestro código por la función `requestInput()`. Esto lo sabemos por que Node nos da un `ReferenceError` que nos dice que la función `requestName()` no está definida.

Vamos a arreglar esto. En tu archivo `index.js`, escribe el siguiente código:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name = '';
  var base = 0;

  console.log('** Bienvenido al Calculador de Área **');

  // Aquí cambiamos la función *requestName()* por *requestInput()*, además le pasamos un string como argumento para mostrar la pregunta en la terminal.
  name = await requestInput('¿Cuál es tu nombre?\n');
  console.log(`¡Hola, ${name}!`);

  // Aquí cambiamos la función *requestBase()* por *requestInput()*, aquí también pasamos un string como argumento para mostrar la pregunta en la terminal.
  base = await requestInput('¿Cuál es la base del rectángulo?\n');
  console.log(`La base del rectángulo es ${base}.`);
}

function requestInput(question) {
  return new Promise(function(resolve) {
    interface.question(question, function(input) {
      resolve(input);
    })
  })
}

run();
```

#### Ejercicio

Ahora que hemos eliminado la repetición en nuestro código, vamos a agregar la tercera pregunta.

En tu archivo `index.js`:

1. Crea una variable `height` donde puedas guardar la altura del rectángulo.
2. Utiliza la función `requestInput()` para pedirle al usuario la alturo del rectángulo. No te olvides de decirle a Node que espere a que el usuario introduzca sus datos.
3. Asigna el valor de retorno de la función `requestInput()` a la variable `height`.
5. Imprime un mensaje al usuario que diga `La altura del rectángulo es <height>.`.
5. Asegúrate de que tu programa funciona corriéndolo en la terminal.

### VII. Terminando Nuestro Programa

Si lograste completar el código anterior. Tu programa se verá de esta manera:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name   = '';
  var base   = 0;
  var height = 0;

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestInput('¿Cuál es tu nombre?\n');
  console.log(`¡Hola, ${name}!`);

  base = await requestInput('¿Cuál es la base del rectángulo?\n');
  console.log(`La base del rectángulo es ${base}.`);

  // Aquí es donde agregamos la tercera pregunta y guardamos el resultado de esta función en una variable llamada *height*
  height = await requestInput('¿Cuál es la altura del rectángulo?\n');
  console.log(`La base del rectángulo es ${height}.`);
}

function requestInput(question) {
  return new Promise(function(resolve) {
    interface.question(question, function(input) {
      resolve(input);
    })
  })
}

run();
```

Ahora tenemos que calcular el área. Antes de hacer esto, tenemos que convertir los valores de las variables `base` y `height` a números utilizando la función `parseInt()`. Esta función toma un `string` y lo convierte en número. Puedes aprender más de esta función [aquí](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt).

> **JavaScript** convierte implícitamente los valores de `strings` numéricos a números cuando los multiplicas entre sí. Sin embargo, se considera una buena práctica convertirlos explícitamente para evitar problemas en tu código.

En tu archivo `index.js`, escribe el siguiente código:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name   = '';
  var base   = 0;
  var height = 0;

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestInput('¿Cuál es tu nombre?\n');
  console.log(`¡Hola, ${name}!`);

  base = await requestInput('¿Cuál es la base del rectángulo?\n');
  // Aquí convertimos el valor de la variable *base* a un número.
  base = parseInt(base);
  console.log(`La base del rectángulo es ${base}.`);

  height = await requestInput('¿Cuál es la altura del rectángulo?\n');
  // Aquí convertimos el valor de la variable *height* a un número.
  height = parseInt(height);
  console.log(`La base del rectángulo es ${height}.`);
}

function requestInput(question) {
  return new Promise(function(resolve) {
    interface.question(question, function(input) {
      resolve(input);
    })
  })
}

run();
```

Una vez hecho esto, tenemos que multiplicar los valores de `base` y `height` para calcular el área de nuestro rectángulo, y mostrar el resultado a el usuario.

En tu archivo `index.js`, escribe el siguiente código:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name   = '';
  var base   = 0;
  var height = 0;
  // Aquí creamos una variable *area* para guardar el valor del área.
  var area   = 0;

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestInput('¿Cuál es tu nombre?\n');
  console.log(`¡Hola, ${name}!`);

  base = await requestInput('¿Cuál es la base del rectángulo?\n');
  base = parseInt(base);
  console.log(`La base del rectángulo es ${base}.`);

  height = await requestInput('¿Cuál es la altura del rectángulo?\n');
  height = parseInt(height);
  console.log(`La base del rectángulo es ${height}.`);
  // Aquí calculamos el área del rectángulo e imprimos el resultado para que
  // el usuario pueda verlo.
  area = base * height;
  console.log(`El área del rectángulo es ${area}.`);
}

function requestInput(question) {
  return new Promise(function(resolve) {
    interface.question(question, function(input) {
      resolve(input);
    })
  })
}

run();
```

Ahora, vamos a decirle a nuestro *CLI* que cierre la interfaz cuando el programa termine de ejecutarse. Para hacer esto, tenemos que usar la función de `close()`.

En tu archivo `index.js`, escribe el siguiente código:

```js
const readline  = require('readline');
const interface = readline.createInterface({
  input:  process.stdin,
  output: process.stdout
});

async function run() {
  var name   = '';
  var base   = 0;
  var height = 0;

  console.log('** Bienvenido al Calculador de Área **');

  name = await requestInput('¿Cuál es tu nombre?\n');
  console.log(`¡Hola, ${name}!`);

  base = await requestInput('¿Cuál es la base del rectángulo?\n');
  base = parseInt(base);
  console.log(`La base del rectángulo es ${base}.`);

  height = await requestInput('¿Cuál es la altura del rectángulo?\n');
  height = parseInt(height);
  console.log(`La base del rectángulo es ${height}.`);

  area = base * height;
  console.log(`El área del rectángulo es ${area}.`);

  interface.close();
}

function requestInput(question) {
  return new Promise(function(resolve) {
    interface.question(question, function(input) {
      resolve(input);
    })
  })
}

run();
```

### VIII. *package.json*

Por último, vamos a mejorar el modo en el que ejecutamos nuestro programa. Hasta ahora hemos ejecutado este comando en la terminal `node index.js`. Sin embargo, por convención, nos gustaría poder correr nuestro programa ejecutando este comando en vez `npm start`.

En los archivos de tu proyecto, abre el archivo `package.json` en tu editor. Probablemente veas esto:

```json
{
  "name": "area-calculator",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {}
}
```

Este archivo de *[JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)* contiene información sobre tu proyecto, como el nombre, la versión, las dependencias que necesita para funcionar (otras librerías externas a este proyecto), y *scripts*, entre otros.

Los *scripts* son las instrucciones que se ejecutan en la terminal al usar `npm` más el nombre del *script*. El nombre de tu *script* tiene que ser uno de los nombres aceptados por *NPM*. Puedes ver esto ejecutando `npm help` en tu terminal.

En tu archivo `package.json`, vamos a agregar un *script* llamado `start`. Para hacer esto, escribe lo siguiente:

```json
{
  "name": "area-calculator",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {}
}
```

Como puedes ver, debajo de `"test"` agregamos el *script* `"start"` que ejecuta la instrucción `node index.js` en nuestra terminal. Ahora, en vez de ejecutar `node index.js` podemos usar `npm start`. Mucho mejor.

Con esto hemos terminado. Esperamos que ahora te sientas lo suficientemente cómodo desarrollando aplicaciones *CLI*. Practica estos conceptos por tu cuenta y comparte con otros lo que hiciste.

¡Mucho éxito!
