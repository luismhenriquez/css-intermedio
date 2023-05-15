# Funciones

Ya hemos visto algunas funciones en CSS como `attr()`, `not()` o `url()` pero existen más. En esta sección vamos a ver las funciones que nos permiten decirle al navegador que haga cálculos dinámicos en tiempo real.

## calc()

La función calc nos permite pasarle una operación matemática como parámetro.
`calc(2px + 20px)` esto sería una operación válida aunque no tenga mucho sentido hacer ese cálculo.

Podemos utilizar esta función en cualquier propiedad que espere un valor numérico, `width`, `color`, etc.

El uso más habitual de esta función es para hacer cálculos entre valores absolutos y relativos, por ejemplo: `width: calc(100% - 30px)`

Es MUY IMPORTANTE que vigiléis los espacios, si no dejáis espacios entre los valores y el operador no funcionará

Podemos usar suma `+`, resta `-`, multiplicación `*` y división `/`

Y como último detalle podemos anidar varios calc(), aunque esto no es muy frecuente `calc(calc(100% / 2) / 2)`

## min()

Esta función permite establecer el valor más pequeño de una lista de expresiones separadas por comas.

Si le pasamos 2 valores, por ejemplo `width: min(100%, 900px)`, lo que sucederá es que nuestro contenedor tendrá un ancho de 900px si el viewport mide más de 900px, en el caso de que mida menos, cojerá el valor de 100%.

## max()

Esta función funciona de una forma muy similar a `min()` pero haciendo lo contrario, cogerá el valor máximo siempre que pueda, si usamos el mismo ejemplo `width: max(100%, 900px)`, el contenedor medirá siempre el 100% hasta que el viewport tenga menos de 900px, en ese caso el contenedor medirá 900px de ancho.

## clamp()

Esta funcíon nos permite pasarle 3 valores `clamp(mínimo, ideal, máximo)` Con estos tres parámetros le diremos cual es el mínimo tamaño que debe tener, el ideal y hasta donde puede crecer, lo que nos da muchísimo control sobre los tamaños de forma dinámica.
