========
Python 3
========
  
.. image:: /logos/logo-python.png
    :scale: 25%
    :alt: Logo JS
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con Python 3, el lenguaje de propósito general que me gusta utilizar en mis proyectos y en mi trabajo del día a dia.

.. contents:: Índice 

Elementos básicos del lenguaje
##############################

Comentarios
***********
Los comentarios se pueden realizar de dos tipos:

* Comentarios de una sola línea:

.. code:: Python

    # Comentario de una sola linea
 
* Comentarios multilínea:

.. code:: python

    '''
    Esto es un comentario multilínea
    Aquí podemos establecer mas de 
    una linea
    '''

Estructura en Python
********************
La estructura de Python se presenta de un modo ligeramente distinto al de otros lenguajes de programación:

.. code:: python

    # Las variables se declaran sin usar palabra reservada como var:
    variable = "contenido"   # python no utiliza ; para finalizar línea.

    # En las estructuras de control, funciones y clases de python sustituye las llaves por ``:``, y la identación del contenido es obligatoria:
    for n in numeros:
        print(numeros[n])
    

Extensión
*********
La extensión utilizada por los archivos Python es ``py``

Ejecución
*********
Para ejecutar un script de python 3 lo hacemos del siguiente modo: ``python3 script.py``

Preparación del script 
**********************
Cuando creamos un nuevo script python tenemos que tener en cuenta un par de líneas, la primera es el interprete que es python y la segunda la codificación que utilizamos en España utf8.

Ejemplo:

.. code:: python

    #!/usr/bin/env python3
    #_*_ coding: utf8 _*_

Repositorio de paquetes
***********************
Python además de contar con una biblioteca estandar también tiene un repositorio conocido como PyPI 
al cual podemos acceder en: `pypi.org <https://pypi.org/>`_.

Palabras reservadas de Python 3
*******************************
En Python existen las siguientes palabras reservadas:

* and
* as 
* assert 
* async
* await
* break 
* class 
* continue 
* def 
* del 
* elif 
* else 
* except 
* False
* finally 
* for 
* from 
* global 
* if 
* import 
* in 
* is 
* lambda 
* None
* nonlocal
* not 
* or 
* pass
* raise 
* return 
* True
* try 
* while 
* with 
* yield


Variables y tipos de datos
##########################

Variables
*********
Las variables se definene de forma dinámica, lo que significa que no se especifica su tipo de antemano y puede cambiar su valor en todo momento.

Ejemplo:

.. code:: Python

    nombre = "Antonio"

Constantes
**********
Las constantes no existen como tales en Python, pero si se utiliza la convención de declararlas en mayúsculas
para recordar que es un dato que no debería ser mutable.

Ejemplo:

.. code:: python 

    DNI = "23435324Z"

Tipos de datos primitivos
*************************
Los tipos de datos mas comunes son los siguientes:

+--------------+-----------------------------------------------+-----------------------------+
| Tipo de dato | Denominación                                  | Ejemplo                     |
+==============+===============================================+=============================+
| str          | Cadena de texto                               | 'cadena', "cadena"          |
+--------------+-----------------------------------------------+-----------------------------+
| int          | Número Entero                                 | 20, 5, -3, 0                |
+--------------+-----------------------------------------------+-----------------------------+
| float        | Número con decimales                          | 20.53, 12.5, -18.353        |
+--------------+-----------------------------------------------+-----------------------------+
| bool         | Verdadero o falso                             | True, False                 |
+--------------+-----------------------------------------------+-----------------------------+
| list         | Matriz de datos                               | [1, 5, "Hola", True]        |
+--------------+-----------------------------------------------+-----------------------------+
| tuple        | Matriz de datos inmutable                     | ("hola", 15, False)         |
+--------------+-----------------------------------------------+-----------------------------+
| dict         | Objeto con orden de tipo clave:valor          | {'nombre':'Pedro', edad: 45}|
+--------------+-----------------------------------------------+-----------------------------+

Ejemplos:

.. code:: python 

    cadena = "Dia de paga"
    otraCadena = 'Cadena de comillas simples es lo mismo'
    entero = 27
    decimal = 22.83
    booleano = True
    lista = [1, 5, 13, "Papiro"]
    tupla = (3, "guay", True)
    diccionario = {'profesion': 'programador', 'hobbie':'DIY'}

Entrada y Salida de datos
#########################
En Python 3 la entrada y salida de datos se presenta de la siguiente forma:

* Entrada de datos:

.. code:: python

    nombre = input('Escribe tu nombre: ')

* Salida de datos: 

.. code:: python

    # Cadena formateada:
    print("Te llamas {}".format(nombre))
    # Cadena concatenada:
    print("Te llamas " + nombre)
    

Como vemos en el ejemplo anterior tenemos dos formas de imprimir, concatenando con + cada una de las cadenas y variables
o bien utilizar el formato que funciona introduciendo dentro de la cadena unas llaves ``{}`` y luego justo despúes de la cadena 
la unimos con la función ``.format()`` en la cual iremos añadiendo cada una de las variables presentes:

.. code:: python

    print("Te llamas {}, tienes {} años y vives en {}.".format(nombre,edad,ciudad))


Operadores
##########

Operadores Aritméticos
**********************
Los operadores aritméticos que se presentan en python son los mismos que en la mayoría de lenguajes,
``+, -, *, /, %``

Estos podemos utilizarlos del siguiente modo:

.. code:: python

    # asignación:
    suma = 2 + 2

    # salida de datos:
    print(3 - 2)

    # si utilizamos + en cadenas las concatenamos:
    cadenas = "cadena uno" + " y " + " cadena dos"

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

    # Si decimos que 3 es mayor que 2 
    print(3 > 2)
    # el resultado que sale por consola es True.


Operadores Lógicos
******************
En Python se utilizan los mismos operadores lógicos que en la mayoría de lenguajes de programación, sin embargo presentan un aspecto diferente:

+-----------+-----------+------------------------------------------------------------+
| Operador  | símbolo   | condición                                                  |
+===========+===========+============================================================+
| Y (and)   | and       | La condición se cumple si todos son verdaderos             |
+-----------+-----------+------------------------------------------------------------+
| O (or)    | or        | La condición se cumple si al menos uno es verdadero        |
+-----------+-----------+------------------------------------------------------------+
| NO (not)  | !         | La condición se cumple si es diferente a lo que se compara |
+-----------+-----------+------------------------------------------------------------+

Ejemplos:

.. code:: python

    # Resultado False:
    print(5 > 7 and 3 < 6)
    # Resultado True:
    print(5 > 7 or 3 < 6)
    # Resultado True
    print(6 != 3)

Estructuras de control
######################
En python disponemos de estructuras de control como ``if``, ``for`` y ``while``.

Condicional if
**************
Las condiciones sencillas en python funcionan del siguiente modo:

.. code:: python

    saludo = input("Di hola: ")

    if saludo == 'Hola':
        print('Hola a tí también')

También tenemos condiciones con una salida alternativa si no se cumple esta:

.. code:: python

    nacimiento = input('Dime tu nacimiento: ')

    if nacimiento <= 2002:
        print('Eres mayor de edad')
    else:
        print('Eres menor de edad')
    

Condicional if-elif
*******************
Las condiciones compuestas nos ofrecen varios caminos posibles:

.. code:: python

    edad = input('Dime tu edad: '):
    
    if edad >= 18:
        print('Eres mayor de edad')
    elif edad < 18:
        print('Eres menor de edad')
    elif edad >= 65:
        print('Ya eres un anciano')
    else:
        print('No es una edad correcta')

Bucle for
*********
El bucle for en python se presenta de un modo muy similar al foreach de otros lenguajes:

* Uso con rango definido:

.. code:: python

    mensaje = input("Escribe tu mensaje: ")
    numero = int(input("¿cuántas veces lo repito? "))

    for n in range(0, numero):
        print("{} : {}".format(n,mensaje))

Bucle while
***********
El bucle While es similar a otros lenguajes, pero no se presenta la figura del bucle do-while.

Ejemplo:

.. code:: python

    numero = 10
    juego = True

    while juego == True:
        adivina = int(input('Adivinia el número >> '))
        print('Fallaste!')

        if adivina == numero:
            print('Acertaste!')
            juego = False

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

Estructuras de datos
####################

Listas
******
Las listas son un tipo de dato mutable que agrupa un conjuto de valores de distintos tipos:

.. code:: python

    lista = [1, 15, -12, 3.81, "cadena", True]

* Recorrer valores de una lista e imprimirlos con ``for``:

.. code:: python

    lista = ["uno", "dos", "tres", "cuatro"]

    for l in lista:
        print(l)

* Ver cuantos elementos hay en una lista con ``len()``:

.. code:: python

    print(len(lista))

* Imprime un elemento de la lista por su posición:

.. code:: python

    print(lista[2])

* Muestra un rango de elementos de la lista:

.. code:: python

    print(lista[0:2])

* Muestra el último elemento de la lista:

.. code:: python

    print(lista[len(lista)-1])

* Borra el último elemento de la lista con ``pop()``:

.. code:: python

    lista.pop()
    print(lista)

* Borrar un elemento por su posición con ``del``:

.. code:: python

    del lista[2]
    print(lista)

* Añadir un elemento a la lista con ``append()``:

.. code:: python

    lista.append("nuevo texto")
    print lista

* Convertir lista a cadena de texto con ``join()``:

.. code:: python

    lista = ['P','e','p','e']
    lista = ''.join(lista)
    print(lista)

* Crear una lista a partir de un rango o una tupla con ``list()``:

.. code:: python

    numeros = range(0,30)
    lista = list(numeros)
    print(lista)

* Ordenar elementos de listas por orden numérico o alfabético:

.. code:: python

    lista = ["gato", "nocilla", "avión", "leche"]
    
    # Orden normal:
    print(sorted(lista))

    # Orden inverso:
    print(sorted(lista, reverse=True))

* Verificar si se encuentra un elemento en la lista:

.. code:: python

    lista = ["gato", "nocilla", "avión", "leche"]

    'gato' in lista // esto devuelve true o false dependiendo de si la cadena existe o no en la lista.
    'perro' not in lista // igual que antes pero preguntando si no existe

Tuplas
******
Las tuplas son similiares a las listas pero con la diferencia de que estas son inmutables.

Ejemplo de lista:

.. code:: python

    tupla = (1, 'palabra', True, 3.53)

* Recorrer valores de una tupla e imprimirlos:

.. code:: python

    tupla = (1, 'palabra', True, 3.53)

    for t in tupla:
        print(t)

* Ver cuantos elementos hay en una tupla con ``len()``:

.. code:: python

    print(len(tupla))

* Imprime un elemento de la tupla por su posición:

.. code:: python

    print(tupla[2])

* Muestra un rango de elementos de la tupla:

.. code:: python

    print(tupla[0:2])

* Muestra el último elemento de la tupla:

.. code:: python

    print(tupla[len(tupla)-1])

* Convertir tupla a cadena de texto con ``join()``:

.. code:: python

    tupla = ('P','e','p','e')
    tupla = ''.join(tupla)
    print(tupla)

* Crear una tupla a partir de un rango o lista con ``tuple()``:

.. code:: python

    lista = [10, "hola", 3.43]
    tupla = tuple(lista)
    print(tupla)

* Ordenar elementos de tuplas por orden numérico o alfabético:

.. code:: python

    tupla = (9, 2, 3, 5, 1)
    
    # Orden normal:
    print(sorted(tupla))

    # Orden inverso:
    print(sorted(tupla, reverse=True))

Diccionarios
************
Los diccionarios en python se asemejan a los objetos literales en javascript u otros lenguajes de programación.
Se construye por pares de datos que son clave y valor ``{'nombre':'Antonio'}`` y pueden anidar todo tipo de datos e incluso más diccionarios.

Ejemplo de uso:

.. code:: python

    diccionario = {'nombre':'Pepe', 'edad': 37, 'profesion':'agricultor'}
    print(diccionario)

* Imprimir un valor del diccionario:

.. code:: python

    print(diccionario['nombre'])

* Convertir diccionario a tupla con ``items()``:

.. code:: python

    tupla = diccionario.items()
    print(tupla)

* Copiar un diccionario con ``copy()``:

.. code:: python

    otro = diccionario.copy()
    print(otro)

* Recuperar solo las claves del diccionario con ``keys()``:

.. code:: python

    claves = diccionario.keys()
    print(claves)

* Recuperar solo los valores del diccionario con ``values()``:

.. code:: python 

    valores = diccionario.values()
    print(valores)

* Recorrer e imprimir todos los elementos del diccionario:

.. code:: python

    for d in diccionario:
        print(d + " Su valor es: " + diccionario[d])

Funciones Internas
##################
Como en la mayoría de lenguajes de programación, en Python existen funciones predefinidas.

Funciones de cadenas
********************
Aquí tenemos las funciones mas utilizadas para tratamiento de cadenas de texto:

* Para saber la longitud de una cadena con ``len()``:

.. code:: python

    nombre = "Alba María"
    print(len(nombre))

* Convertir valor numérico a cadena con ``str()``:

.. code:: python

    numero = 27
    numero = str(numero)
    print(numero)

* Convertir una cadena en una lista ``split()``:

.. code:: python

    lista = nombre.split()
    print(lista)

* Reemplazar una cadena por otra con ``replace()``:

.. code:: python

    frase = "Soy la persona mas afortunada"
    print(frase.replace('Soy', 'Era'))

* Convertir a mayúsculas la cadena con ``upper()``:

.. code:: python

    frase = "Hace buen día"
    print(frase.upper())

* Convertir a minúsculas la cadena con ``lower()``:

.. code:: python

    frase = "MI nombre Es Alfredo"
    frase = frase.lower()
    print(frase)

Funciones numéricas
*******************
Estas son las funciones numéricas mas comunes en python:

* Convertir un valor a entero con ``int()``:

.. code:: python

    numero = int(input("introduce un número: "))
    print(numero)

* Convertir un valor a decimal con ``float()``:

.. code:: python

    numero = float(input("introduce un número: "))
    print(numero)

* Redondear un valor decimal con ``round()``:

.. code:: python

    numero = 13.583
    print(round(numero))

* Crear un rango de números con ``range()``:

.. code:: python

    rango = range(1,11)
    print(list(rango))

* Mostrar el valor mayor de un rango con ``max()``:

.. code:: python 

    print(max(rango))

* Mostrar el valor mínimo de un rango con ``min()``:

.. code:: python

    print(min(rango))

* Sumar todos los valores de un rango con ``sum()``:

.. code:: python

    print(sum(rango))
    
Otras funciones comunes
***********************
Tenemos una serie de funciones de uso común en python:

* Averiguar que tipo de dato contiene una variable con ``type()``:

.. code::

    variable = "cadena"
    print(type(variable))

Funciones
#########
Las funciones en Python se declaran con ``def`` en lugar de ``function`` como en muchos otros lenguajes:

.. code:: python 

    # Creación:
    def saludar():
        print('Hola mundo')

    # Llamada:
    saludar()

* Recibir parametros en una función:

.. code:: python

    # Añadimos un nombre:
    nombre = input('¿Cómo te llamas?: )

    # Creamos la función que recibirá un valor que imprimimos:
    saludar(persona):
        print("Hola {}".format(persona))

    # y llamamos a la función pasándole la variable nombre:
    saludar(nombre)

* Recibir parametros infinitos añadiendo ``*`` a un parametro:

    .. code:: python

        def miFuncion(*unNombre):
        for persona in unNombre:
            print("Se llama {}".format(persona))

        miFuncion("Pepe", "Antonio", "Alfredo")

Clases
######
Las clases en python tienen una estructura similar al de otros lenguajes,
la mayor diferencia reside en el encapsulamiento lo que normalmente utilizamos ``this`` pasa a ser ``self`` y tenemos que 
pasarlo a los métodos que vayan a utilizar atributos de la clase (osea practicamente siempre):

.. code:: python

    class Persona():
        # atributos de clase
        nombre = ""
        genero = ""
        peso = 0
        estatura = 0

        # Constructor
        def __init__(self):
            self.nombre = "Alfredo"
            self.genero = "Masculino"
            self.peso = 82
            self.estatura = 174

        # Métodos:
        def datos(self):
            print("Su nombre es {}, su género {}, pesa {} kilos y mide {}.".format(self.nombre, self.genero, self.peso, self.estatura))


    # creacion del objeto:
    antonio = Persona()
    # Ejecutando metodo del objeto:
    antonio.datos()
    
* Implementación de clases que reciben parámetros:

.. code:: python

    class Persona():
            nombre = ""
            genero = ""
            peso = 0
            estatura = 0
            # Pasamos los parámetros por el constructor y los asignamos a los atributos:
            def __init__(self, para_nombre, para_genero, para_peso, para_estatura):
                self.nombre = para_nombre
                self.genero = para_genero
                self.peso = para_peso
                self.estatura = para_estatura

            def datos(self):
                print("Su nombre es {}, su género {}, pesa {} kilos y mide {}.".format(self.nombre, self.genero, self.peso, self.estatura))

    # Al crear el objeto le enviamos los parámetros correspondientes:
    antonio = Persona('Antonio', 'Masculino' ,79, 168)

    antonio.datos()

* Para heredar una clase en python lo hacemos como en la mayoría de lenguajes:

.. code:: python

    class Luis(Persona):
        def __init__(self):
            self.nombre = "Luis"
            self.genero = "Masculino"
            self.peso = 79
            self.estatura = 158

    luis = Luis()
    # y podemos acceder a los metodos del padre como a sus atributos:
    luis.datos()

* Acceso a atributos y metodos de otras clases:

.. code:: python 

    class Animal:
        tipo = "perro"
        edad = 5

        def __init__(self):
            print("animal creado")

        def saberEdad(self):
            return self.edad
        
        

    class Mascota:
        def __init__(self):
            # creamos el objeto y usamos self para poder manejarlo en toda la clase:
            self.animal = Animal()
            # y con un punto podemos recuperar atributos y metodos:
            print("Mi mascota es un {}".format(self.animal.tipo, self.animal.saberEdad()))

        def cumple(self, nuevaEdad):
            self.animal.edad = nuevaEdad
            print("Mi {} cumple {} años".format(self.animal.tipo, self.animal.saberEdad()))

    mascota = Mascota()

    mascota.cumple(6)

En este ejemplo se podía haber usado la herencia, pero lo he realizado de este modo para mostrar 
como se puede recuperar atributos y metodos de otro objeto cuando la herencia no encaja tanto.

Manejo de errores
#################
El manejo de errores en Python se hace con ``try`` y ``except`` seguido opcionalmente por ``finally``:

.. code:: python

    try: 
        print(nombre)
    except NameError:
        print('No has escrito un nombre')
    finally KeyboardInterrupt:
        print('Fin de la ejecución')

* Generar errores personalizados con ``raise``:

.. code:: python

    try: 
        raise IOError
    except IOError:
        print('Ocurrió un error')
        exit()

Módulos Internos
################
Los módulos son archivos que proveen de ciertas funciones y clases para realizar determinadas tareas. En python los 
mas utilizados son:

* Con ``os`` podemos navegar por el sistema de archivos:

.. code:: python

    import os

    os.mkdir('prueba')

* Podemos administrar archivos de forma mas detallada con ``shutil``:

.. code:: python

    import shutil

    shutil.copyfile('archivo.txt', 'nuevo.txt')
    
    shutil.move('/carpeta/origen', '/carpeta/destino')

* Si necesitamos trabajar con números aleatorios ``random`` es nuestro módulo:

.. code:: python

    import random

    # Elegir un elemento al azar:
    lista = ['galletas', 'tortitas', 'sandwich']
    random.choice(lista)

    # Dame un número al azar que puede ser decimal:
    random.random()

    # Y un número al azar basado en un rango de enteros:
    random.randrange(15)

* Y para trabajar con fechas y tiempo ``datetime``:

    import datetime

    # fecha de hoy:
    fecha = datetime.date.today()
    # guardar una fecha:
    felizVeinte = datetime.date(2020, 1, 1)

    print(fecha)
    print(felizVeinte)

Módulos y paquetes
##################
Podemos crear nuestros propios módulos en python para cortar partes del código específicas:

* Lo primero es crear un nuevo archivo.py y guardar ahí por ejemplo una clase.
* Luego creamos un segundo archivo que será el principal.py y para importarlo basta con escribir ``import archivo`` al comienzo del proyecto.

Si lo que queremos es guardar el módulo en una carpeta entonces estamos hablando de un Paquete:

* Los paquetes son archivos.py que guardamos en una carpeta.
* Dentro de esa carpeta creamos siempre un archivo llamado ``__init__.py`` para que el interprete lo considere un paquete.
* Luego en el archivo principal.py lo importamos con la línea ``from carpeta import archivo``

Y para poner un alias a un paquete o módulo de python ya sea estandar o personalizado utilizamos ``as``:

.. code:: python

    from carpeta import archivo as traductor


Manejor de archivos
###################
En python podemos crear y modificar archivos con la función ``open()``:

Cuando abrimos un archivo en python siempre asignamos un permiso:

+---------------+--------------+
| Permiso       | Nomenclatura |
+===============+==============+
| Escritura     | w            |
+---------------+--------------+
| Lectura       | r            |
+---------------+--------------+
| Actualización | a            |
+---------------+--------------+

* En el caso de escritura:

.. code:: python

    # abrimos el archivo con escritura por ejemplo:
    archivo = open('archivo.txt', 'w')

    # Escribimos varias líneas:
    archivo.write('Hola')
    archivo.write('\n')
    archivo.write('Lo de antes es un salto de línea')

    # Y lo cerramos
    archivo.close()

* En caso de lectura:

.. code:: python

    archivo = open('archivo.txt', 'r')

    # Y lo guardamos en una lista eliminando los saltos:
    lista = archivo.read().split('\n')

    for l in lista:
        print(l)

    archivo.close()

* En caso de actualización:

.. code:: python

    archivo = open('archivo.txt', 'a')

    archivo.write('\n')
    archivo.write('linea adicional')

    archivo.close() 