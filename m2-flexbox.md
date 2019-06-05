# Flexbox

CSS Flexbox nos proporciona una forma eficiente de alinear y distribuir el espacio entre elementos de una página.

## Contenedores flexibles y elementos flexibles

**Contenedor padre (Flex Container)**: Contiene los llamados elementos flexibles.
**Contenedores hijos (Flex Items)**: Estos son elementos dentro del contenedor.

## Let's do that!

```html
<div class="flex-container">
  <div class="flex-item">1</div>
  <div class="flex-item">2</div>
  <div class="flex-item">3</div>
  <div class="flex-item">4</div>
</div>
```

```CSS
.flex-container {
  display: flex;
  width: 600px;
  background-color: #ddf58c;
}

.flex-item {
  background-color: #67c3e6;
  width: 100px;
  height: 100px;
  margin: 10px;
}
```

## Propiedades del contenedor padre

- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content.

### Flex direction

```css
.flex-container {
  flex-direction: row || column || row-reverse || column-reverse;
}
```

Por defecto: `row`

### Flex Wrap

```css
.flex-container {
  flex-wrap: wrap || nowrap || wrap-reverse;
}
```

Por defecto: `nowrap`

### Flex-flow

Abreviatura de `flex-direction` + `flex-wrap`

```css
flex-flow: row wrap-reverse;
```

### Justify-content

```css
.flex-container {
  justify-content: flex-start || flex-end || center || space-between ||
    space-around;
}
```

### Align-items

Similar a `justify-content`. Pero de forma vertical.

```css
.flex-container {
  align-items: flex-start || flex-end || center || stretch || baseline;
}
```

### Align-content

Gestiona cómo se alinean los
elementos dentro del contenedor, con múltiples líneas. La diferencia con `align-items` es que el primero alinea elementos, y `align-content` las filas. Además, `align-self`, alinea los elementos de forma independiente.

```css
.flex-container {
  align-content: flex-start || flex-end || center || stretch;
}
```

## Propiedades de los flex-items

## Order

Por defecto, todos los elementos tienen el orden 0, lo que los muestra en el mismo orden que salen en el código HTML.

> Si el orden de un elemento en concreto se cambia a 1, ese elemento será colocado al final. Cuando a otro elemento se le asigne el valor 2, será colocado a continuación del elemento con orden 1.

```css
.flex-item:nth-child(1) {
  order: 1;
}
.flex-item:nth-child(2) {
  order: 2;
}
```

### Flex-grow

Por defecto tendrá el valor 0, que indica que el elemento no crecerá dentro del contenedor.

```css
.flex-item {
  flex-grow: 0;
}
```

Cambiemos el valor

```css
.flex-item {
  flex-grow: 1;
}
```

### Flex-shrink

Por defecto, tendrá el valor 1. Lo que significa que el elemento se reducirá cuando cambie el tamaño de la ventana del navegador.

```css
.flex-item {
  flex-shrink: 1;
}
```

Cuando el valor se establezca a 0, este elemento no reducirá su tamaño aunque el navegador cambie de tamaño.

```css
.flex-item {
  flex-shrink: 0;
}
```

### Flex-basis

Define el tamaño predeterminado de un elemento antes de que se distribuya el espacio restante.

Si indicamos como valor auto, el tamaño del elemento será igual al contenido.

```css
.flex-item {
  flex-basis: auto;
}
```

## Flex

Es la abreviatura de `flex-grow`, `flex-shrink` y `flex-base`. Es por ello que resulta de gran utilidad en diversas ocasiones, por el ahorro de escribir propiedades.

```css
.flex-item {
  /* Esto: */
  flex: 0 1 auto;
  /* Es lo mismo que esto:
    flex-grow : 0;
    flex-shrink : 1;
   flex-basis : auto;
    */
}
```

## Align-self

Se utiliza para posicionar un elemento en particular, cambiando su posición a lo largo del eje transversal, sin afectar al resto de elementos.

`align-self` funciona igual que `align-item`, salvo que el primero alinea un objeto en particular.

Por lo tanto, los valores que podemos utilizar son`auto || flex-start || flex-end || center || baseline || stretch`.

```css
.flex-item:nth-child(2) {
  align-self: flex-end;
}
```

## Conclusión

En conclusión, el uso de Flexbox para creación de layouts es una técnica muy flexible y eficaz
