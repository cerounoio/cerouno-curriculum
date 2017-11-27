---
title: Colecciones en JavaScript
program: DAW
module: M1
layout: main
---

# Colecciones en JavaScript

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Entender como funcionan los *arrays* y los *objects* en JavaScript
* Cambiar y acceder valores en un *array*
* Usar *for loops* para modificar valores en una colección de datos
* Usar *for...in* para modificar valores en una colección de datos
* Usar *forEach()* para modificar valores en una colección de datos

### II. Preparación

Ahora que ya has aprendido de clases, métodos y atributos, es hora de entender como funcionan las colecciones de datos en JavaScript. Esto te permitirá realizar operaciones más complejas y reducir la repetición en tus implementaciones.

Para empezar con este tutorial, en tu terminal, crea un directorio ejecutando el siguiente comando:

```bash
$ mkdir colecciones_en_javascript && cd colecciones_en_javascript
```

Ahora crea un archivo `miPrograma.js` en tu terminal ejecutando el siguiente comando:

```bash
$ touch miPrograma.js
```

Una vez hecho esto podemos escribir nuestro programa.

### III. *Arrays*

Los **arrays** son colecciones de datos ordenados por posición. Estas colecciones pueden tener diferentes tipos de datos y están delimitadas por corchetes (`[` o `]`).

Por ejemplo, si definimos un *array* de verduras, este puede escribirse de esta manera:

```js
var verduras = ['tomate', 'cebolla', 'papa'];
```

La posición de un elemento en un *array* es llamada *índice*. Ésta te permite encontrar un elemento fácilmente en una colección. El primer índice de un *array* es la posición `0`.

Por ejemplo, si queremos encontrar el primer elemento del *array* `verduras`, lo podemos hacer de esta manera:


```js
verduras[0];
```

Para insertar un dato en un *array* puedes hacerlo utilizando el índice de la posición donde quieres insertar el elemento. Por ejemplo, si quieres insertar una nueva verdura, puedes hacerlo de esta manera:

```js
verduras[10] = 'brocoli';
```

También puedes crear *arrays* con diferentes tipos de datos, e incluso, otros *arrays*.

Por ejemplo:

```js
var muchasCosas = ['libreta', 0, 5, 'casa', undefined, null, true, [2, 'perro']];
```

> Si quieres agregar un valor al final de un *array*, puedes utilizar el método `push()`. Por ejemplo, si quieres agregar un valor `'papa'` en el *array* llamado `verduras`, puedes hacerlo de esta manera, `verduras.push('papa')`. Si quieres retirar el último valor de un *array*, puedes usar el método `pop()`. Por ejemplo, `verduras.pop()`.

#### Ejercicio

En tu archivo `miPrograma.js` implementa los siguientes requerimientos y ejecuta tu programa en la terminal después de cada paso.

1. Crea un *array* con cinco nombres de frutas (`pera`, `manzana`, `durazno`, `mango`, `ciruela`) y guárdalo en una variable llamada `frutas`.
2. Imprime el nombre de la fruta que está en el *index* `2`.
3. Asigna un nuevo nombre de fruta `naranja` en el *index* `20` e imprime su valor.
4. Imprime tu *array*. ¿Qué pasa con los lugares vacíos?

#### Solución

Antes de seguir, vamos a revisar el ejercicio anterior. Si seguiste las instrucciones correctamente, tu archivo `miPrograma.js` debe verse como esto:

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);
```

Si ejecutas tu programa en la terminal, debes de ver lo siguiente:

```bash
$ node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
```

### IV. *Objects*

Los **objects** en JavaScript son una estructura de datos que nos permite tener colecciones de datos organizadas por atributo. Estos están delimidos por llaves (`{` o `}`).

Por ejemplo, si definimos una colección de ropa y la ordenamos por marca, podríamos escribirla así:

```js
var coleccionDeRopa = { gucci: 'pantalon', armani: 'abrigo', burberry: 'abrigo' };
```

Ahora, si queremos acceder a un valor en nuestro *object*, sólo tenemos que usar el atributo que lo contiene. Por ejemplo, para encontrar el valor de `burberry`, podemos hacerlo de esta manera:

```js
coleccionDeRopa.burberry;
```

También podemos agregar valores a nuestro *object* de la misma manera:

```js
coleccionDeRopa.versace = 'pantalon';
```

#### Ejercicio

En tu archivo `miPrograma.js` implementa los siguientes requerimientos y ejecuta tu programa en la terminal después de cada paso.

1. Crea un *object* con cuatro ingredientes y cantidades (2 nueces, 4 huevos, 1 barra de mantequilla, 1 cucharada de azúcar). Usa los nombres de los ingredientes como atributos. Guarda el *object* en una variable llamada `ingredientes`.
2. Imprime la cantidad del ingrediente `nueces`.
3. Crea un nuevo atributo `litrosDeAgua` y asigna la cantidad `1.5`.
4. Imprime tu *object*.

#### Solución

Antes de seguir, vamos a revisar el ejercicio anterior. Si seguiste las instrucciones correctamente, tu archivo `miPrograma.js` debe verse como esto:

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);

var ingredientes = { nueces: 2, huevos: 4, barraDeMantequilla: 1, cucharadaDeAzucar: 1};
console.log(ingredientes.nueces);
ingredientes.litrosDeAgua = 1.5;
console.log(ingredientes);
```

Si ejecutas tu programa en la terminal, debes de ver lo siguiente:

```text
$ node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
2
{ nueces: 2,
  huevos: 4,
  barraDeMantequilla: 1,
  cucharadaDeAzucar: 1,
  litrosDeAgua: 1.5 }
```

> Los atributos de los objetos en JavaScript no sólo sirven para guardar estructuras de datos sino que también pueden guardar funciones. Por ejemplo, en nuestro objeto `ingredientes`, tú puedes agregar una función declarando un atributo y asignando una función de esta manera: `ingredientes.cocinando = function() { console.log('Estoy cocinando.') }`. Una vez definida esto, puedes invocar esta nueva función de este modo: `ingredientes.cocinando()`.

### V. *For loops*

Cuando tenemos varios elementos en una colección, y queremos realizar una accion por cada uno de los elementos, usamos `for` *loops* (o *ciclos* en español). La sintaxis es un poco extraña, pero practicamente sigue este proceso:

1. Primero definimos una variable para llevar la cuenta de cuantos vueltas lleva el *loop*.
2. Luego le asignamos un valor inicial a nuestra variable.
2. Después le decimos a nuestro *loop* hasta cuando continuar.
3. Por último, agregamos una unidad a nuestra variable para llevar la cuenta de las vueltas que lleva nuestro *loop*.

Para ejemplificar esto, en tu archivo `miPrograma.js` escribe el siguiente código:

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);

var ingredientes = { nueces: 2, huevos: 4, barraDeMantequilla: 1, cucharadaDeAzucar: 1};
console.log(ingredientes.nueces);
ingredientes.litrosDeAgua = 1.5;
console.log(ingredientes);

// Aquí declaramos la variable *pasos* que nos va a permitir llevar la cuenta.
var pasos;
// 1. Aquí establecemos que el valor inicial de nuestra variable *pasos* es  
// igual a uno.
// 2. Luego decimos que este *loop* va a seguir mientras la variable *pasos*
// sea menor o igual a *10*.
// 3. Por último agregamos una unidad a nuestra variable *pasos* para llevar
// la cuenta.
for(pasos = 0; pasos < 10; pasos++) {
  //Aqui imprimos el valor de la variable *pasos* en cada vuelta del *loop*.
  console.log(`Este es el paso ${pasos}.`);
}
```

Ahora corre tu programa en la terminal para ver nuestro *loop* en acción:

```text
node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
2
{ nueces: 2,
  huevos: 4,
  barraDeMantequilla: 1,
  cucharadaDeAzucar: 1,
  litrosDeAgua: 1.5 }
  Este es el paso 0.
  Este es el paso 1.
  Este es el paso 2.
  Este es el paso 3.
  Este es el paso 4.
  Este es el paso 5.
  Este es el paso 6.
  Este es el paso 7.
  Este es el paso 8.
  Este es el paso 9.
```

También puedes usar esta técnica para acceder a cada elemento en un *array* usando el índice de cada elemento. En tu archivo `miPrograma.js`, escribe el siguiente código.

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);

var ingredientes = { nueces: 2, huevos: 4, barraDeMantequilla: 1, cucharadaDeAzucar: 1};
console.log(ingredientes.nueces);
ingredientes.litrosDeAgua = 1.5;
console.log(ingredientes);

var pasos;
for(pasos = 0; pasos < 10; pasos++) {
  console.log(`Este es el paso ${pasos}.`);
}

// Aquí usamos la misma variable *pasos* para definir nuestro *loop*
for(pasos = 0; pasos < 5; pasos++) {
  // Aquí usamos la variable *pasos* para acceder al elemento del array
  // *frutas*
  console.log(`La fruta es ${frutas[pasos]}.`);
}
```

Ahora, al correr tu programa en la terminal, verás esto:

```text
$ node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
2
{ nueces: 2,
  huevos: 4,
  barraDeMantequilla: 1,
  cucharadaDeAzucar: 1,
  litrosDeAgua: 1.5 }
Este es el paso 0.
Este es el paso 1.
Este es el paso 2.
Este es el paso 3.
Este es el paso 4.
Este es el paso 5.
Este es el paso 6.
Este es el paso 7.
Este es el paso 8.
Este es el paso 9.
La fruta es pera.
La fruta es manzana.
La fruta es durazno.
La fruta es mango.
La fruta es ciruela.
```

También podemos usar una variación de la sintaxis del `for` *loop* que es más fácil de entender. A esta versión le llamamos `for...in`. En tu archivo `miPrograma.js` escribe lo siguiente:

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);

var ingredientes = { nueces: 2, huevos: 4, barraDeMantequilla: 1, cucharadaDeAzucar: 1};
console.log(ingredientes.nueces);
ingredientes.litrosDeAgua = 1.5;
console.log(ingredientes);

var pasos;
for(pasos = 0; pasos < 10; pasos++) {
  console.log(`Este es el paso ${pasos}.`);
}

for(pasos = 0; pasos < 5; pasos++) {
  console.log(`La fruta es ${frutas[pasos]}.`);
}

// Aquí usamos una sintaxis alternativa para nuestro *for loop*,
// primero definimos el nombre de la variable que contiene el indice y
// luego pasamos la coleccion *frutas* sobre la cual vamos a iterar.
for(var indice in frutas) {
  // Aquí usamos la variable *indice* para acceder al valor de la colección
  // *frutas*
  console.log(`Me gusta ${frutas[indice]}.`);
}
```

Si corres tu programa en la terminal, verás lo siguiente:

```text
$ node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
2
{ nueces: 2,
  huevos: 4,
  barraDeMantequilla: 1,
  cucharadaDeAzucar: 1,
  litrosDeAgua: 1.5 }
Este es el paso 0.
Este es el paso 1.
Este es el paso 2.
Este es el paso 3.
Este es el paso 4.
Este es el paso 5.
Este es el paso 6.
Este es el paso 7.
Este es el paso 8.
Este es el paso 9.
La fruta es pera.
La fruta es manzana.
La fruta es durazno.
La fruta es mango.
La fruta es ciruela.
La fruta es pera.
La fruta es manzana.
La fruta es durazno.
La fruta es mango.
La fruta es ciruela.
```

#### Ejercicio

En tu archivo `miPrograma.js` agrega los siguientes requerimientos. No te olvides de correr el programa después de cada paso:

1. Define una variable llamada `ciudades`. Esta variable va a guardar un *array* que tiene tres elementos `Monterrey`, `Guadalajara`, `Ciudad de México`.
2. Imprime este *array*.
3. Define un *loop* que imprima el mensaje `Me gusta <ciudad>.` por cada elemento del *array* `ciudades` usando la sintaxis tradicional.
4. Define un *loop* que imprima el mensaje `Me gusta mucho <ciudad>.` por cada elemento del *array* `ciudades` usando la sintaxis `for...in`.

#### Solución

Antes de continuar, vamos a revisar el ejercicio anterior. Si seguiste las instrucciones correctamente, tu archivo `miPrograma.js` debe verse como esto:

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);

var ingredientes = { nueces: 2, huevos: 4, barraDeMantequilla: 1, cucharadaDeAzucar: 1};
console.log(ingredientes.nueces);
ingredientes.litrosDeAgua = 1.5;
console.log(ingredientes);

var pasos;
for(pasos = 0; pasos < 10; pasos++) {
  console.log(`Este es el paso ${pasos}.`);
}

for(pasos = 0; pasos < 5; pasos++) {
  console.log(`La fruta es ${frutas[pasos]}.`);
}

for(var indice in frutas) {
  console.log(`Me gusta ${frutas[indice]}.`);
}

var ciudades = ['Monterrey', 'Guadalajara', 'Ciudad de México'];
console.log(ciudades);
for(pasos = 0; pasos < 3; pasos++) {
  console.log(`Me gusta ${ciudades[pasos]}.`);
}

for(var indice in ciudades) {
  console.log(`Me gusta mucho ${ciudades[indice]}.`);
}
```

Si ejecutas tu programa en la terminal, debes de ver lo siguiente:

```text
$ node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
2
{ nueces: 2,
  huevos: 4,
  barraDeMantequilla: 1,
  cucharadaDeAzucar: 1,
  litrosDeAgua: 1.5 }
Este es el paso 0.
Este es el paso 1.
Este es el paso 2.
Este es el paso 3.
Este es el paso 4.
Este es el paso 5.
Este es el paso 6.
Este es el paso 7.
Este es el paso 8.
Este es el paso 9.
La fruta es pera.
La fruta es manzana.
La fruta es durazno.
La fruta es mango.
La fruta es ciruela.
Me gusta pera.
Me gusta manzana.
Me gusta durazno.
Me gusta mango.
Me gusta ciruela.
Me gusta naranja.
[ 'Monterrey', 'Guadalajara', 'Ciudad de México' ]
Me gusta Monterrey.
Me gusta Guadalajara.
Me gusta Ciudad de México.
Me gusta mucho Monterrey.
Me gusta mucho Guadalajara.
Me gusta mucho Ciudad de México.
```

### VI. `forEach()`

Existe una manera más fácil de iterar sobre un *array* usando el método `forEach()`. Este método acepta una función como argumento que define el código a ejecutar en cada paso.

> Además de `forEach()` existen otros métodos de *array* que pueden ayudarte en tu código. Por ejemplo, para ordenar los valores de un *array* puedes usar `sort()`. Para aprender más de los métodos disponibles, ve la documentación [aquí](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

Para ejemplificar esto, vamos a crear un *array* `mascotas` con cuatro elementos. En tu archivo `miPrograma.js` escribe lo siguiente:

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);

var ingredientes = { nueces: 2, huevos: 4, barraDeMantequilla: 1, cucharadaDeAzucar: 1};
console.log(ingredientes.nueces);
ingredientes.litrosDeAgua = 1.5;
console.log(ingredientes);

var pasos;
for(pasos = 0; pasos < 10; pasos++) {
  console.log(`Este es el paso ${pasos}.`);
}

for(pasos = 0; pasos < 5; pasos++) {
  console.log(`La fruta es ${frutas[pasos]}.`);
}

for(var indice in frutas) {
  console.log(`Me gusta ${frutas[indice]}.`);
}

var ciudades = ['Monterrey', 'Guadalajara', 'Ciudad de México'];
console.log(ciudades);
for(pasos = 0; pasos < 3; pasos++) {
  console.log(`Me gusta ${ciudades[pasos]}.`);
}

for(var indice in ciudades) {
  console.log(`Me gusta mucho ${ciudades[indice]}.`);
}

// Aquí definimos un *array* nuevo que contiene cuatro elementos.
var mascotas = ['perro', 'gato', 'hámster', 'loro'];
// Aquí usamos el método *forEach()* para iterar sobre nuestro *array*. Como
// puedes ver, este método acepta una función como argumento.
mascotas.forEach(function(mascota){
  // Aquí imprimimos un mensaje en cada vuelta del ciclo.
  console.log(`Tengo un ${mascota}.`);
});
```

Si ejecutas tu programa, verás este mensaje en tu terminal:

```text
$ node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
2
{ nueces: 2,
  huevos: 4,
  barraDeMantequilla: 1,
  cucharadaDeAzucar: 1,
  litrosDeAgua: 1.5 }
Este es el paso 0.
Este es el paso 1.
Este es el paso 2.
Este es el paso 3.
Este es el paso 4.
Este es el paso 5.
Este es el paso 6.
Este es el paso 7.
Este es el paso 8.
Este es el paso 9.
La fruta es pera.
La fruta es manzana.
La fruta es durazno.
La fruta es mango.
La fruta es ciruela.
Me gusta pera.
Me gusta manzana.
Me gusta durazno.
Me gusta mango.
Me gusta ciruela.
Me gusta naranja.
[ 'Monterrey', 'Guadalajara', 'Ciudad de México' ]
Me gusta Monterrey.
Me gusta Guadalajara.
Me gusta Ciudad de México.
Me gusta mucho Monterrey.
Me gusta mucho Guadalajara.
Me gusta mucho Ciudad de México.
Tengo un perro.
Tengo un gato.
Tengo un hámster.
Tengo un loro.
```

#### Ejercicio

En tu archivo `miPrograma.js` agrega los siguientes requerimientos. No te olvides de correr el programa después de cada paso:

1. Define una variable llamada `peliculas`. Esta variable va a guardar un *array* que tiene cuatro elementos `Toy Story`, `Batman`, `Avengers`, `Titanic`.
2. Imprime este *array*.
3. Define un *loop* que imprima el mensaje `Mi película favorita es <película>.` por cada elemento del *array* `ciudades` usando la sintaxis tradicional.
4. Define un *loop* que imprima el mensaje `Mi película favorita es <película>.` por cada elemento del *array* `ciudades` usando la sintaxis `for...in`.
5. Define un *loop* que imprima el mensaje `Mi película favorita es <película>.` por cada elemento del *array* `ciudades` usando `forEach()`.

#### Solución

Si seguiste las instrucciones correctamente, tu archivo `miPrograma.js` debe verse como esto:

```js
var frutas = ['pera', 'manzana', 'durazno', 'mango', 'ciruela'];
console.log(frutas[2]);
frutas[20] = 'naranja';
console.log(frutas[20]);
console.log(frutas);

var ingredientes = { nueces: 2, huevos: 4, barraDeMantequilla: 1, cucharadaDeAzucar: 1};
console.log(ingredientes.nueces);
ingredientes.litrosDeAgua = 1.5;
console.log(ingredientes);

var pasos;
for(pasos = 0; pasos < 10; pasos++) {
  console.log(`Este es el paso ${pasos}.`);
}

for(pasos = 0; pasos < 5; pasos++) {
  console.log(`La fruta es ${frutas[pasos]}.`);
}

for(var indice in frutas) {
  console.log(`Me gusta ${frutas[indice]}.`);
}

var ciudades = ['Monterrey', 'Guadalajara', 'Ciudad de México'];
console.log(ciudades);
for(pasos = 0; pasos < 3; pasos++) {
  console.log(`Me gusta ${ciudades[pasos]}.`);
}

for(var indice in ciudades) {
  console.log(`Me gusta mucho ${ciudades[indice]}.`);
}

var peliculas = ['Toy Story', 'Batman', 'Avengers', 'Titanic'];
console.log(peliculas);
for(pasos = 0; pasos < 4; pasos++) {
  console.log(`Mi película favorita es ${peliculas[pasos]}.`);
}

for(var indice in peliculas) {
  console.log(`Mi película favorita es ${peliculas[indice]}.`);
}

peliculas.forEach(function(pelicula){
  console.log(`Mi película favorita es ${pelicula}.`);
})
```

Si ejecutas tu programa en la terminal, debes de ver lo siguiente:

```text
$ node miPrograma.js
durazno
naranja
[ 'pera',
  'manzana',
  'durazno',
  'mango',
  'ciruela',
  <15 empty items>,
  'naranja' ]
2
{ nueces: 2,
  huevos: 4,
  barraDeMantequilla: 1,
  cucharadaDeAzucar: 1,
  litrosDeAgua: 1.5 }
Este es el paso 0.
Este es el paso 1.
Este es el paso 2.
Este es el paso 3.
Este es el paso 4.
Este es el paso 5.
Este es el paso 6.
Este es el paso 7.
Este es el paso 8.
Este es el paso 9.
La fruta es pera.
La fruta es manzana.
La fruta es durazno.
La fruta es mango.
La fruta es ciruela.
Me gusta pera.
Me gusta manzana.
Me gusta durazno.
Me gusta mango.
Me gusta ciruela.
Me gusta naranja.
[ 'Monterrey', 'Guadalajara', 'Ciudad de México' ]
Me gusta Monterrey.
Me gusta Guadalajara.
Me gusta Ciudad de México.
Me gusta mucho Monterrey.
Me gusta mucho Guadalajara.
Me gusta mucho Ciudad de México.
Tengo un perro.
Tengo un gato.
Tengo un hámster.
Tengo un loro.
[ 'Toy Story', 'Batman', 'Avengers', 'Titanic' ]
Mi película favorita es Toy Story.
Mi película favorita es Batman.
Mi película favorita es Avengers.
Mi película favorita es Titanic.
Mi película favorita es Toy Story.
Mi película favorita es Batman.
Mi película favorita es Avengers.
Mi película favorita es Titanic.
Mi película favorita es Toy Story.
Mi película favorita es Batman.
Mi película favorita es Avengers.
Mi película favorita es Titanic.
```

Ahora que ya sabes como manejar colecciones en JavaScript, sigue creando *loops* que iteren sobre `arrays` y `objects`. También no te olvides de revisar la documentación [aquí](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) y experimenta con otros métodos disponibles de *array*.
