=======
Flutter
=======

.. image:: /logos/logo-flutter.png
    :scale: 75%
    :alt: Logo JS
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con Flutter, el SDK para desarrollo de Apps para Android e IOS. 

.. contents:: Índice

Instalación de Flutter
######################
Para instalar Flutter en nuestro ordenador debemos hacer lo siguiente:

* Visitar la página web https://flutter.dev/docs/get-started/install y descargar el sdk correspondiente a nuestro sistema operativo.
* Descomprimir el contenido del archivo
* Para añadir Flutter a nuestro path si estamos en linux en la carpeta que extragimos el directorio flutter (fuera del mismo) ejecutar ``export PATH="$PATH:`pwd`/flutter/bin"`` para añadir al path. 
* comprobar si se ha añadido con ``echo $PATH``
* ejecutar ``flutter doctor`` para comprobar que todo va bien y comprobar que nos falta (un emulador y un IDE como Android Studio o Visual Studio Code)
* Recuerda que necesitas una licencia y aceptar los terminos de esta, para ello ejecuta ``flutter doctor --android-licenses``

.. attention:: 
    Si no funciona flutter doctor es que no ha salido bien la configuración, otro modo de realizar la instalación del SDK es acceder al directorio flutter->bin y ejecutar ``./flutter``, después debería funcionar el comando ``flutter doctor``

Preparar Android Studio para trabajar con Flutter
*************************************************
* Descargamos y descomprimimos Android Studio de https://developer.android.com/studio/
* Si trabajamos con Linux extraemos el directorio y accedemos a la carpeta bin donde podremos ejecutar ``studio.sh``
* Podemos instalar un acceso directo en nuestro sistema Linux en ``editor de menu`` que en Mint podemos encontrarlo haciendo clic derecho en inicio -> configurar y clic en el botón ``abrir editor de menu``
* Localizamos la ruta del archivo y la ejecutamos: ``android-studio/bin/ ./studio.sh`` según donde se deje puesto. (usr normalmente)
* Ejecutamos Android Studio y en la página de menú principal hacemos clic en configure->plugins y buscamos e instalamos los plugins **dart** y **flutter**
* Vamos a añadir un SDK accediendo desde la pantalla principal a configure->SDK tools y hacemos clic en install para escoger uno.
* Solo nos falta ir a configure->ADV tools y configurar un nuevo dispositivo virtual. Recomiendo Pixel3XL de 6.3"

De este modo estamos listos para trabajar con Android Studio.

.. attention::
    Es posible que tengamos problemas con el emulador Android debido a la ausencia del modulo KVM. Si es así ejecutamos en terminal: ``sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386`` y reiniciamos Android Studio. Si no funciona siempre podemos utilizar un dispositivo físico.


Fundamentos Básicos
###################
Lo primero que debemos entender en Flutter es que todo se compone con **Widgets**

Los Widgets son clases en Flutter basadas en Dart que muestran una sección gráfica en nuestra aplicación.

Ejemplo de Uso:

.. code-block:: dart

    AppBar(
	    title: Text('Hola mundo'),
	)

Este ejemplo muestra una barra con un texto. Para ello hace uso de dos widgets, AppBar y Text.

Árbol de Widgets
****************
En cada página de Flutter comenzamos siempre con uno de los siguientes Widgets Abstractos:
* StatelessWidget: No tiene estado, por tanto no puede saber si una propiedad cambia.
* StatefulWidget: Tiene estado y por tanto puede saber si existen cambios en el.

Dentro de cada uno de estos dos Widgets abstractos podemos encontrar comunmente los siguientes widgets:
* Scaffold: Define el fondo de pantalla.
* AppBar: Barra superior.
* TabBar: Barra inferior.
* Container: contenedor central.
* Text: Texto común.
* Row: Fila.

Estructura de un proyecto en Flutter
************************************
Cada proyecto de Flutter presenta el siguiente árbol de directorios:
* android: carpeta con el archivo ya generado.
* build: carpeta de aplicación ya compilada.
* lib: carpeta donde se guardan los archivos de pantallas en Android.
* test: directorio donde se guardan los test de cada aplicación.

Archivos destacados:
* pubspec.yaml: Archivo de configuración donde podemos realizar cambios y agregar dependencias.

Instalación de dependencias
***************************
Cuando recuperamos un proyecto Flutter de algún repositorio para instalar sus dependencias ejecutamos ``flutter packages get``

Creando tu primer Proyecto
##########################
Vamos a comenzar a crear un nuevo proyecto en Flutter:

* Creamos un nuevo proyecto Flutter, seleccionamos la primera opción y en el apartado SDK hacemos clic en Install SDK, localizamos la carpeta de flutter y aceptar.
* Borramos la carpeta test. 
* Nos dirigimos al directorio lib y abrimos el archivo main.dart y borramos todo su contenido.
* Ahora escribimos el siguiente código:

.. code:: dart

    // Importamos la librería de material:
    import 'package:flutter/material.dart';

    // Creamos la función principal:
    void main(){
        // Arrancamos la aplicación con esta línea:
        runApp(new MyApp());
    }

    // Creamos el widget principal:
    class MyApp extends StatelessWidget{
        // cargamos el método build con un decorador para sobreescribirlo:
        @override // el parámetro context que recibe contiene el arbol de widgets
        build(context){
            // retornamos un widget que recibirá otros widgets inferiores:
            return MaterialApp(
            // en la key home le pasamos un widget que se dibujará en la pantalla llamado center:
            home: Center(
                // center recibe un child y sirve para centrar todos los elementos:
                child: Text("Hola mundo"), // en su child escribimos un texto con el widget Text.
            )
            );
        }
    }

Una vez escrito el código podemos ejecutar el emulador o reiniciarlo en caso de tenerlo ya funcionando.

.. hint:: 
    Tenemos un snippet para crear la primera pantalla de flutter que lo genera todo, se ejecuta cuando el archivo mainl.dart esta en blanco escribiendo la palabra ``mateApp`` y pulsando la tecla **intro***

Elementos que tiene MaterialApp():

* debugShowCheckedModeBanner: true por defecto, muestra una banda roja en la esquina superior derecha. **false** para eliminarla
* home: devuelve la pantalla principal, en su lugar podemos mostrar distintos scaffolds importados de otros archivos a través de un Widget Center().


Separar la lógica en varios archivos
************************************
Para tener una buena lectura del código es necesario seguir una estructura de directorios y archivos donde podamos separar las distintas páginas y componentes que se agrupan en Flutter:

* Primero nos situamos dentro de la carpeta **lib** y creamos un nuevo **package** al que llamaremos **src**.

Ahora podemos ir incluyendo en esta carpeta los distintos elementos de nuestro proyecto.

Primera APP en Flutter
######################
Vamos a crear de nuevo la primera app que nos muestra flutter.

Scaffold
********
El Scaffold como ya hemos dicho antes define el fondo de nuestra pantalla, de modo que tenemos que definirlo en cada una de las pantallas que vayamos creando.

Pociciones de un Scaffold:

* appBar: Barra menú superior.
* body: Cuerpo de la pantalla.
* floatingActionButton: Botón emergente que suele mostrarse abajo a la derecha por defecto.
* floatingActionButtonLocation: Establece la posición del botón flotante. Ejemplo: ``floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat``

Ejemplo de Scaffold:

* Creamos un package en **src** llamado **pages** y dentro de esta nueva carpeta creamos el archivo **home_page.dart** y escribimos lo siguiente:

.. code:: dart

    import 'package:flutter/material.dart';


    // Creamos un widget que usaremos como pantalla
    class HomePage extends StatelessWidget{

        // Sobreescribimos el método build para crear la pantalla:
        @override
        // El widget principal siempre es build y recibe en el context la referencia de todos los widgets:
        Widget build(BuildContext context){
            // Y retornamos un widget llamado scaffold:
            return Scaffold(
                appBar: AppBar( // Recibiremos una barra superior en appbar
                    title: Text("Título"), // El title recibirá un widget de tipo texto.
                ),
                body: Center( // Y tambien body recibiremos un contenedor centrado.
                    child: Text("hola mundo"), // dentro añadimos un texto.
                ),
            );
        }
    }

* Para hacer funcionar esta página la tenemos que cargar desde main.dart:

.. code:: dart

    import 'package:flutter/material.dart';
    // importamos el archivo donde hemos escrito el scaffold:
    import 'package:flutterapp/src/pages/home_page.dart';

    void main(){
        runApp(new MyApp());
    }

    class MyApp extends StatelessWidget{
        @override
        build(context){
            return MaterialApp(
                home: Center(
                // ahora dentro del Center podemos cargar la pantalla que hemos creado:
                child: HomePage(),
                )
            );
        }
    }

Y así tenemos listo un scaffold.

Columnas
********
En Flutter podemos crear disposiciones por columnas (de arriba abajo), para ello utilizamos el widget **Column**.

Este contiene las siguientes características:
* mainAxisAligment: Sirve para alinear horizontalmente los elementos que veremos.
* children: es el lugar donde colocaremos los widgets cargados siempre en una matriz de widgets. 

Ejemplo de uso:

.. code:: dart

    import 'package:flutter/material.dart';


    class HomePage extends StatelessWidget{

    @override
    Widget build(BuildContext context){
            return Scaffold(
                appBar: AppBar(
                    title: Text("Título"),
                ),
                body: Center(
                    child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: <Widget>[
                        Text('Hola', style: TextStyle(fontSize: 25)),
                        ],
                    ),
                ),
            );
        }
    }

Botton Flotante
***************
Es muy común ver en apps un botón flotante abajo a la derecha o en otra posición. Este botón lo añadimos en **Scaffold** y se llama **FloatingActionButton**

Este botón tiene las siguientes características:

* child: Recibe un icono o un texto.
* onPressed: Ejecuta un método anónimo personalizado.

.. code:: dart

    import 'package:flutter/material.dart';


    class HomePage extends StatelessWidget{

        @override
        Widget build(BuildContext context){
            return Scaffold(
                appBar: AppBar(
                    title: Text("Título"),
                ),
            body: Center(
                child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                        children: <Widget>[
                            Text('Hola', style: TextStyle(fontSize: 25)),
                        ],
                ),
            ),
            floatingActionButton: FloatingActionButton(
                    child: Icon(Icons.add),
                    onPressed: (){
                    print("Hola mundo");
                }
            ),
            floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,
            );
        }
    }

StatefulWidget
**************
Si vamos a hacer cambios en nuestra pantalla, lo idoneo es pasarse a un **StatefulWidget**

Ejemplo de StateFulWidget:

.. code:: dart

    import 'package:flutter/material.dart';


    class HomePage extends StatefulWidget {

        @override
        createState() => _HomePageState();
    }

    class _HomePageState extends State<HomePage>{

        // Esta variable es por lo que vamos a necesitar el stateful:
        int _contador = 0;

        Widget build(BuildContext context){
            return Scaffold(
                appBar: AppBar(
                    title: Text("Título"),
                ),
                body: Center(
                    child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: <Widget>[
                        Text('Hola', style: TextStyle(fontSize: 25)),
                        Text('$_contador', style: TextStyle(fontSize: 20))
                    ],
                    ),
                ),
                floatingActionButton: FloatingActionButton(
                    child: Icon(Icons.add),
                    onPressed: (){
                    setState((){
                        _contador++;
                    });
                    }
                ),
                floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,
            );
        }
    }

.. hint::
    Recuerda que puedes imprimir una variable en dart utilizando el símbolo $ dentro de las comillas Ej: '$_contador'

.. hint::
    Recuerda que el síbmolo _ indica que la variable o el método es privado

.. hint:: 
    con el método setState() redibujamos la pantalla para que se muestren los cambios. Sin el no pasaría el contador de 0 aunque se incremente internamente.


Filas
*****
Las filas las generamos con el widget **Row()**

Tiene las siguientes características:

* mainAxisAligment: Como en Column pero con las opciones start,center, end, space around, space between.
* children: Recibe una lista de widgets que irá mostrando de izquierda a derecha.

Ejemplo de uso:

.. code:: dart 

    import 'package:flutter/material.dart';


    class HomePage extends StatefulWidget {

        @override
        createState() => _HomePageState();
        }

        class _HomePageState extends State<HomePage>{

        // Esta variable es por lo que vamos a necesitar el stateful:
        int _contador = 0;

        Widget build(BuildContext context){
            return Scaffold(
                appBar: AppBar(
                    title: Text("Título"),
            ),
            body: Center(
                child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: <Widget>[
                        Text('Hola', style: TextStyle(fontSize: 25)),
                        Text('$_contador', style: TextStyle(fontSize: 20))
                    ],
                ),
            ),
            floatingActionButton: Row(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: <Widget>[
                    SizedBox(width:30),
                    FloatingActionButton(child: Icon(Icons.exposure_zero), onPressed: (){}
                    ),
                    Expanded(child: SizedBox()),
                    FloatingActionButton(child: Icon(Icons.add), onPressed: (){}),
                    SizedBox(width: 5.0),
                    FloatingActionButton(child: Icon(Icons.remove), onPressed: (){}),
                ],
            ),
            floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,
            );
        }
    }

Crear tus propios widgets
*************************
Crear tus propios widgets es muy útil para separar código en las páginas y así poder hacer el código mas legible.

Ejemplo para crear un Widget:

.. code:: dart

    import 'package:flutter/material.dart';


    class HomePage extends StatefulWidget {

        @override
        createState() => _HomePageState();
    }

    class _HomePageState extends State<HomePage>{

        // Esta variable es por lo que vamos a necesitar el stateful:
        int _contador = 0;

        Widget build(BuildContext context){
            return Scaffold(
                appBar: AppBar(
                    title: Text("Título"),
                ),
                body: Center(
                    child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: <Widget>[
                        Text('Hola', style: TextStyle(fontSize: 25)),
                        Text('$_contador', style: TextStyle(fontSize: 20))
                    ],
                    ),
                ),// Llamamos aquí en su lugar al nuevo widget _botonera():
                floatingActionButton: _botonera(),
                floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,
            );
        }
        // Creamos un método de tipo widget:
        Widget _botonera(){
            // retornamos un widget con el contenido que queremos mostrar:
            return Row(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: <Widget>[
                    SizedBox(width:30),
                        FloatingActionButton(child: Icon(Icons.exposure_zero), onPressed: _reiniciar),
                        Expanded(child: SizedBox()),
                        FloatingActionButton(child: Icon(Icons.add), onPressed: _sumar),
                        SizedBox(width: 5.0),
                        FloatingActionButton(child: Icon(Icons.remove), onPressed: _restar),
                    ],
                    ); // recuerda poner el ; en lugar de ,
                }

                    // aprovechamos para agregar metodos que alteren el número para suma, resta y reinicio:
                    void _reiniciar(){
                        setState(() => _contador = 0);
                    }
                    void _sumar(){
                        setState(()=> _contador++);
                    }
                    void _restar(){
                        setState(()=> _contador--);
                    }
                }
    }


Widgets de Flutter
##################
En esta sección vamos a ver los widgets mas usados en flutter.

Crear Listas con ListView
*************************
Para crear una lista utilizamos el widget **ListView**.

Este widget contiene los siguientes elementos:

* Children: recibe una lista de widgets que contiene algunos widgets específicos:    
    * ListTile: Elemento de la lista, se pueden poner tantos cuantos sean necesarios.
    * Divider: Línea divisora que se coloca entre cada ListTile.


Ejemplo de uso:

.. code:: dart

    import 'package:flutter/material.dart';

    class HomePage extends StatelessWidget {
        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Listas')
            ),
            body: ListView(
                children: <Widget>[
                ListTile(
                    title: Text('Titulo de elemento')
                ),
                Divider(),
                ListTile(
                    title: Text('Titulo de elemento 2')
                ),
                Divider(),
                ListTile(
                    title: Text('Titulo de elemento 3')
                )
                ]
            )
            );
        }
    }

pasar Lista de dart a List de Flutter
+++++++++++++++++++++++++++++++++++++
Lo mas común en Flutter es encontrarse listas dart con la información y es necesario realizar una serie de pasos para mostrarla en un ListView.

Ejemplo de conversión:

.. code:: dart

    import 'package:flutter/material.dart';

    class HomePage extends StatelessWidget {
        // Creamos una lista de la compra:
        final compra = ['leche', 'galletas', 'huevos', 'patatas', 'arroz'];

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: Text('Listas')
                ),
                body: ListView(
                    children: _crearListado()
                )
            );
        }

        // Creamos un nuevo List de tipo widget que contendrá los ListTile de nuestra lista:
        List<Widget> _crearListado(){
            // Ahora vamos a crear otra lista dentro para guardar los elementos de la lista en dart:
            List<Widget> lista = new List<Widget>();
            // Recorremos la lista con un bucle:
            for(String c in compra){
            // Guardamos cada elemento de la lista en un listtile:
            final compraTemp = ListTile(
                title: Text(c)
            );
            // añadimos cada listtile al List:
            lista.add(compraTemp);
            // y añadimos un divisor:
            lista.add(Divider());
            }
            // devolvemos la lista:
            return lista;
        }
    }

Pasar un JSON local a ListView
++++++++++++++++++++++++++++++
Veamos como utilizar un JSON como proveedor de información dinámica a la hora de generar un menu.

Lo primero será crear un package en la raiz del proyecto llamado **data** y en la nueva carpeta creamos el archivo **opciones.json**:

.. code:: json

    {
        "nombreApp" : "Menu",
        "rutas" : [
            {
            "ruta" : "alerts",
            "icono" : "add_alert",
            "texto": "Avisos"
            },
            {
            "ruta" : "acceso",
            "icono" : "accessibility",
            "texto": "Acceso"
            },
            {
            "ruta" : "info",
            "icono" : "folder_open",
            "texto": "Información"
            }
        ]
    }

Para que podamos utilizar un archivo json necesitamos agregarlo en **pubspec.yaml** dentro de assets:

.. code:: dart

    assets:
        - data/opciones.json

.. warning::
    Tras modificar pubspec.yaml tenemos que detener el emulador pulsando el botón rojo y volver a ejecutarlo

El siguiente paso es generar un proveedor de servicios o Provider, para ello accedemos a la carpeta **src** y creamos el package **providers** en el cual crearemos el archivo **menu_provider.dart**:

.. code:: dart

    // Importamos el paquete de servicios de flutter:
    import 'package:flutter/services.dart' show rootBundle;
    // para parsear un json necesitamos en conversor de dart:
    import 'dart:convert';

    class _MenuProvider{
        // Creamos una lista dinámica:
        List<dynamic> opciones = [];

        // con Future no necesitamos hacer nada en el constructor:
        _MenuProvider(){}

        // Utilizaremos Future para recuperar la información de forma asincrona:
        Future<List<dynamic>> cargarDatos() async{
            // cargamos el archivo json:
            final respuesta = await rootBundle.loadString('data/opciones.json');

            // parseamos el JSON a dart:
            Map dataMap = json.decode(respuesta);

            // seleccionamos el apartado rutas:
            opciones = dataMap['rutas'];

            // devolvemos las opciones:
            return opciones;
        }
    }

    // Creamos el objeto inmutable del menu:
    final menuProvider = new _MenuProvider();

Ahora nos vamos a la página donde queremos cargar el listado y utilizamos un **Future Builder** para realizar promesas en Flutter:

.. code:: dart

    import 'package:flutter/material.dart';
    // Importamos el archivo menuProvider:
    import 'package:flutterapp/src/providers/menu_provider.dart';

    class HomePage extends StatelessWidget {
        final compra = ['leche', 'galletas', 'huevos', 'patatas', 'arroz'];

        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Menu Principal')
            ),// cargamos el nuevo widget menu:
            body: _menu()
            );
        }

        // Creamos un Widget para mostrar el provider:
        Widget _menu(){
            print(menuProvider.opciones);
            // devolvemos un Future builder:
            return FutureBuilder(
            future: menuProvider.cargarDatos(), // en future ejecutamos la llamada a la informacion
            initialData: [], // por defecto tenemos que asignar un initialData vacío
            builder: (BuildContext context, AsyncSnapshot<List<dynamic>> snapshot){ // en el builder crearemos el ListView con los datos del JSON
                return ListView(
                children: _opciones(snapshot.data), // Los listtiles los construiremos en un nuevo método
                );
            }

            );
        }

        // creamos el método que hará los listtiles como antes pero usando el JSON parseado:
        List<Widget> _opciones(List<dynamic> datos){
            final List<Widget> opciones = [];
            // recorremos los datos JSON recibidos por parametros:
            datos.forEach((opcion){
            final widgetTemp = ListTile(
                title: Text(opcion['texto']),
                leading: Icon(Icons.account_circle, color: Colors.amber),
                trailing: Icon(Icons.keyboard_arrow_right, color: Colors.amberAccent),
                onTap: (){

                }
            );

            // los vamos pasando como antes a la Lista:
            opciones.add(widgetTemp);
            opciones.add(Divider());
            });

            return opciones;
        }
    }

Creando Utilidades - Obtener los iconos de JSON para el listado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Hay un modo bastante ordenado de hacer las cosas, tenemos un solo icono hardcodeado y necesitamos solucionar ese problema. Nuestro JSON trae unos nombres de icono que podemos utilizar como clave para extraer dichos iconos de forma dinámica. 
Para eso nos creamos una utilidad, en la carpeta **src** creamos una carpeta llamada **utils** y dentro un archivo al que llamaremos **iconos_util.dart**:

.. code:: dart

    import 'package:flutter/material.dart';

    // creamos la lista para referenciar los iconos a unas claves que serán la referencia a seguir:
    final _iconos = <String, IconData>{
        'add_alert': Icons.add_alert,
        'accessibility': Icons.accessibility,
        'folder_open': Icons.open_in_new
        };

        // Ahora creamos una función que nos devolverá un icono según la clave recibida:
        Icon getIcon(String nombreIcono){
        return Icon(_iconos[nombreIcono], color: Colors.amber);
    }

Volvemos al listado para utilizar nuestro utilidad de iconos:

.. code:: dart

    import 'package:flutter/material.dart';
    import 'package:flutterapp/src/providers/menu_provider.dart';
    // importamos la utilidad:
    import 'package:flutterapp/src/utils/icono_utils.dart';

    class HomePage extends StatelessWidget {

        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Menu Principal')
            ),//
            body: _menu()
            );
        }

        Widget _menu(){
            print(menuProvider.opciones);
            return FutureBuilder(
            future: menuProvider.cargarDatos(),
            initialData: [],
            builder: (BuildContext context, AsyncSnapshot<List<dynamic>> snapshot){
                return ListView(
                children: _opciones(snapshot.data),
                );
            }

            );
        }

        List<Widget> _opciones(List<dynamic> datos){
            final List<Widget> opciones = [];
            datos.forEach((opcion){
            final widgetTemp = ListTile(
                title: Text(opcion['texto']),
                // le pasamos al leading la funcion getIcon y por parametros el codigo del icono:
                leading: getIcon(opcion['icono']),
                trailing: Icon(Icons.keyboard_arrow_right, color: Colors.amberAccent),
                onTap: (){

                }
            );

            opciones.add(widgetTemp);
            opciones.add(Divider());
            });

            return opciones;
        }
    }

Navegacion
##########

Navegación entre páginas
************************

Vamos a ver como navegar a través de distintas pantallas de flutter.

Para ello nos valemos del punto anterior en el que creamos un listado y establecer un cambio.

* Vamos a la carpeta **pages** y creamos un archivo llamado **avisos_page.dart** en el que escribimos lo siguiente:

.. code:: dart

    import 'package:flutter/material.dart';

    class AvisosPage extends StatelessWidget {
        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Página de Avisos')
            ),
            body: Center(
                child: Text('No existen avisos')
            ),
            );
        }
    }


* Regresamos a **home_page.dart** para agregar el vínculo:

.. code:: dart

    import 'package:flutter/material.dart';
    import 'package:flutterapp/src/providers/menu_provider.dart';
    import 'package:flutterapp/src/utils/icono_utils.dart';

    // Importamos la página avisos:
    import 'package:flutterapp/src/pages/avisos_page.dart';

    class HomePage extends StatelessWidget {

        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Menu Principal')
            ),//
            body: _menu()
            );
        }

        Widget _menu(){
            print(menuProvider.opciones);
            return FutureBuilder(
            future: menuProvider.cargarDatos(),
            initialData: [],
            builder: (BuildContext context, AsyncSnapshot<List<dynamic>> snapshot){
                return ListView(        // El widget opciones deberá enviar el contexto de la app:
                children: _opciones(snapshot.data, context),
                );
            }

            );
        }
                                                    // del mismo modo lo recibirá:
        List<Widget> _opciones(List<dynamic> datos, context){
            final List<Widget> opciones = [];
            datos.forEach((opcion){
            final widgetTemp = ListTile(
                title: Text(opcion['texto']),
                leading: getIcon(opcion['icono']),
                trailing: Icon(Icons.keyboard_arrow_right, color: Colors.amberAccent),
                onTap: (){
                    // Creamos la ruta:
                    final route = MaterialPageRoute(
                    // apuntamos la ruta con el metodo de la página de rutas:
                    builder: (context) => AvisosPage()
                    );

                    // realizamos la navegación agregandole el contexto y la ruta:
                    Navigator.push(context, route);
                }
            );

            opciones.add(widgetTemp);
            opciones.add(Divider());
            });

            return opciones;
        }
    }


Navegación por rutas
********************
Desde nuestro main se puede configurar un sistema de enrutamiento con el atributo **routes** en el widget **MaterialApp**.

.. code:: dart

    import 'package:flutter/material.dart';
    // se importan las páginas que vamos a enrutar:
    import 'package:flutterapp/src/pages/home_page.dart';
    import 'package:flutterapp/src/pages/avisos_page.dart';

    void main(){
        runApp(new MyApp());
    }

    class MyApp extends StatelessWidget{
        @override
        build(context){
            return MaterialApp(
            title: 'Mi aplicación de prueba',
                debugShowCheckedModeBanner: false,
                // cambiamos el home por initialRoute:
                initialRoute: '/',
                // y ahora establecemos las rutas en routes:
                routes: <String, WidgetBuilder>{
                '/': (BuildContext context) => HomePage(),
                'avisos': (BuildContext context) => AvisosPage()
                }
            );
        }
    }

Ahora veamos como sería la página **home_page.dart** con la navegación por rutas:

.. code:: dart 

    import 'package:flutter/material.dart';
    import 'package:flutterapp/src/providers/menu_provider.dart';
    import 'package:flutterapp/src/utils/icono_utils.dart';


    class HomePage extends StatelessWidget {

        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Menu Principal')
            ),//
            body: _menu()
            );
        }

        Widget _menu(){
            print(menuProvider.opciones);
            return FutureBuilder(
            future: menuProvider.cargarDatos(),
            initialData: [],
            builder: (BuildContext context, AsyncSnapshot<List<dynamic>> snapshot){
                return ListView(
                children: _opciones(snapshot.data, context),
                );
            }

            );
        }

        List<Widget> _opciones(List<dynamic> datos, context){
            final List<Widget> opciones = [];
            datos.forEach((opcion){
            final widgetTemp = ListTile(
                title: Text(opcion['texto']),
                leading: getIcon(opcion['icono']),
                trailing: Icon(Icons.keyboard_arrow_right, color: Colors.amberAccent),
                onTap: (){
                    // Utilizamos pushNmaed y le pasamos el contexto y nombre de la ruta asignada:
                    Navigator.pushNamed(context, 'avisos');
                }
            );

            opciones.add(widgetTemp);
            opciones.add(Divider());
            });

            return opciones;
        }
    }

Tarjeta o Card Widget
#####################
Las tarjetas en flutter se utilizan bastante para presentar conjunto de elementos y este widget se llama **card**

Los atributos mas comunes de **card**:

* child: se le adigna un widget hijo, puede ser una column o un row por ejemplo para añadir mas contenido.

Veamos un ejemplo de uso en un listado:

.. code:: dart

    import 'package:flutter/material.dart';
    import 'package:flutterapp/src/providers/menu_provider.dart';

    class HomePage extends StatelessWidget {

        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Menu Principal')
            ),//
            body: _menu()
            );
        }

        Widget _menu(){
            print(menuProvider.opciones);
            return FutureBuilder(
            future: menuProvider.cargarDatos(),
            initialData: [],
            builder: (BuildContext context, AsyncSnapshot<List<dynamic>> snapshot){
                return ListView(
                children: <Widget>[
                    // vamos a crear un widget nuevo donde almacenar la tarjeta
                    _tarjeta()
                ],
                );
            }

            );
        }

        // Y aquí vemos como ir organizando en una columna la tarjeta:
        Widget _tarjeta(){
            return Card(
            child: Column(
                children: <Widget>[
                ListTile(
                    leading: Icon(Icons.photo_album, color: Colors.red),
                    title: Text('Título de la tarjeta'),
                    subtitle: Text('Subtítulo de la tarjeta'),
                ),
                Row(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: <Widget>[
                    FlatButton(
                        child: Text('OK'),
                        onPressed: (){},
                    )
                    ]
                )
                ]
            )
            );
        }

    }

Imágenes
########
Podemos cargar imágenes en Flutter con el widget FadeInImage.

Atributos de FadeInImage:

* image: aquí colocaremos un widget de tipo networkImage o assetImage con una image desde internet o desde el dispositivo local.
* placeholder: es la imagen que se muestra mientras espera a que termine de cargar la imagen real porque esta anterior se encuentre en un servidor remoto.
* fadeInDuration: animacion programable en milisegundos para hacer un efecto fundido cuando se carge la imagen.
* height: alto de la imagen.
* width: ancho de la imagen.


Por convención creamos en la raiz de nuestro proyecto una carpeta llamada **assets** y editamos el archivo **pubspec.yaml** para añadir una nueva línea al apartado assets:

.. code:: dart

      assets:
        - ...
        - assets/

Ahora podemos cargar desde esa carpeta cualquier imagen en nuestro código:

.. code:: dart 

    import 'package:flutter/material.dart';
    import 'package:flutterapp/src/providers/menu_provider.dart';

    class HomePage extends StatelessWidget {

        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Menu Principal')
            ),//
            body: _menu()
            );
        }

        Widget _menu(){
            print(menuProvider.opciones);
            return FutureBuilder(
            future: menuProvider.cargarDatos(),
            initialData: [],
            builder: (BuildContext context, AsyncSnapshot<List<dynamic>> snapshot){
                return ListView(
                children: <Widget>[
                    _tarjeta()
                ],
                );
            }

            );
        }

        Widget _tarjeta(){
            return Card(
            child: Column(
                children: <Widget>[
                FadeInImage( // podemos cargar una imagen desde la red:
                    image: NetworkImage('https://i11c.3djuegos.com/juegos/12860/resident_evil_5__2016_/fotos/ficha/resident_evil_5__2016_-3314278.jpg'),
                    // o desde la carpeta assets:
                    placeholder: AssetImage('assets/re5.jpg'),
                    fadeInDuration: Duration(milliseconds: 3000),
                    height: 300.0,
                )
            ]
            )
            );
        }
    }

Alertas 
#######
Las alertas las realizamos con el widget **showDialog**.

Este widget posee los siguientes atributos:

* context: recibe el contexto de los widgets.
* barrierDimissible: permite o no cerrar la alerta tocando fuera de esta.
* builder: es donde creamos la estructura de la alerta.

Ejemplo de uso de una alerta:

.. code:: dart

    import 'package:flutter/material.dart';
    import 'package:flutterapp/src/providers/menu_provider.dart';

    class HomePage extends StatelessWidget {

        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Ejemplo de alerta')
            ),//
            body: Center(
                child: RaisedButton(
                child: Text('Lanzar alerta'),
                color: Colors.deepPurple,
                textColor: Colors.amber,
                shape: StadiumBorder(),
                onPressed: () => _alerta(context)
                )
            )
            );
        }

        // para crear una alerta creamos un nuevo método que no retorna nada:
        void _alerta(BuildContext context){
            // lanzamos el widget showDialog:
            showDialog(
            context: context,
            barrierDismissible: true,
            builder: (context){
                // En el builder le pasamos el widget AlertDialog:
                return AlertDialog(
                shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(20.0)), // el shape da forma a la ventana
                title: Text('Título del mensaje'),
                content: Column(
                    mainAxisSize: MainAxisSize.min,
                    children: <Widget>[
                    Text('Este es el contenido de la alerta'),
                    FlutterLogo(size: 80.0)
                    ]
                ),// el atributo actions recibe los botones que ejecutarán diferentes eventos:
                actions: <Widget>[
                    FlatButton(
                    child: Text('Cancelar'),
                    onPressed: ()=> Navigator.of(context).pop(),
                    ),
                    FlatButton(
                    child: Text('Aceptar'),
                    onPressed: ()=> Navigator.of(context).pop(),
                    )
                ]
                );
            }
            );
        }

    }


Avatar circular
###############
En Flutter se suele generar avatares circulares, esto se hace con la ayuda del widget **CircleAvatar**.

Atributos del widget:

* child: Recibe un widget como por ejemplo un texto.
* backgroundColor: personaliza el color del circulo.
* backgroundImage: recibe una imagen 
* radius: establece el tamaño de la esfera del avatar.

Ejemplo de uso:

.. code:: dart 

    import 'package:flutter/material.dart';
    
    class HomePage extends StatelessWidget {
        @override
        Widget build(BuildContext context) {
            return Scaffold(
            appBar: AppBar(
                title: Text('Ejemplo de avatar'),
                actions: <Widget>[
                Container(
                    padding: EdgeInsets.all(5.0),
                    child: CircleAvatar(
                    backgroundImage: AssetImage('assets/re5.jpg'),
                    radius: 25.0,
                    )
                )
                ]
            ),//
            body: Center(
                child: CircleAvatar(
                child: Text('ICONO'),
                backgroundColor: Colors.deepPurple,
                radius: 55.0
                )
            )
            );
        }

    }


**PENDIENTE DE CONTINUAR**