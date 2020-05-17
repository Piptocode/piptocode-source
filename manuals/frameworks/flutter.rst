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

Separar la lógica en varios archivos
************************************
Para tener una buena lectura del código es necesario seguir una estructura de directorios y archivos donde podamos separar las distintas páginas y componentes que se agrupan en Flutter:

PROXIMAMENTE...