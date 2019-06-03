# Responsive Design ó Diseño responsivo

## ¿Qué es Responsive Design?

Diseño que responde o diseño responsivo.
Se trata de redimensionar y colocar los elementos de la web de forma que se adapten al ancho de cada dispositivo permitiendo una correcta visualización y una mejor experiencia de usuario.

Por lo general, ocuparemos reglas CSS para este fin.

En resumen:
Se trata de entregar el contenido de manera óptima, considerando las características de hardware, software y tipos de conexiones, del dispositivo que el usuario esté usando

## Viewport

Es como la vista o ventana. Nos sirve para definir qué área de pantalla está disponible al renderizar un documento, nivel de escalado y el zoom que debe mostrar inicialmente. Todo ello, con parámetros que le damos a la propia etiqueta META.

Disponemos de los siguientes parámetros en la etiqueta META:

- **Width**: anchura virtual (emulada) de la pantalla o anchura del viewport.
- **Height**: altura virtual de la pantalla o anchura del viewport.
- **Initial-scale**: la escala inicial del documento.
- **Minimum-scale**: la escala mínima que se puede poner en el documento.
- **Maximum-scale**: la escala máxima configurable en el documento.
- **User-scalable**: si se permite o no al usuario hacer zoom.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

Veremos unos ejemplos:
https://mediaqueri.es/

Media Queries
Módulo de CSS3 que permite cambiar la presentación del contenido a características del dispositivo.

Estructura:

```css
@media media type and (condition) {
}
```

## Uso de Media queries

Las Media queries consisten de un media type y una o más expresiones, implicando características del medio, la cual se resuelve como verdadera o falsa. El resultado de la consulta es verdadera si el tipo de medio especificado en el media query concuerda con el tipo de dispositivo que está siendo mostrado y todas las expresiones en el media query son verdaderas.

```html
<!-- CSS media query on a link element -->
<link rel="stylesheet" media="(max-width: 800px)" href="example.css" />

<!-- CSS media query within a style sheet -->
<style>
  @media (max-width: 600px) {
    .facet_sidebar {
      display: none;
    }
  }
</style>
```

Cuando una media query es verdadera, la hoja de estilo correspondiente o reglas de estilos son aplicadas, siguiendo las reglas normales de cascada.

| Nota: Repasar los operadores lógicos AND, OR, NOT ;)

## Puntos de quiebre (breakpoints)

Los puntos de quiebre (o breakpoints) son los anchos (en pixeles) en los que ocurren cambios en nuestra página para que se adapte a diferentes pantallas.

En vez de utilizar los valores que se nos ocurran para los anchos de diferentes pantallas, se han definido ciertos valores para determinar el tipo de pantalla que se está usando:

- Hasta 575px son teléfonos móviles en modo vertical.
- De 576px a 767px son teléfonos móviles en modo horizontal.
- De 768px a 991px son tabletas.
- De 992px a 1199px son pantallas de escritorio normales.
- 1200px o más son pantallas grandes como televisores.

Sin embargo, cuando hablamos de puntos de quiebre nos referimos a un ancho específico, por ejemplo 768px, que es el momento en el que cambia la pantalla de teléfono móvil a tableta.

Estos valores son sólo una referencia. El ancho de la mayoría de pantallas de escritorio hoy en día, por ejemplo, es de más de 1200px.

A continuación veremos cómo utilizar estos puntos de quiebre para crear aplicaciones que se adaptan a diferentes pantallas.

## Mobile first

Se le llama a la técnica de comenzar el diseño o adaptar los elementos en de la página web en móviles. Es decir, primero se definen las reglas dirigidas a teléfonos móviles y con media queries ajustamos el contenido para pantallas más anchas.

Veamos un ejemplo. Imagina que queremos ir incrementando el tamaño de la letra de acuerdo al ancho de la pantalla:

- 14px en teléfonos móviles.
- 15px para tabletas.
- 16px para pantallas de escritorio normales.
- 17px para pantallas grandes.

Lo primero que vamos a definir es el estilo para telefonos móviles y después utilizamos media queries para los demás:

```css
/* mobile first */
body {
  font-size: 14px;
}

/* tabletas */
@media (min-width: 768px) {
  body {
    font-size: 15px;
  }
}

/* escritorio normales */
@media (min-width: 992px) {
  body {
    font-size: 16px;
  }
}

/* pantallas grandes */
@media (min-width: 1200px) {
  body {
    font-size: 17px;
  }
}
```

## En conclusión

Los media queries son el componente fundamental de responsive design, pero para que una página sea completamente adaptable debes verificar también que las imágenes, videos, tablas, etc. se vean bien en todos los dispositivos.

Por último, si quieres ver ejemplos de responsive design te recomiendo estos dos sitios:

https://mediaqueri.es/
https://responsivedesign.is/examples/

## Herramientas para responsive design

https://material.io/tools/resizer/
http://resizemybrowser.com/
https://designmodo.com/responsive-test/
https://www.thinkwithgoogle.com/intl/es-419/feature/testmysite
