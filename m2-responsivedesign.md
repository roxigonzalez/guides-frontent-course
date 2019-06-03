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

## Herramientas para responsive design

https://material.io/tools/resizer/
http://resizemybrowser.com/
https://designmodo.com/responsive-test/
https://www.thinkwithgoogle.com/intl/es-419/feature/testmysite
