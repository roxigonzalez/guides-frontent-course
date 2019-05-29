# Ajax

## Introducción

El método _XMLHttpRequest_ (XHR) permite a los navegadores comunicarse con el servidor sin la necesidad de recargar la página. Este método, también conocido como Ajax (_Asynchronous JavaScript and XML_), permite la creación de aplicaciones ricas en interactividad.

Las peticiones Ajax son ejecutadas por el código JavaScript, el cual envía una petición a una URL y cuando recibe una respuesta, una función de devolución puede ser ejecutada la cual recibe como argumento la respuesta del servidor y realiza algo con ella. Debido a que la respuesta es asíncrona, el resto del código de la aplicación continua ejecutándose, por lo cual, es imperativo que una función de devolución sea ejecutada para manejar la respuesta.

A través de varios métodos, jQuery provee soporte para Ajax, permitiendo abstraer las diferencias que pueden existir entre navegadores. Los métodos en cuestión son `$.get()`, `$.getScript()`, `$.getJSON()`, `$.post()` y `$().load()`.

A pesar que la definición de Ajax posee la palabra "XML", la mayoría de las aplicaciones no utilizan dicho formato para el transporte de datos, sino que en su lugar se utiliza HTML plano o información en formato JSON (_JavaScript Object Notation_).

## Conceptos Clave

La utilización correcta de los métodos Ajax requiere primero la comprensión de algunos conceptos clave.

### GET vs. POST

Los dos métodos HTTP más comunes para enviar una petición a un servidor son GET y POST.

El método GET debe ser utilizado para operaciones no-destructivas — es decir, operaciones en donde se esta "obteniendo" datos del servidor, pero no modificando. Por ejemplo, una consulta a un servicio de búsqueda podría ser una petición GET. Por otro lado, las solicitudes GET pueden ser almacenadas en la cache del navegador, pudiendo conducir a un comportamiento impredecible si no se lo espera. Generalmente, la información enviada al servidor, es enviada en una cadena de datos (en inglés _query string_).

El método POST debe ser utilizado para operaciones destructivas — es decir, operaciones en donde se está incorporando información al servidor. Por ejemplo, cuando un usuario guarda un artículo en un blog, esta acción debería utilizar POST. Por otro lado, este tipo de método no se guarda en la cache del navegador. Además, una cadena de datos puede ser parte de la URL, pero la información tiende a ser enviada de forma separada.

### Tipos de Datos

Generalmente, jQuery necesita algunas instrucciones sobre el tipo de información que se espera recibir cuando se realiza una petición Ajax. En algunos casos, el tipo de dato es especificado por el nombre del método, pero en otros casos se lo debe detallar como parte de la configuración del método:

text
~ Para el transporte de cadenas de caracteres simples.

html
~ Para el transporte de bloques de código HTML que serán ubicados en la página.

script
~ Para añadir un nuevo _script_ con código JavaScript a la página.

json
~ Para transportar información en formato JSON, el cual puede incluir cadenas de caracteres, vectores y objetos.

Es recomendable utilizar los mecanismos que posea el lenguaje del lado de servidor para la generación de información en formato JSON.

jsonp
~ Para transportar información JSON de un dominio a otro.

xml
~ Para transportar información en formato XML.

_A pesar de los diferentes tipos de datos de que se puede utilizar, es recomendable utilizar el formato JSON, ya que es muy flexible, permitiendo por ejemplo, enviar al mismo tiempo información plana y HTML._

### Asincronismo

Debido a que, de forma predeterminada, las llamadas Ajax son asíncronas, la respuesta del servidor no esta disponible de forma inmediata. Por ejemplo, el siguiente código no debería funcionar:

```javascript
var response;
$.get("foo.php", function(r) {
  response = r;
});
console.log(response); // indefinido (undefined)
```

En su lugar, es necesario especificar una función de devolución de llamada; dicha función se ejecutará cuando la petición se haya realizado de forma correcta ya que es en ese momento cuando la respuesta del servidor esta lista.

```javascript
$.get("foo.php", function(response) {
  console.log(response);
});
```

## Métodos Ajax de jQuery

Como se indicó anteriormente, jQuery posee varios métodos para trabajar con Ajax. Sin embargo, todos están basados en el método `$.ajax`, por lo tanto, su comprensión es obligatoria. A continuación se abarcará dicho método y luego se indicará un breve resumen sobre los demás métodos.

_Generalmente, es preferible utilizar el método \$.ajax en lugar de los otros, ya que ofrece más características y su configuración es muy comprensible._

### \$.ajax

El método `$.ajax` es configurado a través de un objeto, el cual contiene todas las instrucciones que necesita jQuery para completar la petición. Dicho método es particularmente útil debido a que ofrece la posibilidad de especificar acciones en caso que la petición haya fallado o no. Además, al estar configurado a través de un objeto, es posible definir sus propiedades de forma separada, haciendo que sea más fácil la reutilización del código. Puede visitar [http://api.jquery.com/jQuery.ajax/](http://api.jquery.com/jQuery.ajax/) para consultar la documentación sobre las opciones disponibles en el método.

**Utilizar el método \$.ajax**

```javascript
$.ajax({
  // la URL para la petición
  url: "post.php",

  // la información a enviar
  // (también es posible utilizar una cadena de datos)
  data: {id: 123},

  // especifica si será una petición POST o GET
  type: "GET",

  // el tipo de información que se espera de respuesta
  dataType: "json",

  // código a ejecutar si la petición es satisfactoria;
  // la respuesta es pasada como argumento a la función
  success: function(json) {
    $("<h1/>")
      .text(json.title)
      .appendTo("body");
    $('<div class="content"/>')
      .html(json.html)
      .appendTo("body");
  },

  // código a ejecutar si la petición falla;
  // son pasados como argumentos a la función
  // el objeto jqXHR (extensión de XMLHttpRequest), un texto con el estatus
  // de la petición y un texto con la descripción del error que haya dado el servidor
  error: function(jqXHR, status, error) {
    alert("Disculpe, existió un problema");
  },

  // código a ejecutar sin importar si la petición falló o no
  complete: function(jqXHR, status) {
    alert("Petición realizada");
  }
});
```

#### Opciones del método `$.ajax`

El método \$.ajax posee muchas opciones de configuración, y es justamente esta característica la que hace que sea un método muy útil. Para una lista completa de las opciones disponibles, puede consultar [http://api.jquery.com/jQuery.ajax/](http://api.jquery.com/jQuery.ajax/); a continuación se muestran las más comunes:

async
~ Establece si la petición será asíncrona o no. De forma predeterminada el valor es `true`. Debe tener en cuenta que si la opción se establece en `false`, la petición bloqueará la ejecución de otros códigos hasta que dicha petición haya finalizado.

cache
~ Establece si la petición será guardada en la cache del navegador. De forma predeterminada es `true` para todos los _dataType_ excepto para "_script_" y "_jsonp_". Cuando posee el valor `false`, se agrega una cadena de caracteres anti-cache al final de la URL de la petición.

complete
~ Establece una función de devolución de llamada que se ejecuta cuando la petición esta completa, aunque haya fallado o no. La función recibe como argumentos el objeto jqXHR (en versiones anteriores o iguales a jQuery 1.4, recibe en su lugar el objeto de la petición en crudo `XMLHTTPRequest`) y un texto especificando el estatus de la misma petición (`success`, `notmodified`, `error`, `timeout`, `abort`, o `parsererror`).

context
~ Establece el alcance en que la/las funciones de devolución de llamada se ejecutaran (por ejemplo, define el significado de `this` dentro de las funciones). De manera predeterminada `this` hace referencia al objeto originalmente pasado al método `$.ajax`.

data
~ Establece la información que se enviará al servidor. Esta puede ser tanto un objeto como una cadena de datos (por ejemplo `foo=bar&baz=bim`.)

dataType
~ Establece el tipo de información que se espera recibir como respuesta del servidor. Si no se especifica ningún valor, de forma predeterminada, jQuery revisa el tipo de _MIME_ que posee la respuesta.

error
~ Establece una función de devolución de llamada a ejecutar si resulta algún error en la petición. Dicha función recibe como argumentos el objeto jqXHR (en versiones anteriores o iguales a jQuery 1.4, recibe en su lugar el objeto de la petición en crudo `XMLHTTPRequest`), un texto especificando el estatus de la misma petición (`timeout`, `error`, `abort`, o `parsererror`) y un texto con la descripción del error que haya enviado el servidor (por ejemplo `Not Found` o `Internal Server Error`).

success
~ Establece una función a ejecutar si la petición ha sido satisfactoria.

timeout
~ Establece un tiempo en milisegundos para considerar a una petición como fallada.

traditional
~ Si su valor es true, se utiliza el estilo de serialización de datos utilizado antes de jQuery 1.4. Para más detalles puede visitar [http://api.jquery.com/jQuery.param/](http://api.jquery.com/jQuery.param/).

type
~ De forma predeterminada su valor es "GET". Otros tipos de peticiones también pueden ser utilizadas (como PUT y DELETE), sin embargo pueden no estar soportados por todos los navegadores.

url
~ Establece la URL en donde se realiza la petición.

La opción `url` es obligatoria para el método `$.ajax`;

Como se comentó anteriormente, para una lista completa de las opciones disponibles, puede consultar [http://api.jquery.com/jQuery.ajax/](http://api.jquery.com/jQuery.ajax/).

### Métodos Convenientes

En caso que no quiera utilizar el método `$.ajax`, y no necesite los controladores de errores, existen otros métodos más convenientes para realizar peticiones Ajax (aunque, como se indicó antes, estos están basados el método `$.ajax` con valores preestablecidos de configuración).

Los métodos que provee la biblioteca son:

\$.get
~ Realiza una petición GET a una URL provista.

\$.post
~ Realiza una petición POST a una URL provista.

\$.getScript
~ Añade un script a la página.

\$.getJSON
~ Realiza una petición GET a una URL provista y espera que un dato JSON sea devuelto.

Los métodos deben tener los siguientes argumentos, en orden:

url
~ La URL en donde se realizará la petición. Su valor es obligatorio.

data
~ La información que se enviará al servidor. Su valor es opcional y puede ser tanto un objeto como una cadena de datos (como `foo=bar&baz=bim`).

success callback
~ Una función opcional que se ejecuta en caso que petición haya sido satisfactoria. Dicha función recibe como argumentos la información de la petición y el objeto en bruto de dicha petición.

data type
~ El tipo de dato que se espera recibir desde el servidor. Su valor es opcional.

**Utilizar métodos convenientes para peticiones Ajax**

```javascript
// obtiene texto plano o html
$.get("/users.php", {userId: 1234}, function(resp) {
  console.log(resp);
});

// obtiene información en formato JSON desde el servidor
$.getJSON("/details.php", function(resp) {
  $.each(resp, function(k, v) {
    console.log(k + " : " + v);
  });
});
```

## Ejemplos
