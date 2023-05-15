# Estilar listas

Las listas traen por defecto unos estilos predefinidos que son `padding-left`, `margin-top` y `margin-bottom`, si queremos resetearlos los tendremos que poner a 0.

## Viñetas personalizadas

Por defecto los navegadores muestran las listas con un pequeño círculo negro, pero esto lo podemos modificar de varias formas, la que nos ofrece CSS es la propiedad `list-style-type` y los valores disponibles son:

- Valores gráficos
  - disc
  - circle
  - square
- Valores numéricos
  - decimal
  - decimal-leading-zero
  - lower-roman
  - upper-roman
  - armenian
  - georgian
- Valores alfanuméricos
  - lower-greek
  - lower-latin
  - upper-latin
  - lower-alpha
  - upper-alpha

Por último si queremos eliminar las viñetas podemos usar el valor `none`

## Colocación de las viñetas

Para modificar dónde se coloca el texto respecto a la viñeta, tenemos la propiedad `list-style-position`

Esta propiedad tiene los valores `outside` e `inside`, y sólo se aprecia si el elemento de lista tiene más de una línea de contenido.

## Viñetas personalizadas

Si queremos personalizar las viñetas con una imágen o un icono tenemos la propiedad `list-style-image` que recibe el valor `url()` con la ruta de la imagen.

Si necesitamos adaptar la imagen o aplicarle estilos extra la mejor opción es utilizar un `::before` con la propiedad `background-image`, de esa forma tendremos un control total sobre la imagen.

## Pseudo elemento ::marker

Este pseudo elemento es el equivalente a la propiedad `accent-color` pero en listas.
Si queremos personalizar el color o el tamaño de la fuente de la viñeta podemos utilizar este pseudo elemento.

No se aplica a la lista, se aplica como selector independiente, es decir, no pondremos `.list::marker`, si no que pondremos directamente `::marker` y aplicaremos los estilos.
