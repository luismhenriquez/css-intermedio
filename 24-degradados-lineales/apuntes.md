# Degradados

La propiedad background-image también nos permite hacer degradados, tenemos tres tipos de degradados distintos:

## Degradados lineales

Este es el degrado más común, va de un lado del elemento hacia el opuesto. La sintaxis más sencilla que podemos utilizar es `linear-gradient(colorA, colorB)`

Este es el ejemplo más básico, pero podemos añadir una opción más, la dirección del degradado.
Para establecer la dirección podemos usar las palabras clave: to bottom (valor por defecto), to left, to right, to top, to top right, to top left, to bottom right o to bottom left.
También podemos establecer el ángulo del degradado en grados, desde 0deg hasta 360deg

Tanto si establecemos la dirección con una palabra clave como si la establecemos en grados, éste SIEMPRE debe ser el primer valor antes de establecer los colores.

`linear-gradient(ángulo, colorA, colorB)`

Respecto a la cantidad de colores podemos tener tantos colores separados por comas como queramos.

Por defecto los colores se repartirán de manera equitativa entre todos los colores que haya, pero podemos establecer comienzos y final de cada uno de los colores, esto es algo opcional pero si queremos establecerlos hay que tener en cuenta que el primer color empezará en 0% y el último acabará en 100%.

`linear-gradient(ángulo, colorA stop, colorB start)`

Si tuvieramos 3 colores, al color central podríamos establecerle un punto de inicio y un punto de final

`linear-gradient(ángulo, colorA stop, colorB start stop, ColorC start)`

Ejemplos reales:

![image](examples/1.png)

`linear-gradient(orange 50px, purple 50px 100px, lime 100px)`

![image](examples/2.png)

`linear-gradient(orange 25px, purple 50px 100px, lime 125px);`

Las paradas de color se pueden establecer en cualquier medida válida en css

## Degradados radiales

Con esta función haremos degradados radiales, estos degradados empiezan en un punto y se extienden hacia afuera.

La sintaxis más sencilla que podemos utilizar es
`radial-gradient(colorA, colorB)`

Al igual que con los degradados lineales si no establecemos paradas de color los colores se distribuirán a partes iguales.

`background-image: radial-gradient(orange, purple)`

![image](examples/3.png)

Si queremos establecer paradas de color, siguen las mismas reglas que en los degradados lineales.

`radial-gradient(orange 50px, purple 50px 75px, lime 75px)`

![image](examples/4.png)

Si no le damos forma a nuestro degadrado este se ajustará al tamaño del contenedor, si es cuadrado tendremos un círculo, si es rectangular tendremos una elipse, para dar forma a nuestro degradado tenemos otro parámetro.

`radial-gradient(circle, orange 100px, purple 100px)`

![image](examples/6.png)

`radial-gradient(ellipse, orange 100px, purple 100px)`

![image](examples/7.png)

También podemos controlar el tamaño total de nuestro degradado colocando las medidas al principio, si ponemos un valor será un círculo, si ponemos dos valores será una elipse

radial-gradient(50px, orange 100px, purple 100px)

`radial-gradient(50px, orange 100px, purple 100px)`

![image](examples/8.png)

`radial-gradient(50px 100px, orange 100px, purple 100px)`

![image](examples/9.png)

En los degradados radiales podemos establecer el centro del degradado con la palabra clave at, y al igual que en los degradados lineales tenemos dos valores

`radial-gradient(at X Y, colorA, colorB)`

El primer valor es el eje x y el segundo el eje y, la posición 0 0 corresponde a la esquina superior izquierda.

También tenemos disponibles las palabras claves top, right, bottom, left y center

`radial-gradient(at 0 0, orange 100px, purple 100px)`

![image](examples/5.png)

Para establecer el tamaño tenemos otra forma de hacerlo que es a través del uso de cuatro palabras clave:

- closest-side: El degradado se extiende hasta el lado que esté más cerca de su centro
- farthest-side: El degradado se extiende hasta el lado que esté más lejos de su centro
- closest-corner: El degradado se extiende hasta la esquina que esté más cerca de su centro
- farthest-corner: El degradado se extiende hasta la esquina que esté más lejos de su centro

## Degradados cónicos

Un degradado cónico es similar a un degradado radial. Ambos son circulares y utilizan el centro del elemento como punto de origen para las paradas de color. Sin embargo, donde las paradas de color de un degradado radial emergen del centro del círculo, un degradado cónico las coloca alrededor del círculo.

`conic-gradient(orange, purple)`

![image](examples/10.png)

Si no especificamos un ángulo para los colores el degradado se divide uniformemente entre los colores, comenzando en 0deg y terminando en 360deg. Si introducimos un tercer valor, eso crea un gradiente más suave y comenzamos a obtener esa perspectiva de aspecto de cono.

`conic-gradient(orange, purple, orange)`

![image](examples/11.png)

Si no especificamos lo contrario, este tipo de degradados empiezan en 0deg, pero podemos modificarlo. Si añadimos el parámetro `from` podemos establecer el inicio del degradado.

`conic-gradient(from 90deg, orange, purple)`

![image](examples/12.png)

Al igual que en los otros degradados podemos establecer paradas de color

`conic-gradient(orange 25%, purple 25%)`

![image](examples/13.png)

Si tenemos más colores y establecemos distintas paradas de color podemos crear un gráfico de tarta

`conic-gradient(orange 25%, purple 25% 50%, lime 50% 75%, blue 75%)`

![image](examples/14.png)

También podemos desplazar el centro al igual que en los degradados radiales con la palabra `at`

Con un solo valor moveremos el centro horizontalmente

`conic-gradient(at 100px, orange, purple, lime)`

![image](examples/15.png)

Con dos valores moveremos el centro horizontal y verticalmente

`conic-gradient(at 300px 300px, orange, purple, lime)`

![image](examples/16.png)

## Repetición de degradados

Tenemos la opción de hacer degradados lineales y radiales repetidos, para ello tenemos dos funciones, repeating-linear-gradient() y repeating-gradial-gradient()
Esta función nos sirve para repetir degradados para rellenar un contendor con el mismo patrón

Para repetir un degradado lineal de una forma simple podemos poner:
`repeating-linear-gradient(orange 20px 40px, purple 40px 60px);`

![image](examples/17.png)

La longitud del degradado que se repite es la distancia entre la primera y la última parada de color.
Las posiciones de las paradas de color se desplazan automáticamente hasta rellenar el contenedor

También tenemos la opción de añadir un ángulo o palabras clave para la dirección del degradado, exáctamente igual que si usáramos linear-gradient()

`repeating-linear-gradient(45deg, orange 20px 40px, purple 40px 60px);`

![image](examples/18.png)

Los degradados radiales siguen exáctamente los mismos principios, se establecerían así

`repeating-radial-gradient(orange 20px 40px, purple 40px 60px);`

![image](examples/19.png)

Aparte de esto, podéis usar los mísmos parámetros que vimos en los degradados radiales para personalizarlos
