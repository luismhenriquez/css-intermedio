# Filter

La propiedad filter nos va a permitir aplicar efectos gráficos a nuestras imágenes.

Hay que tener en cuenta que filter es una propiedad que crea un nuevo contexto de apilamiento, y eso es algo que puede causar problemas en algunas situaciones porque puede ocultar elementos.

## blur(px)

Aplica un desenfoque Gaussiano a la imagen. El valor de 'radio' define el número de píxeles que se mezclan entre sí, por lo que un valor mayor creará un mayor desenfoque.
`filter: blur(5px);`

## brightness(number || %)

Aplica una multiplicación lineal a la imagen, haciendo que parezca más o menos brillante.
Admite valores numéricos y en porcentaje, con valores numéricos el 1 será la imagen por defecto, y 0 será sin brillo. Si usamos porcentaje el 100% será la imagen por defecto.
`filter: brightness(0.4);`

## contrast(number || %)

Ajusta el contraste de la imagen de entrada. Un valor por debajo 100% disminuye el contraste, mientras que un valor por encima lo aumenta. Un valor de 0% creará una imagen que es completamente gris, mientras que un valor de 100% deja la entrada sin cambios.
`filter: contrast(200%);`

## grayscale(number || %)

Un valor de 100% es completamente en escala de grises, mientras que un valor de 0% deja la entrada sin cambios.
`filter: grayscale(50%);`

## hue-rotate(angle)

El cambio relativo en el tono de la muestra de entrada. Un valor de 0deg deja la entrada sin cambios. Una rotación de tono positiva aumenta el valor de tono, mientras que una rotación negativa lo reduce.
`filter: hue-rotate(90deg);`

## invert(number || %)

Este filtro invierte el color a su contrario en el círculo cromático. Un valor de 100% o de 1 hace que el color esté completamente invertido, mientras que un valor de 0 deja la entrada sin cambios.
`filter: invert(1);`

## opacity (number || %)

Este valor funciona prácticamente igual que la propiedad opacity de CSS.

Un valor de 0 es completamente transparente, mientras que un valor de 100% deja la entrada sin cambios.
`filter: opacity(25%);`

## saturate (number || %)

Este valor nos permite cambiar la saturación de la imagen.

Un valor por debajo 100% desatura la imagen, mientras que un valor por encima 100% la sobresatura.
`filter: saturate(30%);`

## sepia (number || %)

Convierte la imagen de entrada a sepia, dándole una apariencia más cálida, más amarilla / marrón.
Un valor de 100% es completamente sepia, mientras que un valor de 0% deja la entrada sin cambios.
`filter: sepia(60%);`

## drop-shadow (offset-x offset-y blur color)

Aplica un efecto de sombra a la imagen de entrada

- offset-x offset-y (requerido)
  Estos valores determinan el desplazamiento de la sombra. offset-x especifica la distancia horizontal, donde los valores negativos colocan la sombra a la izquierda del elemento.
  offset-y especifica la distancia vertical, donde los valores negativos colocan la sombra sobre el elemento.

- blur (Opcional)
  El radio de desenfoque de la sombra, cuanto mayor es el valor, más grande y borrosa se vuelve la sombra. Si no se especifica, el valor predeterminado es 0, lo que da como resultado un borde nítido y sin borrosidad. No se permiten valores negativos.

- color (Opcional)
  El color de la sombra, si no se especifica, se utiliza el valor de la propiedad.

`filter: drop-shadow(16px 16px 20px blue);`
