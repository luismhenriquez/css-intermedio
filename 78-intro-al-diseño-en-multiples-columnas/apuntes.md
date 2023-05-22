# Diseño en multiples columnas

El módulo de diseño de múltiples columnas CSS amplía el modo de diseño de bloques para permitir la definición fácil de múltiples columnas de texto.

El diseño en columnas nos permite emular la maquetación de un periódico de forma sencilla y sin tener que hacer uso de JavaScript para hacer cálculos de viewport ni meter saltos de línea innecesarios.

Hay dos propiedades que controlan la cantidad y el ancho de las columnas `column-count` y `column-width`

## column-count

Con esta propiedad estableceremos el número de columnas que queremos en nuestro diseño, por ejemplo `column-count:2`

## column-width

Esta propiedad establece el ancho MÍNIMO deseado, si no se especifica será el navegador el que divida el espacio disponible entre el número de columnas establecido.

## column-gap

Con esta propiedad podemos establecer la separación entre columnas

## column-rule

Esta propiedad es un shorthand nos permite generar una línea entre columnas, tiene la misma sintaxis que border y podemos dividir esta propiedad en `column-rule-width`, `column-rule-style` y `column-rule-color`

## column-span

Esta propiedad hace posible que un elemento se extienda sobre todas las columnas
