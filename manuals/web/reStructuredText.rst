================
reStructuredText
================

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con Sphinx, un framework que tiene como proposito la creación de sitios web orientados a la documentación como es este mismo sitio.

.. contents:: Índice

Estilo de fuente
################
Para añadir estilo al texto hay que rodearlo con el siguiente formato:

* Texto en negrita: ``**negrita**`` 

Ejemplo: **negrita**

* Texto remarcado en bloque de código: ````print()````

Ejemplo: ``print()``

Listados
########
Hay dos tipos de listado que podemos definir:

* Listado por puntos:

.. code-block:: 

    * Elemento 1
        * subelemento
    * Elemento 2

Ejemplo: 

* Elemento 1
    * subelemento
* Elemento 2


* Listado numerico:

.. code-block::

    #. Un elemento
        #. Subelemento
    #. Otro elemento

Ejemplo:

#. Un elemento
    #. Subelemento

* Listado vacio:

.. code-block::
    
    | Un elemento
    | otro elemento

Ejemplo:

| Un elemento
| otro elemento

* Listado horizontal:

.. code-block::

    .. hlist::
        :columns: 3

        * A list of
        * short items
        * that should be
        * displayed
        * horizontally

Ejemplo:

.. hlist::
    :columns: 3

    * A list of
    * short items
    * that should be
    * displayed
    * horizontally

Bloque Literal
##############

Un bloque literal es un bloque que se encuentra más desplazado a la derecha y se presenta con un título destacado:

.. code-block::

    Esto es un texto normal. Lo siguiente es un bloque literal::
        Esto es un texto literal,
        va un poco más desplazado a la derecha

    Y listo

Ejemplo:

Esto es un texto normal. Lo siguiente es un bloque literal::
    Esto es un texto literal,
    va un poco más desplazado a la derecha

Y listo

Línea de código
###############

Es un bloque que tiene un prompt de estilo consola de python:

.. code-block::

    >>> Y aqui tenemos un codigo con prompt

Ejemplo: 

>>> cd documents

Tablas
######

Hay dos formas comunes de crear una tabla:

* Completa:

.. code-block::

    +--------------------+---------------+----------------+
    | Cabecera 1         | Cabecera 2    | Cabecera 3     |
    | Columna opcional   |               |                |
    +====================+===============+================+
    | Cuerpo 1, columna1 | columna 2     | columna 3      |
    +--------------------+---------------+----------------+
    | Cuerpo 2           | ...           |                |
    +--------------------+---------------+----------------+

Ejemplo:

+--------------------+---------------+----------------+
| Cabecera 1         | Cabecera 2    | Cabecera 3     |
| Columna opcional   |               |                |
+====================+===============+================+
| Cuerpo 1, columna1 | columna 2     | columna 3      |
+--------------------+---------------+----------------+
| Cuerpo 2           | ...           |                |
+--------------------+---------------+----------------+

* Sencilla:

.. code-block::

    ===== =====
    A      B
    ===== =====
    Falso xdd
    Verda vss
    Falso fas
    ===== =====

Ejemplo:

===== =====
A      B
===== =====
Falso xdd
Verda vss
Falso fas
===== =====

Links
#####

Para crear un enlace podemos utilizar el siguiente código:

.. code-block::

    Enlaces, para ir a google `aquí <https://google.es>`_.

Ejemplo:

Enlaces, para ir a google `aquí <https://google.es>`_.

Encabezados
###########

* Encabezado sección:

.. code-block::

    =======================
    Encabezado para sección
    =======================

.. code-block::

    Encabezado para partes
    ######################

.. code-block::

    Encabezado para capitulos
    *************************

.. code-block::

    Encabezado para subsecciones
    ----------------------------

.. code-block::

    para parrafos
    """""""""""""

Cada uno va generando distintos niveles de profundidad en la navegación de la web.

Campos destacados
#################

son textos que podemos desctacar con : : y luego añadirles una descripción

.. code-block::

    :campo: Texto del campo

Ejemplo:

:campo: Texto del campo

Mensajes
########

Podemos mostrar distintos mensajes de alerta entre otras cosas para los lectores:

* Atención:

.. code-block::

    .. attention::
        Texto de atención

Ejemplo:

.. attention::
    Texto de atención

* Precaución:

.. code-block::

    .. caution::
        Texto de cuidado

Ejemplo:

.. caution::
    Texto de cuidado

* Peligro:

.. code-block::

    .. danger::
        Texto de peligro

Ejemplo:

.. danger::
    Texto de peligro

* Error:

.. code-block::

    .. error::
        Texto de error

Ejemplo:

.. error::
    Texto de error

* Sugerencia:

.. code-block::

    .. hint::
        Texto de sugerencia

Ejemplo:

.. hint::
    Texto de sugerencia

* Importante:

.. code-block::

    .. important::
        Texto de importante

Ejemplo:

.. important::
    Texto de importante

* Nota: 

.. code-block::

    .. note::
        Texto de nota

Ejemplo:

.. note::
    Texto de nota

* Truco:

.. code-block::

    .. tip::
        Texto de consejo

Ejemplo:

.. tip::
    Texto de consejo

* Peligro: 

.. code-block::

    .. warning::
        Texto de alerta

Ejemplo:

.. warning::
    Texto de alerta

Imágenes
########

Podemos cargar imágenes y ajustarlas a nuestro gusto:

.. code-block::

    .. image:: picture.jpg
        :height: 100px
        :width: 200 px
        :scale: 50 %
        :alt: alternate text
        :align: right

Ejemplo:

.. image:: ../../picture.jpg
    :height: 1000 px
    :width: 2000 px
    :scale: 50 %
    :alt: alternate text
    :align: center

Entrada
#######

Similar a la entrada de un blog o una red social

.. code-block::

    .. topic:: Topic Title

        Subsequent indented lines comprise
        the body of the topic, and are
        interpreted as body elements.

Ejemplo:

.. topic:: Topic Title

    Subsequent indented lines comprise
    the body of the topic, and are
    interpreted as body elements.


Barra Lateral
#############

Una barra lateral a la derecha donde poner texto entre otras cosas

.. code-block::

    .. sidebar:: Sidebar Title
        :subtitle: Optional Sidebar Subtitle

        Subsequent indented lines comprise
        the body of the sidebar, and are
        interpreted as body elements.

Ejemplo:

.. sidebar:: Sidebar Title
    :subtitle: Optional Sidebar Subtitle

    Subsequent indented lines comprise
    the body of the sidebar, and are
    interpreted as body elements.

Bloque de texto
###############

Un bloque de texto es un texto que esta más desplazado a la derecha:

.. code-block::

    .. line-block::

        Lend us a couple of bob till Thursday.
        I'm absolutely skint.
        But I'm expecting a postal order and I can pay you back
            as soon as it comes.
        Love, Ewan.

Ejemplo:

.. line-block::

    Lend us a couple of bob till Thursday.
    I'm absolutely skint.
    But I'm expecting a postal order and I can pay you back
        as soon as it comes.
    Love, Ewan.

Bloque de código
################

En un bloque de código podemos escribir el código de nuestros programas y podemos hacerlo de distintas formas:

* De forma sencilla:

.. code-block::

    .. code-block:: 

        def my_function():
            "just a test"
            print 8/2

Ejemplo:

.. code-block:: 

    def my_function():
        "just a test"
        print 8/2

* Para un lenguaje de programación conocido:

.. code-block::

    .. code:: python

        def my_function():
            "just a test"
            print 8/2

Ejemplo:

.. code:: python

    def my_function():
        "just a test"
        print 8/2

* Combinado con un texto explicativo:

.. code-block::

    .. compound::

        The 'rm' command is very dangerous.  If you are logged
        in as root and enter ::

            cd /
            rm -rf *

        you will erase the entire contents of your file system.

Ejemplo:

.. compound::

    The 'rm' command is very dangerous.  If you are logged
    in as root and enter ::

        cd /
        rm -rf *

    you will erase the entire contents of your file system.

* Bloque de código numerado:

.. code-block::

    .. code-block:: javascript
        :linenos:

        function saludar(){
                console.log('Hola mundo');
            }

Ejemplo:

.. code-block:: javascript
    :linenos:

    function saludar(){
            console.log('Hola mundo');
        }

Comenzar a partir de cierto número definido y poner nombre al archivo:

.. code-block::

    .. code-block:: python
        :caption: this.py
        :name: this-py

        print 'Explicit is better than implicit.'

Ejemplo:

.. code-block:: python
    :caption: this.py
    :name: this-py

    print 'Explicit is better than implicit.'

O subrayar partes del código:

    .. code-block:: python
        
        .. code-block:: python
            :emphasize-lines: 3,5

            def some_function():
                interesting = False
                print 'This line is highlighted.'
                print 'This one is not...'
                print '...but this one is.'

Ejemplo:

.. code-block:: python
    :emphasize-lines: 3,5

    def some_function():
        interesting = False
        print 'This line is highlighted.'
        print 'This one is not...'
        print '...but this one is.'

Fórmulas matemáticas
####################

Estilo definido para formulas matemáticas.

.. code-block::

    .. math::

        α_t(i) = P(O_1, O_2, … O_t, q_t = S_i λ)

Ejemplo:

.. math::

    α_t(i) = P(O_1, O_2, … O_t, q_t = S_i λ)

Epígrafe
########

Introducir epígrafes en la página

.. code-block::

    .. epigraph::

        No matter where you go, there you are.

        -- Buckaroo Banzai

Ejemplo:

.. epigraph::

    No matter where you go, there you are.

    -- Buckaroo Banzai

Índice
######

Crea un índice en base a todas las cabeceras de la página en la que se encuentra
y la va organizando de forma jerárquica

* Índice normal:

    .. code-block::

        .. contents:: Tabla de contenidos

* Índice abreviado:

    .. code-block::

        .. contents:: Tabla reducida
            :depth: 2

Puedes ver un ejemplo de índice con el mismo índice de esta página.

Meta data
#########

Genera etiquetas de meta data para la cabecera del documento html final:

.. code-block::

    .. meta::
        :description: The reStructuredText plaintext markup language
        :keywords: plaintext, markup language

    .. meta::
        :description lang=en: An amusing story
        :description lang=fr: Une histoire amusante

Fecha y hora
############

Crea un registro de la fecha y hora a la que se ha guardado el documento:

.. code-block::

    .. |date| date::
    .. |time| date:: %H:%M

    Today's date is |date|.

    This document was generated on |date| at |time|.

Ejemplo:

.. |fecha| date::
.. |hora| date:: %H:%M

Today's date is |fecha|.

This document was generated on |fecha| at |hora|.

Clase destacada
###############

Crea una clase especial que será reflejada en el índice:

.. code-block::

    .. class:: special

    This is a "special" paragraph.

Ejemplo:

.. class:: Pensamiento

    Aquello que da vueltas por la cabeza.

También existe la clase excepcional que no va indexada:

.. code-block::

    .. class:: exceptional remarkable

        An Exceptional Section
        ======================

        This is an ordinary paragraph.

Ejemplo:

.. class:: exceptional remarkable

    Algo Excecional
    ======================

    Y esto es un texto ordinario.


Crea una referencia a una clase y la indexa automáticamente:

    .. code-block::

        .. class:: multiple

            First paragraph.

            Second paragraph.

Ejemplo:

.. class:: multiple

        primer texto.

        segundo texto.

Menu de documentos
##################

Crea un menú que enlaza a otros documentos:

.. code-block::

    .. toctree::
        :maxdepth: 2
        :caption: Contenidos:

        documento

Es un listado de documentos que tenemos creado para cada manual en nuestro sitio en formato rst. Cada uno de ellos se irá asignando según el nombre del archivo, en este ejemplo sería documento.

Versiones
#########

Define las versiones de la documentación expuesta:

.. code-block::

    .. versionadded:: 2.5

    .. versionchanged:: 3.4

    .. deprecated:: 3.2

Ejemplo:

.. versionadded:: 2.5

.. versionchanged:: 3.4

.. deprecated:: 3.2

Título
######

Crea un simple y sencillo título pequeño:

..code-block::

    .. rubric:: title

Ejemplo:

.. rubric:: title

También existe la versión algo más centrada y detallada:

.. code-block::

    .. centered:: LICENSE AGREEMENT

Ejemplo:

.. centered:: LICENSE AGREEMENT


Crear un glosario
#################

Crea tu propio glosario de palabras que se añadirán al index cuando se compile la web:

.. code-block::

    .. glossary::

        environment
            A structure where information about all documents under the root is
            saved, and used for cross-referencing.  The environment is pickled
            after the parsing stage, so that successive runs only need to read
            and parse new and changed documents.

        source directory
            The directory which, including its subdirectories, contains all
            source files for one Sphinx project.

Ejemplo:

.. glossary::

    environment
        A structure where information about all documents under the root is
        saved, and used for cross-referencing.  The environment is pickled
        after the parsing stage, so that successive runs only need to read
        and parse new and changed documents.

    source directory
        The directory which, including its subdirectories, contains all
        source files for one Sphinx project.

Cada título del glosario se enlaza directamente con el índice.