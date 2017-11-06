---
title: Pizzatron
program: DAW
module: M1
layout: main
---

# Pizzatron

### I. Objetivos de Aprendizaje

Después de este proyecto, los estudiantes podrán:

* Crear una aplicación *CLI* en JavaScript y Node.js
* Utilizar *control flow* para controlar el flujo del programa
* Seguir requerimientos básicos
* Entender la interface del módulo `readline`
* Uso básico de *promises*

### II. Descripción

Vas a organizar una fiesta en tu casa, y piensas invitar a tus amigos. Quieres ordenar varias pizzas pero no sabes cuantas ordenar. La veces anteriores haz pedido mucha pizza y al final de la noche sobran muchas rebanadas. Sin embargo, ahora que sabes programar, quieres crear un programa en tu terminal que te permita calcular cuanta pizza ordenar.

### III. Requerimientos

Para satisfacer los requerimientos del proyecto, debes hacer lo siguiente debes construir una aplicación *CLI* que puedas ejecutar desde tu terminal usando el comando `npm start`.

#### Implementación Básica

Esta aplicación deberá hacer lo siguiente:

1. Al correr este programa, la aplicación deberá mostrar un mensaje de bienvenida.
2. Después de mostrar el mensaje de bienvenida, la aplicación deberá pedirte el número de personas que van a asistir a la fiesta, y mostrarte un mensaje confirmando los datos de entrada del usuario.
3. Después, la aplicación deberá pedirte el número de rebanadas de pizza que se comerán por persona. Para la implementación básica, la pizza tendrá **ocho rebanadas**.
4. Si el número de pizzas no es un entero, tienes que redondear el número de pizzas hacia arriba. Por ejemplo, si tu cálculo del número de pizzas es 5.1, tienes que redondearlo a 6. El resultado siempre debe ser un entero.
5. Al terminar el programa, e

Ejemplo:

```bash
** Bienvenido a Pizzatron **
¿Cuántas personas van a venir a tu fiesta?
27
27 personas van a venir a tu fiesta.

¿Cuántas rebanadas de pizza se come cada persona?
4

Tienes que pedir 14 pizzas medianas para tu fiesta.
```

#### Extensiones

##### Tamaños de Pizza

Además de los requerimientos básicos, el programa calculará los tamaños óptimos de pizza a pedir. Para esto toma en cuenta que la pizza chica tiene **seis rebanadas**, la mediana **ocho rebanadas** y la grande **diez rebanadas**.

Por ejemplo, utilizando el ejemplo anterior:

```bash
** Bienvenido a Pizzatron **
¿Cuántas personas van a venir a tu fiesta?
27
27 personas van a venir a tu fiesta.

¿Cuántas rebanadas de pizza se come cada persona?
4

Tienes que pedir 10 pizzas grandes y 1 pizza mediana para tu fiesta.
```

##### Calculador de Precio

Además de los requerimientos básicos, el programa calculará el costo total a pagar, cuánto le toca de propina al repartidor y cuánto le toca pagar a cada quien. El precio por pizza y el resultado del precio por persona, deberá estar redondeado a dos decimales.

Por ejemplo, utilizando el ejemplo anterior:

```bash
** Bienvenido a Pizzatron **
¿Cuántas personas van a venir a tu fiesta?
27
27 personas van a venir a tu fiesta.

¿Cuántas rebanadas de pizza se come cada persona?
4

¿Cuánto cuesta cada pizza?
125

¿Qué porcentaje de la cuenta le van a dar de propina al repartidor?
10

Tienes que pedir 14 pizzas medianas para tu fiesta. Cada invitado tiene que pagar 71.30 pesos.
```

### IV. Criterios de Evaluación

#### Funcionalidad

Valor: 60 por ciento

1. El estudiante no tiene un programa funcional.
2. El estudiante tiene un programa funcional y no completó la implementación básica.
3. El estudiante tiene un programa funcional y completó la implementación básica.
4. El estudiante tiene un programa funcional, completó la implementación básica, y terminó una extensión.
5. El estudiante tiene un programa funcional, completó la implementación básica, y terminó dos extensiones.

#### Estructura

Valor: 20 por ciento

1. El estudiante tiene un código complicado y difícul de entender.
2. El estudiante utiliza funciones en alguna parte de su implementación pero no en otras.
3. El estudiante separa las funcionalidades de su código en funciones claramente definidas.
4. El estudiante separa las funcionalidades de su código en funciones claramente definidas y elimina la repetición de su código.
5. El estudiante crea objetos y módulos claramente definidos y elimina la repetición de su código.

#### Formato

Valor: 20 por ciento

1. El estudiante tiene un estilo inconsistente y variables no descriptivas.
2. El estudiante tiene un estilo consistente en su mayoría.
3. El estudiante tiene un estilo consistente.
4. El estudiante tiene un estilo consistente, y variables y funciones descriptivas.
5. El estudiante tiene un estilo consistente, variables y funciones descriptivas, y sigue una guía de estilo.

### V. Entrega

Para entregar esta tarea, deberás crear un repositorio llamado `pizzatron` en tu cuenta de *Github* y tener tu implementación ahí. Tu repositorio deberá tener un archivo `README.md` que explique como descargar tu programa y ejecutarlo en la computadora de tu evaluador.

Al momento de tu evaluación, deberás darle el `url` de tu repositorio a tu evaluador.
