==========
JavaScript
==========

.. image:: /logos/logo-js.png
    :scale: 55%
    :alt: Logo JS
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con JavaScript, el lenguaje de la web que se ha expandido considerablemente desde hace unos años.

.. contents:: Índice

Elementos básicos de Javascript
###############################
Para ejecutar Javascript desde la web tenemos que implementarlo en la página utilizando la etiqueta ``<script>``

Esta etiqueta la añadimos preferentemente por motivos de rendimiento justo antes de la etiqueta de cierre del ``<body>``.

.. code:: html

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
    </head>
    <body>
        <!-- Implementar una librería javascript desde un archivo externo -->
        <script src="app.js"></script>
    </body>
    </html>

Comentarios en Javascript
*************************
Existen dos clases de comentarios en Javascript:

1. Comentarios de una línea:

.. code:: javascript

    // Comentario de una línea

2. Comentario multilínea:

.. code:: javascript

    /* Comentario de 
    varias líneas
    donde poder escribir
    con más detalle
    */

Modo estricto
*************
El modo estricto o Strict mode revisa el código para comprobar si estamos trabajando correctamente:

.. code:: javascript

    "use strict"

con esta sentencia en la primera línea ya no podremos pasar sin decrarar variables entre otras cosas.

Entrada y salida
****************
Para la entrada de datos utilizamos el método ``prompt()`` del siguiente modo:

.. code:: javascript

    var nombre = prompt("¿Cómo te llamas?");

Y para la salida podemos utilizar ``alert()``:

.. code:: javascript

    alert('Me llamo Alfredo');

Otro método de salida común es la consola y para ello utilizamos ``console``:

.. code:: javascript

    console.log('Mensaje desde consola');

En ``console`` existen otros métodos como ``error()`` que destacan el mensaje de la consola con ese aspecto de fallo.

Reglas de Estilo
****************
La convención en Javascript es utilizar el estilo de escritura camelCase.

Lo que quiere decir que los nombres de las variables comenzarán siempre en minúscula e intercalarán cada palabra que la defina comenzando en mayúsculas: ``nombreDeVariable``

En el caso de las clases hay que comenzar el nombre en mayúsculas siempre: ``class MiClase``

Variables o Contenedores
########################
Cuando hablamos de variables o contenedores nos referimos a aquellos espacios de memoria donde almacenamos información.

Variables
*********
En JavaScript las variables tienen un alcance global y se declaran del siguiente modo:

.. code:: javascript

    let nombre = "Laura";
    // Usamos nuestra variable para mostrarla la información en consola:
    console.log(nombre);

Estos datos que almacenamos pueden ser modificados a lo largo de la ejecución del código.

Constantes
**********
Las constantes son un tipo de contenedor que tras ser asignado no permite la modificación de su contenido:

.. code:: javascript

    const PI = 3.1416;
    console.log(PI);

Tipos de datos
##############
Javascript cuenta con una serie de tipos de datos muy común.

Datos Numéricos
***************
Javascript cuenta con los siguientes tipos de numéricos:

#. Integer o Enteros: ``let edad = 31;``
#. Float o Coma Flotante: ``let precio = 32.44;``

También contamos con métodos para convertir los números:

#. Convertir cadena de texto a numérico: ``let ahoraEntero = Number(cadena);``
#. Conversión de Float a Integer: ``precioJusto = precio.parseInt();``
#. Conversión de Integer a Float: ``edadDecimal = edad.parseFloat();``

Cadenas de texto
****************
Las cadenas de texto son conjuntos de letras y números que conforman un dato.

#. Una cadena se puede asignar con comillas dobles: ``let nombre = "Pepe";``
#. También la podemos asignar con comillas simples: ``let nombre = 'Alfredo';``
#. Existe un tipo de cadena que se declara con acento grave y puede cargar variables:

.. code:: javascript

    let nombre = "Javier";

    let frase = `Te llamas ${nombre}`;

Jugar con comillas simples, dobles o plantillas nos brinda el uso de distintos caracteres.

Si queremos convertir un número en cadena:

.. code:: javascript

    let edad = String(miEdad);

Booleanos
*********
Los booleanos son un tipo de dato que solo ofrecen los valores True (verdadero) o False (falso).

Ejemplo de uso:

.. code:: javascript

    let heComido = True;

Objetos Literales
*****************



Métodos y objetos predefinidos de Javascript
###########################################
Javascript cuenta con una serie de métodos y objetos de los cuales podemos destacar algunos muy utilizados.

Fechas
******
Con el objeto ``date()`` podemos trabajar con fechas:

.. code:: javascript

    // Para empezar debemos crear un objeto nuevo:
    let fecha = new Date();

    // Si queremos obtener el día utilizamos el siguiente método:
    fecha.getDay();

    // Podemos ver cual es el día del mes:
    fecha.getDate();

    // Y así podemos obtener más tipos de datos como la hora:
    fecha.getHours();

    // Y podemos asignarle fechas:
    fecha.setDate(5);


#################





