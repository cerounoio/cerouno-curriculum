---
title: Introduccion a JavaScript
program: DAW
module: M1
layout: main
---

# Introducción a JavaScript

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Usar los tipos de datos de JavaScript
* Crear variables y guardar datos en ellas
* Entender los operadores
* Usar condicionales para controlar el flujo de un programas
* Declarar y llamar funciones

### II. Historia de JavaScript

En los comienzos de Internet, [Brendan Eich](https://en.wikipedia.org/wiki/Brendan_Eich) creó **JavaScript** (abreviado `JS`) en 10 días mientras trabajaba como ingeniero en Netscape. Inicialmente, Eich quería incorporar el lenguaje (Scheme)[https://en.wikipedia.org/wiki/Scheme_(programming_language)] en el navegador, pero sus superiores le pidieron que modificara la syntaxis para que se pareciera más a  (Java)[https://en.wikipedia.org/wiki/Java_(programming_language)]. Netscape lanzó JavaScript con Netscape 2 en 1996, y Microsoft lanzó su propia implementación, llamada *JScript*, ese mismo año.

> El nombre de *JavaScript* fue una idea de mercadotecnia en un intento de usar la popularidad del lenguaje *Java* de Sun Microsystems. Esta decisión sigue ocasionando confusión entre quienes no saben programar. Cuando los programadores escuchamos a alguien intercambiar con descuido los nombres de estos lenguajes, no podemos evitar juzgar el conocimiento de nuestro interlocutor. Para aprender más de la historia de *JavaScript* haz click [aquí](https://en.wikipedia.org/wiki/JavaScript).

Para estandarizar el lenguaje, Netscape desarrollo un estándar del lenguaje y lo mandó a [ECMA](https://en.wikipedia.org/wiki/Ecma_International), una organización encargada de establecer estándares en sistemas de comunicación e información. Este estándar, llamado ECMAScript (también abreviado *ES*), es el que determina la especificación de JavaScript, esto es, como debe funcionar el lenguaje en las diferentes implementaciones del mismo.

La versión de la especificación actual del lenguaje es ES2017, sin embargo, muchos navegadores todavía no terminan de adoptar la especificación establecida en *ES2015*. A partir de *ES2015* (también llamado *ES6*) se busca liberar anualmente las especificaciones de *ES*.

### III. ¿Por qué aprender JavaScript?

**JavaScript** fue creado para hacer Internet más dinámico. JS es un lenguaje de programación orientado a objetos. Tradicionalmente, JS se ha utilizado dentro de los navegadores para dar interactividad en las páginas web. Por ejemplo, cuando haces click en un botón y quieres que algo cambie en una página web, usas JavaScript.

Sin embargo, JavaScript puede ser *client-side* o *server-side*. Esto significa que podemos usar JS para controlar la interfaz del usuario que corre en el navegador (cliente), así como el código que corre en el servidor.

Debido esta flexibilidad y versatilidad, JS es el lenguaje más usado en el desarrollo de aplicaciones web en el mundo.

Ahora, vamos a aprender *JavaScript*.

### IV. Tipos de Datos

Existen seis tipos de datos en JavaScript:

* Número
* *String* (*cadena de caracteres* en español)
* Booleano
* *Null* (o *nulo* en español)
* *Undefined* (o *indefinido* en español)
* Símbolo (sólo disponible en *ES2015*)

#### Números

Este tipo de datos utiliza números. En JavaScript, los números son escritos sin comas, así que tres mil cuatrocientos setenta y cinco se escribe así:

```js
3475
```

Los números pueden ser negativos o tener decimales, por lo que podemos escribirlos así:  

```js
-3475
0.5
1.5
-4.56
```

> Todos los números en *JavaScript* son *floats* de *64-bits*. Este tipo de datos son representaciones de números en la memoria de la computadora. Sin embargo, estos números no son exactos en operaciones matemáticas de alta precisión. Por ejemplo: mientras que en una operación matemática normal `0.2 + 0.1` es igual a `0.3`, en *JavaScript* `0.2 + 0.1` es igual a `0.30000000000000004`.
Puedes aprender más sobre este tema [aquí](https://es.wikipedia.org/wiki/Formato_en_coma_flotante_de_doble_precisi%C3%B3n).


#### Strings

Un *string* (o *cadena de caracteres* en español) es un tipo de datos alfanumérico que siempre va escrito entre comillas y se ve así:

```js
"Hola, soy un string."
```

Puedes usar comillas sencillas (`''`) o dobles (`""`) al escribir *strings*, pero deben escribirse la misma para abrir y cerrar tu *string*.

```js
'Hola, uso comillas sencillas'
"Hola, uso commillas dobles"
```

> Es una buena práctica mantener consistencia en el uso de comillas sin importar si estas son dobles o sencillas.

Normalmente usamos *strings* cuando tenemos que manejar cualquier tipo de texto. Si vas a escribir números que no van a hacer operaciones matemáticas, los escribimos como strings *también*.

#### Booleanos

Este tipo de datos nos sirven para describir lógica binaria. Los *booleanos* (o *boolean* en inglés) tienen sólo uno de dos valores: `true` o `false`. Esto funciona como un interruptor de luz, este está prendido o apagado.

```js
true
false
```

Nosotros usamos los *booleans* para controlar el que código ejecutar en un programa. A este proceso se le llama *control flow* (o *control de flujo* en español).

#### Null y Undefined

*Null* es un tipo de datos que signfica que el valor es `nada`. Esto no quiere decir que sea `0` o que sea un *string* vacío, sino que es `nada`. En otros lenguajes de programación como `Ruby`, *null* es representado como `Nil`.

*Undefined* (o *indefinido* en español) es un valor que no está declarado en nuestro programa. Por ejemplo, si nuestro programa hace referencia a una variable o a una función que no existe, el programa nos dirá que esta variable o función está `undefined`.

#### Símbolos

Los símbolos (o *symbols* en inglés) son un tipo de datos especiales diseñados para servir como identificadores únicos o propiedades semiprivadas de objetos. Por el momento, ignora este tipo de datos. Si quieres saber más acerca de los símbolos haz click [aquí](http://exploringjs.com/es6/ch_symbols.html).

### V. Variables

Cuando escribimos un programa, es probable que queramos reusar los mismos valores en múltiples ocasiones. Escribir el mismo valor una y otra vez es bastante tedioso.

Cuando escribimos un programa, necesitamos guardar temporalmente pequeñas piezas de datos que puedan ser manipuladas después. Estos lugares donde guardamos datos se llaman variables. Como su nombre lo indica, los datos guardados dentro de una *variable* pueden cambiar (o *variar*).

#### Declarando una Variable

Al escribir una variable decimos que la estamos *declarando*, es decir, defininos su nombre, y algunas veces, su contenido. Para declarar una variable necesitamos usar dos partes: la palabra `var` y el nombre de la variable.

En tu terminal, ejecuta la siguiente instrucción:

```bash
$ node
```

Esto va a iniciar un *REPL* (*Read Evaluate Print Loop*) que te permite escribir código de manera interactiva en tu terminal.

Escribe el siguiente código en tu *REPL* y presiona `Enter`:

```js
var miNombre;
undefined
```

> Cuando declaramos una variable sin asignar un valor, Node dice que el valor de la variable no está definido o que está *undefined*.

Ahora vamos a asignar un valor a la variable usando tu nombre. Ejecuta el siguiente código en tu *REPL*:

```js
miNombre = 'Jorge'
'Jorge'
```

También puedes asignar números a las variables. Ejecuta el siguiente código en tu *REPL*.

```js
var miEdad = 36
undefined
```

Ahora llama tu variable en tu *REPL* y verás que el valor de la variable `miEdad` es `36`.

```js
miEdad
36
```

> Tal vez te preguntes por que al declarar una variable con un valor, *Node* nos muestra el mensaje de *undefined*. Cuando una declaración no tiene un valor de retorno, este valor está *undefined*. No te preocupes por entender esto ahora, tal vez esto sea más claro cuando veamos *funciones*.

#### Cómo Nombrar a Una Variable
