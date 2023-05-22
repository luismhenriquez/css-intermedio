# flexbox

Flexbox es un módulo más de CSS, mucha gente piensa que flexbox es algo aparte de CSS y no es así.

Lo más importante que tenéis que saber sobre flexbox es que consiste en un sistema de layout en 2 ejes, un eje principal al que llamaremos `main-axis` y un eje secundario al que llamaremos `cross-axis`

![flexbox-axis](/84-intro-flexblox/flexbox-axis.png)

Lo segundo que tenéis que recordar es que flex trabaja con un sistema de padres e hijos, es decir, un contenedor que tenga hijos, al contenedor lo llamaremos `flex-container` y a los hijos `flex-items`, un hijo puede ser a su vez contenedor de otros hijos y ser a la vez `flex-item` y `flex-container`

Flexbox funciona a través de la propiedad `display`, y para crear un contenedor flexible pondremos: `display: flex` o `display: inline-flex`, dependerá de si queremos un contenedor de bloque o uno de línea

## flex-direction

Esta es la propiedad que controla el flujo de los hijos sobre el eje principal. Por defecto, su valor es `row`, es decir fila, por eso los elemento se colocan uno al lado del otro. Otro valor que acepta es `column` y los elementos se apilarán en columna.

También tenemos las opciones `row-reverse` y `column-reverse`, con estas opciones invertimos el flujo del contenido, con `row-reverse` el eje principal irá de derecha a izquierda y con `column-reverse`, el eje principal irá de abajo arriba

## flex-wrap

Con esta propiedad controlaremos qué pasa con el contenido si se desborda del contenedor.

Por defecto su valor es `no-wrap` lo que hará que los elementos se encojan para entrar en el contenedor, pero si queremos evitar esto tenemos 2 valores que podemos usar.

- wrap: Permitirá que el contenido que se desborde salte de línea,

- wrap-reverse: Hace que el contenido salte de línea en la dirección opuesta al main axis, hacer esto cambiará la dirección del eje secundario.

## flex-flow

Esto es un shorthand que engloba `flex-direction` y `flex-wrap`.

```
    body{
        flex-direction: column;
        flex-wrap: wrap
    }

     // Su equivalente es:

    body{
        flex-flow: column wrap;
    }
```

## justify-content

Con esta propiedad podremos alinear los elementos en el `main-axis`, esto no significa horizontalmente, significa que los podremos alinear en la dirección y orientación del eje principal.

El valor por defecto es `flex-start (start)`, es decir, los elementos se colocarán al principio del eje principal, pero tenemos más valores posibles.

- center: Los elementos se colocan en el centro del eje principal.

- flex-end (end): Los elementos se colocan al final del eje principal.

- space-between: Los elementos se colocan con el mismo espacio entre ellos, colocando el primer hijo al principio del eje y el último al final del eje

- space-around: Los elementos se colocan con el mismo espacio entre ellos, pero cada elemento tendrá la misma separación por los lados, ésto ocasiona que el primer y último elemento tengan menos separación.

- space-evenly: Los elementos se colocan con el mismo espacio entre ellos, y cada elemento tendrá la misma separación tanto entre ellos como el primero y el último.

## align-items

Con esta propiedad vamos a poder alinear los elementos en el `cross-axis` o eje secundario.

El valor por defecto es stretch, que hace que los elementos se estiren para ocupar todo el espacio disponible, siempre y cuando no tengan un `height` o `width` declarado, dependiendo de la dirección del `main-axis`. No conocer esto es el motivo principal por el que se deforman las imágenes cuando usamos flexbox.

Aparte de `stretch` tenemos más valores disponibles

- flex-start (start)
  Coloca los elementos al principio del `cross-axis`
- flex-end (end)
  Coloca los elementos al final del `cross-axis`
- center
  Coloca los elementos en el centro del `cross-axis`

- baseline
  Todos los elementos flexibles son ajustados de modo que sus bases queden alineadas.

## align-content

Esta propiedad funciona de una forma similar a `justify-content`, sólo la podremos utilizar junto con `flex-wrap` cuando los elementos generen varias líneas. El valor por defecto es `stretch` al igual que en `align-items` pero tenemos disponibles los mismos valores que en `justify-content`:

- flex-start (start): Los elementos se colocan al final del eje secundario.

- center: Los elementos se colocan en el centro del eje secundario.

- flex-end (end): Los elementos se colocan al final del eje secundario.

- space-between: Los elementos se colocan con el mismo espacio entre ellos, colocando el primer hijo al principio del eje y el último al final del eje

- space-around: Los elementos se colocan con el mismo espacio entre ellos, pero cada elemento tendrá la misma separación por los lados, ésto ocasiona que el primer y último elemento tengan menos separación.

- space-evenly: Los elementos se colocan con el mismo espacio entre ellos, y cada elemento tendrá la misma separación tanto entre ellos como el primero y el último.

## column-gap

Esta propiedad nos permite establecer espaciado entre columnas

## row-gap

Esta propiedad nos permite establecer espaciado entre filas

## gap

Esta propiedad nos permite establecer espaciado entre filas y columnas, el primer valor será para filas y el segundo para columnas, si sólo ponemos un valor, se aplicará a filas y columnas

## flex-grow

Esta propiedad nos permite controlar el factor de crecimiento de un elemento, es decir, del espacio restante disponible, cuanta parte le corresponde a él.

El valor de `flex-grow` tiene que ser un número positivo y ese valor será el factor de creciemiento.

El valor por defecto de `flex-grow` es 0

Veamos un ejemplo:

Si tenemos un contenedor de 1000px con 3 elementos de 250px dentro.

El espacio restante disponible son 1000px menos el espacio que ocupan los elementos en total, 750px.

1000 - 750 = 250px de espacio disponible.

El cálculo que hace el navegador es 250 dividido entre la suma total de los valores de `flex-grow`

Si tenemos un `.item` con un `flex-grow:1` la operación será `250 / 1 = 250`, es decir, el item con `flex-grow:1` crecerá 250px.

## flex-shrink

Con esta propiedad vamos a controlar el factor de reducción de los elementos, funciona a través del mismo algoritmo que `flex-grow`, la diferencia es que en lugar de utilizar el espacio restante disponible, utiliza el espacio que falta entre el tamaño total de los elementos y el espacio disponible

El valor de `flex-shrink` tiene que ser un número positivo y ese valor será el factor de reducción.

El valor por defecto de `flex-shrink` es 1, por eso los elementos encogen automáticamente cuando no caben.

Pongamos un ejemplo para que lo veaís con números:

Tenemos un contenedor de 1000px con 5 elementos de 200px dentro, en este contexto los elementos caben perfectamente.

Si ahora reducimos el espacio disponible a 700px los elementos se ven forzados a encogerse para caber en el contenedor, si hicieramos un cálculo de cuanto se han reducido, la suma total nos daría 300px, los elementos ocupan 1000px totales y se tienen que ajustar a los 700px actuales, 1000 - 700 = 300px

El cálculo que hace el navegador es el mismo que cuando trabajamos con `flex-grow`, la diferencia es que ahora para hacer el cálculo usará esos 300px que faltan para conseguir que todos los elementos puedan caber sin reducirse.

Sabiendo esto, la operación sería 300 / 5, recordad que `flex-shrink` tiene un valor por defecto de 1 y que tenemos 5 items, por lo cual cada item se habrá reducido en 60px

## flex-basis

Esta propiiedad nos sirve para especificar cual es el tamaño inicial de un elemento flexible en el `main-axis`, si utilizamos `width` o `height` prevalecerá el valor de `flex-basis` que le corresponda dependiendo de la orientación del `main-axis`

## order

Esta propiedad nos permite alterar el orden en el que se dibujarán los elementos, es MUY IMPORTANTE que recordéis que NO CAMBIA el flujo del HTML, sólo la parte visual, eso significa que propiedades como `:nth-child()` funcionarán exáctamente igual aunque visualmente los elementos aparezcan en otro orden.

El valor inicial de `order` es 0, y acepta números enteros positivos y negativos, visualmente los elementos se colocarán en orden ascendente en el flujo del `main-axis`

## align-self

Esta propiedad nos va a permitir alinear un elemento de forma independiente en el `cross-axis`. Es una propiedad de los `flex-items`
