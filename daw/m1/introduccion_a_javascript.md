---
title: Introduccion a JavaScript
program: DAW
module: M1
layout: main
---

# Introducción a *JavaScript*

### I. Objetivos de Aprendizaje

Después de esta lección, los estudiantes podrán:

* Usar los tipos de datos de *JavaScript*
* Crear variables y guardar datos en ellas
* Entender los operadores
* Usar condicionales para controlar el flujo de un programas
* Declarar y llamar funciones

### II. Historia de *JavaScript*

En los comienzos de Internet, [Brendan Eich](https://en.wikipedia.org/wiki/Brendan_Eich) creó **JavaScript** (abreviado `JS`) en 10 días mientras trabajaba como ingeniero en Netscape. Inicialmente, Eich quería incorporar el lenguaje (Scheme)[https://en.wikipedia.org/wiki/Scheme_(programming_language)] en el navegador, pero sus superiores le pidieron que modificara la syntaxis para que se pareciera más a  (Java)[https://en.wikipedia.org/wiki/Java_(programming_language)]. Netscape lanzó *JavaScript* con Netscape 2 en 1996, y Microsoft lanzó su propia implementación, llamada *JScript*, ese mismo año.

> El nombre de *JavaScript* fue una idea de mercadotecnia en un intento de usar la popularidad del lenguaje *Java* de Sun Microsystems. Esta decisión sigue ocasionando confusión entre quienes no saben programar. Cuando los programadores escuchamos a alguien intercambiar con descuido los nombres de estos lenguajes, no podemos evitar juzgar el conocimiento de nuestro interlocutor. Para aprender más de la historia de *JavaScript* haz click [aquí](https://en.wikipedia.org/wiki/JavaScript).

Para estandarizar el lenguaje, Netscape desarrollo un estándar del lenguaje y lo mandó a [ECMA](https://en.wikipedia.org/wiki/Ecma_International), una organización encargada de establecer estándares en sistemas de comunicación e información. Este estándar, llamado *ECMAScript* (también abreviado *ES*), es el que determina la especificación de *JavaScript*, esto es, como debe funcionar el lenguaje en las diferentes implementaciones del mismo.

La versión de la especificación actual del lenguaje es *ES2017*, sin embargo, muchos navegadores todavía no terminan de adoptar la especificación establecida en *ES2015*. A partir de *ES2015* (también llamado *ES6*) se busca liberar anualmente las especificaciones de *ES*.

### III. ¿Por qué aprender *JavaScript*?

**JavaScript** fue creado para hacer Internet más dinámico. *JS* es un lenguaje de programación orientado a objetos. Tradicionalmente, *JS* se ha utilizado dentro de los navegadores para dar interactividad en las páginas web. Por ejemplo, cuando haces click en un botón y quieres que algo cambie en una página web, usas *JavaScript*.

Sin embargo, *JavaScript* puede ser *client-side* o *server-side*. Esto significa que podemos usar *JS* para controlar la interfaz del usuario que corre en el navegador (cliente), así como el código que corre en el servidor.

Debido esta flexibilidad y versatilidad, *JS* es el lenguaje más usado en el desarrollo de aplicaciones web en el mundo.

Ahora, vamos a aprender *JavaScript*.

### IV. Tipos de Datos

Existen seis tipos de datos en *JavaScript*:

* Número
* *String* (*cadena de caracteres* en español)
* Booleano
* *Null* (o *nulo* en español)
* *Undefined* (o *indefinido* en español)
* Símbolo (sólo disponible en *ES2015*)

#### Números

Este tipo de datos utiliza números. En *JavaScript*, los números son escritos sin comas, así que tres mil cuatrocientos setenta y cinco se escribe así:

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
'Hola, soy un string.'
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

> Cuando declaramos una variable, esta declaración (o *statement*) no tiene un valor de retorno. Por lo tanto, Node nos muestra que el resultado de esta declaración está *undefined*. No te preocupes por entender esto ahora, tal vez esto sea más claro cuando veamos *funciones*.

Para accesar el valor de esta variable, simplemente escribe el nombre de la variable en tu *REPL* y presiona `Enter`:

```js
miNombre;
undefined
```

Dado que no hemos asignado ningún valor a la variable, el valor de la misma está *undefined*.

Ahora vamos a asignar un valor a la variable usando tu nombre. Ejecuta el siguiente código en tu *REPL*:

```js
miNombre = 'Jorge';
'Jorge'
```

> El símbolo `=` se llama *assignment operator* (*operador de asignación* en español) en *JS* y nos permite asignar un valor a una variable.

También puedes asignar números a las variables. Ejecuta el siguiente código en tu *REPL*.

```js
var miEdad = 36;
undefined
```

Ahora llama tu variable en tu *REPL* y verás que el valor de la variable `miEdad` es `36`.

```js
miEdad;
36
```

#### Cómo Nombrar a Una Variable

Para poder nombrar una variable válida en *JS*, tenemos que seguir estas reglas:

* Los nombres deben iniciar con una letra, el signo de dólar o un guión bajo. No pueden iniciar con un número.
* Los nombres pueden contener cualquiera de los caracteres además de un número, pero no puedes usar un guión medio `-` o un punto `.` en el nombre.
* No puedes usar las palabras ya reservadas por *JS* como `var` o `for`.
* Todas los nombres de variables distinguen entre mayúsculas y minúsculas.

Para mantener su código legible, los programadores de *JS* siguen las siguientes convenciones. Estas no son requeridas por el lenguaje, pero son buenas prácticas:

* Siempre usa nombres que describan la información que planeas asignar a la variable, y no el tipo de información. Un buen nombre de una variable puede ser `numeroDeTelefono` en vez de `numero`.
* Usa el estilo `camelCase` para nombrar tus variables. Por ejemplo, si quieres nombrar una variable con tu nombre y apellido, puedes nombrarla así: `miNombreCompleto`.
* No utilices acentos, `ñ` u otros caracteres que no se utilicen en inglés.

#### Ejercicio

¿Cuál de estos nombres son inválidos en *JavaScript*, cuáles son válidos pero no siguen las convenciones del lenguaje, y cuales son válidos y siguen las convenciones del lenguaje? Utiliza tu *REPL* para encontrar las respuestas.

* `perro`
* `perroYGato`
* `la_vaca_loca`
* `1Tigre`
* `$miNombre`
* `mi-comida-favorita`
* `elNiñoSimón`
* `joaquinSabina`
* `el.punto`

#### Concatenando Strings

Muchas veces utilizamos diferentes variables juntas para componer un *string*. Vamos a crear dos variables, una con tu nombre y otra con tu apellido, y vamos a componer tu nombre completo.

En tu *REPL* ejecuta el siguiente código. Cambia el nombre y apellido por el tuyo:

```js
var miNombre = 'Ada';
undefined

var miApellido = 'Lovelace';
undefined
```

Ya que declaramos las dos variables y les asignamos un valor, ahora podemos usarlas para componer nuestro *string*. En tu *REPL* ejecuta el siguiente código:

```js
miNombre + ' ' + miApellido;
'Ada Lovelace'
```

También puedes asignar el resultado de esta operación a una variable nueva. En tu *REPL* ejecuta el siguiente código:

```js
var miNombreCompleto = miNombre + ' ' + miApellido;
undefined
```

Ahora vamos a accesar el valor de la variable `miNombreCompleto`. En tu *REPL* ejecuta el siguiente código:

```js
miNombreCompleto;
'Ada Lovelace'
```

También puedes concatenar variables con números y *strings*. *JavaScript* transforma los numeros en *strings* para poderlos concatenar en un *string* nuevo.

En tu *REPL* ejecuta el siguiente código:

```js
var miNumeroFavorito = 2;
undefined

var miAnimalFavorito = 'lobo';
undefined

miNumeroFavorito + ' ' + miAnimalFavorito + 's';
'2 lobos'
```

A partir de *ES2015* puedes usar *template literals* para insertar valores en un *string* fácilmente. A este método se le llama *string interpolation*. Para insertar variables usando *template literals*, tienes que crear tu *string* usando *backticks* y `${nombreDeVariable}` en donde quieras insertar tus valores.

En tu *REPL* ejecuta el siguiente código:

```js
`${miNumeroFavorito} ${miAnimalFavorito}s`;
'2 lobos'
```

### V. Expresiones y Declaraciones

En *JavaScript* una **expresión** es una instrucción en tu programa que regresa un valor.

En tu *REPL* escribe las siguientes expresiones:

```js
2 + 2;
2

'Ada';
'Ada'

1 - 3;
-2

4;
4

'María' + ' ' + 'Pérez';
'María Pérez'
```

Cómo puedes ver, en cada uno de las expresiones, el *REPL* nos da un valor de regreso.

Una *declaración* (*statement* en inglés) es una instrucción en tu programa que realiza una acción. Estas acciones pueden contener *expresiones* que regresen un valor, pero esto no es necesario. Cuando las *declaraciones* no contienen una *expresion* que regrese un valor, *Node* nos dirá que el valor de regreso está *undefined*.

En tu *REPL* escribe las siguientes *declaraciones*:

```js
var miCiudadNatal = 'Monterrey';
undefined

var miEdad = 1981 - 2017;
undefined

var miPais = 'México';
undefined

var miHeladoFavorito = 'Chocolate';
undefined
```

#### Ejercicio

¿Cuál de las siguientes líneas de código es una *expresión* y cuál es una *declaración*? Utiliza tu *REPL* para encontrar las respuestas.

* `1 + 5;`
* `"Alan Turing";`
* `var miNombre = "Juan";`
* `"Yo tenía " + 10 + " perritos.";`
* `var elNombreDeMiPapa = "Lord Byron";`

> Probablemente te has dado cuenta que cada vez que escribimos una instrucción en nuestro código al final escribimos este símbolo `;` (*semicolon* en inglés). Esto le dice a *JS* que la instrucción a finalizado. El escribir el símbolo `;` al final de nuestra instrucción es opcional. Sin embargo, la mayoría de los desarrolladores de *JS* lo incluyen para ser más explícitos en su código.

### VI. Operadores

Las expresiones utilizan **operadores** para realizar operaciones que regresen un valor. Hay cinco tipos básicos de operadores en *JS*:


1. [Assignment Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Assignment_operators), los cuáles se usan para asignar un valor a una variable. Por ejemplo: `var color = 'magenta';`;
2. [Arithmetic Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Arithmetic_operators), los cuáles se usan para realizar operaciones matemáticas básicas. Por ejemplo: `var miSuma = 2 + 2;`;
3. [String Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#String_operators), los cuáles se usan para combinar *strings*. Por ejemplo: `var saludo = ¡Hola!' + ' ' + 'Mucho gusto.';`
4. [Comparison Operadores](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Comparison_operators), los cuáles se utilizan para comparar dos valores y regresan un valor *booleano*, es decir, `true` o `false`. Por ejemplo, si escribes este código `3 > 5;`, el valor de retorno es `false`.
Operadores Lógicos, que combinan expresiones y retornar un valor
5. [Logic Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Logical_operators), los cuáles se utilizan para evaluar condiciones lógicas en varias expresiones. Estos regresan un valor *booleano*, es decir, `true` o `false`. Por ejemplo, la expresión `5 > 1 && 3 > 2;` regresa el valor `true`.

> Además de estos cinco tipos básicos de operadores, *JS* tiene otros cinco tipos de operadores. No te preocupes mucho por ells. Puedes aprender más de esto [aquí](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators).

### VII. Condicionales

Los **condicionales** (o *conditionals* en inglés) nos permiten controlar el flujo de un programa. La estructura básica de un condicional dice que si una condición de cumple, una parte del programa se ejecuta, de lo contrario, otra parte del programa se ejecuta en su lugar.

La estructura básica de una *condicional* es la siguiente:

```js
if (expression) {
  statement;
} else {
  statement;
}
```

Si la expresión regresa el valor de `true`, es decir, si evalúa a `true`, entonces el *statement* de esta condición se ejecutará. De lo contrario, si la expresión evalúa a `false`, la sentencia no se ejecutará.

Usualmente, la expresión del condicional tiene un operador lógico para realizar una comparación que evalúa a `falso` o `verdadero`.


Algunos ejemplos de expresiones que podemos usar para una condicional son los siguientes:

* `miNumero < 5`
* `miCiudad === 'Monterrey'`
* `estaCansado === true`


Ahora, veamos un ejemplo de un condicional:

```js
var galleta = 'chocochispas';

if (galleta === 'chocochispas') {
  console.log('¡Esta es una galleta de chocochispas!');
} else if (galleta === 'animalitos') {
  console.log('¿Qué es esto? Ve al OXXO y tráeme chocochispas.');
} else {
  console.log('Seguro quieres una galleta de chocochispas.');
}
```

En el ejemplo anterior, la expresión `galleta === 'chocochispas'` evalúa a `true` por lo que el mensaje que se imprime es `¡Esta es una galleta de chocochispas!`.

Veamos otro ejemplo:

```js
var horasDeSueno = 8;

if (horasDeSueno < 6) {
  console.log('Necesito cafeína, urgente.');
} else {
  console.log('¡Me siento súper bien!');
}
```

En este último ejemplo, dado que el valor de la variable `horasDeSueno` es igual a `8`, la expresión `horasDeSueno < 6` evalúa a `false`. Por lo tanto, el mensaje que se imprime es `¡Me siento súper bien!`.

### VIII. Ejecutando Programas desde Archivos

Hasta ahora hemos escrito programas en el *REPL* de *Node*. Aunque normalmente usamos el *REPL* para experimentar y tratar de resolver problemas en nuestro código (o `bugs`), la mayoría de las veces escribimos programas en archivos de texto que corremos desde la terminal y que podemos modificar en nuestro editor de texto, en este caso `Atom`.

Vamos a crear un archivo en nuestra terminal para escribir nuestro programa. En tu terminal, ejecuta el siguiente comando:

```bash
$ touch MiPrograma.js
```

Los archivos en *Node* se nombran utilizando `upper CamelCase` y tienen la extensión `.js`. Ahora vamos a abrir nuestro archivo con nuestro editor de texto ejecutando el siguiente comando:

```bash
$ atom MiPrograma.js
```

> Los archivos donde se escriben los programas son sólo archivos de texto que tu computadora procesa mediante *interpreters* (o *interpretadores*). Estos interpretadores toman el texto de los archivos y lo traducen en instrucciones que tu computadora puede ejecutar. La extensión de los archivos tampoco importa, pero por convención usamos la extension *js* para archivos de *JavaScript*. Otros lenguajes tienen sus propias convenciones para nombrar las extensiones de los archivos.

Una vez abierto tu archivo en tu editor de texto, escribe el siguiente código y guarda los cambios:

```js
console.log('¡Hola, mundo!');
```

Ahora, en tu terminal, ejecuta tu programa con el siguiente comando en tu terminal:

```bash
$ node MiPrograma.js
¡Hola, mundo!
```

También puedes escribir un programa más complejo. En el archivo de tu programa, borra el código anterior, y escribe lo siguiente:

```js
var misPerritos = 4;

if (misPerritos < 5) {
  console.log('Me hacen falta más perritos.');
} else {
  console.log('¡Tengo muchos perritos!');
}
```

Después de hacer esto, ejecuta tu programa con el siguiente comando en tu terminal:

```bash
$ node MiPrograma.js
```

#### Ejercicio

Para practicar lo que hemos visto, haz lo siguiente:

1. Desde tu terminal, crea un archivo llamado `MiEdad.js`.
2. En el archivo `MiEdad.js` escribe un programa que tenga dos variables, una para tu año de nacimiento y otra para el año actual.
3. El programa debe calcular tu edad actual restando las dos variables.
4. Al ejecutar tu programa desde tu terminal, el programa debe imprimir `"Tengo <tus años> años."`.
