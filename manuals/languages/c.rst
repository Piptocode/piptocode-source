=
C
=
  
.. image:: /logos/logo-c.png
    :scale: 75%
    :alt: Logo JS
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con C, un lenguaje clásico que veo oportuno aprender primero antes que cualquier otro lenguaje que utilices pra trabajo o para proyectos personales. 
 
.. contents:: Índice

Elementos básicos del lenguaje
##############################
 
Comentarios
***********
Los comentarios se pueden realizar de dos tipos:

* Comentarios de una sola línea:

.. code:: c

    // comentario de una linea


* Comentarios multilínea:

.. code:: c

    /* 
    Comentario multilínea
    donde puedes escribir
    en mas de una línea obviamente
    */

Estructura en C
***************
La estructura de C ha inspirado a la mayoría de lenguajes de programación que le precedieron:

.. code:: c

    // en la primera línea importamos la librería estandar de C:
    #include <stdio.h>
    // creamos la función principal main que no retorna nada (void):
    void main (void){
            printf("Hola mundo!\n"); // con \n hacemos un salto de línea
    }
    

Extensión
*********
La extensión utilizada por los archivos C es ``c``
Una vez se compila su extensión pasa a ser ``h``

Compilación y Ejecución
***********************
Para poder compilar un programa escrito en C debemos instalar un compilador, yo personalmente utilizo en linux GCC y el comando para instalarlo es: ``sudo apt install build-essential``

El comando para compilar un programa en C con GCC es ``gcc -o nombre script.c``

La compilación nos devolverá un programa llamado ``hola`` que ejecutamos en Linux como ``./hola``

Preparación del script
**********************
Cuando programamos en C la primera línea que escribimos siempre es la importación de la librería principal:

.. code:: c 

    #include <stdio.h>

Palabras reservadas de C
************************
En C existen las siguientes palabras reservadas:

* auto 
* break
* case 
* char 
* const 
* continue 
* default 
* do 
* double
* else 
* enum 
* extern 
* float 
* for 
* goto
* if
* int 
* long 
* register
* return 
* short
* signed
* sizeof
* static
* struct
* typedef
* union
* unsigned
* void
* volatile
* while


Variables y tipos de datos
##########################

Variables
*********
En C por convención se declara la variable y cuando se requiere necesario la asignación en la misma línea.

Ejemplo:

.. code:: c

    int edad = 22;

Constantes
**********
Las constantes en C se pueden declarar de dos formas, al comienzo del código con la palabra reservada ``#define`` o en la función main con la palabra ``const``

* Ejemplo de declaración con #define:

.. code:: c 

    // justo despues de las importaciones asignamos con #define:
    #define PI 3.1415

* Ejemplo de declaración con #define:

.. code:: c 

    // Dentro de la función main:
    const PI = 3.1415;

En el caso de C, se suele utilizar mas amenudo ``#define``

Tipos de datos primitivos
*************************
Los tipos de datos mas comunes son los siguientes:

+--------------+-----------------------------------------------+-----------------------------+
| Tipo de dato | Denominación                                  | Ejemplo                     |
+==============+===============================================+=============================+
| int          | Número Entero                                 | 20, 5, -3, 0                |
+--------------+-----------------------------------------------+-----------------------------+
| float        | Número con decimales                          | 20.53, 12.5, -18.353        |
+--------------+-----------------------------------------------+-----------------------------+
| double       | Número con decimales preciso                  | 11.3938, 35.23903, 23.33292 |
+--------------+-----------------------------------------------+-----------------------------+
| char         | Almacena uno o varios caracteres              | "a", "z", "17", "hola"      |
+--------------+-----------------------------------------------+-----------------------------+

Ejemplos:

.. code:: c 

    int numero = 27;
    float decimal = 11.38;
    double preciso = 3.1415161820;
    char letra[1] = "a"; // importante definir la cantidad de caracteres que pueden haber en la variable.

Especificadores de Formato
**************************
En C existen los especificadores de formato cuya finalidad se da en la entrada o salida de datos para especificar donde va a ir un dato:

+--------------+-----------------------------------------------+
| Tipo de dato | Denominación                                  |
+==============+===============================================+
| %d           | Número Entero (int)                           |
+--------------+-----------------------------------------------+
| %f           | Número con decimales (float, decimal)         |
+--------------+-----------------------------------------------+
| %c           | Caracter o caracteres (char)                  |
+--------------+-----------------------------------------------+
| %s           | Cadenas de texto (string)                     |
+--------------+-----------------------------------------------+

Entrada y Salida de datos
#########################
C utiliza para entrada de datos la función ``scanf()`` y para la impresión de estos por consola ``printf()``

* Entrada de datos:

.. code:: c

    // acompañamos con un printf esta sentencia que solo lleva el tipo de dato y el enlace a la variable:
    scanf("%d", &edad);

* Salida de datos: 

.. code:: c

    printf("cadena de salida");

* veamos un ejemplo donde escribimos nuestra edad:

.. code:: c

    #include <stdio.h>

    void main(void) {
        int edad;
        printf("Escribe aquí tu edad:\n");
        scanf("%d", &edad);
        printf("Tu edad es de %d años\n", edad);
    }
    

Enumeradores y estructuras de datos
###################################

Enumeradores
************
Los enumeradores nos sirven para generar un tipo de dato utilizando ``typedef`` y ``enum``, por ejemplo en el ejemplo generamos y usamos un tipo Booleano.

Ejemplo:

.. code:: c 

    #include <stdio.h>
    // creamos el enum y lo llamamos BOOLEAN:
    typedef enum{
        false,
        true,
    } BOOLEAN;

    void main(void){
        // creamos una variable de tipo BOOLEAN
        BOOLEAN b_var;
        // esta variable solo aceptará los valores true o false
        b_var = false;
        if(b_var == true){
            printf("Verdadero\n");
        }else{
            printf("Falso\n");
        }
    }

Estructura de datos
*******************
La estructura de datos se genera también con ``typedef`` junto a ``struct``

.. code:: c

    #include <stdio.h>

    typedef struct{
        int inval1;
        int inval2;
        int outval;
    } MY_DATA;

    void add(MY_DATA *d){
        d->outval = d->inval1 + d->inval2;
    }

    void main(void){
        MY_DATA data;

        data.inval1 = 5;
        data.inval2 = 7;
        add(&data);

        printf("La suma de %d y %d es %d\n", data.inval1, data.inval2, data.outval);
    }

Operadores
##########

Operadores Aritméticos
**********************
Los operadores aritméticos que se presentan en C son los siguientes,
``+, -, *, /, %``

Estos podemos utilizarlos del siguiente modo:

.. code:: c

    // asignación:
    int suma = 2 + 2;

    // salida de datos:
    printf("%d\n", 3-2);


Operadores Relacionales
***********************
Los operadores relacionales en C son muy comunes en la mayoría de lenguajes de programación:

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

.. code:: c

    // comparamos un valor en una variable tipo booleana:
    bool num = 3 < 2;
    // imprimimos el resultado que será 0 o 1:
    cout << num << endl;

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

.. code:: c

    #include <stdio.h>

    void main(void) {
        int numero = 10;
        
        numero += 15;
        printf("%i\n", numero);
    }


Operadores Lógicos
******************
En C existen los operadores lógicos AND y OR:

+-----------+-----------+------------------------------------------------------------+
| Operador  | símbolo   | condición                                                  |
+===========+===========+============================================================+
| && (and)  | &&        | La condición se cumple si todos son verdaderos             |
+-----------+-----------+------------------------------------------------------------+
| || (or)   | ||        | La condición se cumple si al menos uno es verdadero        |
+-----------+-----------+------------------------------------------------------------+

Ejemplos:

.. code:: c

    #include <stdio.h>

    void main(void){
            int edad = 67;

            // pregunta con AND:
            if(edad > 18 && edad >= 65){
                    printf("con %d años eres un anciano\n", edad);
            }

            //pregunta con OR:
            if(edad > 18 || edad >= 65){
                    printf("con %d años eres mayor de edad\n", edad);
            }
    }


Estructuras de control
######################
Las estructuras de control en C son el modelo a seguir por sus predecesores.

Condicional if
**************
En C las condiciones if han servido de ejemplo para los futuros lenguajes.

.. code:: c

    #include <stdio.h>

    void main(void){
        int a = 0;
        if(a == 0){

                printf("a es igual a 0\n");
        }
    }


Disponemos de una salida alternativa si no se cumple la condición con ``else``:

.. code:: c

    #include <stdio.h>

    void main(void){
        int a = 0;
        if(a == 0){

                printf("a es igual a 0\n");
        }else{
                printf("a es distinto a 0\n");
        }
    }


Condicional else-if
*******************
Las condiciones compuestas nos ofrecen varios caminos posibles:

.. code:: c

    #include <stdio.h>

    void main(void){
        int a = 0;

        if(a == 0){
            printf("a es igual a 0\n");
        }else if(a == 1){
            printf("a es igual a 1\n");
        }else{
            printf("a es un numero desconocido\n");
        }
    }

Condicional Switch
******************
El condicional Switch nos ofrece varios caminos como ``if-else`` pero de forma mas visual:

.. code:: c

    #include <stdio.h>

    void main(void){
        int a = 0;

        switch(a){
            case 0: 
                printf("a es igual a 0\n");
                break;
            case 1:
                printf("a es igual a 1\n");
                break;
            default:
                printf("a es desconocido\n");
        }
    }

Bucle for
*********
El bucle for en C se presenta muy similar a sus predecesores:

.. code:: c

    #include <stdio.h>

    void main(void){
        int a;

        for(a = 0; a < 5; a++){
            printf("a es igual a %d\n", a);
        }
        printf("a es igual a %d y hemos acabado\n", a);
    }

Bucle while
***********
Con while podemos ejecutar un bucle que termina al cumplir la condición o hacerlo infinito.

Ejemplo:

.. code:: c

    #include <stdio.h>

    void main(void){
        int a = 0;

        while(a < 5){
            printf("a es igual a %d\n", a);
            a++;
        }
        printf("a es igual a %d y hemos terminado\n", a);
    }

Bucle Do-while
**************
Con do while creamos un bucle que siempre va a ejecutar al menos una sola vez aunque no se llegue a cumplir la condición:

.. code:: c 

    #include <stdio.h>

    void main(void){
        int a = 0;

        do{
            printf("a es igual a %d\n", a);
            a++;
        }while(a == 0);
        printf("a es igual a %d y hemos terminado\n", a);
    }

Romper un bucle
***************
Podemos romper el funcionamiento de un bucle for o while con la palabra reservada ``break``:

.. code:: c 

    #include <stdio.h>

    void main(void){
        int a = 0;

        while(1){
            printf("a es igual a %d\n", a);
            a++;
            if(a == 5){
                break;
            }
        }
        printf("a es igual a %d y hemos acabado/n", a);
    }

Estructuras de datos
####################

Arrays
******
Existen varios tipos de arrays, y son un poco raros de manejar en C.

Ejemplo de uso con enteros:

.. code :: c

    #include <stdio.h>

    void main(void){
        int a[10];
        int count;

        for(count = 0; count <10; count++){
            a[count] = count;
            printf("Repetición número %d\n", a[count]);
        }
    }

Strings
*******
En C para hacer trabajar con Strings tenemos que utilizar la librería ``<string.h>``

* Unir dos strings: 

.. code :: c

    #include <stdio.h>
    #include <string.h>

    void main(void){
        // creamos tres cadenas de caracters y rellenamos las dos primeras:
        char str1[10] = "Primera";
        char str2[10] = "Segunda";
        char str3[20];
        // añadimos a la tercera la primera cadena:
        strcpy(str3, str1);
        // concatenamos un espacio en blanco:
        strcat(str3, " ");
        // y concatenamos la segunda cadena con la tercera.
        strcat(str3, str2);

        printf("%s + %s = %s\n", str1, str2, str3);
    }

* comparar dos strings:

.. code:: c

    #include <stdio.h>
    #include <string.h>

    void main(void){
        char str1[10] = "hola";
        char str2[10] = "saludo";
        if(strcmp(str1, str2) == 0){ // si da 0 son iguales y si es != distinto no.
            printf("Las dos cadenas son idénticas.\n");
        }else{
            printf("Son cadenas diferentes.\n");
        }
    }

* entrada de datos tipo string:

.. code:: c

    #include <stdio.h>

    void main(void){
        int val;
        char string[10] = "250";

        sscanf(string, "%d", &val);
        printf("El valor en el string es %d\n", val);
    }

* medir la longitud de un string:

.. code:: c 

    #include <stdio.h>
    #include <string.h>

    void main(void){
        char str1[10] = "Primero";

        printf("La longitud de la cadena %s es %ld\n", str1, strlen(str1));
    }

Funciones
#########
Las funciones en C son la referencia para muchos lenguajes que le han precedido:

.. code:: c 

    #include <stdio.h>

    int sum(int a, int b){
        int res;
        res = a + b;
        return res;
    }

    void main(void){
        int y = 2;
        int z = sum(5, y);

        printf("La suma de 5 y %d es %d\n", y, z);
    }

Punteros
########
Un puntero es una dirección de memoria que apunta a una variable y su propósito es el ahorro de memoria. Se usa comunmente en llamadas a funciones, manejo de strings y arrays.

Ejemplo de uso:

.. code:: c 

    #include <stdio.h>

    void main(void){
        int a;
        // declarar un puntero:
        int *ptr_a;
        // asignar variable a un puntero:
        ptr_a = &a;

        a = 5;
        printf("El valor de a es %d\n", a);
        // modificar un puntero:
        *ptr_a = 6;
        
        printf("El valor de a es %d\n", a);

    }

* Punteros en arrays:

.. code:: c 

    #include <stdio.h>

    void main(void){
        int a[10];
        int count;

        for(count = 0; count <10; count++){
            a[count] = count * 10 + count;
        }

        printf("El primer y segundo elemento son %d y %d\n", a[0], a[1]);
        printf("Y con sus punteros son, %d y %d\n", *a, *(a+1));
    }

* Punteros en strings:

.. code:: c 

    #include <stdio.h>

    void main(void){
        char str1[10] = "primero";
        char str2[10] = "segundo";
        char str3[20];

        char *src, *dst;

        src= str1;
        dst = str3;
        while(*src != 0){
            *dst = *src;
            src++;
            dst++;
        }
        src = str2;

        while(*src != 0){
            *dst = *src;
            src++;
            dst++;
        }
        *dst = 0;

        printf("%s + %s = %s\n", str1, str2, str3);
    }

* Punteros en funciones:

.. code:: c

    #include <stdio.h>
                                // declarando un parametro puntero:
    int operacion(int a, int b, int *res){
        int sum;
        sum = a + b;
        *res = a - b; // utilizando el puntero para almacenar el resultado de la operacion
        return sum;
    }

    void main(void){
        int b = 2;
        int diff;

        printf("La suma de 5 y %d es %d\n", b, operacion(5, b, &diff));
        printf("La diferencia de 5 y %d es %d\n", b, diff);
    }

Manejo de Archivos
##################
En C existe la posibilidad de manejar archivos de modo que podemos leer, editar y crear nuevos:

Escritura de archivos
*********************
Para escribir un nuevo archivo desde cero utilizamos el modificador ``wb``:

.. code:: c 

    #include <stdio.h>

    void main(void){
        FILE *fp;
        int value;

        fp = fopen("entrada.txt", "wb");
        if(fp){
            for(value = 48; value < 58; value++){
                fputc(value, fp);
            }
            fclose(fp);
        }
    }

- Añadir un texto formateado con la función ``fprintf()``:

.. code:: c

    #include <stdio.h>

    void main(void){
        FILE *fp;
        int value;

        fp = fopen("entrada.txt", "wb");
        if(fp){
            fprintf(fp, "Esto es un texto.\n");
            fprintf(fp, "Esto es otro texto.\n");
            fclose(fp);
        }
    }

Lectura de archivos
*******************
Si queremos leer un archivo usamos el modificador ``rb``:

.. code:: c 

    #include <stdio.h>

    void main(void){
        FILE *fp;
        int value;

        fp = fopen("entrada.txt", "rb");
        if(fp){
            while(1){
                value = fgetc(fp);
                if(value == EOF) break;
                else printf("%c", value);
            }
            fclose(fp);
        }
    }

Actualización de archivos
*************************
Para actualizar un archivo existente sin destruir la información que ya posee usaremos el modificador ``ab``:

.. code:: c 

    #include <stdio.h>

    void main(void){
        FILE *fp;
        int value;

        fp = fopen("entrada.txt", "ab");
        if(fp){
            fprintf(fp, "Esto es un texto.\n");
            fprintf(fp, "Esto es otro texto.\n");
            fclose(fp);
        }
    }

Si ejecutamos este codigo varias veces veremos como se incluyen nuevas líneas a nuestro script.

Empaquetado y Preprocesamiento
##############################

Crear paquetes
**************
En C podemos dividir el código y llamarlo en la cabecera

1. Tenemos un archivo llamado por ejemplo ``funcion.c`` que contiene una función específica:

.. code:: c 

    int add_valores(int a, int b, int c){
        return a + b + c;
    }

2. Ahora necesitamos un archivo que exporte la función y lo llamamos ``funcion.h``:

.. code:: c 

    extern int add_valores(int a, int b, int c);

3. Y ahora en nuestro archivo principal podemos importar este paquete:

.. code:: c

    #include <stdio.h>
    // llamada del archivo funcion.h:
    #include "function.h"

    void main(void){
        printf("El total es %d\n", add_valores(1,2,3));
    }

.. important::
    Para compilar este programa ejecutamos `gcc -o miprograma main.c function.c`

El preprocesador
****************
El archivo de intercambio que creamos antes llamado ``funcion.h`` es un archivo de preprocesamiento, podemos saltarnos ese paso y añadir directamente la línea al codigo principal:

.. code:: c 

    #include <stdio.h>
    extern int add_valores(int a, int b, int c);

    void main(void){
        printf("El total es %d\n", add_valores(1,2,3));
    }

.. important::
    Es necesario ejecutar la compilación de ambos al mismo tiempo igualmente 