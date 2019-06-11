# Preprocesadores

Los preprocesadores de CSS extienden las funcionalidades de un CSS común, permitiéndonos tener variables (sí, variables), funciones :D, mixins, reutilizar código, tener más flexibilidad al momento del desarrollo y otras cosas más.

## ¿Cómo funciona?

En términos simples, mediante un lenguaje de script escribimos código parecido al que usamos en CSS (esto dependerá del preprocesador que estemos usando), luego este código será compilado y como resultado de esta compilación tendremos un archivo CSS.
Hasta aquí puede que te preguntes, ¿si al final vamos a tener archivo CSS, por qué usar un preprocesador y no solo CSS?
No olvides lo que mencionamos antes lo de extender las funcionalidades de CSS

En la actualidad existen una serie de preprocesadores con sintaxis parecidas y algunas diferencias. Por mencionar algunos preprocesadores tenemos [**Sass**](https://sass-lang.com/), [**Less**](http://lesscss.org/) y [**Stylus**](http://stylus-lang.com/), entre los más usados hoy en día y existe una amplia documentación, ejemplos y frameworks compatibles con ellos (Bootstrap por ejemplo), por lo que aprender a usarlos no te será complicado, solo dependerá del tiempo que inviertas en leer y practicar.

## SASS

Sass es un lenguaje de hoja de estilos.

Este usa la [indentación](https://es.wikipedia.org/wiki/Indentaci%C3%B3n) para separar bloques de código y el carácter nueva línea para separar reglas. La sintaxis más reciente, **SCSS**, usa el formato de bloques como CSS. Este usa llaves para denotar bloques de código y punto y coma (;) para separar las líneas dentro de un bloque.
La sintaxis indentada es `.sass` y los ficheros SCSS tienen las extensiones `.scss`.

### Ventajas

- Mediante SASS podemos nestear las reglas de CSS, asimismo, podemos anidar los selectores hijos dentro de los padres, para no repetir el uso de éstos, así como tener un archivo más legible.
- Gracias al uso de variables y funciones, SASS nos ayuda a escribir menos código y a evitar que se repita.
- También se puede implementar con punto y coma y llaves, o se puede usar indentado para la creación del código.

### Desventajas

- Tener muchos estilos anidados puede llevar a ralentizar el renderizado del sitio web.

```css
.clase .sub-clase .sub-sub-clase .sub-sub-sub-clase {
  /* estilos */
}
```

### Instalación

#### Para Windows

- Instalar Compass.app o
- Instalar npm luego `npm install -g sass`

**Compass.app** es un marco de creación de hojas de estilo que facilita la creación y el mantenimiento de las hojas de estilo y el marcado

**npm** Si instalas sass por medio de npm podrás hacer esto en la terminal

`sass --watch input.scss output.css`

Donde el archivo `input.scss` es donde tendremos el código a compilar `scss` o `sass`. Y `output.css` es el código css compilado.

### Variables

El concepto de variables es el mismo que conocemos para JavaScript y otros lenguajes de programación. Permite guardar momentáneamente cierto valor, para ser utilizado luego.

En el caso de CSS, nos permite por un lado evitar la repetición de valores (por ejemplo un color, una familia tipográfica o una medida), y por otro centralizar dicho dato de forma tal que para su modificación haya que cambiar el valor una sola vez.

**Ejemplo**

### Cálculos

La posibilidad de realizar cálculos también agiliza el trabajo. Podemos sumar (+), restar (-), multiplicar (+) y dividir (/).

Los cálculos pueden realizarse entre números o entre variables que contengan información numérica.

**Ejemplo**

### Nesting

Teniendo en cuenta la naturaleza de un elemento dentro de otro en el HTML, es muy común que los selectores de CSS se vuelvan algo así muy pronto:
_Ver ejemplo_

SASS permite introducir un elemento dentro de otro tal como hacemos en el código HTML. Esto facilita el trabajo generando una situación análoga a la que tenemos en el marcado semántico: _Ejemplo2_

### Mixins

En ciertas ocasiones el código a repetir en un archivo CSS es más que simplemente un valor. Los mixins nos permiten centralizar la escritura de varios renglones de CSS, para luego insertarlo donde queramos. _Ejemplo_

Los mixins también permiten la inclusión de parámetros, de forma que no siempre el código generado es idéntico. _Ejemplo2_

### Herencia

SASS también permite que ciertos elementos “hereden” el estilo de otros, la sintaxis es.

`@extend propiedades_heredadas`

_Ver ejemplo_

### Import

Otra posibilidad es la de dividir en diferentes archivos para organizar el código. Podemos tener un archivo `estilos.scss`, y luego otro llamado `_reset.scss`; el guión bajo al principio del nombre indica que se trata de un **“partial”**, un archivo parcial que luego será importado dentro de otro.

`_reset.scss`

```scss
/* Archivo: _reset.scss */
* {
  margin: 0;
  padding: 0;
}
```

**estilos.scss**

```scss
/* Archivo: estilos.scss */
@import "reset";

p {
  font-family: "Lato", sans-serif;
}
```

El archivo resultante estilos.css, tendrá el código de estilos.scss, con el código de \_reset.scss importado en el lugar indicado.

### Pero ¿cómo funciona en los navegadores?

El código SASS, aunque muy parecido al de CSS nativo, **no puede ser interpretado por los navegadores.**

El código sirve para el desarrollo, pero luego debe ser compilado por estos pre-procesadores, transformándolo en CSS estándar.

Con cada cambio que hace el diseñador/desarrollador al código SASS, los preprocesadores generan **automáticamente la versión CSS**. Por lo general ocurre en tiempo real y de forma automática en el entorno de desarrollo.

Para más información al respecto, visitar el sitio web oficial de SASS.
