# ¿Qué es una variable?

Es un espacio en memoria que almacena un valor, después usaremos ese valor en todos los sitios necesarios y si en algún momento necesitamos cambiar ese valor, sólo tendremos que cambiar el valor de la variable

Deben ir **SIEMPRE** en un selector.

La sintaxis de una variable es: <br>
Para declararla: --nombre: valor <br>
Para usarla: propiedad: var(--nombre)

Las variables css pueden almacenar cualquier **VALOR** válido en CSS, no pueden almacenar ni selectores ni propiedades.

Es importante que sepais que las variables se almacenan a nivel de documento por lo que tienen herencia y cascada, eso significa que se pueden heredar y que se pueden sobreescribir.

Respecto al ámbito (dónde las podemos usar) pueden ser globales (accesibles desde cualquier selector) o locales (accesibles sólo desde el elemento donde se declaran)
