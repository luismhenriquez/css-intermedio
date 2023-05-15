# Estilar formularios

Dar estilos a formularios es una de las cosas que más complicaciones suele tener, no sólo por que cada formulario puede tener distintos requisitos, si no porque cada campo puede tener varios estados y distintos mensajes de error.

En esta sección veremos como controlar estos estilos a través de pseudoclases que nos facilitarán esta tarea.

## Estilos por defecto de un input

Los input (entrada de datos) suelen traer una serie de propiedades predefinidas por el navegador que pueden complicar el dar estilos personalizados.

Estos estilos son `background-color` y `border`

Para resetear estos estilos se suele poner:

```
input {
  background-color: transparent;
  border: none;
}
```

## :focus

Representa un elemento (como una entrada de formulario) que ha recibido el foco. Generalmente se activa cuando el usuario hace click.

Cuando hacemos foco sobre un input (lo tenemos seleccionado) se añade un estilo con `outline`, para resetearlo se suele poner

```
input:focus{
  outline:none
}
```

## :focus-within

Representa un elemento que coincide con la pseudoclase :focus o tiene descendientes que coincidan con :focus

## :focus-visible

Esta pseudo clase solo se activará cuando el navegador considere necesario mostrar el foco, por ejemplo cuando el usuario esté navegando utilizando el teclado.

## :valid

Representa cualquier elemento `<input>` cuyo contenido se valide satisfactoriamente. Esto permite que los campos válidos adopten fácilmente una apariencia que ayuda al usuario a confirmar que sus datos están formateados correctamente.

## :invalid

Representa cualquier elemento `<input>` u otro elemento cuyos contenidos no cumplen los requisitos de validación

## :required

Respresenta cualquier elemento `<input>` que tenga el atributo required, lo añadimos para identificar un campo obligatorio

## :optional

Respresenta cualquier elemento `<input>` que NO tenga el atributo required.

## :checked

Representa cualquier `<input>` radio, checkbox u option que está marcado o conmutado a un estado on.

Para cambiar el color con el que se marca el check tenemos la propiedad `accent-color`, esta propiedad sirve para cambiar el color de todos los input que no sean de entrada de datos (radio, checkbox, range y progress)

## ::placeholder

Este pseudo elemento nos permite dar estilos al placeholder de un input

## :placeholder-shown

Esta pseudo clase nos permite dar estilos cuando el placeholder se está mostrando.

## resize

Esta propiedad nos va a permitir controlar si un text area se puede redimensionar o no

El valor por defecto es `both` que nos permitirá redimensionar el text area tanto horizontal como verticalmente, y para modificar este comportamiento tenemos los valores

- none: Impide que se pueda redimensionar
- vertical: Permite que se pueda redimensionar sólo verticalmente
- horizontal: permite que se pueda redimensionar sólo horizontalmente
