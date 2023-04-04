# Responsive Web Design

Es un conjunto de técnicas de diseño y desarrollo web que mediante el uso de estructuras flexibles y junto con Media Queries especificados en CSS, logran adaptar un sitio web al dispositivo en el que se ve.

Esto engloba muchas cosas a tener en cuenta, aspecto, experiencia de usuario, múltiples dispositivos, optimizaciones de carga usando tanto HTML (por ejemplo, con carga de imágenes específicas a través de la etiqueta picture), como CSS y JavaScript para adaptar el entorno al dispositivo en todos los sentidos.

En CSS tenemos varias formas de trabajar con el responsive design.

# Media queries

[Documentación Oficial](https://developer.mozilla.org/es/docs/Web/CSS/Media_Queries/Using_media_queries)

Las media queries (consultas de medios) son útiles cuando deseas modificar tu página web o aplicación en función del tipo o tamaño de dispositivo.

Funcionan como un condicional y en el caso de que se cumpla la condición se aplicarán los estilos

La sintaxis de una media query se compone de un _media type_ opcional y una lista de _media features_

Los _media type_ o dispositivos pueden ser:

- all: Para todos los dispositivos, es el valor por defecto.
- print: Para medios impresos.
- screen: Para pantallas.
- speech: Para lectores de pantallas.

`@media <dispositivo> { Estilos a aplicar }`

Los _media features_ o características describen las carácterísticas que debe tener nuestro dispositivo para aplicarse. Aquí incluimos tamaño del dispositivo, preferencias del usuario, si el dispositivo admite hover sobre los elementos o incluso el número de bits por color entre otras opciones.

`@media (min-width: 768px) { Estilos a aplicar }`

Las _media features_ más conocidas son los breakpoints, "puntos de ruptura" donde cambiamos estilos en función del ancho y/o alto del dispositivo, NO existe ningún estandar que recoja las medidas a utilizar pero las más comunes son:

- 320px
- 340px
- 720px
- 768px
- 1024px
- 1400px

Estos son los que se denominan "major breakpoints", es decir puntos de ruptura que cambian en función de las distintas medidas de dispositivos. En sitios web con una cierta complejidad es habitual que existan "minor breakpoints", cambios en un tamaño específico para corregir detalles del maquetado.

Si queremos añadir un _media type_ y una _media feature_ en la misma media query tenemos el operador lógico _and_

`@media screen and (min-width: 768px) { Estilos a aplicar }`

También existen los operadores lógicos not y only, pero su uso no es muy común.

Podemos aplicar media queries diréctamente en el HTML con el atributo media:

`<link rel="stylesheet" media="(max-width: 800px)" href="example.css" />`

Pero hay que tener en cuenta que estas hojas css se cargarán igualmente aunque no se estén aplicando

# Etiqueta meta viewport

Esta etiqueta fue creada por Apple con el lanzamiento del Iphone 1 y a día de hoy aún no existe ningún reemplazo nativo, se estába trabajando en @viewport, pero al final se abandonó el proyecto.
Si quitamos esta etiqueta meta las media queries dejarán de funcionar, para comprobarlo hay que saber testearlas correctamente

# Diseño adaptativo vs responsive

Puede parecer lo mismo, pero no lo es. Ambos enfoques se complementan entre sí, por lo que no hay una forma correcta o incorrecta de hacerlo.

El diseño adaptativo consiste en crear un sitio web para escritorio y otro para movil, puede parecer un enfoque anticuado, pero hay situaciones donde la web movil es tan distinta a la web de escritorio que usar el mismo código para las 2 es algo muy complejo y no compensa.

IMPORTANTE, esto no implica que el sitio web de escritorio no tenga que ser responsive, también se debe hacer la web de escritorio en su concepto para un ancho reducido.

# Mobile first vs Desktop first

En un enfoque mobile first se empieza a construir la versión mobile desde el principio y después se va adaptando el contenido hacia tamaños más grandes, en el enfoque desktop first se hace al contrario, se empieza por escritorio y se va adaptando el contenido hacia tamaños más pequeños.

Técnicamente, no hay mucha diferencia si un proyecto se inicia desde una pantalla más pequeña y vamos subiendo el tamaño que si lo hacemos al revés, de pantalla grande a una más pequeña. Esa es la teoría, pero en la práctica es mucho más fácil empezar desde móvil e ir subiendo, principalmente porque al tener menos sitio para distribuir el contenido es mejor tomar esa decisión desde el principio.

# Elementos anidados

Es muy común pensar que cuando se habla de responsive todas las medidas deberían ser relativas, porcentajes, unidades de viewport etc, pero esto es falso, en todos los sitios web hay contenido que no necesita escalar ni cambiar de tamaño, en esos casos las unidades absolutas son muy útiles.

# Links para consultar más información

Ejemplo de diseño responsive

- https://mediaqueri.es/
- https://www.awwwards.com/websites/responsive-design/

Principios básicos del diseño responsive

- https://blog.froont.com/9-basic-principles-of-responsive-web-design/

Libros recomendados

- Responsive web design. Ethan marcotte
- Responsive design patterns. Ethan marcotte
- Responsive Design: Patterns & Principles. Ethan marcotte
