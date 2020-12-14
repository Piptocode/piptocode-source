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

* Y si queremos que un estilo sea para todos los elementos utilizamos el asterísco (*):

.. code:: css

    * {

    }

De ese modo vamos insertando dentro de los paréntesis las reglas de estilo con las cuales podremos definir tamaño de textos, colores, posición, animaciones, etc...

Comentarios en CSS
******************
Para escribir comentarios en CSS utilizamos el siguiente formato:

.. code:: css

    /* Esto es un comentario en CSS */

Elementos hijos dentro de CSS
*****************************
Los elementos hijo son aquellas etiquetas html dentro de otras que podemos seleccionar de las siguientes formas:

* Hijo de otra etiqueta: seleccionar el hijo de una etiqueta ``ul li{}``
* Hijo de Id: la etiqueta hija del id se selecciona con un símbolo menor que: ``#main > p {}``

Ejemplo:

.. code:: css

    #nav > div p {
        color: red;
    }


pseudo-clases
*************
Las pseudo-clases son elementos que se activa según la interactuación del usuario con la etiqueta a la que asignemos las reglas:

* active: Se activan los estilos cuando estamos pinchando sobre el elemento:

.. code:: css

    a:active {
        color: yellow;
    }

* hover: Se activan los estilos cuando posicionamos el cursor sobre el elemento:

.. code:: css

    a:hover {
        background: yellow;
    }

* visited: define el estilo de un enlace visitado:

.. code:: css

    a:visited {
        color: green;
    }

* checked: nos sirve para establecer el estilo de un radio, option o checkbox seleccionado:

.. code:: css

    checkbox:checked{
        margin-left: 25px;
        border: 1px solid blue;
    }

* disabled: Reperesenta a cualquier input deshabilitado:

.. code:: css

    input:disabled{
        background: red;
    }

* enabled: Reperesenta a cualquier input habilitado:

.. code:: css

    input:enabled{
        background: red;
    }

* focus: Se activa cuando pinchamos en un input:

.. code:: css

    input:focus {
        background:blue;
        color:green;
    }

* required: define el estilo de aquellos inputs que tienen el atributo required asignado:

.. code:: css

    input:required {
        background:blue;
        color:red;
    }

* valid: define el estilo de un campo input cuando es valido:

.. code:: css

    input:valid {
        background: blue;
    }

* invalid: define el estilo de un campo input cuando no es valido:

.. code:: css

    input:invalid {
        background: red;
    }

* first-child: es el primer elemento de un conjunto de hermanos:

.. code:: css

    div:first-child {
        color: blue;
    }

* last-child: es el último elemento de un conjunto de hermanos:

.. code:: css

    div:last-child {
        color: blue;
    }

* first-letter: define el estilo de la primera letra de un texto:

.. code:: css

    p:first-letter {
        color: blue;
    }   

Pseudo-elementos
****************
Los pseudo-elementos son elementos que podemos insertar antes o después de una etiqueta html:

* before: incluiremos un elemento antes de la etiqueta seleccionada.
* after: incluiremos un elemento después de la etiqueta seleccionada.

Ejemplo de uso:

.. code:: css

    a::before { 
        content: "texto anterior ";
        color: blue;
    }

Importar hojas de estilo dentro de otra hoja de estilo
######################################################
Podemos importar una hoja de estilo en nuestra hoja base utilizando la regla ``@import`` del siguiente modo:

.. code:: css

    @import url(desktopStyle.css)

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

Sombreado de texto
******************
Para crear un sombreado de texto utilizamos la regla ``text-shadow`` a la cual le introducimos valores para la posición horizontal, la posición vertical y la densidad de la sombra en pixels, por último el color:

.. code:: css

    p {
        text-shadow: 5px 5px 10px #FF0000;
    }

Crear múltiples columnas de texto
*********************************
Se puede asignar un texto con columnas como si se tratase de un periódico con la regla ``multi-column``:

.. code:: css

    div {
        column-count: 3;
    }

Y especificar la separación entre columnas:

.. code:: css 

    div {
        column-gap: 40px;
    }

También podemos definir el estilo de línea divisora entre columnas y el grosor de esta:

.. code:: css

    div {
        columns-rule-style: dashed;
        columns-rule-width: 3px
    }
    
Ajustar ancho y alto 
####################

Ancho
*****
El ancho se define con la regla ``width`` y podemos trabajar con porcentajes (%) o pixels (px), también existen reglas para definir el ancho mínimo de un elemento con la regla ``min-width`` y el ancho máximo permitido con ``max-width``:

ejemplo:

.. code:: css

    div{
        width: 100%;
    }

    div{
        min-width: 150px;
    }

    div{
        max-width: 400px;
    }
    
Alto
****
Para el alto tenemos la regla ``height`` con sus respectivos ``min-height`` y ``max-height`` para valores precisos:

ejemplo:

.. code:: css

    div{
        height: 100%;
    }

    div{
        min-height: 150px;
    }

    div{
        max-height: 400px;
    }


Modelo de caja en CSS
#####################
El modelo de caja en CSS es aquel espacio en el que se puede trabajar su tamaño y espacio.

Márgenes
********
Los márgenes son el espacio que podemos definir en el exterior de la caja css y se utiliza la regla ``margin``:

* margin: define con un solo tamaño el espaciado de toda la caja.
* margin-left: define el espacio del margen izquierdo.
* margin-right: define el espacio del margen derecho.
* margin-top: define el espacio del margen superior.
* margin-bottom: define el espacio del margen inferior.

Lo definimos así:

.. code:: css
    
    div {
        margin: 20px;
    }

Y también podemos definir el ancho verticual y el ancho horizontal pasándole dos valores:

.. code:: css

    div {
        margin: 20px 15px;
    }

O cada uno de ellos utilizando solo la regla ``margin`` comenzando desde arriba, derecha, abajo e izquierda:

.. code:: css

    div {
        margin: 15px 28px 13px 26px;
    }

Relleno
********
El relleno es el espacio que se define dentro de las cajas CSS con ``padding``:

* padding: define con un solo tamaño el espaciado de toda la caja.
* padding-left: define el espacio del margen izquierdo.
* padding-right: define el espacio del margen derecho.
* padding-top: define el espacio del margen superior.
* padding-bottom: define el espacio del margen inferior.

Lo definimos así:

.. code:: css

    div {
        padding: 20px;
    }

Y también podemos definir el ancho verticual y el ancho horizontal pasándole dos valores:

.. code:: css

    div {
        padding: 20px 15px;
    }

O cada uno de ellos utilizando solo la regla ``padding`` comenzando desde arriba, derecha, abajo e izquierda:

.. code:: css

    div {
        padding: 15px 28px 13px 26px;
    }

Bordes
######
Podemos definir distintas propiedades de los bordes con las reglas de ``border``

con la regla ``border`` se puede definir directamente el grosor del borde, el estilo y el color:

.. code:: css

    div {
        border: 2px dotted blue;
    }

Estilo del borde
****************
Existen diversos estilos de bordes que podemos definir con la regla ``border-style`` los cuales tenemos:

* solid
* dotted
* dashed
* double
* groove
* ridge
* inset 
* outset 

Ejemplo de uso:

.. code:: css

    p {
        border-style: dashed;
    }

Esta regla también tiene otro conjunto de reglas para cada borde:

* ``border-left-style``
* ``border-right-style``
* ``border-top-style``
* ``border-bottom-style``

Y podemos usarlas del siguiente modo:

.. code:: css

    div {
        border-top-style: 15px;
    }

Grosor del borde
****************
Para definir el grosor del borde tenemos una regla llamada `border-width` y tiene las siguientes opciones:

* medium
* thin
* thick
* initial
* Pixels

su uso es el siguiente:

.. code:: css

    div {
        border-width: thin;
    }

También podemos utilizar pixels para todos los bordes:

.. code:: css

    div {
        border-width: 15px;
    }

Definirlos de vertical a horizontal:

.. code:: css

    div {
        border-width: 5px 25px;
    }

O incluso cada uno de los bordes de arriba a derecha, abajo e izquierda:

.. code:: css

    div {
        border-width: 1px 8px 7px 17px;
    }

Esta regla también tiene otro conjunto de reglas para cada borde:

* ``border-left-width``
* ``border-right-width``
* ``border-top-width``
* ``border-bottom-width``

Y podemos usarlas del siguiente modo:

.. code:: css

    div {
        border-top-width: 15px;
    }

Color del borde
***************
Para elegir el color del borde se utiliza la regla ``border-color``: 

.. code:: css

    div {
        border-color: red;
    }

Esta regla también tiene otro conjunto de reglas para cada borde:

* ``border-left-color``
* ``border-right-color``
* ``border-top-color``
* ``border-bottom-color``

Y podemos usarlas del siguiente modo:

.. code:: css

    div {
        border-top-color: 15px;
    }

Redondeado del borde
********************
Existe una regla llamada ``border-radius`` con la cual definimos el redondeo del filo de nuestro contenedor:

.. code:: css

    div {
        border-radius: 5px;
    }

Y podemos bordear una esquina que queramos:

* border-top-left-radius
* border-top-right-radius
* border-bottom-left-radius
* border-bottom-right-radius

Usando una imagen como borde
****************************
Con la regla ``border-image-source`` y la regla ``border-image-width`` podemos definir una imagen como borde:

.. code:: css

    div {
        border-image-source: url('borde.png');
        width: 2;
    }

Fondos
######
Para trabajar con fondos en css utilizamos el conjunto de reglas ``background``

Color de fondo
**************
Para lograr un fondo de color utilizamos la regla ``background-color``:

.. code:: css

    body {
        background-color: #FF0000;
    }

Degradado de fondo
******************
Con el atributo ``linear-gradient`` podemos definir un degradado de dos o varios colores:

.. code:: css

    body {
        background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(9,9,121,1) 35%, rgba(0,212,255,1) 100%);
    }

Degradado radial
****************
Con el atributo ``radial-gradient`` podemos definir un degradado radial de dos o más colores:

.. code:: css

    body {
        background: radial-gradient(20% 20%, #99CC00, #99CC99);
    }

Imagen de fondo
***************
Si queremos utilizar una imagen de fondo tenemos la regla ``background-image`` y se usa del siguiente modo:

.. code:: css

    body {
        background-image: url('fondo.png');
    }

Ajustar imagen de fondo
***********************
Para esta tarea podemos utilizar la regla ``background-position`` que tiene varios ajustes:

* top
* center
* bottom
* right
* left

Ejemplo de uso:

.. code:: css

    body{
        background-position: center center;
    }

Repetir fondo
*************
Existe una regla llamada ``background-repeat`` con la que definimos si se repite el fondo y como se repite:

* repeat-x: se repite solo en horizontal.
* repeat-y: se repite solo en vertical.
* repeat: se repite rellenando.
* space: se repite pero dejando espacio entre imágenes.
* round: se repite ajustando las imágenes.
* no-repeat: no se repite.

Ejemplo de uso:

.. code:: css

    body{
        background-repeat: round;
    }

Tamaño del fondo
****************
Existe una regla para establecer el tamaño del fondo llamada ``background-size``:

* auto: Muestra la imagen en su tamaño original.
* pixels: se puede definir el tamaño con dos valores, primero el horizontal y luego el vertical (500px 250px)
* porcentaje: lo mismo que pixels pero con porcentajes (100% 50%)
* cover: Cubrirá la imagen hasta que uno de los bordes toque el final dejando un claro en los otros.
* contain: cubre todo el fondo estirando la imagen.
* initial: devuelve la imagen a su estado original.
* inherit: hereda el tamaño del padre.

Uso de la regla:

.. code:: css

    body{
        background-size: 100% 50%;
    }

Colores
#######
Existen tres formas destacadas de trabajar con colores en CSS:

* Keywords: Nombres de colores como red, yellow, green, black...
* Hexadecimal: #FF0000, #000000, #FF33AB
* RGB: rangos del 0 a 255 de cada color: rgb(255, 128, 0)

Podemos definir la opacidad con la regla ``opacity``:

.. code:: css

    div {
        opacity: 0.5;
    }

E incluso si utilizamos rangos RGB podemos utilizar RGBA y añadir directamente la opacidad:

.. code:: css

    div {
        background: rgba(247, 235, 185, 0.5);
    }

Cambiar el diseño del cursor
############################
Para cambiar el diseño del cursor utilizamos la regla ``cursor`` que posee los siguientes cursores:

* auto: El navegador define de forma automática el cursor.
* default: El cursor flecha por defecto.
* none: Ocultar el cursor.
* context-menu: muestra un aviso de que existe un menú contextual.
* help: muestra un símbolo de ayuda.
* pointer: muestra el cursor de un enlace.
* progress: muestra una barra de progreso.
* wait: muestra un indicador de espera.
* cell: muestra una cruz.
* crosshair: muestra otro tipo de cruz.
* text: muestra un indicador para comenzar a escribir.
* vertical-text: muestra un indicador en vertical.
* alias: muestra una cadena.
* copy: muestra una cruz verde.
* move: muestra una mano cerrada para arrastrar.
* no-drop: no permite el arrastre.
* not-allowed: muestra simbolo de prohibición.

Ejemplo de uso:

.. code:: css

    div {
        cursor: pointer;
    }

Posicionar elementos en CSS
###########################
Para establecer que posición debe llevar cada elemento dentro de otros utilizamos la regla ``position`` que tiene varios atributos:

* static: Por defecto. Los elementos se mostrarán en el orden que van apareciendo.
* relative: El elemento será posicionado a nuestro antojo utilizando las reglas top, right, left y bottom.
* absolute: El elemento se verá fijado por su posición.
* fixed: El elemento se verá de forma fija y flotante donde queramos con las reglas top, left, right y bottom.

Ejemplo de uso:

.. code:: css

    div {
        position: fixed;
        top: 0;
    }

Orden de los elementos
**********************
Podemos establecer el orden de cada elemento con la regla ``z-index``:

.. code:: css 

    div {
        z-index: 1;
    }

Cuanto mayor es el número más al frente se muestra.

Limite visible de los elementos hijos
*************************************
Podemos limitar la visibilidad de un elemento hijo cuando este se muestre por fuera con ``overflow``:

* visible: el contenido es visible aunque sobrepase el contenedor padre.
* hidden: Oculta los elementos que sobrepasan el contenedor padre.
* scroll: similar a hidden pero nos aparece una barra de desplazamiento lateral para ver los elementos ocultos.

Ejemplo de uso:

.. code:: css

    div {
        overflow: hidden;
    }

Flotar elementos
################
Los elementos html se pueden flotar con ``float``, esto se puede hacer con las siguientes propiedades:

* left
* right
* inherit
* none

Ejemplo de uso:

.. code:: css

    div {
        float: right;
    }

Resetear flotado de elementos
*****************************
Para que los elementos vuelvan a ser normales a partir de un punto escribimos:

.. code:: css

    clear: both;

Sombreado de contenedores
#########################
Existe una regla css para sombrear cajas llamada ``box-shadow`` y funciona como text-shadow:

.. code:: css

    div {
        box-shadow: 5px 5px 8px #F0F0F0F0;
    }

Transformar elementos
#####################
Podemos transformar elementos cambiando su posición o forma con la regla ``transform`` que recibe los siguientes atributos:

* translate(12px, 15px): cambia de posición un elemento de forma horizontal y vertical.
* translateX(5px): cambia la posición horizontal de un elemento.
* translateY(8px): cambia la posición vertical de un elemento.
* scale(2, 0.5): cambia el tamaño de un elemento horizontal y verticalmente que puede servir para hacer un zoom.
* scaleX(5): cambia el tamaño horizontal de un elemento.
* scaleY(2): cambia el tamaño vertical de un elemento.
* rotate(0.5turn): Invierte la postura de un elemento.
* skew(19deg, -3deg): Rota horizontalmente y verticalmente un elemento en grados.
* skewX(30deg): Rota horizontalmente el elemento.
* skewY(15deg): Rota verticalmente el elemento.
* rotateX(50deg): Gira el elemento de forma horizontal
* rotateY(50deg): Gira el elemento de forma vertical


Ejemplo de uso:

.. code:: css

    div {
        transform: rotateY(80deg);
    }

Definir el origen de un elemento
********************************
El origen desde donde se realiza la transformación lo definimos con la regla ``transform-origin`` y posee las siguientes coordenadas:

* Izquierda: 0%
* Centro: 50%
* Derecha: 100%
* Arriba: 0% 0%
* Centro absoluto: 50% 50%
* Abajo: 0% 100%

.. code:: css

    tramsform-origin: 20%;
    

Definir como se muestran los elementos
######################################
Con la regla ``display`` podemos definir como se muestran el elemento seleccionado:

    * block: Se muestra el elemento como un bloque
    * inline: Se muestra el elemento en línea
    * none: oculta el elemento.
    * table: los elementos se muestran como en una tabla.
    * flex: los elementos se muestran en línea de forma flexible y puede acceder al modelo flexbox.

Ejemplo de uso:

.. code:: css

    div {
        display: block;
    }

Flexbox: Especificar la posición de los elementos
*************************************************
Podemos especificar como se presentarán los elementos dentro de un contenedor div con la regla ``flex-direction`` que posee los siguientes atributos:

* row (por defecto): Los elementos internos del div se van posicionando a la derecha.
* row-reverse (por defecto): Los elementos internos del div se van posicionando a la izquierda.
* column: Los elementos internos del div se van mostrando de arriba hacia abajo.
* column-reverse: Los elementos internos del div se van mostrando de abajo hacia arriba.

Ejemplo de uso:

.. code:: css

    div{
        display: flex;
        flex-direction: column;
    }


Flexbox: Mover elementos internos de izquierda a derecha
********************************************************
Para mover los elementos que se encuentran dentro de un contenedor de izquierda a derecha utilizamos la regla ``justify-content`` y asignamos uno de los siguientes atributos:

* start: Los elementos se juntan en la izquierda.
* center: Los elementos se juntan en el centro.
* space-between: Los elementos dejan toda la separación posible entre ellos.
* flex-end: Los elementos se ajustan al final

Ejemplo:

.. code:: css

    div {
        display: flex;
        justify-content: center;
    }

Flexbox: Mover elementos internos de arriba a abajo
***************************************************
Para mover los elementos que se encuentran dentro de un contenedor de arriba a abajo utilizamos la regla ``align-items`` con los siguientes atributos:

* stretch: los elementos rellenan todo el espacio posible de arriba hacia abajo.
* center: los elementos se juntan todos en el centro.
* start: los elementos se ajustan arriba del todo.
* end: los elementos se ajustan abajo del todo.

Ejemplo:

.. code:: css

    div {
        display: flex;
        align-items: center;
    }

La regla ``align-self`` funciona del mismo modo pero con un solo elemento.

Flexbox: Controlar salto de línea en hijos
******************************************
Existe una regla llamada `flex-wrap` que se utiliza para controlar el comportamiento de flexbox en sus hijos para permanecer todos en la misma línea o hacer un salto automático:

* nowrap: los elementos permanecerán en la misma línea aunque sobrepasen el contenedor padre.
* wrap: los elementos al llegar al límite del contenedor padre irán saltando abajo.
* wrap-reverse: lo mismo que wrap pero a la inversa.

Ejemplos:

.. code:: css

    div {
        display: flex;
        flex-wrap: wrap;
    }

Diseño responsivo
#################
Con CSS se puede crear un diseño adaptado a todos los dispositivos.

Formatos de Tamaño
******************
Tenemos distintos tamaños:

* Pixels: 15px;
* EM: 2em; Calcula unos 16px en base al contenedor padre.
* REM: 1rem; Calcula unos 16px pero no es afín al contenedor padre.
* Porcentajes: 10%; Ofrece un diseño totalmente líquido que se ajusta siempre al contenedor al que pertenece.

HTML responsivo
***************
Para preparar nuestro documento html y que sea responsivo debe de tener la siguiente etiqueta ``viewport``:

``<meta name="viewport" content="width=device-width, initial-scale=1.0">``

**detalles del atributo content**:

* width = device-width: quiere decir que el ancho de pantalla se ajustará al dispositivo actual.
* initial-scale = 1.0: definimos la escala de pantalla en 1.

Ajustar tamaño según resolución con media queries
*************************************************
Con el media querie ``@media`` definimos que reglas mostraremos según el tamaño de pantalla.

Los dispositivos disonibles son:

* screen: para definir que trabajamos con una pantalla.
* print: para definir que vamos a imprimir.
* all: para definir que sean reglas para todos los dispositivos.

Los parametros disponibles son:

* min-width: Tamaño mínimo para mostrar estilos.
* max-width: Tamaño máximo para mostrar estilos.
* orientation: Orientación de la pantalla entre portrait (vertical) y landscape (horizontal).

Ejemplo de uso:

.. code:: css

    @media screen and (max-width: 440px){
        bodoy {
            background: red;
        }
    }

Animaciones
###########
Podemos definir animaciones para interactuar con elementos del siguiente modo:

1. Definimos en que etiqueta irá nuestra animacion con la regla ``animation`` escribiendo el nombre de la animación y la duración de la misma:

.. code:: css

    div {
        animation: girar 5s;
    }

2. Y ahora creamos la animación con un keyframe en el cual establecemos el comienzo con ``from`` y el final de la animación con ``to``:

.. code:: css

    @keyframes animacion{ 
        from{
            transform:rotate(180deg)
        }
        to{
            transform:rotate(0deg)
        }

3. podemos decirle que la animación nunca se detenga:

.. code:: css

    div {
        animation: girar 5s infinite;
    }

4. Y que alterne en sentido contrario:

.. code:: css

    div {
        animation: girar 5s infinite alternate;
    }