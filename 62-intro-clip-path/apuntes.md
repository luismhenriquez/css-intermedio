# Clip-path

La propiedad clip-path crea una región de recorte que establece qué parte de un elemento debe mostrarse. Se mostrarán las partes que están dentro de la región, mientras que las que estén fuera se ocultan, esto suele causar ciertos problemas cuando se usa por primera vez.

Existen bastantes valores que se pueden aplicar a la propiedad `clip-path`, pero en esta sección vamos a ver los que se usan en la mayoría de ocasiones.

- inset();
- circle();
- ellipse();
- polygon();

## inset()

Este valor nos crea un recorte rectangular.

Admite de 1 a 4 valores, con las mismas reglas que `margin` o `padding`

- 1 valor: se aplicará a todos los lados del rectángulo
- 2 valores: se aplicará el primer valor al eje vertical y el segundo al eje horizontal
- 3 valores: se aplicará el primer valor al lado superior, el segundo al eje horizontal y el tercero al lado inferior
- 4 valores: se aplicará el primer valor al lado superior, el segundo al lado derecho, el tercero al lado inferior y el cuarto al lado izquierdo.

Además tenemos la opción de añadir la palabra clave `round` para generar un "border-radius", el número de valores después de usar `round` siguen las mismas normas que las de `border-radius`

- 1 valor: se aplicará a todas las esquinas del rectángulo
- 2 valores: se aplicará el primer valor a las esquinas superior izquierda e inferior derecha
- 3 valores: se aplicará el primer valor a la esquina superior izquierda, el segundo a las esquinas superior derecha e inferior izquierda y el tercer valor a la esquina inferior derecha
- 4 valores: se aplicará el primer valor a la esquina superior izquierda, el segundo a la esquina superior derecha, el tercer valor a la esquina inferior derecha y el cuarto a la esquina inferior izquierda.

## circle()

Crea un recorte circular que admite los mismos valores de posicionamiento que los degradados radiales circulares.

Por ejemplo
`clip-path: circle(200px at top right);`

El punto 0 0 será la esquina superior izquierda.

## ellipse()

Crea un recorte elíptico y, al igual que `circle()`, admite los mismos valores de posicionamiento que los degradados radiales.

Por ejemplo
`clip-path: ellipse(200px 100px at top right);`

El punto 0 0 es la esquina superior izquierda.

## polygon()

Este es el recorte que más se suele usar, hay que establecer pares de valores y se necesitan como mínimo 3, la figura más básica que podemos hacer es un triángulo.

Los valores se pueden establecer en cualquier medida, pero lo más habitual es hacerlo con porcentajes

Cada una de las parejas establece las coordenadas X e Y respectivamente.
En el primer valor 0 equivale a la izquierda y 100% a la derecha
En el segundo valor, 0 será arriba y 100% abajo.

Esto sería un triángulo.
`clip-path: polygon(50% 0%, 0% 100%, 100% 100%);`

No existe límite de parejas, por lo que se pueden llegar a hacer formas realmente complejas.

# Herramienta gráfica para clip-path

[clippy](https://bennettfeely.com/clippy/)
