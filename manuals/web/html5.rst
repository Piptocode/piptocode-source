=====
HTML5 
=====
 
.. image:: /logos/logo-html5.png
    :scale: 25%
    :alt: Logo HTML5
    :align: center

.. |date| date::
.. |time| date:: %H:%M
 
Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con HTML5, HyperText Markup Language que se utiliza para crear la estructura de un sitio web.

.. contents:: Índice
 
Sintaxis HTML5
##############
HTML5 se basa en el uso de etiquetas definidas para cada función como cabeceras, párrafos, contenedores, imágenes, videos, enlaces...

La estructura básica de una etiqueta html es la siguiente:

.. code:: html

    <head>

* Esto es una etiqueta html completa con contenido y etiqueta de cierre:

.. code:: html

    <p>esto es un párrafo</p>

* También existen etiquetas html que no utilizan etiqueta de cierre:

.. code:: html

    <img src="foto.jpg">

Cada etiqueta tiene uno o varios atributos disponibles para personalizarla como es el caso de ``src`` en el ejemplo anterior.

Existen dos clases de atributos que sirven para todas las etiquetas html:
Lo que se encuentra entre comillas definido en el atributo se denomina valor.

* id: sirve para establecer un identificador que utilizaremos para personalizar con CSS y JavaScript nuestra etiqueta.
* class: sirve exactamente para lo mismo que id.
* data-: el prefijo data- seguido de cualquier palabra sirve para añadir metadatos a nuestros archivos multimedia. Ej: "data-formato", "data-duracion".
* title: con title podemos definir una frase o palabra que se mostrará cuando situemos el cursor sobre la etiqueta que lo posee.

Generalmente y aunque se puede utilizar tanto uno como el otro para los mismos propósitos, en lo personal yo acostumbro a utilizar id para trabajar con JavaScript y class para trabajar con CSS

Ejemplo de uso:

.. code:: html

    <div class = "contenedor-uno">
    
    </div>

Comentarios en HTML5
********************
Los comentarios podemos utilizarlos del siguiente modo:

.. code:: html

    <!-- Esto es un comentario -->

Realizar un salto de línea
**************************
Para realizar un salto de línea utilizamos la etiqueta ``<br>``

Añadir línea divisora
*********************
Para añadir una línea divisora horizontal utilizamos la etiqueta ``<hr>``

Crear un contenedor
*******************
Un contenedor es una estructura donde colocaremos distintas etiquetas html y se utiliza para crear secciones y objetos que tendrán distintos estilos en nuestro código:

.. code:: html

    <div>
        <h2>Esto es una cabezera</h2>
        <p>Esto es un párrafo</p>
    </div>

También existen las etiquetas ``<span>`` que tienen un funcionamiento similar a div pero se suelen utilizar para encapsular cosas más pequeñas.

Estructura HTML5
****************
La estructura básica de un documento HTML5 se define con las siguientes etiquetas:

* <!DOCTYPE HTML>: Etiqueta con la que se declara la versión de HTML que utilizamos la cual es la versión 5.
* <html>: Define el tipo de documento que estamos trabajando.
* <head>: Es la cabecera del documento, aquí se añade la meta información y vinculamos hojas de estilos, fuentes, etc...
* <body>: Es donde escribimos las etiquetas HTML que comprenderán nuestro código.

Ejemplo de estructura base:

.. code:: html

    <!DOCTYPE HTML>
    <html lang = "es">
        <head>
        
        </head>
        <body>
        
        </body>
    </html>

Semántica HTML5
***************
Este tipo de estructura que encontramos dentro del body sirve para que cuando un motor de búsqueda lea nuestro sitio web sepa exactamente que partes de su contenido corresponden a cada una de las partes típicas de un sitio, estas etiquetas funcionan exactamente igual que ``<div>``.

Existen las siguientes etiquetas:

* <section>: se utiliza para representar una sección general.
* <article>: Representa un componente de una página tipo documento o página.
* <aside>: Suele ser un contenido que se dispone en un lateral, como un menú vertical entre otras cosas.
* <header>: Indica que estamos trabajando con la cabecera del sitio web.
* <nav>: Sirve para indicar que estamos en la barra de navegación.
* <footer>: Representa el pie de página.

Estructura común semántica HTML5:

.. code:: html

    <html>
        <head>
        
        </head>
        <body>
            <header>
                
            </header>
            <nav>
            
            </nav>
            <article>
                <section>
                
                </section>
            </article>
            <aside>
            
            </aside>
            <footer>
            
            </footer>
        </body>
    </html>

Etiquetas del head
##################
Estas son las distintas etiquetas disponibles para configurar nuestro documento con las que podemos:

* Definir la codificación de caracteres, normalmente utilizamos UTF-8:

.. code:: html

    <meta charset = "utf-8" />

* Definir el título de la página que aparece en la pestaña del navegador:

.. code:: html

    <title>Título de mi página</title>

* Definir la descripción del sitio web para los navegadores:

.. code:: html

    <meta name = "description" content = "Esta es una descripción del sitio web" />

* Definir palabras clave para mejorar su indexación:

.. code:: html

    <meta name = "keywords" content = "clave, palabra clave, frase mágica, magia" />

* Definir el autor de la página:

.. code:: html

    <meta name = "author" content = "Guillermo Granados Gómez" />

* Definir la importación de una hoja de estilo:

.. code:: html

    <link rel = "stylesheet" href = "style.css" />

* O declarar un script que para mejora del rendimiento es preferible hacerlo antes del cierre de body:

.. code:: html

    <script src = "script.js"></script>

Etiquetas del body
##################

Cabeceras
*********
Las cabeceras son los textos iniciales de un documento o subtítulos o bien título de capítulos, estos se generan del siguiente modo de mayor a menor con etiquetas que van desde ``<h1>`` hasta ``<h6>``:

.. code:: html

    <h1>Título</h1>
    <h2>Subtítulo</h2>
    <h3>Título tercero</h3>
    <h4>Título cuarto</h4>
    <h5>Título quinto</h5>
    <h6>Título sexto</h6>

Párrafos
********
Con la etiqueta ``<p>`` podemos añadir párrafos a nuestro documento html del siguiente modo:

.. code:: html

    <p>Esto es un párrafo</p>

Enlaces 
*******
Podemos enlazar páginas, documentos, imágenes, etc con la ayuda de la etiqueta ``<img>`` y sus atributos específicos:

* href: Requerido para establecer la ruta del archivo. Posee rutas especiales como
    * Ruta de archivo: "carpeta/archivo.html"
    * Vínculo externo: "https://www.google.es"
    * Vínculo hacia una parte del documento: "#id-etiqueta"
    * Abrir en correo: "mailto:direccion@email.com"
    * Abrir en teléfono: "tel:600600600
* ping: sirve para notificar a otra url que se ha pulsado el Vínculo
* download: Indica que al hacer clic se descargue el archivo.

Ejemplo de uso:

.. code:: html

    <a href="archivo.html">Ir a Archivo</a>

Listas
******
Tenemos una serie de etiquetas para crear listas que si son numeradas comienzan con la etiqueta ``<ol>`` y si son viñetas comienza con ``<ul>``.
Para añadir elementos a la lista introduciremos etiquetas ``<li>`` tantas veces como elementos queramos introducir. 
Las listas poseen el siguiente atributo:

* reversed: ordena la lista numérica en orden decreciente.

Ejemplo de uso:

.. code:: html

    <ul>
        <li>Elemento 1</li>
        <li>Elemento 2</li>
        <li>Elemento 3</li>
    </ul>

Imágenes 
********
Para visualizar imágenes en el documento utilizamos la etiqueta ``<img>`` con los siguientes atributos:

* src: Requerido para establecer la ruta del archivo.
* alt: Recomendado, añade un texto alternativo si no se carga la página.

Ejemplo de uso:

.. code:: html

    <img src="imagen.png" alt="Mapa del Tesoro">

Cita
****
Añade un texto un poco desplazado a la derecha con la etiqueta ``<blockquote>``:

.. code:: html

    <blockquote>
        "El que no arriesga, no gana"
    </blockquote>

Elementos expandibles
*********************
Crea un texto desplegable con contenido oculto, se compone de una etiqueta ``<details>`` la cual llevará dentro una etiqueta inicial llamada ``<summary>`` y todo lo que siga debajo de esta anterior solo se verá al pinchar en el desplegable:

.. code:: html

    <details>
        <summary>Texto Visible</summary>
        <p>Contenido coulto de la página</p>
    </details>

Letra pequeña
*************
Se puede generar una letra específicamente más pequeña con la etiqueta ``<small>``:

.. code:: html

    <small>Sitio web creado por Guillermo Granados Gómez</small>

Citar texto
***********
Al añadir la etiqueta ``<cite>`` en alguna frase o palabra esta se verá en formato cursivo:

.. code:: html

    <p>En este <cite>párrafo</cite> podemos ver la cita</p>

Resaltar texto
**************
Al añadir la etiqueta ``<strong>`` en alguna frase o palabra esta se verá en formato negrita:

.. code:: html

    <p>En este <strong>párrafo</strong> se puede apreciar una palabra en negrita.</p>

Tachar texto
************
Al añadir la etiqueta ``<s>`` en alguna frase o palabra esta se verá tachada:

.. code:: html

    <p>En este <s>párrafo</s> vemos un texto tachado.</p>

Agregar Audio
*************
Para añadir un archivo de audio que se reproduzca en el navegador utilizamos la etiqueta ``<audio>`` la cual posee los siguientes atributos:

* src: Requerido para localizar la ruta del archivo de sonido.
* controls: establece un panel de control.
* autoplay: ejecutará el archivo de audio tras cargar la página.
* loop: el archivo de audio se repite siempre cuando finaliza.
* preload: sirve para establecer que el archivo no sea almacenado en cache, para comprobar si tiene metadatos y para establecer que si se almacene en cache "por defecto"

Ejemplo de uso:

.. code:: html

    <audio src="sonido.mp3" controls></audio>

Agregar Vídeos
**************
Podemos insertar archivos de video e incluso tener un sencillo reproductor generado automáticamente con html utilizando la etiqueta ``<video>`` y en su interior añadiremos el video en distintos formatos con la etiqueta ``<source>`` y poseen los siguientes atributos:

* controls: en video - Establece un panel de control.
* autoplay: en video - reproducirá el archivo al cargar la página.
* loop: en video - repetirá indefinidamente el video cada vez que termine
* preload: sirve para establecer que el archivo no sea almacenado en cache, para comprobar si tiene metadatos y para establecer que si se almacene en cache "por defecto"
* poster: en video - carga una imagen en el video de espera cuando este no esta reproduciéndose.
* mute: en video - el video se muestra en silencio.
* src: en source - vincula el archivo de vídeo a nuestro archivo html.

Ejemplos de uso:

.. code:: html

    <video controls poster = "fotoPoster.png">
        <source src="video.mp4">
        <source src="video.mkv">
    </video>

Crear un lienzo
***************
Un lienzo es un apartado dinámico donde podemos generar animaciones que el usuario tiene la posibilidad de interactuar con ellas. Para ello se utiliza la etiqueta ``<canvas>``:

.. code:: html

    <canvas id="lienzo">
        <p>Texto que aparecerá si el navegador no es compatible con canvas</p>
    </canvas>

Incrustrar un sitio web externo
*******************************
Con la etiqueta ``<iframe>`` podemos incrustrar una página web en una porción de la nuestra, su uso más habitual es el de cargar videos externos o mapas:

.. code:: html

    <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m12!1m3!1d4455419.399511362!2d-4.148695983812638!3d39.545659644016645!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!5e0!3m2!1ses!2ses!4v1577590100649!5m2!1ses!2ses" width="600" height="450" frameborder="0" style="border:0;" allowfullscreen=""></iframe>

Nota: El motor de búsqueda Google no ve con buenos ojos esta práctica más allá de cargar mapas y videos entre otras cosas.

Crear un botón
**************
Los botones se generan con la etiqueta ``<button>`` y pueden tener distintas finalidades y se suelen accionar desde javascript capturandolos a través de su id.

.. code:: html

    <button id="saluda">Pinchame</button>

    <script>
    document.getElementById('saluda').addEventListener('click', () =>{
        alert('Hola');
    });
    </script>

Con un script podemos trabajar recuperando elementos HTML e interactuar con la página web.

Formularios
###########
Los formularios conforman una serie de campos donde normalmente transmitiremos información al lado del servidor. 
Estos se generan con la etiqueta ``<form>`` y posee los siguientes atributos:

* method: Es el método con el que se transmiten los datos que puede ser GET o POST
    * GET: Los datos se envían por la url a través de parámetros y se utiliza principalmente para recuperar información.
    * POST: Los datos se envían ocultos para que el usuario no pueda verlos con el propósito de hacer el envío más seguro. 
* action: Este atributo sirve para identificar el archivo del lado del servidor que recibirá y procesará la información.
* enctype: Este atributo se suele utilizar con la opción "multipart/form-data" y sirve para indicar al servidor que va a recibir un archivo en uno de sus campos.

Ejemplo de estructura de un formulario de login:

.. code:: html

    <form method="POST" action="login.php">
        <label for="username">Usuario: </label>
        <input type="text" name="username" placeholder="usuario">
        <label for="password">Contraseña: </label>
        <input type="password" name="password" placeholder="contraseña">
        <input type="submit" value="Iniciar Sesión">
    </form>

Etiqueta label
**************
La etiqueta ``<label>`` sirve para añadir un texto específico para un campo del formulario y lo hacemos utilizando el atributo ``for`` el cual se vincula al atributo ``name`` de la etiqueta ``<input>`` del siguiente modo:

.. code:: html

    <label for="usuario">Usuario: </label>
    <input type="text" name="usuario">

Campos del formulario
*********************
Para trabajar con los campos del formulario se utiliza la etiqueta ``<input>`` que va acompañada de los siguientes atributos:

* name: Obligatorio - Sirve para que el servidor pueda identificar y procesar el campo.
* type: Obligatorio - Sirve para definir con que tipo de campo estamos trabajando y posee los siguientes valores
    * text: Texto sencillo.
    * password: Contraseña.
    * submit: botón para procesar formulario.
    * reset: botón para vaciar el formulario.
    * email: dirección de correo electrónico.
    * checkbox: casilla de comprobación. Se utiliza el atributo ``checked`` en el mismo input cuando queremos marcar por defecto una casilla.
    * color: despliega un menu de seleccion de colores.
    * date: despliega un menu de fechas.
    * file: sirve para subir un archivo al servidor. Se utiliza siempre junto al atributo ``enctype`` en la etiqueta ``<form>``.
    * hidden: campo oculto, envía información oculta.
    * number: campo para introducir números. Recibe también atributos ``min`` y ``max`` para indicar el rango de números permitidos.
    * radio: botón de selección. Sirve para seleccionar una sola opción que acompañamos con el atributo ``value`` siempre para indicar al servidor la opción escogida. Se puede utilizar el atributo ``checked`` para establecer una opción por defecto. 
    * range: Sirve para introducir un número que indicaremos entre un atributo ``min`` y un atributo ``max`` de modo que nunca podrá superar ninguno de los dos. Se puede utilizar el atributo ``step`` para indicar el salto entre números cuando vamos escogiendolos.
    * search: Cuadro de texto específico para realizar búsquedas.
    * tel: Sirve para introducir un número de teléfono.
    * url: campo de URL.
* placeholder: sirve para poner un texto en las casillas que desaparece cuando comenzamos a escribir.
* autofocus: se selecciona el campo por defecto al arrancar la página.
* autocomplete: sirve para recordar información en los campos y tiene dos valores ``on`` por defecto y ``off``
* required: campo requerido, el formulario no se envía si está en blanco.
* pattern: sirve para establecer unas reglas de escritura. Ej de validación código postal: ``pattern="[0-9]{5}"``
* value: introduce un valor por defecto en el campo.
* maxlength: establece un número máximos de caracteres permitidos
* minlength: establece un número de caracteres mínimos permitidos.
* readonly: El campo se mostrará pero no podremos rellenarlo.

Ejemplo de campo input:

.. code:: html

    <input type="text" name="usuario" placeholder="introduce el nombre de usuario" required>

Selector
********
En los formularios también contamos con un campo de tipo selector y este se genera con la etiqueta ``<select>`` el cual recibirá dentro las distintas opciones con etiquetas ``<option>``:

* selected: es un atributo que indica la opción escogida por defecto.

.. code:: html

    <select name="lista">
        <option value="1">Elemento 1</option>
        <option value="2" selected>Elemento 2</option>
        <option value="3">Elemento 3</option>
    </select>

Caja de texto
*************
Existe otro tipo de campo que se genera con la etiqueta ``<textarea>`` y este nos presenta una caja de texto que va cambiando de tamaño de forma dinámica. Posee los mismos atributos que input y algunos propios como:

* rows: recibe un valor numérico y establece el número de filas.
* cols: recibe un valor numérico y establece el número de columnas. 

.. code:: html

    <textarea name="texto" placeholder="aparezco si borras el siguiente texto" rows="30" cols="40">Aquí se muestra un texto de ejemplo</textarea>

Agrupar apartados del formulario
********************************
Con la etiqueta ``<fieldset>`` podemos agrupar apartados del formulario y este va acompañado normalmente de la etiqueta ``<legend>`` que nos muestra un texto en el recuadro del apartado:

.. code:: html

    <form>
        <fieldset name="datos-personales">
            <legend>Datos personales</legend>
            <input type="text" name="nombre" placeholder="nombre">
        </fieldset>
    </form>

Ejemplo de formulario de registro
*********************************
Este es un ejemplo de un formulario de registro para ver todos los campos disponibles:

.. code:: html

    <form method="POST" action="registro.php" enctype="multipart/form-data">
        <fieldset>
        <legend>Datos personales</legend>
        <label for="nombre">Nombre completo:</label>
        <input type="text" name="nombre" placeholder="Nombre y apellidos" autofocus required>
        <label for="nacimiento">Fecha de nacimiento:</label>
        <input type="date" name="nacimiento" required>
        <label>Género:</label>
        <input type="radio" name="masculino" value="ok">Masculino
        <input type="radio" name="femenino" value="ok">Femenino
        <label for="telefono">Número de teléfono:</label>
        <input type="tel" name="telefono" pattern="[0-9]{9}" minlength="9" maxlength="9" placeholder="Tu número de teléfono">
        <label for="dni">DNI: </label>
        <input type="file" name="dni" required>
        <label for="color">Color favorito:</label>
        <input type="color" name="color">
        <label for="favorito">Número favorito:</label>
        <input type="number" name="favorito" min="1" max="10" placeholder="debe ser un número del 1 al 10">
        <label for="pagina">Sitio web personal: </label>
        <input type="url" name="pagina" placeholder="Si tienes web rellena este campo">
        <label for="provincia">Provincia (Andalucía): </label>
        <select name="provnicia">
            <option selected>Elige tu provincia</option>
            <option value="malaga">Málaga</option>
            <option value="cadiz">Cádiz</option>
            <option value="huelva">Huelva</option>
            <option value="sevilla">Sevilla</option>
            <option value="jaen">Jaén</option>
            <option value="cordoba">Córdoba</option>
            <option value="almeria">Almería</option>
            <option value="granada">Granada</option>
            <option value="ceuta">Ceuta</option>
            <option value="melilla">Melilla</option>
        </select>
        </fieldset>
        <fieldset>
        <legend>Tipo de solicitud</legend>
        <input type="checkbox" name="basico" value="ok"> Plan básico
        <input type="checkbox" name="medio" value="ok" checked> Plan intermedio
        <input type="checkbox" name="avanzado" value="ok"> Plan avanzado
        <label for="observaciones">Observaciones:</label>
        <textarea name="observaciones" placeholder="Informanos de todo aquello que necesites" cols="40" rows="10" maxlength="100"></textarea>
        </fieldset>
        <fieldset>
        <legend>Datos de acceso</legend>
        <label for="correo">Correo Electrónico:</label>
        <input type="email" name="correo" placeholder="Introduce tu dirección de Email" required>
        <label for="password">Contraseña:</label>
        <input type="password" name="password" placeholder="Introduce tu contraseña" required>
        <input type="text" value="La contraseña debe ser fuerte" readonly>
        </fieldset>
        <input type="hidden" name="oculto" value="información secreta">
        <input type="submit" value="Darse de alta">
        <input type="reset" value="vaciar campos">
    </form>

