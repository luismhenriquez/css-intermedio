# Transform

La propiedad transform nos permite transformar la posición, la rotación, la escala y el sesgo (inclinación) de un elemento.

Esta propiedad nos permite trabajar en los 3 ejes de un elemento, X horizontal, Y vertical, Z profundidad.

Los valores de transform se aplican desde el centro del elemento por defecto, pero podemos modificarlo con la propiedad `transform-origin`

Como último detalle, el uso de la propiedad transform SIEMPRE genera un contexto de apilamiento nuevo.

## Translate

El primer valor de la propiedad transform que vamos a ver es `translate`, este valor nos va a permitir mover un elemento en cualquiera de sus 3 ejes, esta propiedad NO sustituye a position, nos permite mover un elemento igual que position, pero con algunas ventajas y desventajas que iremos viendo, dependiendo de la situación será más recomendable usar una u otra.

`Translate` lo podemos utilizar como shorthand poniendo translate(ejeX, ejeY) o podemos mover en un eje concreto usando translateX(), translateY()

Los valores que admite esta función pueden ir en cualquier medida válida en CSS, aunque existe una pequeña particularidad si el valor se lo ponemos en `%`
Cuando usamos `%` junto con `translate` la medida no se aplica respecto al contenedor padre, como estamos acostumbrados, si no que usará como valor la propia medida del elemento.

También podemos usar el valor translateZ() para mover el elemento en el eje Z y también existe una variante de translate que es `translate3D` que permite agrupar los 3 ejes, de esto hablaré más adelante en la sección cuando hablemos de transformaciones 3D

## Rotate

Este valor nos va a permitir rotar un elemento alrededor de su `transform-origin` sobre cualquiera de los 3 ejes, el valor de rotación lo podemos poner en grados (20deg) o en número de vueltas (.5turn), también existe la opción de poner la rotación en grados radianes o radianes pero apenas se utiliza esa forma.

Si usamos la función rotate por defecto rotaremos el elemento sobre el eje Z, `rotate(45deg)` equivale a `rotateZ(45deg)`

Si queremos rotar sobre alguno de los otros dos ejes, utilizaremos `rotateX()` o `rotateY()`

## Perspective

Al rotar un elemento sobre el eje X o el eje Y, es habitual que buscamos un efecto 3D que sólo con rotate no podemos conseguir, para ello existe la propiedad `perspective`, esta propiedad nos permite modificar la distancia a la que se encuentra el usuario del elemento, lo más común es establecer una distancia en píxeles, y dependiendo del tamaño del elemento pondremos más o menos distancia.

Es muy importante recordar que cuando usamos la propiedad `perspective` no se aplica sobre el elemento, si no que lo aplicaremos sobre el contenedor del elemento.

Si queremos aplicar perspective a un elemento que no tiene padre, deberemos utilizar la función `perspective()` como valor añadido al transform, y este se recomienda ponerlo en primer lugar antes del resto de transformaciones.

También podemos modificar la posición en la que se encuentra la perspectiva, por defecto será el centro, pero podemos usar la propiedad `perspective-origin` para modificar la posición.

Para modificar la posición podemos usar palabras claves (top, bottom, left y right) o podemos establecer los valores con cualquier medida válida en CSS, lo más común es establecerlo en píxeles o en porcentaje

Cuando utilizamos palabras clave el eje va implícito en la palabra clave, pero si utilizamos valores numéricos tenemos dos opciones:

```
perspective-origin: x-position;

perspective-origin: x-position y-position;
```

## Scale

Este valor nos permite escalar un elemento en los ejes X e Y.

Podemos escalar los 2 ejes simultáneamente usando la función `scale()`, si sólo ponemos un valor se usará ese valor para los dos ejes y si ponemos dos valores el primero será el eje X y el segundo el eje Y

Si queremos escalar independientemente tenemos las funciones `scaleX()` y `scaleY()`.

El valor por defecto de la escala es 1, si ponemos `scaleX(1)` no veremos ningun cambio, para escalar usaremos ese valor como referencia, por lo que `scaleX(2)` hará que el elemento mida el doble de ancho y si pusieramos `scaleX(0.5)` el elemento medirá la mitad de ancho.

Un error muy común es escalar un elemento que contiene más elementos, eso hará que los elementos hijos se deformen, para solucionarlo hay que aplicar la escala opuesta a los hijos.

## Skew

Con skew podemos sesgar un elemento en el eje X o en el eje Y.

Al igual que en el resto de funciones tenemos `skew()` como shorthand.

```
skew(x-axis)
skew(x-axis, y-axis)
```

También tenemos `skewX()` y `skewY()` para sesgar los ejes independientemente.

Para sesgar el elemento le pasamos un valor en grados para establecer el ángulo de inclinación.

## Transformaciones múltiples

Se pueden aplicar varias transformaciónes a un mismo elemento, pero hay que recordar que las transformaciones se aplicarán en el orden que se declaren.

Cuando mezclamos `rotate` y `translate` los ejes cambian de sitio y es algo que causa mucha confusión al inicio, esto sólo afecta a los ejes dentro de transform, los valores de position no se ven afectados pero sí los del box model.

Tenemos una alternativa en forma de shorthand para agrupar todas las transformaciones.

El cálculo se hace multiplicando matrices que representan un sistema de coordenadas.

Aquí os dejo un link con toda la explicación
https://dev.opera.com/articles/understanding-the-css-transforms-matrix/

Hacer el cálculo es una tarea compleja y para ello tenemos generadores de matrices.

https://angrytools.com/css-generator/transform/

## Problemas comunes al utilizar transform

- Las transformaciones NO se pueden aplicar a elementos en línea.
- Utilizar transform genera un nuevo contexto de apilamiento.
