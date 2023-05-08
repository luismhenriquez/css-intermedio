# Background

La propiedad background sirve para establecer el contenido y/o el comportamiento del fondo de un contenedor.

El fondo de un elemento es el tamaño total del mismo sin incluir el margen, es decir, el contenido, el padding y el borde.

## Background color

Esta propiedad aplica colores sólidos al fondo en un elemento. Admite cualquier código de color válido en css, rgb; hsl; hexadecimal y keywords.

## Background image

Esta propiedad sirve para establecer imágenes o degradados al fondo de un elemento.

No es incompatible con background-color, pero hay que tener en cuenta que la imagen o el degradado siempre se colocará por encima del color de fondo.

Para usar una imagen usamos la función url() y dentro pondremos la ruta donde tenemos nuestra imagen.
Podemos utilizar cualquier formato de imagen válido en HTML.

`background-image(./imagen.jpg)`

## Background repeat

Esta propiedad controla si la imagen se repetirá para rellenar todo el fondo del contenedor. Los valores que admite esta propiedad son:

- repeat: Valor por defecto
- repeat-x: Repite la imagen horizontalmente
- repeat-y: Repite la imagen verticalmente
- no-repeat: No repite la imagen

## Background position

Esta propiedad nos permite mover una imagen de fondo dentro de su contenedor, por defecto sus valores son 0 0, que corresponden a la esquina superior izquierda, el primer valor corresponde al eje x y el segundo al eje y.

Para mover la imagen podemos usar cualquier medida válida en css, pero si usamos porcentajes hay algo a tener en cuenta, si ponemos `background-position: 100% 0` la imagen se colocará a la derecha, alineará el último pixel de la imagen con el último pixel del contenedor.

También tenemos palabras clave que hacen más facil el control de la posición

- top: equivale a 0% verticalmente
- right: equivale a 100% horizontalmente
- bottom: equivale a 100% verticalmente
- left: equivale a 0 horizontalmente
- center: equivale a 50% tanto horizontal como verticalmente

Al utilizar palabras clave da igual poner `top center` que `center top`, esto es algo que sólo pasa al usar las palabras clave, al usar valores numéricos hay que respetar el orden.

## Background size

Esta propiedad nos permite controlar el tamaño de la imagen de fondo, por defecto su valor es `auto` y deja que el navegador calcule las medidas en función del tamaño real de la imagen y la relación de aspecto para no deformar la imagen.

Si queremos establecer la medida manualmente tenemos varias formas de hacerlo.

- Un valor: Se aplicará al ancho de la imagen
- Dos valores: El primero será el ancho de la imagen y el segundo el alto de la imagen.
- Palabras clave:
  - cover: Con este valor la imagen cubrirá el contenedor completo sin deformarse, pero cortando la imagen si fuera necesario.
  - contain: Con este valor la imagen se agrandará todo lo posible hasta que el ancho o el alto sea de las mismas medidas que las del contenedor.

## Background attachment

Esta propiedad especifica cómo se comportará el fondo cuando hagamos scroll, hay tres valores que podemos utilizar:

- Scroll: Es el valor por defecto
- Fixed: Hace que el fondo quede fijado al viewport, por lo que aunque hagamos scroll el fondo no se moverá.
- Local: Si tenemos contenido con scroll en un contenedor hará que la imagen de fondo se mueva junto con el scroll.

## Background origin

Esta propiedad define en qué zona del box-model se empieza a pintar el fondo.

Esta propiedad sólo funciona cuando usamos background-image.

Tenemos 3 valores posibles.

- border-box: El fondo se empieza a pintar desde la esquina izquierda superior del contenedor
- padding-box: Este es el valor por defecto. El fondo se empieza a pintar desde la esquina superior izquierda de la zona que corresponda al padding
- content-box: El fondo se empieza a pintar desde la esquina superior izquierda de la zona que corresponda al contenido

## Background clip

Esta propiedad define en qué zona del box-model se pinta el fondo. Tenemos 3 valores posibles.

- border-box: Este es el valor por defecto, rellenará todo el box-model
- padding-box: rellenará desde el contenido hasta la parte que corresponda al padding
- content-box: rellenará sólo la parte que corresponda a contenido

## Background múltiples

Podemos incluir varias imágenes y/o degradados en el mismo contenedor, los tenemos que colocar separados por comas, lo único que tenemos que tener en cuenta es el orden de dibujado, el último que ponemos es el último que se dibuja

## Background shorthand

Si utilizamos la propiedad background podemos asignar múltiples propiedades en una sola línea

background: image position / size repeat attachment origin clip color

No es necesario declarar todos los valores en la declaración, pero hay que recordar cuáles son los valores por defecto de las propiedades que no declaremos:

- background-image: none
- background-position: 0% 0%(esto es lo mismo que top left)
- background-size: auto
- background-repeat: repeat
- background-attachment: scroll
- background-origin: padding-box
- background-clip: border-box
- background-color: transparent

El orden de las propiedades por norma general no importa, pero hay 3 normas que no nos podemos saltar:

- background-origin y background-clip deben declararse en el orden correcto. Esto se debe a que pueden compartir el mismo valor, si sólo ponemos un valor se aplicará a las dos propiedades, si ponemos dos valores, el primero será para background-origin y el segundo para background-clip
- background-size se debe declarar inmediatamente después background-position, y ambas propiedades deben estar separados por una barra (/).
- Si se usa el shorthand para declarar múltiples background sólo el último podrá tener la propiedad background-color.
