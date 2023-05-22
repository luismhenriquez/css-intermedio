# grid

CSS Grid es un modelo de layout (geometría de los elementos) , al igual que `flex` se creó para ayudar con la maquetación en diferentes dispositivos, pero la gran diferencia respecto a `flex` es que `grid` funciona con un sistema bidemensional, mientras que flex es unidimensional.

Esto no significa que haya que elegir entre `flex` o `grid`, ese es uno de los mayores errores que tiene la gente cuando empieza con css, pensar que hay módulos de CSS que sustituyen a otros, y es muy importante que recordéis que esto no es así, no existe esa famosa batalla en redes sociales de `flex` vs `grid`, cada cual se usa en la parte de la web que hace falta y en la mayoría de las ocasiones se usarán en conjunto.

Al igual que `flex`, `grid` también trabaja con un sistema de padres e hijos, tendremos el `grid-container` como padre y los `grid-items` como hijos. También es posible que un `grid-item` sea un `grid-container` aunque esta situación no se da tan a menudo como en `flexbox`.

## Terminología y uso

Hay cuatro conceptos asociados a grid que hace falta conocer para entender cómo funciona internamente grid:

- Grid-line: Cada una de las líneas que se colocan a los lados de las columnas y filas, son líneas virtuales que crea el navegador.

- Grid-track: Cada una de las filas y columnas de nuestro grid.

- Grid-cell: Cada una de las celdas donde podemos poner contenido.

- Grid-area: Agrupación de grid cells que no formen ni una fila ni una columna.

Grid se utiliza a través de la propiedad display, y al igual que en `flexbox` tenemos la opción de crear un grid de bloque con `display:grid` o un grid de línea con `display: inline-grid`

## Establecer filas y columnas

Para establecer filas y columnas tenemos dos propiedades que se le asignan al `grid-container`

Tenemos `grid-template-columns` para establecer columnas y `grid-template-rows` para establecer filas.

Como valor / valores pondremos tantos como columnas y filas queramos es decir, si queremos una grilla de 4 columnas y 3 filas pondremos 4 valores en `grid-template-columns` y 3 valores en `grid-template-rows`, los valores establecerán la medida el ancho de cada columna y el alto de cada fila.

```
  grid-template-columns: 100px 200px 150px 100px;
  grid-template-rows: 150px 100px 100px;
```

## Gap, el espacio entre tracks

Si queremos dar espaciado entre celdas tenemos la propiedad nativa `grid-gap`, pero si recordáis lo que comentamos en flexbox tenemos la propiedad `gap` que sive para todos los sitemas de layout.

Tenemos `gap` para el espaciado en filas y columnas y admite dos valores, primer valor para filas y segundo para columnas, si queremos dar un solo valor se aplicará tanto a filas como a columnas.

También existe la opción de usar `row-gap` y `column-gap` para dar la separación individualmente a filas y columnas respectivamente.

## La medida fr y auto

Esta medida sirve para que le navegador calcule automáticamente la medida de los `grid-tracks`

`fr` viene de fracción, y lo que hace el navegador es sumar el número total de fracciones que tenemos, dividirlo entre el número de filas o columnas que tenemos, y asignar a cada uno el número de fracciones que le corresponden.

```
  grid-template-columns:25% 50% 25%;
  es "equivalente" a
  grid-template-columns:1fr 2fr 1fr;
```

Es muy habitual confundir `fr` con `auto`, el comportamiento es muy distinto, cuando usamos `fr` ya hemos visto que se divide el espacio disponible, si usamos `auto` la celda tendrá únicamente el ancho que necesite el elemento

## Función repeat()

La función repeat sirve para repetir patrones de filas o de columnas.

Recibe, como mínimo, 2 parámetros, el primero será el número de filas o columnas que queremos repetir, y el segundo será la medida o medidas que queremos repetir.

Por ejemplo, si queremos 4 columnas de 100px pondremos: `grid-template-columns: repeat(4, 100px)`

Si quisiéramos un patron de 6 columnas de 100px 50px 200px 100px 50px 200px, podemos poner `grid-template-columns: repeat(2, 100px 50px 200px)`

Cuando usamos `repeat()` también podemos añadir columnas o filas antes o después `grid-template-columns: 100px repeat(2, 1fr)`

## grid-column y grid-row

Cuando trabajamos con grid, los items no tienen que estar donde se colocan por el flujo del html, si no que podemos colocarlo donde mejor nos cuadre desde el css, para ello tenemos las propiedades `grid-column-start`, `grid-column-end`, `grid-row-start` y `grid-row-end`, pero podemos usar el shorthand `grid-column` y `grid-row` para establecer en qué columna y fila empieza y termina el elemento.

Si tenemos una grilla, por ejemplo, de 4 columnas y 2 filas podemos colocar cualquier elemento donde queramos estableciendo en qué columna y fila queremos que comience y termine.
Si queremos que un elemento empiece en la `grid-line` 2 y llegue hasta la 4 sólo tendremos que ponerle `grid-column-start: 2` y `grid-column-end: 4`, lo podemos simplificar con el shorthand `grid-column: 2 / 4` separando los valores con una `/`

Si queremos indicarle a un elemento que ocupe varias columnas no es necesario que contemos las `grid-lines`, tenemos la opción de usar la palabra clave `span` para indicarle el número de columnas o filas que queremos que ocupe.

```
  grid-column:2 / 6;
  Es equivalente a:
  grid-column: 2 / span 4
```

En el caso de que queramos que ocupe todas las columnas o filas disponibles podemos usar como valor `-1` para que llegue hasta la última `grid-line` disponible.

## Grid áreas

Para colocar contenido dentro de nuestro grid también tenemos la opción de definir áreas, y para darle tamaño a nuestro grid seguiremos usando `grid-template-columns` y `grid-template-rows`

```
  grid-template-areas:'header header header'
                      'aside main main'
                      'footer footer footer'
```

En este ejemplo estamos diciendo que nuestro layout tiene 3 columnas y 3 filas, cada fila irá encerrada entre comillas y cada nombre que pongamos separado por espacios será una columna.

Si el nombre de la columna se repite podemos usar `.` o `-` para indicar que esa columna tiene el mismo nombre.

Es muy importante mantener la coherencia entre filas y columnas, no podemos tener una fila con 3 columnas y otra con 4, todas las filas deben tener el mismo número de columnas.

Después para colocar los elementos sólo tendremos que poner `grid-area: nombre en el template`

## Grids dinámicos

Hasta ahora hemos trabajado con medidas fijas y fr pero no tenemos forma de establecer el número de columnas o filas de forma dinámica sin usar `media queries` pero grid nos da una serie de palabras clave para que sea el navegador el que calcule las medidas y el número de tracks en función del espacio disponible.

- Tamaño de los items dinámico
  - min-content: ocupará el menor espacio necesario
  - max-content: Es el equivalente a `auto` ocupará lo maximo necesario
  - fit-content(max): Es una mezcla entre min-content y max content. Como parámetro le dirémos cual es su máximo, y como mínimo será `min-content`
- Tamaño de los tracks dinámico
  - minmax(min, max): Es una función que nos permite establecer el mínimo y máximo tamaño de los grid tracks.
- Autogeneración de tracks

  Estas opciones sólo se pueden usar con `repeat()`, ya que sustituyen al número de tracks.

  - auto-fill: Genera tracks vacíos de las medidas establecidas para rellenar el espacio restante.
  - auto-fit: Expande o hace saltar de línea los items en función del espacio disponible.

## Alineamiento en grid

Alinear en grid suele causar problemas al inicio, ya que tenemos que pensar en 2 ejes y en 2 referencias distintas, los `grid-tracks` y los `grid-items`

Para alinear los `grid-tracks` tenemos las propiedades `justify-content` para el eje horizontal y `align-content` para el eje vertical, ambas admiten los mismos valores que en flexbox, el funcionamiento y el algoritmo que usan para colocar los elementos es exactamente el mismo. Estas propiedades nos sirven para alinear los `grid-tracks` respecto al `grid-container`.

Por otro lado para alinear los `grid-items` tenemos las propiedades `justify-items` y `align-items`, estas propiedades nos sirven para alinear los `grid-items` respecto al `grid-track`.

Estas propiedades admiten los valores: `stretch`, que es el valor por defecto, `start`, `center`, `end` y `baseline`

## Grid flow

Cuando trabajamos con grid los items se colocan por defecto de izquierda a derecha empezando desde arriba y generando filas en función del número de columnas, 6 items ordenados en columnas de 3 generarán 2 filas, pero esto es algo que podemos modificar a traves de la propiedad `grid-auto-flow`, por defecto tiene el valor `row` pero podemos establecerlo en `column` para que los items se coloquen de arriba abajo generando columnas en lugar de filas.

También es común que se generen más tracks de los que hemos establecido en un comienzo, los que hemos establecido es lo que se denomina grid explícito, y el resto de tracks que crea el navegador de forma automática es el grid implícito.

Para controlar las medidas de los tracks impícitos tenemos las propiedades `grid-auto-columns` y `grid-auto-rows`

Cuando tenemos items que ocupan 2 o más tracks grid sigue manteniendo el orden de colocación, lo que ocasiona que queden huecos vacíos, para que grid intente rellenar esos huecos tenemos el valor `dense`
