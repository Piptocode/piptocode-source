=====
PHP 7
===== 
 
.. image:: /logos/logo-php.png
    :scale: 15%
    :alt: Logo PHP
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con PHP 7, el lenguaje de la web y uno de los mas usados para desarrollo backend.

.. contents:: Índice

Elementos básicos del lenguaje 
##############################

Comentarios
***********
Los comentarios se pueden realizar de dos tipos:

* Comentarios de una sola línea:

.. code:: php

    // Comentario de una sola línea

* Comentarios multilínea:

.. code:: php

    '''
    /* Este comentario 
    tiene más de una línea.
    Puede servir para escribir
    un manual u otras cosas.
    */
    '''

Estructura en php
******************
La estructura de PHP 7 se presenta de un modo similar a lenguajes como C o Perl:

* Un vistazo a PHP puro:

.. code:: php

    // el código php se inicia siempre con su simbolo menor que interrogación y php:
    <?php 
        // declaramos las variables usando una llave y podemos inicializarlas directamente: 
        $variable = 20;

        // en condicionales o estructuras de control es identico a otros lenguajes:
        if($valor == 20){
            echo "el valor es igual";
        }
    ?> // y finaliza del mismo modo
    
* Ejecutando código php junto a HTML:

.. code:: php

    <?php 
        // podemos tener código php incrustado en HTML gracias a sus símbolos de inicio y fin:
        $titulo = "practicando PHP";
    ?>

    <html>
        <head>
        </head>
        <body>
            <!-- E incrustar valores impresos en etiquetas html entre otras cosas: -->
            <h1><?php echo $titulo; ?></h1>
        </body>
    </html>

* También podemos cargar etiquetas HTML con PHP:

.. code:: php

    <?php 
        echo "<p>Etiqueta incrustada desde php</p>";
    ?>

Otro dato importante como en la mayoría de lenguajes hay que evitar la ausencia de ; ya que en algunos casos no da error pero en otros si.

.. attention:: 
    Para cargar los archivos PHP correctamente desde el navegador deben estar alojados en la carpeta del directorio web.
    
Extensión
*********
La extensión utilizada por los archivos php es ``php``

Ejecución
*********

Existen dos métodos para ejecutar código PHP:

* El primero y mas común es cargar el archivo desde la url en el servidor local o remoto.
* El segundo es ejecutandolo desde PHP-CLI, por ejemplo: ``php hola.php``. Muy útil para probar partes del código.

.. important::
    Para utilizar PHP-CLI tenemos que instalarlo ejecutando ``sudo apt install php7.4-cli``

Información de nuestro servidor
*******************************
Si queremos conocer la información de nuestro servidor basta con crearnos un archivo con el nombre por ejemplo info.php y añadir la siguiente función:

.. code:: php

    <?php
        phpinfo();
    ?>

Abrimos el archivo en el navegador desde el servidor y se mostrará toda la info de este.

Documentación de PHP oficial
****************************
La documentación oficial de php nos brinda cientos de funciones que pueden ayudarnos en nuestro día a dia. 

Podemos acceder en el siguiente `enlace <https://www.php.net/docs.php>`_.

Palabras reservadas de PHP 7
*****************************
En php existen las siguientes palabras reservadas:

* __halt_compiler()
* abstract
* and
* array()
* as
* break
* callable
* clase
* catch
* class
* clone
* const
* continue
* declare 
* default
* die() 
* do 
* echo 
* else 
* elseif
* empty()
* enddeclare
* endfor
* endforeach
* endif
* endswitch
* endwhile
* eval()
* exit()
* extends
* final 
* finally
* for 
* foreach
* function 
* global
* goto 
* if 
* implements
* include 
* include_once 
* instanceof 
* insteadof
* interface 
* isset()
* list()
* namespace
* new
* or
* print
* private
* protected
* public 
* require
* require_once
* return
* static
* switch
* throw
* trait 
* try 
* unset()
* use 
* var 
* while 
* xor 
* yield
* yield from 

Variables y tipos de datos
##########################

Variables
*********
Las variables se definen de forma similar a Perl, con una llave inicial.

Ejemplo:

.. code:: php

    <?php
        $variable = "contenido de variable";
    ?>

.. attention::
    Es imprescindible almacenar contenido en las variables para que no genere errores. Por ejemplo poner unas comillas "". 

Constantes
**********
Para definir constantes tenemos que recurrir a una función llamada define()

Ejemplo:

.. code:: php 

    <?php

        // Recibe dos parámetros, el primero el nombre de la constante en mayúsculas y el segundo el valor.
        define("NOMBRE",     "Ariana");
    ?>

Tipos de datos primitivos
*************************
Los tipos de datos mas comunes son los siguientes:

+------------------+-----------------------------------------------+-----------------------------+
| Tipo de dato     | Denominación                                  | Ejemplo                     |
+==================+===============================================+=============================+
| string           | Cadena de texto                               | 'cadena', "cadena"          |
+------------------+-----------------------------------------------+-----------------------------+
| integer          | Número Entero                                 | 20, 5, -3, 0                |
+------------------+-----------------------------------------------+-----------------------------+
| float            | Número con decimales                          | 20.53, 12.5, -18.353        |
+------------------+-----------------------------------------------+-----------------------------+
| bool             | Verdadero o falso                             | true, false                 |
+------------------+-----------------------------------------------+-----------------------------+
| array            | Matriz de datos                               | array('valor', 'otro_valor')|
+------------------+-----------------------------------------------+-----------------------------+
| array asociativo | Objeto con orden de tipo clave:valor          | array('clave' => 'valor')   |
+------------------+-----------------------------------------------+-----------------------------+



Ejemplos:

.. code:: php 

    $cadena = "Dia de paga"
    $otraCadena = 'Cadena de comillas simples es lo mismo'
    $entero = 27
    $decimal = 22.83
    $booleano = true
    $array = array(2.4, true, 6, 'Metro');
    $array_asociativo = array(
        'nombre' => 'Guillermo',
        'apellidos' => 'Granados Gómez',
        'telefono' => '744607487',
        'ciudad' => 'Málaga'
    );

Entrada y Salida de datos
#########################
Para realizar la entrada de datos en PHP al ser un lenguaje definido para web se utilizan formularios y se realiza mediante POST:

* Entrada de datos: 

.. code:: php

    <?php
        $valor = $_POST['name'];
    ?>

* Salida de datos: 

.. code:: php

    <?php
        echo $valor;
    ?>
    

Luego para concatenar utilizamos el ``.`` en cada elemento:

.. code:: php

    <?php
        echo "tu nombre es " . $nombre " y vives en " . $ciudad;
    ?>

Operadores
##########

Operadores Aritméticos
**********************
Los operadores aritméticos que se presentan en php son los mismos que en la mayoría de lenguajes,
``+, -, *, /, %``

Estos podemos utilizarlos del siguiente modo:

.. code:: php

    <?php
        // Estos son los operadores aritméticos:
        $suma = 5 + 8;
        $resta = 3 - 2;
        $multiplicar = 2 x 5;
        $dividir = 4 / 2;
        $resto = 20 % 5;

        // Y estos son operadores de incremento y decremento:

        $valor++;
        $valor--;

    ?>

Operadores Relacionales
***********************
Los operadores relacionales en php son los mismos que en la mayoría de lenguajes de programación:

+-----------------+---------+
| Operador        | símbolo |
+=================+=========+
| Mayor que       | >       |
+-----------------+---------+
| Menor que       | <       | 
+-----------------+---------+
| Igual que       | ==      |
+-----------------+---------+
| Mayor igual que | >=      |
+-----------------+---------+
| Menor igual que | <=      |
+-----------------+---------+

Cuando hablamos del uso de un solo ``=`` nos referimos a la asignación de un valor en una variable.

Como en muchos lenguajes, si imprimimos por consola la relación entre un valor y otro el resultado será True o False:

.. code:: php
    
    <?php
        // Si decimos que 3 es mayor que 2 
        echo 3 < 2
        // el resultado que sale por consola es True.
    ?>

Operadores Lógicos
******************
En php se utilizan los mismos operadores lógicos que en la mayoría de lenguajes de programación, sin embargo presentan un aspecto diferente:

+-----------+-----------+------------------------------------------------------------+
| Operador  | símbolo   | condición                                                  |
+===========+===========+============================================================+
| Y (and)   | &&        | La condición se cumple si todos son verdaderos             |
+-----------+-----------+------------------------------------------------------------+
| O (or)    | ||        | La condición se cumple si al menos uno es verdadero        |
+-----------+-----------+------------------------------------------------------------+
| NO (not)  | !         | La condición se cumple si es diferente a lo que se compara |
+-----------+-----------+------------------------------------------------------------+

Ejemplos:

.. code:: php

    # Resultado False:
    print(5 > 7 && 3 < 6)
    # Resultado True:
    print(5 > 7 || 3 < 6)
    # Resultado True
    print(6 != 3)

Asignación
**********
Nos permiten asignar datos a variables. Esto ya lo hemos visto también en ejemplos anteriores:

.. code:: php

    <?php
        // Podemos asignar cadenas o números:
        $nombre = "Guillermo";
        $numero = 8;
        // Y podemos asignarle el valor de otras variables:
        $otroNumero = $numero;

        // Y asignar incrementos directamente a los valores que ya posean:
        $numero -= 2;
        $numero += 2;
        $numero *= 2;
        $numero /= 2;
    ?>

Con este último operaremos con el valor asignado sumando, restando, multiplicando o dividiendo el valor que ya posee.

Estructuras de control
######################
En php disponemos de estructuras de control como ``if``, ``switch``, ``for`` y ``while``.

Condicional if
**************
Las condiciones sencillas en php funcionan del siguiente modo:

.. code:: php

    <?php
        $saludo = 'Hola';

        if ($saludo == 'Hola'){
            echo 'Hola a tí también';
        }
    ?>

También tenemos condiciones con una salida alternativa si no se cumple esta:

.. code:: php

    <?php
        $nacimiento = 2003;

        if($nacimiento <= 2002){
            echo 'Eres mayor de edad';
        }else{
            echo 'Eres menor de edad';
        }
    ?>

Condicional if-else if
**********************
Las condiciones compuestas nos ofrecen varios caminos posibles:

.. code:: php

    $edad = 66:
    
    if($edad >= 18){
        echo 'Eres mayor de edad';
    }else if($edad < 18){
        echo 'Eres menor de edad';
    }else if($edad >= 65){
        echo 'Ya eres un anciano';
    }else{
        echo 'No es una edad correcta';

Condicional Switch
******************
El switch podemos utilizarlo para tomar distintos caminos fijos. Se utiliza a menudo en PHP.

.. code:: php 

    <?php
        $valor = 5;

        switch($valor){
            case (1):
                echo "el número es 1";
                break;
            case (2):
                echo "el número es 2";
                break;
            case (3):
                echo "el número es 1";
                break;
            case ('Juan'):
                echo "no es un número, ¡es Juan!";
                break;
            default:
                echo "No encuentro el número";
        }
    ?>

Bucle for
*********
El bucle for en php se presenta de un modo muy similar al de lenguajes como Javascript o Perl:

* Uso con rango definido:

.. code:: php

    <?php
        for($i = 0; $i <= 10; $i++){
            echo "repetición " . $i;
        }
    ?>

* Bucle for multidimensional:

.. code:: php

    <?php
        echo "<table border='1'>";
        for($i = 0; $i <= 10; $i++){
            echo "<tr> ";
            for($j = 0; $j <= 10; $j++){
                echo "<td>" . $i . "</td>";
            }
            echo "</tr>";

        }
        echo "</table>";
    ?>

Bucle foreach
*************
El bucle diseñado para iterar con matrices de datos en PHP, el cual es similar a for-in que se utiliza en Python o Javascript:

.. code:: php

    <?php
        $matriz = array("Pedro","Luis","Antonio");

        foreach($matriz as $nombres){
            echo $nombres;
            echo "<br>";
        }
    ?>

Bucle while
***********
El bucle While es similar a Perl o Javascript entro otros.

* Ejemplo de bucle while:

.. code:: php

    <?php

        $numero = 1;
        while($numero <= 10){
            echo "impresión numero" . $numero;
            //Atención, si no establecemos un incrementador se imprimirá de forma infinita:
            $numero++;
        }

    ?>

* Bucle do-while:

.. code:: php 

    <?php
        $numero = 1;

        do {
            echo "ejecucion numero " . $numero;
        } while($numero == 1);

    ?>

Estructuras de datos
####################

Matrices
********
Las matrices o arrays en PHP son bastante útiles para organizar datos.

.. code:: php

    <?php
        $matriz = [1, 15, -12, 3.81, "cadena", True];
        echo "Tengo " . $matriz[1] . " años";
    ?>

* Recorrer valores de una matriz e imprimirlos con ``for``:

.. code:: php

    <?php 
        echo "Estos son los medios de transportes disponibles: <br>";
        for($i = 0; $i <= 3; $i++){
            echo "- " . $transporte[$i] . "<br>"; 
        }
    ?>

* Ver cuantos elementos hay en una lista con ``count()``:

.. code:: php

    <?php
        count($matriz);
    ?>

* Imprime un elemento de la lista por su posición:

.. code:: php

    <?php 
        echo $matriz;
    ?>


* Borra el último elemento de la lista con ``array_pop()``:

.. code:: php
    
    <?php
        array_pop($matriz);
    ?>

* Borrar un elemento por su posición con ``unset()``:

.. code:: php

    <?php 
        unset($matriz[1]);
    ?>

* Añadir un elemento al final de la lista con ``array_push()``:

.. code:: php

    <?php 
        array_push($matriz, 'nocilla', 'galleras');
    ?>

* Convertir lista a cadena de texto con ``implode()``:

.. code:: php

    <?php 
        implode(",", $matriz);
    ?>

* Ordenar elementos de listas por orden numérico o alfabético:

.. code:: php

    <?php
        $lista = ["gato", "nocilla", "avión", "leche"]
        
        sort($lista);
    ?>

* Verificar si se encuentra un elemento en la lista y devuelve true o false:

.. code:: php

    <?php 
        echo array_search('verde', $matriz);
    ?>

Array Asociativos
*****************
Los arrays asociativos vienen a ser lo mismo que los diccionarios en Python o los Objetos en Javascript.

Se construye por pares de datos que son clave y valor del mismo modo que en Python o Javascript.

Ejemplo de uso:

.. code:: php

    <?php 
        // asignar datos uno a uno:
        $datos['nombre'] = "Guillermo";
        $datos['ciudad'] = "Málaga";

        // asignar multiples valores de una vez:
        $datos = array(
            "nombre" => "Guillermo",
            "ciudad" => "Málaga"
        );
    ?>

* Imprimir un valor del diccionario:

.. code:: php

    <?php
        echo $datos['nombre'] . " de " . $datos['apellidos'];
    ?>

* Ver la estructura del array con ``print_r()``:

.. code:: php

    <?php
        print_r($datos);
    ?>

* Recuperar solo las claves del diccionario con ``array_keys()``:

.. code:: php

    <?php
        print_r(array_keys($array));
    ?>

* Recorrer e imprimir todos los elementos del array asociativo:

.. code:: php

    <?php
        foreach($datos as $dato){
            echo $dato . " ";
        }
    ?>

* Recorrer e imprimir todos los elementos por clave => valor:

.. code:: php 

    <?php
        foreach($datos as $clave => $valor){
            echo $clave . ": " . $valor . "\n";
        }
    ?>

Arrays asociativos multidimensionales
#####################################
Los arrays asociativos multidimensionales son similares a arrays de objetos o listas de diccionarios según que lenguaje.

* Añadiendo los valores de forma manual:

.. code:: 

    <?php
        // Añadir manualmente los distintos objetos de la matriz multidimensional:
        $datos[0]['nombre'] = "Eduardo";
        $datos[0]['apellidos'] = "Lopez Aguirre";
        $datos[0]['telefono'] = "667248135";
        $datos[0]['ciudad'] = "Sevilla";

        $datos[1]['nombre'] = "Antonia";
        $datos[1]['apellidos'] = "Martinez Santos";
        $datos[1]['telefono'] = "67748970";
        $datos[1]['ciudad'] = "Cádiz";

        $datos[2]['nombre'] = "Enrique";
        $datos[2]['apellidos'] = "Casas Nuñez";
        $datos[2]['telefono'] = "609752147";
        $datos[2]['ciudad'] = "Madrid";

        // Para imprimir hacemos lo mismo que arriba pero añadiendo el índice correspondiente:
        echo "Me llamo " . $datos[1]['nombre'] . " " . $datos[1]['apellidos'] . " soy de " . $datos[1]['ciudad'] . " y mi número de teléfono es: " . $datos[1]['telefono'];

    ?>

* Añadiendo los valores de forma masiva:

.. code:: php 

    <?php
        // Añadir manualmente los distintos objetos de la matriz multidimensional:
        $datos = array(
            0 => array(
                'nombre' => "Eduardo",
                'apellidos' => "Lopez Aguirre",
                'telefono' => "667248135",
                'ciudad' => "Sevilla"
            ),
            1 => array(
                'nombre' => "Antonia",
                'apellidos' => "Martinez Santos",
                'telefono' => "67748970",
                'ciudad' => "Cádiz"
            ),
            2 => array(
                'nombre' => "Enrique",
                'apellidos' => "Casas Nuñez",
                'telefono' => "609752147",
                'ciudad' => "Madrid"
            )
        );

        // Del mismo modo podemos imprimir los valores:
        echo "Me llamo " . $datos[2]['nombre'] . " " . $datos[2]['apellidos'] . " soy de " . $datos[2]['ciudad'] . " y mi número de teléfono es: " . $datos[2]['telefono'];

    ?>

Recorrer array multidimensional asociativo con foreach
******************************************************
Gracias al uso del **foreach** nuestro trabajo siempre será mas sencillo aunque se trate de un array multidimensional:

.. code:: php 

    <?php
        // Añadir manualmente los distintos objetos de la matriz multidimensional:
        $datos = array(
            0 => array(
                'nombre' => "Eduardo",
                'apellidos' => "Lopez Aguirre",
                'telefono' => "667248135",
                'ciudad' => "Sevilla"
            ),
            1 => array(
                'nombre' => "Antonia",
                'apellidos' => "Martinez Santos",
                'telefono' => "67748970",
                'ciudad' => "Cádiz"
            ),
            2 => array(
                'nombre' => "Enrique",
                'apellidos' => "Casas Nuñez",
                'telefono' => "609752147",
                'ciudad' => "Madrid"
            )
        );

        echo "<table border='1'>";
        echo "<tr>
                <td> Nombre </td>
                <td> Apellidos </td>
                <td> Teléfono </td>
                <td> Ciudad </td>
        </tr>";
        // Con foreach ya no es necesario pasarle una variable de incremento al índice porque el bucle ya recorre todo el array horizontal y verticalmente.
        foreach($datos as $listado){
            echo "<tr>";
                echo "<td>" . $listado['nombre'] . "</td>";
                echo "<td>" . $listado['apellidos'] . "</td>";
                echo "<td>" . $listado['telefono'] . "</td>";
                echo "<td>" . $listado['ciudad'] . "</td>";
            echo "</tr>";
        }
        echo "</table>";

    ?>

Funciones Internas
##################
Como en la mayoría de lenguajes de programación, en php existen funciones predefinidas.

Funciones de cadenas
********************
Aquí tenemos las funciones mas utilizadas para tratamiento de cadenas de texto:

* Para saber la longitud de una cadena con ``strlen()``:

.. code:: php

    <?php
        $nombre = "Alba María";
        echo strlen($nombre);
    ?>

* Convertir valor numérico a cadena con ``(String)``:

.. code:: php

    <?php
        $numero = 27;
        $cadena = (String)$numero;
        echo $cadena;
    ?>

* Convertir una cadena en una lista ``explode()``:

.. code:: php

    <?php
        $cadena = "Galletas,Pan,Atún,Patatas";
        $matriz = explode(",", $cadena);
        for($i = 0; $i < count($matriz); $i++){
            echo $matriz[$i] . "\n";
        }
    ?>

* Reemplazar una cadena por otra con ``str_replace()``:

.. code:: php

    <?php
        $frase = "Estaba estudiando programación \n";
        echo str_replace("Estaba", "Estoy", $frase);
    ?>

* Convertir a mayúsculas la cadena con ``strtoupper()``:

.. code:: php

    <?php
        $frase = "Estaba estudiando programación \n";
        echo strtoupper($frase);
    ?>

* Convertir a minúsculas la cadena con ``strtolower()``:

.. code:: php

    <?php
        $frase = "ESTABA estudiando programación \n";
        echo strtolower($frase);
    ?>

Funciones numéricas
*******************
Estas son las funciones numéricas mas comunes en php:

* Convertir un valor a entero con ``(int)``:

.. code:: php

   <?php
        $cadena = "237";
        $numero = (int)$cadena;
        echo $numero;
    ?>

* Convertir un valor a decimal con ``(float)``:

.. code:: php

    <?php
        $cadena = "237";
        $numero = (float)$cadena + 10.25;
        echo $numero;
    ?>

* Redondear un valor decimal con ``round()``:

.. code:: php

    <?php
        echo round(1.95583, 2);
    ?>

* Crear un rango de números con ``range()``:

.. code:: php

    <?php
        foreach (range(0, 20) as $numeros) {
            echo $numeros . "\n";
        }
    ?>

* Mostrar el valor mayor de un rango con ``max()``:

.. code:: php 

    <?php
        echo max(1, 5, 8, 3, 20);
    ?>

* Mostrar el valor mínimo de un rango con ``min()``:

.. code:: php

    <?php
        echo min(1, 5, 8, 3, 20);
    ?>

* Sumar todos los valores de un rango con ``array_sum()``:

.. code:: php

    <?php
        $matriz = [1, 5, 8, 3, 20];
        echo array_sum($matriz);
    ?>
    
Otras funciones comunes
***********************
Tenemos una serie de funciones de uso común en php:

* Averiguar que tipo de dato contiene una variable con ``gettype()``:

.. code:: php

    <?php
        $matriz = [1, 5, 8, 3, 20];
        echo gettype($matriz);
    ?>

* Trabajar las fechas con la función ``date()``:

.. code:: php

    <?php
        echo "Dia: " . date('d') . "<br>";
        echo "Inicial del día: " . date('D') . "<br>";
        echo "Día de la semana: " . date('l') . "<br>"; 
        echo "Días transcurridos desde que comenzó el año: " . date('z') . "<br>";
        echo "Semanas transcurridas desde que comenzó el año: " . date('W') . "<br>";
        echo "Mes en el que estoy: " . date('m') . "<br>";
        echo "Mes en el que estoy sin cero: " . date('n') . "<br>";
        echo "Iniciales del mes el que estoy sin cero: " . date('M') . "<br>";
        echo "Dias que tiene el mes en el que estoy: " . date('t') . "<br>";
        echo "Año en el que estoy: " . date('Y') . "<br>";
        echo "Año abreviado: " . date('y') . "<br>";
        // Si nos da 0 es false y si da 1 es true:
        echo "Saber si es año bisiesto: " . date('L') . "<br>";
        echo "Fecha formato ISO-8601: " . date('c') . "<br>";
        // Este formato es ideal para almacenar fechas en bases de datos:
        echo "Hora UNIX: " . date('U') . "<br>";

        // AJUSTES DE TIEMPO:
        echo "Hora AM o PM: " . date('a') . "<br>";
        echo "Hora AM o PM en mayúsculas: " . date('A') . "<br>";
        echo "Hora en formato Swatch Internet Time : " . date('B') . "<br>";
        echo "Hora en formato 12: " . date('g') . "<br>";
        echo "Hora en formato 24: " . date('G') . "<br>";
        echo "Hora formato 12 con 0 inicial: " . date('h') . "<br>";
        echo "Hora formato 24 con 0 inicial: " . date('H') . "<br>";
        echo "Minutos con cero: " . date('i') . "<br>";
        echo "Segundos con ceros: " . date('s') . "<br>";
        echo "Microsengundos: " . date('u') . "<br>";
        echo "Zona temporal: " . date('e') . "<br>";
        // 0 false, 1 true:
        echo "Horario de sol reducido: " . date('I') . "<br>";
        echo "Desfase frente al meridiano de Greenwitch: " . date('O') . "<br>";

    ?>

* Comprobar si existe una variable con ``isset()`` y eliminarla con ``unset()``:

.. code:: php 

    <?php
        $valor = "X";

        echo "La variable tiene un valor igual a " . $valor . "<br>";

        unset($valor);

        if(isset($valor)){
            echo "La variable tiene un valor igual a " . $valor . "<br>";
        }else{
            echo "Ya no tiene ningún valor";
        }
    ?>

Funciones
#########
Las funciones en php se declaran del siguiente modo:

.. code:: php 

   <?php
        function saludar(){
            echo "Hola amigo";
        }
        // ejecutar función:
        saludar();
    ?>

* Recibir parametros en una función:

.. code:: php

    <?php
        function tablas($numero){
            for($multiplicar = 0; $multiplicar <= 10; $multiplicar++){
                echo $numero . " x " . $multiplicar . " = " . $numero * $multiplicar . "<br>";
            }
        }

        tablas(5);
    ?>

Ambito en funciones 
********************
El ambito de las funciones en php nos facilita el uso de variables que se encuentran fuera de una función
para poder manejarlas sin tener que pasarlas por parámetros.

ejemplo:

.. code:: php 

    <?php
        // esto es una variable que se encuentra fuera de la función
        $saludo = "Hola amigo";

        function saludar(){
            // para recuperarla sin pasarla por parámetros podemos usar el modificador global:
            global $saludo;
            echo $saludo;
        }

        saludar();
    ?>

* Recibir parametros infinitos añadiendo ``*`` a un parametro:

    .. code:: php

        def miFuncion(*unNombre):
        for persona in unNombre:
            print("Se llama {}".format(persona))

        miFuncion("Pepe", "Antonio", "Alfredo")

Variables predefinidas 
######################
PHP cuenta con un set de variables predefinidas disponibles en cualquier parte del programa para tratar distintos aspectos
como peticiones GET y POST, recuperar archivos con FILES, etc.

Variable GET 
************
Con **$_GET** Recuperamos la información recibida por parametros en la barra de navegación. Esto muestra la información
que recibimos como ya es de saber:

.. code:: php

    <form method="GET">
        <label for="nombre">Introduce tu nombre</label>
        <input type="text" name="nombre">
        <br>
        <input type="submit" value="Mostrar">
    </form>

    <?php
        echo "Tu nombre es " . $_GET['nombre'];
    ?>

Variable POST 
*************
Podemos enviar los datos via post y utilizar la variable **$_POST** para recuperarlos:

.. code:: php 

    <form method="POST">
        <label for="nombre">Introduce tu nombre</label>
        <input type="text" name="nombre">
        <br>
        <input type="submit" value="Mostrar">
    </form>

    <?php
        echo "Tu nombre es " . $_POST['nombre'];
    ?>

Variable SERVER
***************
Con la variable **$_SERVER** podemos recuperar información de quien visita la web.

Estas son algunas de las cosas que podemos recuperar:

.. code:: php 

    <?php
    // Para saber la ip del visitante:
    $ip = $_SERVER['REMOTE_ADDR'];
    echo "Tu ip es: " . $ip . "<br>";

    // Para saber el puerto que esta usando el cliente:
    $puerto = $_SERVER['REMOTE_PORT'];
    echo "Estas usando el puerto: " . $puerto . "<br>";

    // Para saber la ip del servidor:
    $serverIP = $_SERVER['SERVER_ADDR'];
    echo "La ip del servidor es: " . $serverIP . "<br>";

    // Para saber el nombre del Servidor (por defecto la ip de este si no tiene nombre definido):
    $host = $_SERVER['SERVER_NAME'];
    echo "El nombre del servidor es: " . $host . "<br>";

    //Para saber el navegador:
    $navegador = $_SERVER['HTTP_USER_AGENT'];
    echo "Tu navegador es: " .  $navegador . "<br>";

    //Para saber el archivo donde te encuentras de la web:
    $ruta = $_SERVER['PHP_SELF'];
    echo "Estas en: " .  $ruta . "<br>";

    //El metodo con el que se esta procesando la url:
    $metodo = $_SERVER['REQUEST_METHOD'];
    echo "Se esta usando el Método: " .  $metodo . "<br>";

    //Ver la url que se utilizo para realizar la petición:
    $uri = $_SERVER['REQUEST_URI'];
    echo "Se esta usando el Método: " .  $uri . "<br>";

    //Visualizar la raiz del directorio donde se encuentra el archivo:
    $raiz = $_SERVER['DOCUMENT_ROOT'];
    echo "La raiz del servidor es: " .  $raiz . "<br>";

    //Ofrece un valor no vacío si la petición se realiza en https:
    $peticion_segura = $_SERVER['HTTPS'];
    echo "Se vera algo si estamos usando https: " .  $peticion_segura . "<br>";

    ?>

Variable FILES
**************
La variable **$_FILES** recupera un archivo subido desde un formulario.

Ejemplo de uso:

.. code:: php 

    <form method="POST" enctype="multipart/form-data">
        <input type="file" name="archivo">
        <input type="submit" value="cargar">
    </form>

    <?php
        echo "<pre>";
        print_r($_FILES['archivo']);
        echo "</pre>";
    ?>

Variable SESSION
****************
La variable **$_SESSION** se utiliza para recordar datos en el navegador del cliente 
como usuarios, procesos de compras y otras cosas.

Ejemplo de uso:

.. code:: php 

    <?php
        // Para poder invocar en cualquier parte de nuestro sitio una variable de sesión tenemos que inicializar la sesión:
        session_start();

        // La asignamos a una variable de sesión:
        $_SESSION['info'] = "Información importante";

        // Y ahora podemos utilizar las variables de sesión:
        echo $_SESSION['info'];

        // Si queremos borrar las variables de sesión de nuestra web utilizamos este parametro:
        session_destroy();
    ?>

Clases
######
EN PROCESO...

Manejor de archivos
###################
En php podemos crear y modificar archivos con la función ``fopen()``:

Cuando abrimos un archivo en php siempre asignamos un permiso:

+---------------+--------------+
| Permiso       | Nomenclatura |
+===============+==============+
| Escritura     | w - w+       |
+---------------+--------------+
| Lectura       | r - r+       |
+---------------+--------------+
| Actualización | a - a+       |
+---------------+--------------+

* En el caso de escritura:

.. code:: php

    <?php
        $ip = $_SERVER['REMOTE_ADDR'];
        $navegador = $_SERVER['HTTP_USER_AGENT'];
        $contenido = date('U') . " - Fecha: " . date('Y/m/d - H:i:s') . " - Navegador: " . $navegador . " - IP: " . $ip ."\n";
        
        // establecemos el nombre de archivo que vamos a editar:
        $archivoLogs = 'logs.dat';
        // abrimos con permisos de creación extras:
        $manejador = fopen($archivoLogs, 'w+');
        // escribimos los cambios:
        fwrite($manejador,$contenido);
    ?>

* En caso de lectura:

.. code:: php

    <?php
        $archivoLogs = 'logs.dat';
        // abrimos el archivo con permisos de lectura:
        $manejador = fopen($archivoLogs, 'r');
        
        // establecemos la condición con fgetcsv() de manera que los dividirá:
        while($datos = fgetcsv($manejador,1000000, "-")){
            echo "<pre>";
            print_r($datos);
            echo "</pre>";
        }
        fclose($manejador);
    ?>

* En caso de actualización:

.. code:: php

    <?php
        $ip = $_SERVER['REMOTE_ADDR'];
        $navegador = $_SERVER['HTTP_USER_AGENT'];
        $contenido = date('U') . " - Fecha: " . date('Y/m/d - H:i:s') . " - Navegador: " . $navegador . " - IP: " . $ip ."\n";
        
        // establecemos el nombre de archivo que vamos a editar:
        $archivoLogs = 'logs.dat';
        // abrimos con permisos de actualizacion extras:
        $manejador = fopen($archivoLogs, 'a+');
        // escribimos los cambios:
        fwrite($manejador,$contenido);
    ?>

Conectar a bases de datos con PDO
#################################
PDO sirve para conectarse a gran cantidad de bases de datos con el mismo código ya sea MySQL, SQL Server o PostgreSQL entre otras.

MAS ADELANTE SE INCLUIRÁN EJEMPLOS DE USO

PHP CLI
#######

Comandos útiles de PHP:

* php -v: podemos ver la versión que usamos
* php -m: podemos ver los moudlos cargados
* php -i: podemos ver la configuración de php actual
* php -r: enviar código a ejecutar ej: ``echo "hola mundo"``
* php archivo.php: podemos ejecutar un archivo php para ver en que ámbito se ha ejecutado.
* php -S: ejecutar servidor php ``php -S localhost:8000``
* php -S -t: establecer un directorio inicial de arrance del server: ``php -S localhost:8000 -t inicial/``

