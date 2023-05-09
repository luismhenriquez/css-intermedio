# Pseudo-clases

Es una palabra clave que podemos poner a los selectores para especificar un estado concreto del elemento, ya sea por interacción del usuario o por su posición en la estructura del documento.

Muchas de estas pseudoclases se utilizan en elementos de formularios, pero hay otras que vamos a ver en esta sección, como por ejemplo la pseudo clase `:hover` que se utiliza cuando nos situamos sobre un elemento o la pseudo clase `:active` que la podemos utilizar cuando hacemos click sobre un elemento.

Su sintaxis es muy sencilla `selector:pseudoclase { propiedad: valor; }`

## :link

Esta pseudo clase representa enlaces que el usuario aún no ha visitado.

```
    a:link{
        color: orange;
    }
```

## :visited

Esta pseudo clase representa enlaces que el usuario ya ha visitado.

```
    a:visited{
        color: orange;
    }
```

## :hover

Esta pseudo clase se usa para cambiar el estilo de ese elemento cuando hacemos colocamos el ratón encima.

```
    .button:hover{
        color: purple;
        background-color: orange
    }
```

Es importante recordar que esta pseudo clase da problemas en pantallas táctiles, por lo que se recomienda aplicarla SIEMPRE en el estilo escritorio y que no esté presente en el estilo móvil, también tenemos la opción de meter estos estilos en la media query hover

```
    @media (hover: hover) {
        .button:hover {
            color: purple;
            background-color: orange;
        }
    }
```

NOTA: Es importante que no se use la pseudo clase hover en elementos no clickables, por temas de usabilidad eso confunde al usuario.

## :active

Esta pseudo clase se usa generalmente sobre links o botones para establecer el estado activo de ese elemento cuando hacemos click. Este estado comienza al hacer click sobre el elemento con el botón izquierdo y finaliza al soltar el click.

```
    .button:active{
        color: orange;
        background-color: purple
    }
```

## :empty

Esta pseudo clase se usa para dar estilos a elementos que no tienen contenido dentro.

Un uso común de esta pseudo clase es a través de un pseudoelemento, con él generamos un texto de relleno en el caso de que el elemento esté vacío.

```
    .container:empty {
        background-color:red
    }
```

```
    .container:empty::after {
        content: "Este elemento está vacío";
    }
```

## :target

Esta pseudo clase se utiliza para dar estilos a un elemento único con un id que coincide con parámetro #hash en el fragmento de la URL.

Se usaba sobre todo en entornos donde no estaba disponible JavaScript, porque podíamos simular el evento click y hacer cambios en base a esas interacciones.

## :not()

Esta pseudo clase se utiliza para dar estilos elementos que no coincidan con los parámetros establecidos. Se la conoce como la pseudoclase de negación.

Dentro de los paréntesis podemos poner cualquier selector válido en CSS con la única limitación de que no podemos poner otro :not

Este selector tiene especificidad neutra, dependiendo del selector que pongamos entre los paréntesis, la especificidad aumentará más o menos.

## :first-child

Esta pseudo clase se usa para dar estilos al primer elemento entre un grupo de elementos hermanos.

Tiene que ser el primer hijo dentro de un contenedor

## :first-of-type

Esta pseudo clase se usa para dar estilos al primer elemento que coincida con el selector, esta es la gran diferencia entre los dos, que `:first-child` tiene que ser el primer hijo, y `:first-of-type` tiene que ser la primera coincidencia.

Tiene que ser el primer hijo dentro de un contenedor

## nth-child(An +- B)

Esta pseudo clase se usa para dar estilos a los elementos que coincidan con la selección de la formula contando TODOS los hijos del elemento padre.

## nth-of-type(An +- B)

Esta pseudo clase se usa para dar estilos a los elementos que coincidan con la selección de la formula contando SÓLO los hijos que coincidan con el selector.

## La fórmula `An+-B`

Esta es la fórmula en las pseudo clases nth-\* se puede traducir como `A * n +- B`

- A: Corresponde al número por el que se multiplicará el contador, puede tener un valor positivo o negativo, pero el negativo tiene un sólo caso de uso, y es muy poco frecuente
- n: Corresponde al contador, empieza en 0 e irá sumando 1 hasta recorrer todos los elementos que correspondan con el selector.
- operador: podemos sumar o restar, son las dos operaciones que nos permite esta pseudo clase.
- B: Es el elemento offset para saber a partir de qué elemento empezamos a contar

El elemento A es obligatorio, el resto son opcionales teniendo estas posibles combinaciones

- (A)
- (An)
- (An + B)
- (An - B)
- (-An + B)

Ejemplo práctico

```
    <p>1</p>
    <p>2</p>
    <p>3</p>
    <p>4</p>
    <p>5</p>
```

Tenemos 5 párrafos, al usar un selector nth-\* el "bucle" dará 5 vueltas, porque es el número de elementos que tenemos.

Si usamos nth-\* con un sólo número selecionaremos ése hijo en concreto

nth-child(1) -> equivale a first-child

nth-of-type(1) -> equivale a first-of-type

nth-child(3) -> selecciona el tercer hijo del contenedor

nth-of-type(3) -> selecciona el tercer hijo del contenedor que coincida con la selección

Ejemplo 1 nth-child(2n)

- 1ª vuelta: 2 \* 0 = 0 -> Ningún elemento
- 2ª vuelta: 2 \* 1 = 2 -> Segundo elemento
- 3ª vuelta: 2 \* 2 = 4 -> Cuarto elemento
- 4ª vuelta: 2 \* 3 = 6 -> Sexto elemento (no existe)

Ejemplo 2 nth-child(2n + 1)

- 1ª vuelta: 2 \* 0 + 1 = 1 -> Primer elemento
- 2ª vuelta: 2 \* 1 + 1 = 3 -> Tercer elemento
- 3ª vuelta: 2 \* 2 + 1 = 5 -> Quinto elemento

Ejemplo 3 nth-child(2n - 1)

- 1ª vuelta: 2 \* 0 - 1 = -1 -> Ningún elemento
- 2ª vuelta: 2 \* 1 - 1 = 1 -> Primer elemento
- 3ª vuelta: 2 \* 2 - 1 = 3 -> Tercer elemento
- 3ª vuelta: 2 \* 3 - 1 = 5 -> Quinto elemento

Ejemplo 4 nth-child(-2n + 7)

- 1ª vuelta: -2 \* 0 + 7 = 7 -> Séptimo elemento (pero no tenemos)
- 2ª vuelta: -2 \* 1 + 7 = 5 -> Quinto elemento
- 3ª vuelta: -2 \* 2 + 7 = 3 -> Tercer elemento
- 3ª vuelta: -2 \* 3 + 7 = 1 -> Primer elemento

## :nth-last-child

Esta pseudoclase funciona exáctamente igual que `:nth-child`, la diferencia es que empieza a contar desde el último elemento del contenedor en lugar de empezar desde el primero

## :nth-last-of-type

Esta pseudoclase funciona exáctamente igual que `:nth-of-type`, la diferencia es que empieza a contar desde el último elemento del contenedor que coincida con el selector, en lugar de empezar desde el primero

## Palabras clave

Para selecionar pares e impares, podemos usar las palabras clave `even`, para seleccionar los pares y `odd` para seleccionar los impares.

Debemos entender pares como las coincidencias 2, 4, 6, 8, etc y los impares serán las coincidencias 1, 3, 5, 7, etc

## :last-child

Esta pseudo clase se usa para dar estilos al último elemento entre un grupo de elementos hermanos.

Tiene que ser el último hijo dentro de un contenedor

## :last-of-type

Esta pseudo clase se usa para dar estilos al último elemento que coincida con el selector y esté dentro de un contenedor.

## Mezcla de pseudo clases

Las pseudo clases son combinables entre sí, el selector `.box:not(:nth-child(4))` es complétamente válido, pero hay que tener cuidado con la especificidad, este tipo de selectores pueden dar problemas a la hora de querer sobrescribirlos.
