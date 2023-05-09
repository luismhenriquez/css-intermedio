# Pseudo elementos

Los pseudo elementos son un tipo de selector similar a las pseudo clases pero, en este caso, no se usarán para dar estilos en función del estado de un elemento, si no que los utilizaremos para dar estilos a ciertas partes del elemento, generación de contenido o incluso cuando ese elemento está seleccionado.

Su sintaxis hasta el estandar 2.1 era la misma que la de las pseudo clases `selector:pseudo-clase` pero en el estándar CSS 2.2 (CSS3) se introdujo un cambio de sintaxis para diferenciar las pseudo clases de los pseudoelementos, y pasaron a usarse dos puntos dobles `selector::pseudo-elemento` esta sintaxis es soportada por todos los navegadores salvo nuestro querido Internet Explorer.

A diferecia de las pseudo clases sólo podemos utilizar un pseudo elemento por selector.

## ::first-letter

Este pseudo elemento se utiliza para seleccionar la primera letra de un elemento de texto. La única limitación es que no se puede usar en elementos de línea, por lo que si queremos usarlo en un `<span>` o en un `<a>`, éste deberá tener `display:block` o `display:inline-block`

## ::first-line

Este pseudo elemento se utiliza para seleccionar la primera línea de un elemento de texto. Al igual que en el pseudo elemento `::first-letter` no se puede usar en elementos de línea, por lo que si queremos usarlo éste deberá tener `display:block` o `display:inline-block`

## ::selection

Este pseudo elemento se utiliza para dar estilos al texto seleccionado por el usuario.

Como detalle extra, tenemos la propiedad `user-select` para permitir al usuario selccionar o no texto de nuestro sitio web.

## ::after y ::before

Estos son los pseudo elementos más usados en CSS, nos permiten generar dos elementos extra que serán hijos del elemento al que se lo apliquemos.

::after se colocará después del elemento y ::before antes. Usar estos pseudo elementos sería el equivalente a colocar un `<span>` antes y/o después del elemento. Uso `<span>` en lugar de `<div>` porque es muy importante que recordeis que los pseudo elementos `::after` y `::before` son elementos de línea por defecto.

Existe mucha confusión acerca de cuando y cómo usarlos correctamente. La norma principal es que estos pseudo elementos se utilizan para adornar el elemento al que se lo aplicamos. Estos "hijos" no se ven reflejados en el HTML, por lo que no podemos seleccionarlos ni están accesibles desde JavaScript, por lo que a efectos técnicos, estos elementos no existen.

Respecto a las propiedades que les podemos aplicar la respuesta es TODAS. Lo podéis tratar como si se tratara de un `<span>` en todos los sentidos, la única peculiaridad que tienen es que debemos usar la propiedad `content` de manera OBLIGATORIA, si no la usamos los elementos no se pintarán en pantalla.

Otro detalle importante a recordar es que no todos los elementos admiten `::after` y/o `::before`, estos pseudo elementos NO se pueden aplicar en lo que se denominan `REPLACED ELEMENTS`

Estos elementos son aquellos cuyo contenido no se ve afectado por los estilos del documento actual, os dejo aquí el enlace de la documentación oficial para que profundicéis [Elementos de reemplazo](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element)

Los elementos de reemplazo más comunes en los que no funcionan `::after` y `::before` son los `<img>`, los `<input>` que admitan entrada de datos (text, number, etc.) y los `<textarea>`

Una curiosidad sobre estos pseudo elementos es que el selector universal `*` cuando usamos la propiedad `box-sizing` deja fuera a estos pseudolementos, por eso es habitual que cuando hacemos el reseteo del `box-sizing:border-box` se añadan al selector.

```
*, *::before, *::after{box-sizing:border-box}
```

## Content

Esta propiedad es obligatoria en los pseudo elementos `::after` y `::before`

Y como valor tenemos varias opciones:

- Un string o cadena de caracteres: Dentro de la propiedad `content:`, podemos poner entre comillas cualquier texto, emoji, etc. y eso se pintará en nuestro sitio web. [Tabla de símbolos unicode](https://unicode-table.com/es/)

  También puede ser un contenido vacío `content:''`, esto se usa habitualmente cuando lo que buscamos no es generar texto si no tener un elemento extra para realizar adornos o efectos.

- Podemos usar la función url() para meter imágenes, degradados, etc...
  Aunque tenemos la opción, la gestión de imágenes o degradados es más recomendable usar la propiedad background, ya que será más fácil dar estilos a través de esa propiedad.

- Tenemos disponible la función attr() que nos permitirá recuperar el contenido de cualquier atributo del elemento padre.
- También existe el valor `open-quote` y `close-quote` para incluir comillas de citas que se adaptarán al idioma de la web.
- Hay una opción más para content que son los `counters()` pero esos los veremos en la seccion de listas.
