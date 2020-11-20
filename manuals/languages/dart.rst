====
Dart
====

.. image:: /logos/logo-dart.png
    :scale: 60%
    :alt: Logo Dart
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar dart. Dart, junto con Flutter podemos desarrollar aplicaciones Nativas para Android. 
 
.. contents:: Índice

Elementos básicos del lenguaje
##############################

Instalación de Dart
*******************
Nos vamos al sitio: https://dart.dev/ hacemos clic en "get Dart" arriba a la derecha y buscamos la instalación de nuestro sistema.
Para confirmar que esta instalado ejecutamos `dart --version` en una terminal.

Comentarios
***********
Los comentarios se pueden realizar de dos tipos:

* Comentarios de una sola línea:

.. code:: dart

    // Comentario de una sola linea

* Comentarios multilínea:

.. code:: dart

    /*
    Esto es un comentario multilínea
    Aquí podemos establecer mas de 
    una linea
    */

* Documentado especial:

.. code:: dart

    /// Documentado especial [nombre] marcado para identificar mejor y asignar datos por ejemplo [nombre]: guillermo. esto permanecerá

Estructura en Python
********************
La estructura de Dart recuerda a la de lenguajes antecesores como C o C++ pero sin la necesidad de establecer tipo de dato ni importar librerías estandares:

.. code:: dart

    main(){
        print('Hola mundo');
    }
    

Extensión
*********
La extensión utilizada por los archivos Dart es ``dart``

Ejecución
*********
para ejecutar un archivo escribimos `dart holamundo.dart`


Palabras reservadas de Dart
****************************
En Dart existen las siguientes palabras reservadas:

* abstract
* as
* asset
* async
* async*
* await
* break
* case 
* catch
* class 
* const 
* contine 
* default 
* deferred 
* do 
* dynamic
* else
* enum 
* export 
* external 
* extends 
* factory 
* FALSE 
* final 
* finally 
* for 
* get 
* if 
* implements 
* import 
* in 
* is 
* library 
* new 
* null 
* operator 
* try 
* rethrow 
* return 
* set 
* static
* super 
* switch
* sync*
* library 
* this 
* throw 
* TRUE 
* try 
* typedef
* var 
* void 
* while 
* with 
* yield 
* yield*


Variables y tipos de datos
##########################

Variables
*********
Aunque en Dart declaramos la función main sin establecer un tipo de dato no pasa lo mismo con las variables y funciones.

Ejemplo:

.. code:: dart

    int a = 10;
    

Constantes
**********
Las constantes son muy similares en Dart pero de poco uso:

Ejemplo:

.. code:: dart 

    const c = 10;

Final 
*****
En lugar de utilizar constantes en Dart se utiliza mayoritariamente Final para definir este tipo de dato ya que ahorra mas memoria:

.. code:: dart

    final altura = 2.132;


Tipos de datos primitivos
*************************
Los tipos de datos mas comunes son los siguientes:

+--------------+-----------------------------------------------+-----------------------------+
| Tipo de dato | Denominación                                  | Ejemplo                     |
+==============+===============================================+=============================+
| String       | Cadena de texto                               | 'cadena', "cadena"          |
+--------------+-----------------------------------------------+-----------------------------+
| int          | Número Entero                                 | 20, 5, -3, 0                |
+--------------+-----------------------------------------------+-----------------------------+
| double       | Número con decimales                          | 20.53, 12.5, -18.353        |
+--------------+-----------------------------------------------+-----------------------------+
| bool         | Verdadero o falso                             | True, False                 |
+--------------+-----------------------------------------------+-----------------------------+
| list         | Arreglo de datos                               | [1, 5, "Hola", True]       |
+--------------+-----------------------------------------------+-----------------------------+
| map          | Objeto con orden de tipo clave:valor          | {'nombre':'Pedro', edad: 45}|
+--------------+-----------------------------------------------+-----------------------------+

Ejemplos:

.. code:: dart 

    String cadena = "Dia de paga";
    int entero = 27;
    double decimal = 2.332;
    bool booleano = true;
    List<dynamic> lista = [1, 5, 13, "Papiro"];
    // con los mapas se define el tipo de dato tanto de la clave como del valor:
    Map<String, dynamic> mapa = {"profesion": "programador", "hobbie":"DIY", "edad": 32}; 

Tipo de datos que puede tener una lista o un Mapa
*************************************************
Cuando trabajamos con listas o mapas no solo declaramos la variable de tipo ``List`` o ``Map``. También es necesario declarar que tipo de datos va a contener esa lista.

* Ejemplos de uso:

.. code:: dart 

    // Lista que contiene todo tipo de datos:
    List<dynamic> lista = [12, "galletas", true];

    // Lista solo de strings:
    List<String> nombres = ["Luis", "Amelia", "Gabriel"];

    // En los mapas declaramos el tipo de dato que tendrá la clave y el tipo de dato que tendrá el valor:
    Map<String, dynamic> = {"nombre": "Guillermo", "edad": 33};


Entrada y Salida de datos
#########################
En Dart la entrada y salida de datos se presenta de la siguiente forma:

* Entrada de datos:

.. code:: dart

    // Importamos la librería de entrada de datos de la consola:
    import 'dart:io';

    main(){
        // Imprimir en la terminal:
        stdout.writeln('¿Cómo te llamas?');
        // leer información de la consola y guardarlo en una variable:
        String nombre = stdin.readLineSync();

        // Devolver respuesta por consola:
        stdout.writeln('Tu nombre es: ' + nombre);
        // Podemos hacer la misma agregando la variable en una cadena utilizando el simbolo dolar:
        stdout.writeln('Tu nombre es $nombre');
    }

* Salida de datos: 

.. code:: dart

    import 'dart:io';

    main(){
        // La salida de datos normal
        print('Hola que tal');

        // La salida de datos con dart:io 
        stdout.writeln('Hola que tal');

        // imprimir una variable: 
        String nombre = "Guillermo";
        print("Hola $nombre");

    }
    

Operadores
##########

Operadores Aritméticos
**********************
Los operadores aritméticos que se presentan en python son los mismos que en la mayoría de lenguajes,
``+, -, *, /, %``

Estos podemos utilizarlos del siguiente modo:

.. code:: dart

    // asignación:
    suma = 2 + 2;

    // salida de datos:
    print(3 - 2);

    // si utilizamos + en cadenas las concatenamos:
    cadenas = "cadena uno" + " y " + " cadena dos";

    // Y también podemos definir un valor si un elemento es null:
    b??= 20; 

Operadores Relacionales
***********************
Los operadores relacionales en python son los mismos que en la mayoría de lenguajes de programación:

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

.. code:: python

    // Si decimos que 3 es mayor que 2 
    print(3 > 2);
    // el resultado que sale por consola es true.


Operadores Lógicos
******************
En Dart se utilizan los mismos operadores lógicos que en la mayoría de lenguajes de programación, sin embargo presentan un aspecto diferente:

+-----------+-----------+------------------------------------------------------------+
| Operador  | símbolo   | condición                                                  |
+===========+===========+============================================================+
| and       | &&        | La condición se cumple si todos son verdaderos             |
+-----------+-----------+------------------------------------------------------------+
| or        | ||        | La condición se cumple si al menos uno es verdadero        |
+-----------+-----------+------------------------------------------------------------+
| not       | !         | La condición se cumple si es diferente a lo que se compara |
+-----------+-----------+------------------------------------------------------------+

Ejemplos:

.. code:: dart

    // Resultado False:
    print(5 > 7 and 3 < 6);
    // Resultado True:
    print(5 > 7 or 3 < 6);
    // Resultado True
    print(6 != 3);

Estructuras de control
######################
En python disponemos de estructuras de control como ``if``, ``for`` y ``while``.

Condicional if
**************
Las condiciones sencillas en dart funcionan del siguiente modo:

.. code:: dart

    main(){
        int edad = 18;

        if(edad >= 18){
            print('Eres mayor de edad, tienes $edad años');
        }
    }

También tenemos condiciones con una salida alternativa si no se cumple esta:

.. code:: dart

    main(){
        int edad = 16;

        if(edad >= 18){
            print('Eres mayor de edad, tienes $edad años');
        }else{
            print('Tienes $edad y por tanto eres menor de edad');
        }
    }
    

Condicional if-elif
*******************
Las condiciones compuestas nos ofrecen varios caminos posibles:

.. code:: dart

    main(){
        int edad = 68;

        if(edad >= 18){
            print('Eres mayor de edad, tienes $edad años');
        }else if(edad >= 65){
            print('Con $edad, eres un anciano');
        }else{
            print('Tienes $edad y por tanto eres menor de edad');
        }
    }

Condicional Ternario
********************
El condicional ternario abrevia una condición básica if-else para asignar un valor u otro a una variable:

.. code:: dart

    int c = 21;
    String resp = c > 25 ? 'C es mayor a 25' : 'C es menor a 25';
    print(resp);


Bucle for
*********
El bucle for en dart se presenta de un modo muy similar al foreach de otros lenguajes:

* Uso con rango definido:

.. code:: dart

    main(){
        for(int i = 0; i <= 10; i++){
            print('hola mundo! $i');
    }
    }

Bucle For in 
************
El bucle for in esta diseñado para recorrer Listas y Mapas:

.. code:: dart 

    main(){
        List<String> listado = ['Batman', 'Superman', 'Aquaman'];
        // Listar con for clásico:
        for(int i = 0; i < listado.length; i++){
            print(listado[i]);
        }

        // For in:
        for(String listar in listado){
            print(listar);
        }
    }

Bucle while
***********
El bucle While es similar a otros lenguajes:

Ejemplo:

.. code:: dart

    import 'dart:io';

    main(){
        String continuar = 's';
        int contador = 0;
        
        while(continuar == 's'){
            contador++;
            stdout.writeln('Contador: $contador');

            stdout.writeln('desea continuar? (s/n)');
            continuar = stdin.readLineSync();
        }
    }

Ejemplo con bucle infinito:

.. code:: python

    numero = 10
    # al añadir True hacemos un bucle infinito:
    while True:
        adivina = int(input('Adivinia el número >> '))

        if adivina == numero:
            print('Acertaste!')
            // Con exit() finalizamos el programa
            exit()

        print('Fallaste!')

Ciclo do-while 
**************
En Dart disponemos también del ciclo do-while:

.. code:: dart 

    import 'dart:io';

    main(){
    String continuar = 'y';
    int contador = 0;
    
    do{
        contador++;
        stdout.writeln('Contador: $contador');

        stdout.writeln('desea continuar? (y/n)');
        continuar = stdin.readLineSync();
    }while(continuar == 'y');
    }

Romper un bucle y continuar
***************************
Podemos romper un bucle o continuar con las palabras ``break`` y ``continue``

* Ejemplo de uso:

.. code:: dart 

    main(){

    for(int i = 0; i < 10; i++){
        if(i == 5){
        continue;
        }
        print(i);

        if(i == 2){
        break;
        }
    }
    
    }    

condicional switch
******************
En Dart tenemos disponible Switch para controlar el flujo de información:

.. code:: dart 

    // Importamos el paquete para random:
    import 'dart:math';

    main(){
    // Creamos un entero que tenga un random de 7 números:
    int rnd = Random().nextInt(7);

    switch(rnd){
        case 1: 
        print('Lunes');
        break;
        case 2: 
        print('Martes');
        break;
        case 3: 
        print('Miércoles');
        break;
        case 4: 
        print('Jueves');
        break;
        case 5: 
        print('Viernes');
        break;
        case 6: 
        print('Sábado');
        break;
        case 7: 
        print('Domingo');
        break;
        default: 
        print('No es un día de la semana');
    }
    }

Estructuras de datos
####################

Listas
******
Las listas son un tipo de dato mutable que agrupa un conjuto de valores de distintos tipos:

.. code:: dart

    // Lista de strings:
    List<String> personas = ['Pepe', 'Luis'];
    print(personas);

    // Lista de cadenas:
    List<int> numeros =  [10, 12];

    // Añadir registros:
    personas.add('Alfonso');

    // Crear una lista vacia:
    List<String> apellidos = new List();

    // insertar varios registros:
    apellidos.addAll(['Lopez', 'Suarez', 'Martinez']);
    print(apellidos);

    // Agregar en cascada:
    apellidos..add('Gutierrez')
            ..add('Alferez');

    // Definir los elementos que tendrá una lista:
    List<String> meses = new List(12);
    //addAll no nos sirve para listas definidas porque se añade siempre al final y ya tenemos las posiciones asignadas.
    // Se haría así:
    meses[0] = 'Enero';
    meses[1] = 'Febrero';
    meses[2] = 'Marzo';
    print(meses);


Sets
****
Los sets son similiares a las listas pero con la diferencia de que estas son inmutables.

Ejemplo de lista:

.. code:: dart

    // Sets (similar a la lista pero no acepta valores duplicado como las listas)
    Set<String> lenguajes = {'c', 'python', 'dart'};
    // añadir elementos:
    lenguajes.add('PHP');
    print(lenguajes);

    
Mapas
*****
Los mapas en Dart se asemejan a los objetos literales en javascript u otros lenguajes de programación como los diccionarios en Python, etc...
Se construye por pares de datos que son clave y valor ``{'nombre':'Antonio'}`` y pueden anidar todo tipo de datos e incluso más diccionarios.

Ejemplo de uso:

.. code:: dart

    // Prueba con dinamicos e inicializando el objeto:
    Map<String, dynamic> persona = new Map();

    // agregar elementos:
    persona.addAll({"nombre": "Luis", "edad": 32});
    print(persona);


Métodos Internos
################
Como en la mayoría de lenguajes de programación, en Python existen funciones predefinidas.

Métodos de cadenas
********************
Aquí tenemos los métodos mas utilizados para tratamiento de cadenas de texto:

* Para saber la longitud de una cadena con ``length``:

.. code:: dart

    main(){
    String nombre = "Guillermo";

    print(nombre.length);
    }

* Convertir valor numérico a cadena con ``toString()``:

.. code:: dart

    main(){
    int edad = 25;

    print(edad.toString());
    }

* Convertir una cadena en una lista ``split()``:

.. code:: dart

    main(){
        String comprar = "Agua, Galletas, Huevos, Yogurt";

        List listaDeLaCompra = comprar.split(", ");
        
        print(listaDeLaCompra);

    }

* Reemplazar una cadena por otra con ``replaceAll()``:

.. code:: dart

    main(){
        String comprar = "Agua, Galletas, Huevos, Yogurt";

        comprar = comprar.replaceAll(", ", " - ");

        print(comprar);

    }

* Convertir a mayúsculas la cadena con ``toUpperCase()``:

.. code:: dart

    main(){
        String comprar = "Agua, Galletas, Huevos, Yogurt";

        comprar = comprar.toUpperCase();

        print(comprar);

    }

* Convertir a minúsculas la cadena con ``toLowerCase()``:

.. code:: dart

    main(){
        String comprar = "Agua, Galletas, Huevos, Yogurt";

        comprar = comprar.toLowerCase();

        print(comprar);

    }

Funciones numéricas
*******************
Estas son las funciones numéricas mas comunes en Dart:

* Convertir un valor a entero con ``toInt()``:

.. code:: dart

    main(){
    double edad = 38.23;

    int miEdad = edad.toInt();

    print(miEdad);

    }

* Convertir un valor a decimal con ``toDouble()``:

.. code:: dart

    main(){
        int edad = 40;

        double miEdad = edad.toDouble();

        print(miEdad + 17.37);

    }

* Redondear un valor decimal con ``round()``:

.. code:: dart

    main(){
        int edad = 40;

        double miEdad = edad.toDouble() + 183.33234;

        print(miEdad.round());

    }

 
Otras funciones comunes
***********************
Tenemos una serie de funciones de uso común en python:

* Averiguar que tipo de dato contiene una variable con ``runtimeType``:

.. code:: dart

    main(){
        int edad = 40;

        double miEdad = edad.toDouble() + 183.33234;

        print(miEdad.runtimeType);

    }

Funciones
#########
Las funciones en Dart se declaran definiendo el tipo de retorno (int, String, Map) o si no retornan nada (void).

.. code:: dart 

    // Ya sabemos que main es una función, de hecho la principal siempre:
    main(){
        // Para llamar a la función:
        saludar();

        // Si nuestra funcion retorna algo podemos asignar el retorno a una variable del mismo tipo:
        String mensaje = saludo();
        print(mensaje);

    }

    // Para crear una función lo hacemos fuera de main:
    void saludar(){ // al no retornar nada le asignamos el valor void
        print('hola desde la función');
    }

    // Si nuestra función retorna algo como una cadena lo tenemos que definir:
    String saludo(){
        return 'saludo desde retorno';
    }

* Recibir parametros en una función por consola:

.. code:: dart

    // la palabra args define que nuestro programa va a recibir parámetros de consola:
    main(List<String> args) {
        print(args);
    }

Ahora ejecutamos el archivo ``dart argumentos.dart argumento1 argumento2``

Funciones Lambda o de flecha
****************************
Este tipo de funciones tienen como objetivo resumir la función en una sola línea haciendo el retorno directamente tras la flecha:

.. code:: dart

    main(){
        // Uso de la función de flecha:
        int a = 10;
        int b = 15;
        int resultado = sumarFlecha(a,b);
        print(resultado);
    }

    // Decalramos la funcion de flecha:
    int sumarFlecha(int x, int y) => x + y;


Funciones Callback
******************
Las funciones callback se invocan dentro de otra función para ejecutar un código inmediatamente dentro de la función llamada:

.. code:: dart 

    main(){
        // Ejecutamos la función la cual le pasamos un parametro string y un callback:
        obtenerUsuario('100',(Map persona){
            print(persona);
        });
    }

    //creamos una función:
    void obtenerUsuario(String id, Function callback){
        Map usuario = {
            'id': id,
            'nombre': 'Alfredo'
        };
        // Llamamos la función callback que estamos pasandole por parámetro:
        callback(usuario); // Recibirá el usuario.
    }

Promesas 
########
Las promesas son tareas asíncronas que se van a resolver en un futuro.

* Ejemplo de Future: 

.. code:: dart 

    main(){
        // Este es un ejemplo de definir un tipo de future sencillo:
        Future timeout = Future.delayed(Duration(seconds: 3), (){ // Este código se va a ejecutar 3 segundos desupés.
            print('3 segundos después');
        });
        // Como el otro codigo queda a la espera, este se ejecutará antes:
        print('Fin del main');
    }

* Retorno de un Future:

.. code:: dart 

    main(){
    // Definimos la salida como String:
        Future<String> timeout = Future.delayed(Duration(seconds: 3), (){ // Este código se va a ejecutar 3 segundos desupés.
            return 'Retorno de dato';
        });

        // Y ahora lo ejecutamos del siguiente modo para que devuelva el dato retornado:
        timeout.then((texto)=> print(texto));
    }

Async-Await 
***********
Al igual que en lenguajes como Javascript, Dart dispone de Async y Await de forma nativa.

* Supongamos que tenemos un archivo llamado personas.txt:

.. code 

    1. Pepe
    2. Antoni
    3. Alfredo
    4. Ruth

* Veamos como se recuperan los datos con Future:

.. code:: dart 

    // Importamos la librería io:
    import 'dart:io';

    main(){
        // Establecemos una ruta donde se encuentra nuestro archivo:
        String path = Directory.current.path + '/personas.txt';

        // Usamos Then para cumplir la promesa e imprimimos el archivo:
        leerArchivo(path).then(print);

        }
        // Tenemos un Future que retorna un string que recibira como parámetro una ruta: 
        Future<String> leerArchivo(String path){
        // En el creamos un nuevo objeto de tipo file y le pasamos la ruta:
        File file = new File(path);
        // Devolvemos el archivo en formato string:
        return file.readAsString();
    }

* Y ahora vamos a hacerlo con Async-Await:

.. code:: dart 

    import 'dart:io';

    // Cada vez que utilicemos el await tenemos que asignar async en la función donde lo hagamos:
    main() async{
        String path = Directory.current.path + '/personas.txt';
        // Ahora vamos a cambiar el then por un await:
        String texto = await leerArchivo(path);

        print(texto);

    }
    // Transformamos nuestro Future en un async:
    leerArchivo(String path) async{
        File file = new File(path);
        return file.readAsString();
    }

Clases
######
Las clases en Dart tienen una estructura similar al de otros lenguajes,

.. code::  

    import 'dart:io';

    main(){
        // Creamos un objeto a partir de la clase:
        final persona = new Persona();

        // Para añadir datos a sus atributos:
        persona.nombre = 'Guillermo';
        persona.edad = 32;
        persona.bio = 'Soy el tipo ese que programa por estudiar';

        // Al utilizar override para pasar la clase a cadena podemos imprimir el objeto:
        print(persona); 
        }

        // Creamos una clase:
        class Persona {
        // Atributos
        String nombre;
        int edad;
        String bio;

        // Get y sets

        // Constructores

        // Métodos

        // El @override es un decorador y sirve para subscribir un método:
        @override 
        String toString(){
            return '$nombre $edad $bio';
        }
    }

Atributos Privados
******************
Para hacer que los atributos sean privados en Dart el modificador que utilizamos es ``_``

.. code::  

    class Persona {
        // Para hacer un atributo privado ponemos el caracter _
        String _nombre;
        int _edad;
        String _bio;

        // Get y sets

        // Constructores

        // Métodos
        @override 
        String toString(){
            return '$_nombre $_edad $_bio';
        }

    }

Getters y Setters
*****************
Con Get y Set podemos trabajar con atributos privados fuera de clase, osea cuando hemos creado un objeto.

.. code::  

    class Persona {
        String nombre;
        int edad;
        String _bio;

        // Get y sets
        
        // Los gets recuperan información:
        String get bio {
            return _bio;
        }

        // Para establecer el valor al atributo privado utilizamos set:
        set bio(String texto) {
            _bio = texto;
        }

        // Constructores

        // Métodos
        @override 
        String toString(){
            return '$nombre $edad $_bio';
        }

    }

Constructores básicos
*********************
En Dart para las clases como en cualquier lenguaje tenemos los constructores comunes:

* Creamos un archivo llamado Persona.dart:

.. code::  

    class Persona {
        String nombre;
        int edad;
        String _bio;

        // Get y sets
        String get bio {
            return _bio;
        }

        set bio(String texto) {
            _bio = texto;
        }

        // Constructores

        // Constructor básico lleva por defecto el nombre de la clase:
        Persona(int edad, String nombre){ // Normalmente le pasamos argumentos a un constructor
            print('Constructor');
            // Podemos asignar un valor mediante el setter o utilizar el atributo privado:
            bio = 'Hola desde el constructor';
            this._bio = 'Utilizando el privado';
            // Le asignamos los argumentos a sus atributos:
            this.edad = edad;
            this.nombre = nombre;

        }


        // Métodos
        @override 
        String toString(){
            return '$nombre $edad $_bio';
        }

    }

* Y ahora creamos nuestro archivo main.dart:

.. code:: dart 

    import 'persona.dart';

    main(){
        // Ahora le tenemos que pasar los dos parametros al constructor:
        final persona = new Persona(32, 'Guillermo');

        persona.bio = "Soy un tipejo";

        print(persona.bio);
    }

* Veamos como se pasan argumentos posicionales:

.. code:: dart 

    import 'persona.dart';

    main(){
        // Y como es posicional le asignamos el nombre:
        final persona = new Persona(edad:32, nombre:'Guillermo');

        persona.bio = "Soy un tipejo";

        print(persona.bio);
    }

Constructores con nombre 
************************
Los constructores con nombre son constructores adicionales que se generan en las clases

* Ejemplo de clase:

.. code::  

    class Persona{
        String nombre;
        int edad;
        String _bio;

        // Get y sets
        String get bio {
            return _bio;
        }

        set bio(String texto) {
            _bio = texto;
        }

        Persona({this.edad, this.nombre}){ // Podemos hacer opcional los parametros también
            print('Constructor');
        }
        // Vamos a crear un constructor con nombre:
        Persona.persona30( this.nombre ){
            this.edad = 30;
        }


        @override 
        String toString(){
            return '$nombre $edad $_bio';
        }

    }

* Crear objeto en main:

.. code:: dart 

    import 'persona.dart';

    main(){
        final persona = new Persona(edad:32, nombre:'Guillermo');

        // Nos creamos un nuevo objeto con el constructor nombre:
        final persona2 = new Persona.persona30('Alfredo');

        persona.bio = "Soy un tipejo";

        print(persona.bio);
        print(persona2);
    }

Atributos y métodos estáticos
*****************************
Al utilizar el modificador ``static`` podemos acceder a los atributos y métodos que lo posean sin necesidad de crear un objeto.

.. code:: dart 

    class Herramientas{
        // Convertimos en estatico el listado:
        static const List<String> listado = ['Martillo', 'Llave Inglesa','Desarmador'];

        // Metodo estatico:
        static void imprimirListado() => listado.forEach(print);
        }

        main() {
        // Y así podemos acceder al listado sin crear un objeto y lo recorremos con el metodo forEach:
        Herramientas.listado.forEach(print);

        // Vamos a llamar al metodo de forma estatica:
        Herramientas.imprimirListado();

        // Y además podemos añadir o editar información:
        Herramientas.listado.add('Tenazas'); // Esta línea dará error si lo tenemos declarado como const (que sería lo más normal)

        Herramientas.listado.forEach(print);

        // Vamos a llamar al metodo de forma estatica:
        Herramientas.imprimirListado();
    }

Constructor Factory 
*******************
Un constructor factory retorna otro constructor y se suele utilizar para patrones singleton.

* Ejemplo de uso:

.. code:: dart 

    class Rectangulo{
        int base;
        int altura;
        int area;
        String tipo; // Base = altura, es un cuadrado.
        // El constructor factory retorna algo de tipo Rectangulo:
        factory Rectangulo(int base, int altura){
            if(base == altura){
                return Rectangulo.cuadrado(base);
            }else{
                return Rectangulo.rectangulo(base, altura);
            }
        }

        // Creamos un constructor con nombre para el cuadrado:
        Rectangulo.cuadrado(int base){
            this.base = base;
            this.altura = base;
            this.area = base * altura;
            this.tipo = 'Cuadrado';
        }

        // Creamos un constructor con nombre para el rectangulo:
        Rectangulo.rectangulo(int base, int altura){
            this.base = base;
            this.altura = altura;
            this.area = base * altura;
            this.tipo = 'Rectángulo';
        }
    }

    main(List<String> args) {
        // Creamos el objeto y le pasamos los valores:
        final figura = new Rectangulo(10, 15);
        // Si es igual nos mostrará cuadrado y sino rectangulo:
        print(figura.tipo);
    
    }

Patrón Singleton en Dart 
************************
El patrón Singleton es muy útil para crear clases que solo se instancian una vez.

.. code:: dart 

    class MiServicio{
        // Creamos los atributos de forma privada que creará un objeto con el constructor privado:
        static final MiServicio _singleton = new MiServicio._privado();

        // Generamos un constructor de factory que retornará el objeto privado singleton:
        factory MiServicio(){
            return _singleton;
        }

        // En el patrón singleton utilizamos un constructor privado:
        MiServicio._privado();

        String url = 'https://abc';
        String key = 'ABC123';
    }

Herencia
########
Hay varias cosas interesantes que trae consigo Dart en referencia a la herencia.

Uso de extends
**************
Para heredar de una clase padre utilizamos ``extends`` en la clase hija:

.. code:: dart 

    // Creamos una clase:
    class Vehiculo {
        bool encendido = false;

        void encender(){
            encendido = true;
            print('Vehiculo encendido');
        }

        void apagar(){
            encendido = false;
            print('Vehículo apagado');
        }
    }

    // Ahora vamos a crear una clase que herede de Vehículo:
    class Coupe extends Vehiculo{
        int kilometraje = 0;
    }

    main() {
        // Creamos un objeto:
        final ford = new Coupe();
        // Y comprobamos que tenemos todas los atributos y métodos de Vehiculo:
        ford.encender();
        ford.apagar();
    }

Clase abstracta
***************
Las clases abstractas se utilizan en programación para diseñar la estructura de una clase padre que servirá de referencia para las clases hijas

* Ejemplo de uso:

.. code::  

    // Definimos la clase abstracta y de esta no se puede crear objeto ya que es un cascarón de otra clase hija:
    abstract class Vehiculo {
        bool encendido = false;

        void encender(){
            encendido = true;
            print('Vehiculo encendido');
        }

        void apagar(){
            encendido = false;
            print('Vehículo apagado');
        }

        // Creamos un método vacio que tendremos que inicializar en el hijo:
        bool encenderMotor();
    }

    class Coupe extends Vehiculo{
        int kilometraje = 0;

        // Para implementar un metodo vacio del padre usamos el decorador override:
        @override // Este decorador no es obligatorio en esta ocasión pero es una buena práctica cuando sobreescribimos un método ponerlo.
        bool encenderMotor(){
            print('Motor OK!');
            return true;
        }
    }

    main() {

        final ford = new Coupe();
        ford.encender();
        ford.apagar();
        
    }

Super constructor
*****************
El super constructor lo utilizamos para modificar la funcionalidad del constructor padre en el constructor hijo

.. code:: dart 

    class Persona{
        String nombre;
        int edad;

        Persona(this.nombre, this.edad);

        void imprimirNombre() => print('Nombre: $nombre, Edad: $edad');
    }

    // Ahora creamos una clase que hereda de Persona:
    class Cliente extends Persona{
        String direccion;
        List ordenes = [];
        
        // Como el padre tenemos un constructor que recibe parámetros tenemos que llamar un super constructor:
        Cliente(int edadActual, String nombreActual):
            super(nombreActual, edadActual); // Ahora dentro del constructor utilizamos el super constructor y le pasamos los parametros que recibe el constructor hijo
    }

    main() {
        // Creamos un objeto con el hijo:
        final pedro = new Cliente(32, 'Pedro');
        pedro.imprimirNombre();
    }

Sobreescribir métodos
*********************
Para sobreescribir la funcionalidad de un método en dart utilizamos el decorador ``@override``

.. code::  

    class Persona{
        String nombre;
        int edad;

        Persona(this.nombre, this.edad);

        void imprimirNombre() => print('Nombre: $nombre, Edad: $edad');
    }

    class Cliente extends Persona{
        String direccion;
        List ordenes = [];
        
        Cliente(int edadActual, String nombreActual):
            super(nombreActual, edadActual); 

        // Override lo usamos para sobreescribir metodos del padre:
        @override 
        void imprimirNombre(){
            super.imprimirNombre(); // Ponemos esta linea si queremos imprimir el metodo padre original.
            print('Cliente: $nombre ($edad)');
        }
    }

    main() {

        final pedro = new Cliente(32, 'Pedro');

        pedro.imprimirNombre();
    }

Mixins
******
Los mixins son muy parecidos a los extends pero tienen unas características especiales

.. code:: dart 

    // Creamos un mixin que es similar a una clase abstracta pero no tiene constructor a diferencia de esta ni se puede instanciar. 
    mixin Logger{ // Un mixin sirve únicamente como una clase que sirve para que se herede de esta sus atributos y métodos:
        void imprimir(String texto){
            final hoy = DateTime.now();
            print('$hoy :::: $texto');
        }
    }

    // Creamos una clase que herede el mixin:
    abstract class Astro with Logger {
        String nombre;

        Astro(){
            imprimir('--- Init del Astro ---');
        }

        void existo(){
            imprimir('-- Soy un ser celestial y existo --');
        }
    }

    // Creamos una clase que herede de Astro:
    class Asteroide extends Astro{
        String nombre;

        Asteroide(this.nombre){
            imprimir('Soy $nombre');
        }
    }

    main() {
        final ceres = new Asteroide('Ceres');
    }

Manejo de errores
#################
El manejo de errores en Dart se hace con ``catchError``

* Ejemplo de uso:

.. code:: dart

    main(){
        Future<String> timeout = Future.delayed(Duration(seconds: 3), (){ // Este código se va a ejecutar 3 segundos desupés.
            
            // provocamos un error con throw:
            if(1 == 1){
            throw 'Auxilio!, exploto el programa!!!';
            }
            
            return 'Retorno de dato';
        });
        // Utilizamos catchError para capturar cualquier error que suceda mientras se ejecuta el future:
        timeout.then((texto)=> print(texto)).catchError((error)=> print(error));
    }

Programación Reactiva: Streams
##############################
Un Stream es un flujo de datos, es similar a un observable que vigila el flujo de datos de manera constante enviando y recibiendo cambios en tiempo real.

* Ejemplo de uso de Stream:

.. code:: dart 

    // Cargamos la librería async:
    import 'dart:async';

    main(){
        // Creamos un objeto de tipo Stream:
        final streamController = StreamController();

        // Para utilizarlo le añadimos el listen() que es como un subscribe():
        streamController.stream.listen((data){
            print('Despegando! $data');
        });

        // Ahora vamos a agregarle información al stream:
        streamController.sink.add('Apollo 11');

        print('Fin del main');
    }

* Uso de onError, onDone y cancelOnError:

.. code:: dart 

    import 'dart:async';

    main(){
        final streamController = StreamController();
        // Ajustamos el stream con una función lambda:
        streamController.stream.listen(
                (data) => print('Despegando! $data'),
                onError: (err) => print('Error! $err'), //Manejamos un error cuando este suceda.
                onDone: () => print('Mision cumplida'), // Esta opción se desplegará una vez se finalice el stream sin errores
                cancelOnError: true, // Si tenemos en true esta opción se cancelará el programa y apollo 12 no despegará.
        );

        streamController.sink.add('Apollo 11');
        // Podemos lanar un error con los stream:
        streamController.sink.addError('Houston, Tenemos un problema');
        // Si el error esta manejado con onError podremos seguir con el flujo de datos:
        streamController.sink.add('Apollo 12');
        
        print('Fin del main');
    }

* Tipados y Broadcast para transmisiones paralelas:

.. code:: dart 

    import 'dart:async';

    main(){
        // Podemos asignar el tipado para que devuelva un tipo de dato estrictamente:
        final streamController = new StreamController<String>.broadcast(); // El broadcast permite multiples subscripciones
        streamController.stream.listen(
                (data) => print('Despegando! $data'),
                onError: (err) => print('Error! $err'),
                onDone: () => print('Mision cumplida'),
                cancelOnError: true
        );
        // gracias al broadcast podemos volver a generar otro stream similar:
        streamController.stream.listen(
                (data) => print('Vamos! $data'),
                onError: (err) => print('Fallo! $err'),
                onDone: () => print('Funcionó'),
                cancelOnError: true
        );

        streamController.sink.add('Apollo 11');
        streamController.sink.addError('Houston, Tenemos un problema');
        streamController.sink.add('Apollo 12');
        
        print('Fin del main');
    }
