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

Esta es la documentación que he recopilado para trabajar con CSS3, un lenguaje de creación de estilos en cascada.

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

Elementos del head
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

Elementos del body
##################

Cabeceras
*********
Las cabeceras son los textos iniciales de un documento o subtítulos o bien título de capítulos, estos se generan del siguiente modo de mayor a menor:

.. code:: html

    <h1>Título</h1>
    <h2>Subtítulo</h2>
    <h3>Título tercero</h3>
    <h4>Título cuarto</h4>
    <h5>Título quinto</h5>
    <h6>Título sexto</h6>

