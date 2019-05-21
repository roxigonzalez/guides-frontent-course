# Etiquetas semánticas y repaso HTML

## Introducción

Por mucho tiempo, se crearon websites usando el elemento `<div>` para agrupar el contenido de las páginas. Con esto, se solían agregar clases o ids para diferenciar o especificar el propósito de los divs.

![Ver imagen](https://i1.wp.com/html5doctor.com/wp-content/uploads/2009/06/html5-before1.gif)

## Etiquetas HTML5

HTML5 agregar nuevos elementos que permiten dividir el website en partes lógicas. El nombre de esos elementos o etiquetas indican el tipo de contenido que agregará.

Tenemos un ejemplo con la misma estructura del ejemplo anterior pero con etiquetas HTML5

![Ver imagen](https://i0.wp.com/html5doctor.com/wp-content/uploads/2009/06/html5-after1.gif)

### Headers y Footers

El `<header>` y `<footer>` son usados para delimitar el encabezado o pie de página de una página o en un `<article>` o `<section>`

### Navegación

El elemento `<nav>` es usado para la navegación de los websites. También llamados menús.

### Article

Los `<article>` son contenedores de secciones de una página.
Identifica las secciones principales de la página web.
En qué casos aplicaremos estas etiquetas En un blog, por ejemplo, es muy común ver este tipo de estructura, con una etiqueta `<aside>` y una etiqueta
`<article>` ambas secciones son parte importante del contenido.

### Aside

Tiene dos propósitos.

Cuando el elemento `<aside>` esta dentro de `<article>` contiene información relacionada al `<article>`

Cuando está afuera de `<article>` contiene información relacionada a la página web.

### Section

La etiqueta `<section>`
El contenido se divide en porciones. De esta forma todo el contenido está ordenado y organizado en forma lógica.

## Enlaces

Como saben, los enlaces se crean con la etiqueta `<a>`

Podemos crear un enlace para un sitio externo, agregando una URL del sitio. A ese tipo de url se le conoce como ruta **absoluta.**

También podemos agregar un enlace a un página interna de nuestro website. No se necesita especificar el dominio de esta, porque es de la misma página.

A este tipo de rutas se le conoce como **relativa.**

Si todas las páginas del sitio están en el mismo folder, entonces en el valor del href solo se agrega el nombre del archivo html.
De lo contrario, si estuviese en una carpeta diferente se deberá especificar la ubicación del archivo.

## CSS

### Selectores

- Selector Universal
- Selector de elemento
- De clase
- De ID
- Selector de hijo
- Selector de descendiente

Ejemplos:

```css
/* Universol */
* {
  margin: 0;
  padding: 0;
}

/* Clase */
.clase {
  color: red;
}

/* ID */
#aside {
  background-color: aqua;
}

/* De elemento */
h2 {
  color: blue;
}

/* Selector hijo */
ul.main-menu > li {
  display: inline-block;
  margin: 10px 12px;
}

ul.main-menu > li > a {
  color: purple;
}

ul.main-menu > li:last-child > a {
  color: black;
}

/* Pseudo selector  */
ul.main-menu > li > a:hover {
  color: cyan;
}

/* Selector de descendiente */
ul.main-menu a {
  color: pink;
}
```
