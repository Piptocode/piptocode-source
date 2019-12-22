====
CSS3
====

.. image:: /logos/logo-css3.png
    :scale: 25%
    :alt: Logo CSS3
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con CSS3, un lenguaje de creación de estilos en cascada.

.. contents:: Índice

Funcionamiento de CSS
#####################
Con CSS podemos definir estilos recuperando etiquetas HTML de tres formas:

* Escribiendo el nombre de la etiqueta:

.. code:: CSS

    h1 {

    }

* Utilizando el atributo ID de la etiqueta el cual comienza siempre con almohadilla (#):

.. code:: CSS

    #identificador {

    }

* O usando el atributo clase de la etiqueta que comienza con punto (.):

.. code:: CSS

    .clase {

    }

De ese modo vamos insertando dentro de los paréntesis las reglas de estilo con las cuales podremos definir tamaño de textos, colores, posición, animaciones, etc...

Fuentes
#######

Con la etiqueta ``font`` y sus derivados podemos elegir y personalizar las fuentes de nuestro sitio web.

Existen una serie de fuentes que vienen con el sistema:

* Serif
* Sans-Serif
* Monospace
* Cursiva
* Times
* Arial
* Courier
* Comic Sans
* Times New Roman
* Helvetica
* Courier New
* Georgia
* Verdana
* Monaco
* Geneva

Estas fuentes por lo general siempre están instaladas en el ordenador del cliente y por tanto podemos utilizarlas.

Elegir una fuentes
******************
Para elegir una fuente seleccionamos la etiqueta html, id o clase que queremos personalizar y utilizamos la regla ``font-family``:

.. code:: CSS

    p {
        font-family: Arial, Helvetica, Verdana, sans-serif;
    }

Cargar fuentes externas
***********************
Podemos utilizar fuentes de un CDN para nuestros proyectos o fuentes que instalamos en nuestro propio equipo:

1. Añadir una fuente con la regla ``@font-face``:

.. code:: CSS

    @font-face{
    font-family: 'fontName';
    src: url('fontName.eot');
    src: url('fontName.eot?#iefix') format('embedded-opentype'),
        url('fontName.woff') format('woff'),
        url('fontName.ttf') format('truetype'),
        url('fontName.svg#svgFontName')format('svg');
    }

2. Seleccionar la fuente anterior

.. code:: CSS

    p {
        font-family: fontName;
    }

Definir tamaño de texto
***********************
Para cambiar el tamaño de texto se utiliza la regla ``font-size``:

.. code:: CSS

    h1{
        font-size: 18px;
    }

Se suele definir su tamaño en Pixels (px), porcentajes (%), Em (em) o Rem (rem).

Definir grosor de texto
***********************
Para definir el grosor de la fuente utilizamos la regla ``font-weight`` que posee los siguientes valores:

* normal: normal
* bold: grueso
* bolder: más grueso
* lighter: más fino
* 100
* 200
* 300
* 400
* 500
* 600
* 700
* 800
* 900
* inherit: heredado

Lo definimos del siguiente modo:

.. code:: CSS

    p {
        font-weight: bolder;
    }

Transformar texto de minúsculas a mayúsculas y viceversa
********************************************************
Para transformar un texto de mayúsculas a minúsculas utilizamos la regla ``text-transform`` que tiene dos opciones:

* lowercase: minúsculas
* uppercase: mayúsculas

Lo definimos del siguiente modo:

.. code:: CSS

    p {
        text-transform: uppercase;
    }

Alineación de texto
*******************
Para alinear un texto la regla que debemos utilizar es ``text-align`` que tiene los siguientes valores:

* left
* center
* right
* justify

Lo definimos del siguiente modo:

.. code:: CSS

    p {
        text-align: center
    }

Aplicar sangría a la primera línea
**********************************
Podemos identar el texto utilizando la regla ``text-indent`` y añadiendo un valor en px, %, em o rem.

Lo definimos del siguiente modo:

.. code:: CSS

    p {
        text-indent: 1em;
    }

Separación entre caracteres
***************************
La separación de caracteres se aplica con la regla ``letter-spacing`` en valores:

.. code:: CSS

    p {
        letter-spacing: 1em;
    }

Espacio entre líneas
********************
Para modificar el espacio entre cada línea se utiliza la regla ``line-height`` seguido de un número decimal:

.. code:: css

    p {
        line-height: 1.7;
    }

