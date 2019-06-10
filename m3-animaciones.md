# Animaciones

## Introducción

Animaciones: Generar sensación de movimiento.
En nuestra vida necesitamos, transiciones y animaciones. Sino, todo sería súper monótono y aburrido.
En la web también.

**Animación** es una transición, es lo que ocurre de un punto A a un punto B.

Tal como en las animaciones de papel. [Ver vídeo](https://www.youtube.com/watch?v=B2t3auzdUuk).

Se necesita tener muchos estados o transiciones para realizar una animación.

## CSS Transitions

Aprenderemos las propiedades CSS transitions para crear transiciones en el navegador.

Ejemplo:

```html
<div class="circle"></div>
```

```css
CSS .circle {
  width: 200px;
  height: 200px;
  background-color: cyan;
  border-radius: 50%;
  transition-property: background-color width height;
  transition-duration: 1s;
  transition-timing-function: linear;
  transition-delay: 0.5s;
}

.circle:hover {
  background-color: yellow;
  width: 300px;
  height: 300px;
}
```

```
/*Qué propiedades va a cambiar en la transición*/
transition-property: width, height;

/*Cuánto tiempo va a durar la transición*/
transition-duration: 1s;

/*Cuánto tiempo va a tardar la transición en ocurrir*/
transition-delay: 250ms;

/*Función que determina de qué forma se calculan los valores intermedios de la transición*/
transition-timing-function: ease;

```

Lista de propiedades que pueden ser cambiadas con `transition-property`

**transition-timing-function: **
ease: Especifica un efecto de transición con un arranque lento, luego rápido, luego finaliza lentamente (esto es predeterminado).
linear: Especifica un efecto de transición con la misma velocidad de principio a fin.
ease-in: Especifica un efecto de transición con un inicio lento.
ease-out: Especifica un efecto de transición con un final lento.
ease-in-out: Especifica un efecto de transición con un inicio y fin lentos.
cubic-bezier(n,n,n,n): Le permite definir sus propios valores en una función.

Otro buen ejemplo

Transformaciones CSS
La propiedad de transformación aplica una transformación 2D o 3D a un elemento. Esta propiedad le permite rotar, escalar, mover, sesgar, etc., elementos.

La propiedad CSS transform te permite modificar el espacio de coordenadas del modelo de formato visual CSS. Usándola, los elementos pueden ser trasladados, rotados, escalados o sesgados de acuerdo a los valores establecidos.
Si la propiedad tiene un valor diferente a none, se creará un contexto de pila. En ese caso, el objeto actuará como un bloque de contención para los elementos con "position: fixed" que contenga.

Rotate
Define una operación de rotación 2D de un elemento, especificando la cantidad de grados (deg) que este rotará en sentido de las manecillas del reloj.

```
transform:  rotate(deg); 	/* ej. rotate(90deg) */
```

Scale
Especifica una operación de escalado 2D descrita por [sx, sy]

```
transform:  scale(sx[, sy]);	/* ej. scale(2.5, 4)*/
```

Skew
Sesga el elemento a lo largo del eje X y Y por los ángulos especificados. Si no se proporciona ay, no se llevará a cabo el sesgo del eje Y.

```
transform:  skew(ax[, ay]); 	/* ej. skew(90deg,180deg)*/
```

Translate
Especifica una traslación 2D dada por el vector [tx, ty]. Si ty no es especificada, se asumirá que su valor es cero.

```
transform:  translate(tx[, ty]); 	/* ej. translate(50px, 100px) */
```

Ver también

Animaciones CSS
Las animaciones CSS3 permiten animar la transición entre un estilo CSS y otro. Las animaciones constan de dos componentes: un estilo que describe la animación CSS y un conjunto de fotogramas que indican su estado inicial y final, así como posibles puntos intermedios en la misma.
Las animaciones CSS tienen tres ventajas principales sobre las técnicas tradicionales de animación basada en scripts:
Son muy fácil usar para animaciones sencillas, puedes hacerlo incluso sin tener conocimientos de Javascript.
La animación se muestra correctamente, incluso en equipos poco potentes. Animaciones simples realizadas en Javascript pueden verse mal (a menos que estén muy bien hechas). El motor de renderizado puede usar técnicas de optimización como el "frame-skipping" u otras técnicas para mantener que la animación se vea tan suave como sea posible.
Al ser el navegador quien controle la secuencia de la animación, permitimos que optimice el rendimiento y eficiencia de la misma, por ejemplo, reduciendo la frecuencia de actualización de la animación ejecutándola en pestañas que no estén visibles.
Creando una animación
Para crear una secuencia de animación CSS, estilizarás el elemento que quieras animar con la propiedad `animation` y sus sub-propiedades. Con ellas podemos no solo configurar el ritmo y la duración de la animación sino otros detalles sobre la secuencia de la animación. Con ellas no configuramos la apariencia actual de la animación, para ello disponemos de `keyframes` como describiremos más adelante.
Las subpropiedades de `animation` son:
animation-delay
Tiempo de retardo entre el momento en que el elemento se carga y el comienzo de la secuencia de la animación.
animation-direction
Indica si la animación debe retroceder hasta el fotograma de inicio al finalizar la secuencia o si debe comenzar desde el principio al llegar al final.
animation-duration
Indica la cantidad de tiempo que la animación consume en completar su ciclo (duración).
animation-iteration-count
El número de veces que se repite. Podemos indicar infinite para repetir la animación indefinidamente.
animation-name
Especifica el nombre de la regla @keyframes que describe los fotogramas de la animación.
animation-play-state
Permite pausar y reanudar la secuencia de la animación
animation-timing-function
Indica el ritmo de la animación, es decir, como se muestran los fotogramas de la animación, estableciendo curvas de aceleración.
animation-fill-mode
Especifica qué valores tendrán las propiedades después de finalizar la animación (los de antes de ejecutarla, los del último fotograma de la animación o ambos).
Ejemplos en Gitlab
