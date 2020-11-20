===
C++
===
  
.. image:: /logos/logo-cpp.png
    :scale: 25%
    :alt: Logo JS
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

He recopilado la siguiente información para tener un acercamiento a C++ con el propósito de aprender mas sobre el lenguaje que por defecto utilizan las placas Arduino.
 
.. contents:: Índice

Elementos básicos del lenguaje
##############################

Comentarios
***********
Los comentarios se pueden realizar de dos tipos:

* Comentarios de una sola línea:

.. code:: cpp

    // Comentario de una sola linea

* Comentarios multilínea:

.. code:: cpp

    /*
    Esto es un comentario multilínea
    Aquí podemos establecer mas de 
    una linea
    */

Estructura en C++
*****************
La estructura de C++ se presenta casi idéntica a C:

.. code:: cpp

    #include "iostream"

    using namespace std;

    int main(){
        cout << "Hola mundo";
        
        return 0;
    }
    

Extensión
*********
La extensión utilizada por los archivos Python es ``cpp``

Compilación y Ejecución
***********************
Para compilar un script en C++ debemos instalar un compilador, yo personalmente utilizo en linux GCC y el comando para instalarlo es: ``sudo apt install build-essential``

Lo siguiente será compilar la aplicación ejecutando: ``g++ -o hola hola-mundo.cpp``

Y ya podemos ejecutarlo del siguiente modo: ``./hola`` 

Preparación del script 
**********************
Cuando creamos un nuevo script de C++ tenemos que importar la biblioteca principal del lenguaje:

Ejemplo:

.. code:: c++

    // incluimos la librería principal:
    #include "iostream"
    // cargamos el namespace std para no tener que estar poniendolo durante todo el código:
    using namespace std;

Palabras reservadas de C++
**************************
En C++ existen las siguientes palabras reservadas:

* auto 
* const 
* double
* float
* int
* short
* struct
* unsigned
* break
* continue
* else
* for
* long 
* signed
* switch
* void
* clase
* default
* enum 
* goto
* register
* sizeof
* typedef
* volatile
* char
* do
* extern
* if
* return
* static
* union
* while


Variables y tipos de datos
##########################

Variables
*********
Las variables se definene de forma estricta, lo que significa que definimos el tipo de dato que va a tener esta durante su declaración.

Ejemplo:

.. code:: cpp

    int edad = 25;

Constantes
**********
Las constantes se definen de dos formas tal y como se hace en C.

* En la cabecera con ``#define``:

.. code:: cpp 

    #include <iostream>
    using namespace std;

    // definir constante:
    #define PI 3.1416;

    int main(){
        // imprimir la constante:
        cout << "El valor de PI es: " << PI;

        return 0;
    }

* En las funciones con ``const``:

.. code:: cpp 

    #include <iostream>
    using namespace std;


    int main(){
        // declaramos la constante con const:
        const float PI = 3.1416;

        cout << "Mostrando el valor de PI: " << PI << endl;

        return 0;
    }

..important
    Se recomienda el uso de ``const`` ya que del otro modo es mas difícil trabajar con la salida estandar.

Tipos de datos primitivos
*************************
Los tipos de datos mas comunes son los siguientes:

+--------------+-----------------------------------------------+-----------------------------+
| Tipo de dato | Denominación                                  | Ejemplo                     |
+==============+===============================================+=============================+
| void         | Vacío, nada, no retorno                       |                             |
+--------------+-----------------------------------------------+-----------------------------+
| int          | Número Entero                                 | 20, 5, -3, 0                |
+--------------+-----------------------------------------------+-----------------------------+
| float        | Número con decimales                          | 20.53, 12.5, -18.353        |
+--------------+-----------------------------------------------+-----------------------------+
| double       | Número con decimales mas preciso              | 20.53, 12.5234, -18.35332   |
+--------------+-----------------------------------------------+-----------------------------+
| bool         | Verdadero o falso                             | True, False                 |
+--------------+-----------------------------------------------+-----------------------------+
| char         | caracter o conjunto de caracteres             | "a", "x", "patata"          |
+--------------+-----------------------------------------------+-----------------------------+


Ejemplos:

.. code:: cpp 

    #include <iostream>
    using namespace std;

    int main(){
        // tipo char:
        char x = 'a';

        // tipo entero:
        int entero = 10;

        // tipo flotante:
        float decimal = 3.5;

        // operaciones:
        float resultado = entero + decimal;

        // booleano:
        bool valor = false;

        // impresión de resultado:
        cout << resultado << endl;

        return 0;
    }

Entrada y Salida de datos
#########################
La entrada y salida de datos en C++ es algo peculiar, pese a que se puede utilizar ``printf()`` y ``scanf()`` es mas recomendable utilizar ``cout`` y ``cin``

* Entrada de datos:

.. code:: cpp
    
    cout << "introduce un número: << endl; 
    cin >> numero;

* Salida de datos: 

.. code:: cpp

    // salida estandar:
    cout << "Hola amigo" << " así se puede " << " unir cadenas " endl; // endl salto de página o \n.

    // uso de variables:
    cout << "Tu número es " << numero << endl;
     

Operadores
##########

Operadores Aritméticos
**********************
Los operadores aritméticos que se presentan en C++ son los siguientes,
``+, -, *, /, %``

Estos podemos utilizarlos del siguiente modo:

.. code:: c++

    // asignación:
    int suma = 2 + 2;

    // salida de datos:
    cout << 3 - 2 << endl;


Operadores Relacionales
***********************
Los operadores relacionales en C++ son muy comunes en la mayoría de lenguajes de programación:

+-----------------+---------+
| Operador        | símbolo |
+=================+=========+
| Mayor que       | >       |
+-----------------+---------+
| Menor que       | <       | 
+-----------------+---------+
| Igual que       | ==      |
+-----------------+---------+
| Distinto que    | !=      |
+-----------------+---------+
| Mayor igual que | >=      |
+-----------------+---------+
| Menor igual que | <=      |
+-----------------+---------+

Cuando hablamos del uso de un solo ``=`` nos referimos a la asignación de un valor en una variable.

Como en muchos lenguajes, si imprimimos por consola la relación entre un valor y otro el resultado será 0 o 1 (false o true):

.. code:: c++

    // Si decimos que 3 es mayor que 2 
    cout << 3 > 2 << endl;
    // el resultado que sale por consola es 1 (o sea positivo o true).

Operadores de Incremento
************************
Este tipo de operador suma o resta 1 a la cantidad asignada, se utiliza sobre todo en bucles:

* Incremento positivo: ``a++`` , ``++a``
* Incremento negativo: ``a--`` , ``--a``

Operadores de Incremento al asignar
***********************************
Los operadores de incremento realizan una operación aritmética al asignar un número nuevamente:

+-----------------+---------+
| Operador        | símbolo |
+=================+=========+
| Sumar           | ``+=``  |
+-----------------+---------+
| Restar          | ``-=``  | 
+-----------------+---------+
| Multiplicar     | ``*=``  |
+-----------------+---------+
| Dividir         | ``/=``  |
+-----------------+---------+
| Sacar resto     | ``%=``  |
+-----------------+---------+
| Menor igual que | ``<=``  |
+-----------------+---------+

Ejemplo de uso:

.. code:: c++

    #include "iostream"

    using namespace std;

    int main() {
        int numero = 10;
        
        numero += 15;
        cout << numero << endl;

        return 0;
    }


Operadores Lógicos
******************
En C++ existen los operadores lógicos AND y OR:

+-----------+-----------+------------------------------------------------------------+
| Operador  | símbolo   | condición                                                  |
+===========+===========+============================================================+
| && (and)  | &&        | La condición se cumple si todos son verdaderos             |
+-----------+-----------+------------------------------------------------------------+
| || (or)   | ||        | La condición se cumple si al menos uno es verdadero        |
+-----------+-----------+------------------------------------------------------------+
| ! (not)   | !=        | La condición se cumple si el valor comparado es distinto   |
+-----------+-----------+------------------------------------------------------------+

Ejemplos:

.. code:: c++

    #include "iostream"

    using namespace std;

    int main(){
        int edad = 67;

        // pregunta con AND:
        if(edad > 18 && edad >= 65){
                cout << "con " << edad << " años eres un anciano" << endl;
        }

        //pregunta con OR:
        if(edad > 18 || edad >= 65){
                cout << "con " << edad << " años eres mayor de edad" << endl;
        }

        // pregunta con NOT:
        if(edad != 100){
            cout << " con " << edad << " no tienes un centenar de años " << endl;
        }

        return 0;
    }


Estructuras de control
######################
En python disponemos de estructuras de control como ``if``, ``for`` y ``while``.

Condicional if
**************
Las condiciones sencillas en C++ funcionan del siguiente modo:

.. code:: cpp

    #include <iostream>
    #include <string>

    using namespace std;


    int main(){
        int resultado = 0;

        cout << "Cuanto es 39+50?" << endl;
        cin >> resultado;

        if(resultado == 39+50){
            cout << "Respuesta Correcta!" << endl;
        }

        return 0;
    }

También tenemos condiciones con una salida alternativa si no se cumple esta:

.. code:: cpp

    #include <iostream>
    #include <string>

    using namespace std;


    int main(){
        int resultado = 0;

        cout << "Cuanto es 39+50?" << endl;
        cin >> resultado;

        if(resultado == 39+50){
            cout << "Respuesta Correcta!" << endl;
        }else{
            cout << "Respuesta incorrecta, el resultado es: " << 39+50 << endl;
        }

        return 0;
    }
    

Condicional else-if
*******************
Las condiciones compuestas nos ofrecen varios caminos posibles:

.. code:: python

    #include <iostream>

    using namespace std;


    int main(){
        int edad = 0;

        cout << "¿Qué edad tienes?" << endl;
        cin >> edad;

        if(edad >= 18){
            cout << "Eres mayor de edad!" << endl;
        }else if(edad >=16 && edad < 18){
            cout << "Eres un adolescente " << endl;
        }else{
            cout << "Eres menor de edad" << endl;
        }

        return 0;
    }

Condicional switch
******************
Con Switch podemos tomar varios camino en el código:

.. code:: cpp

    #include <iostream>

    using namespace std;


    int main(){
        cout << "Elije una opción: ";
        int opcion;
        cin >> opcion;

        switch(opcion){
            case 1: 
                cout << "Has seleccionado la primera opción" << endl;
                break;
            case 2:
                cout << "Has seleccionado la segunda opción" << endl;
                break;
            case 3:
                cout << "Has seleccionado la tercera opción" << endl;
                break;
            default:
                cout << "Opción incorrecta" << endl;
        }

        return 0;
    }

Bucle for
*********
El bucle for en Cpp se presenta de un modo muy similar a C:

* Uso con rango definido:

.. code:: cpp

    #include <iostream>

    using namespace std;


    int main(){
        
        for(int i=10; i > 0; i--){
            cout << "Cuenta atras... "<< i << endl;
        }

        return 0;
    }

Bucle foreach
*************
El bucle foreach esta diseñado especialmente para recorrer arrays y colecciones de datos.

Ejemplo de uso:

.. code:: cpp

    #include <iostream> 
    using namespace std; 
    
    int main() 
    { 
        int numeros[] = { 8, 154, 32, 25 }; 
    
        for (int num : numeros){
            cout << num << endl; 
        } 
            
    } 

Bucle while
***********
El bucle While es similar a otros lenguajes:

Ejemplo:

.. code:: cpp

    #include <iostream>

    using namespace std;


    int main(){
        
        int numero;
        cout << "Introduce un número" << endl;
        cin >> numero;
        while(numero <= 100){
            cout << "Introduce un número" << endl;
            cin >> numero;
        }

        return 0;
    }

Ejemplo con bucle infinito:

.. code:: cpp

    #include <iostream>

    using namespace std;


    int main(){
        
        int numero;
        numero = 0;
        while(1){
            numero++;
            cout << numero << endl;
        }

        return 0;
    }

Bucle do-while 
**************
Cuando trabajamos con do while tenemos que saber que el algoritmo se ejecutará al menos una vez aunque no se cumpla la condición:

.. code:: cpp 

    #include <iostream>

    using namespace std;


    int main(){
        
        int numero;
        cout << "Introduce un número" << endl;
        cin >> numero;
        do{
            cout << "Introduce un número" << endl;
            cin >> numero;
        }while(numero <= 100);

        return 0;
    }

Romper un bucle
***************
Para romper un bucle while o for se utiliza la palabra reservada ``break``:

.. code:: cpp

    #include <iostream>

    using namespace std;


    int main(){
        
        int numero;
        numero = 0;
        while(1){
            numero++;
            cout << numero << endl;

            if(numero == 100){
                break;
            }
        }

        return 0;
    }

Estructuras de datos
####################

Arrays o Vectores
*****************
Los arrays o vectores son una colección de datos estrictamente definida en el caso de C++

* Ejemplo de uso e impresión de array:

.. code:: cpp

    #include <iostream>

    using namespace std;


    int main(){
        // declaración y asignación de elementos al array:
        int edades[] = {1,2,9,10,16,32,33,22,15};
        
        // estableciendo el tamaño de la cadena, algo similar a la función length en otros lenguajes: 
        int limite = (sizeof(edades)/sizeof(edades[0]));

        // Recorrido e impresión del array:
        for(int i = 0; i < limite; i++){
            cout << edades[i] << endl;
        }

        // cambiando el valor de un elemento de la cadena:
        edades[2] = 27;
        // impresión de un valor específico del array:
        cout << edades[2] << endl;

        return 0;
    }

Matrices
********
Las matrices son básicamente arrays multidimensionales a los que les asignamos una cantidad de casillas y este se puede representar como una tabla a la hora de guardar y acceder a la información:

* Ejemplo de Matriz y recorrido e impresión como si fuese una tabla con un for anidado:

.. code:: cpp 

    # include "iostream"

    using namespace std;

    int main(){
        // creamos una matriz de 4x4
        int matriz[4][4] = {
            {1,2,3,4},
            {4,5,6,7},
            {8,9,10,11},
            {12,13,14,15}
        }; // el primer array representa las filas y el segundo las columnas

        // impresión del número 11:
        cout << matriz[2][3] << endl; 

        // recorrer matriz con un bucle anidado:
        for(int fila = 0; fila <= 3; fila++){
            cout << "==============" << endl;
            cout << "|";
            for(int columna = 0; columna <= 3; columna++){
                cout << matriz[fila][columna] << "|";
            }
            cout << endl;
        }
    }

Funciones
#########
Las funciones en C++ son practicamente iguales a C:

.. code:: cpp 

    #include <iostream>
    #include <string>

    using namespace std;

    int funcion(int num1, int num2){
        return num1 + num2;
    }

    int main(){
        cout << "el total es: " << funcion(10, 15) << endl;

        return 0;
    }

Punteros
########
Vamos a ver un sencillo ejemplo del uso de punteros en C++:

.. code:: cpp 

    #include <iostream>

    using namespace std;

    int funcion(int valor){
        valor = valor + 10;
        return valor;
    }

    int funcionPunteros(int* valor){
        *valor = *valor + 10;
        return *valor;
    }

    int main(){
        int numero = 10;

        cout << "Antes de función " << numero << endl;
        funcion(numero);
        cout << "Después de funcion " << numero << endl;

        cout << "Antes de funcionPunteros " << numero << endl;
        funcionPunteros(&numero);
        cout << "Después de funcionPunteros " << numero << endl;
        
        return 0;
    }

Clases
######
El gran avance de C++ frente a C tradicional es la inclusión del paradigma orientado a objetos.

* Creación de clases con atributos, metodo y creación del objeto:

.. code:: cpp

    #include <iostream>
    using namespace std;

    // creamos la clase:
    class MiClase {
        public: // definimos el tipo de encapsulación si es publica o privada
            // definimos los atributos
            int numero; 
            string cadena; 
            // y esto es un método de ejemplo:
            void miMetodo(){
                cout << "Metodo de prueba" << endl;
            }
            // metodo que recibe parámetros:
            void conParametros(int edad){
                cout << "Tienes " << edad << " años." << endl;
            }
    }; // las clases se cierran con ;

    int main(){
        // creamos un objeto a partir de la clase anterior:
        MiClase miObjeto;

        // podemos acceder directamente a sus atributos
        miObjeto.numero = 20;
        miObjeto.cadena = "Texto de prueba";

        // imprimimos los valores:
        cout << miObjeto.numero << endl;
        cout << miObjeto.cadena << endl;
        // llamar a un método:
        miObjeto.miMetodo();
        // llamar a un metodo y enviar un parámetro:
        miObjeto.conParametros(33);

        return 0;
    }

* Clases con constructor:

.. code:: cpp

    #include <iostream>
    using namespace std;

    class MiClase {
        public:
            string nombre;
            int edad;
            
            // el constructor lleva el nombre de la clase y puede recibir parametros:
            MiClase(string n, int e){
                nombre = n;
                edad = e;

                cout << "Objeto creado con éxito" << endl;
            }

            void presentacion(){
                cout << "Te llamas " << nombre << " y tienes " << edad << " años." << endl;
            }
    };

    int main(){
        MiClase miObjeto("Felipe", 37);

        miObjeto.presentacion();
        return 0;
    }

Tipos de encapsulación en C++
*****************************
Existen tres tipos de encapsulación en C++:

* public: los atributos y métodos son publicos y por tanto se puede acceder a ellos una vez creado el objeto.
* private: los atributos y metodos no pueden ser llamados o modificados desde el objeto.
* protected: los atributos y metodos solo pueden ser llamados o modificados desde otras clases anidadas.

Get y Set 
*********
Para manejar atributos y metodos privados utilizaremos los get y set, estos metodos son una convención en programación:

.. code:: cpp

    #include <iostream>
    using namespace std;

    class MiClase {
        // cada atributo o metodo lo manejaremos en su propia capa de encapsulación.
        private:
            int numA;
        public:
            // Con los setter modificamos el atributo:
            void setNumero(int n){
                numA = n;
            }

            // y con los getter recuperamos el atributo, debemos poner el tipo de devolución como en las funciones:
            int getNumero(){
                return numA;
            }
    };

    int main(){
        MiClase numeros;

        numeros.setNumero(27);
        cout << "El numero establecido es: " << numeros.getNumero() << endl;
    }

Herencia
********
La herencia en C++ se realizaría del siguiente modo:

.. code:: cpp 

    #include <iostream>
    using namespace std;

    // clase padre:
    class Mueble {
        public:
            string mueble = "Mesa";
            void accion(){
                cout << "PONER LA MESA" << endl;
                cout << "=============" << endl;
            }
    };

    // clase hijo que hereda del padre:
    class MesaComedor: public Mueble {
        public:
            string tipo = "Mesa del comedor";
    };

    int main(){
        MesaComedor mesa;

        mesa.accion();
        cout << "Hay que poner la " << mesa.mueble << endl;
        cout << "¿Qué mesa?" << endl;
        cout << "La " << mesa.tipo << endl;
    }

En la herencia de clases existe otro concepto llamado polimorfismo y se basa en reutilizar los metodos de las clases padre para modificarlos en las clases hijo de forma que
podemos reutilizarlos sin necesidad de crear unos nuevos.

Manejo de errores
#################
El manejo de errores en C++ se realiza con **try** y **catch**:

.. code:: cpp 

    #include <iostream>
    using namespace std;

    int main(){
        int numeroA;
        int numeroB = 20;
        int total;

        cout << "introduce un número:" << endl;
        cin >> numeroA;
        total = numeroA + numeroB;

        // con try probaremos a ejecutar una operación:
        try{
            // si el valor es mayor a 20 siginfica que el numeroA no es una letra o un valor igual menor que 0:
            if(total > 20){
                cout << "El resultado de la suma es: " << total << endl; 
            }else{
                // sino provocaremos un error:
                throw(numeroA);
            }
        } // catch caputará el error provocado:
        catch(int numero){
            cout << "El valor introducido no es correcto: " << numero << endl;
        }
    }


Librerías de C++
################
Estas son las librerías estándares mas comunes de C++:

* fstream: permite la manipulación de archivos desde el programa, tanto leer como escribir en ellos.
* oisfwd: contiene declaracioens adelantadas de todas las plantillas de flujos.
* iostream: Parte del STL que contiene los algoritmos estándar. Es la más usada.
* list: Parte de la STL relativa a contenedores tipo list.
* math: Contiene los prototipos de las funciones y otras definiciones.
* memory: utilidades relativas a la gestión de memoria
* new: manejo de memoria dinámica
* numeric: parte de la libería numérica de la STL
* ostream: Algoritmos estandar para los flujos de salida.
* queue: contenedores tipo queue (colas de objetos).
* stdio: contiene los prototipos de las funciones, macros y tipos para manipular datos de entrada y salida.
* stdlib: lo mismo para uso general
* string: para trabajar cadenas de texto.
* typeinfo: mecanismo de identificación de tipos en tiempo de ejecución
* vector: para trabajar las matrices unidimensionales.
* forward_list: sirve para implementar listas enlazadas simples.
* iterator: porporciona un conjunto de clases para interar elementos.
* regex: proporciona fácil acceso al uso de expresiones regulares
* thread: util para trabajar programas multihilos y crear varios hilos en nuestra aplicación.

Módulos y paquetes
##################
He estado buscando información en la red y no he dado con mucho así que he comprobado que se puede crear paquetes del mismo modo que C.

* Archivo ``modulo.cpp`` con la función del paquete:

.. code:: cpp 

    int sumar(int num1, int num2){
        return num1 + num2;
    }

* Archivo de intercambio ``intercambio.h``:

.. code:: cpp 

    extern int sumar(int a, int b);

* Archivo ``main.cpp`` con el código principal:

.. code:: cpp 

    #include "iostream"
    #include "intercambio.h"

    using namespace std;

    int main(){
        cout << sumar(20,15) << endl;
    }

Uso del preprocesador
*********************
Este ejemplo de preprocesado sin utilizar el archivo .h es identico al de C.

* Archivo ``modulo.cpp`` con la función del paquete:

.. code:: cpp 

    int sumar(int num1, int num2){
        return num1 + num2;
    }

* Archivo ``main.cpp`` con el código principal:

.. code:: cpp 

    #include "iostream"
    extern int sumar(int a, int b);

    using namespace std;

    int main(){
        cout << sumar(20,15) << endl;
    }
