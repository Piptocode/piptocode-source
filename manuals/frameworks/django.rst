======
Django
======

.. image:: /logos/logo-django.png
    :scale: 50%
    :alt: Logo HTML5
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.

Esta es la documentación que he recopilado para trabajar con Django, un framework basado en Python que sirve para desarrollar aplicaciones web.

.. contents:: Índice
 
Primeros Pasos
##############

Creación del proyecto
*********************

Vamos a comenzar con Django, para ello lo primero que tenemos que hacer es crear un entorno virtual y ejecutarlo (recomendado).

* A continuación vamos a instalar django ``pip install django``
* Una vez instalado podemos crear un nuevo proyecto ejecutando ``django-admin startproject nombre_proyecto``
* Ahora podemos ejecutar el proyecto para ver si funciona accediendo al directorio del mismo y ejecutando ``python manage.py runserver``
* Nos vamos al navegador y escribimos ``localhost:8000`` para ver si arranca la pantalla de bienvenida de nuestro proyecto.

Primera configuración (settings.py)
***********************************

Nos situamos en el directorio principal del proyecto y accedemos a la carpeta con el mismo nombre de este. Ahí podemos encontrar el archivo ``settings.py`` que sirve para establecer
configuraciones del proyecto.

* debug: ``True`` por defecto, mostrará errores en el navegador. ``False`` para evitar mostrarlos en producción.
* LANGUAGE_CODE: cambiamos el valor por ``es`` para tener el proyecto en español.
* TIME_ZONE: Si somos de España podemos cambiarlo a ``Europe/Madrid``

Arrancar la base de datos
*************************

Para poner en marcha la base de datos del proyecto y que autogenere todo el **CRUD** ejecutamos el comando ``python manage.py migrate`` esto creará por defecto 
una base de datos SQLite, pero podemos cambiarla por una tipo **MySQL** o **PostgreSQL** en ``settings.py``

Crear un Administrador
**********************

Una vez migrada la base de datos para crear un administrador ejecutamos el comando ``python manage.py createsuperuser`` y cumplimentamos los 
datos de nuestro usario con el que podremos acceder al panel en la ruta del navegador ``localhost:8000/admin``

Crear una aplicación
********************

Django es un Framework modular, lo que quiere decir que iremos creando aplicaciones en el para gestionar distintas páginas y así poder reutilizar código.
* Vamos al terminal y ejecutamos ``python manage.py startapp nombre_de_tu_app``, esto nos genera una carpeta con los archivos esenciales para una app (views.py, models.py...) 
* Una vez creada una app es importante declararla en ``settings.py`` en el apartado de aplicaciones instaladas:

.. code:: python 

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'nombre_de_tu_app' # Declaramos nuestra app en esta lista
    ]

Rutas
#####

El archivo de rutas principal de Django lo podemos encontrar en la carpeta que tiene el nombre del proyecto y se llama ``urls.py``.
En este archivo vamos a vincular las rutas que vayamos generando con cada una de las vistas.

Ejemplo de archivo urls.py principal:

.. code:: python 

    # las dos primeras líneas importan el panel de administración y la librería path para agregar rutas
    from django.contrib import admin
    from django.urls import path
    from nombre_de_tu_app import views # Este es el archivo de vista que importamos de la app creada anteriormente

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', views.home, name = 'home'), # Definimos que '' (ruta raiz) apunte a la vista **home** y tenga el name 'home' para luego usar un template tag de rutas.
    ]

Rutas de app
************
Podemos generar otros archivos ``urls.py`` dentro de cada aplicación para gestionar sus rutas internas.

PENDIENTE....

Vistas
######

Las vistas en Django sirven para precargar y procesar datos del servidor que provienen de las plantillas **HTML**. Existen dos formas de crear vistas, las **FBV** (Function-based Views) y las **CBV** (Class-based Views).

FBV (Function-Based Views)
**************************

Son las vistas mas simples de Django, con ellas debes tener un control absoluto de lo que haces.

* Devolver respuesta HTML con **HttpResponse**:

.. code:: python

    from django.shortcuts import HttpResponse # el modulo HttpResponse carga una respuesta HTML directamente sin plantillas.

    # Creamos la función que gestionará la vista home definida como raiz en urls.py:
    def home(request):
        return HttpResponse("<h1>Título de prueba</h1><h2>Subtítulo</h2>") # esta va a retornar una respuesta html

Si nos vamos al navegador y ejecutamos la raiz veremos que el mensaje de bienvenida cambió por este último.

* Devolver una plantilla HTML con **Render**:

.. code:: python

    # importamos render que suele venir importado por defecto:
    from django.shortcuts import render 

    # creamos una función para gestionar los datos de vista:
    def home(request):
        # dentro de esta vista retornamos render y le pasamos por el segundo parámetro la plantilla que vamos a usar:
        return render(request, 'nombre_de_tu_app/home.html')

.. attention::
    Cuando hacemos esto es probable tener un error Template does not exist, se debe a que no hemos creado aun el template, que no hemos añadido la app a INSTALLED_APPS o simplemente cerramos el servidor y volvemos a lanzarlo par que funcione.

Templates
#########

Las plantillas son las que muestran el sitio web mediante etiquetas HTML y también imprimen resultados que gestiona el servidor con **Template Tags**.

* Para comenzar a utilizar templates creamos una carpeta llamada **templates** en el interior de la carpeta de nuestra app y dentro de templates otro directorio con el nombre de la app. (nombre_de_tu_app/templates/nombre_de_tu_app)
* Ahora creamos un archivo html por ejemplo home.html que cargará la página de inicio:

.. code:: html

    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Página de prueba</title>
    </head>
    <body>
        <h1>Bienvenido a mi página de prueba</h1>
        <h2>Aquí haremos pruebas varias</h2>
    </body>
    </html>

.. attention::
    Para que funcione debemos tener listo el render que devuelve este archivo html y al abrir el navegador se mostrará correctamente.

Template Tags
*************

Los Template Tags son un tipo de etiquetas especiales en Django que se utilizan en las plantillas para ejecutar respuestas backend.

Estas etiquetas suelen tener dos tipos de estructuras: ``{% instrucción %}`` o ``{{ datos }}`` según el tipo de tarea que vayamos a ejecutar.

Template tag base
-----------------

Una buena práctica para no repetir código en plantillas es coger todo el contenido común y almacenarlo en una plantilla base:

* Entramos en la carpeta ``nombre_de_tu_app/templates/nombre_de_tu_app`` y creamos un archivo llamado base.html donde copiaremos el contenido común:
* Ahora vamos a quitar el código de home.html y lo pegamos en base.html:

.. code:: html

    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Página de prueba</title>
    </head>
    <body>
        <h1>Bienvenido a mi página de prueba</h1>
        <h2>Aquí haremos pruebas varias</h2>

        <!-- Justo aquí enmedio utilizaremos el template tag base para extender una parte de otra plantilla  -->
        {% block cuerpo %}{% endblock %}

        <footer>Piptocode, hecho con cariño y para amantes de la programación</footer>
    </body>
    </html>

* Finalmente vamos a usar home.html como una plantilla de extensión con su propio código:

.. code:: html 

    <!-- llamamos el template tag con extends: -->
    {% extends 'nombre_de_tu_app/base.html' %}

    <!-- Utilizamos el block content para definir donde irá el contenido de la pagina home respecto a la plantilla base -->
    {% block cuerpo %}
        <h2>Portada</h2>
        <p>Esta es la página principal del sitio y utiliza una plantilla base para el contenido estático</p>
    {% endblock %}

Siguiendo este patrón podemos reutilizar el código base de la web en nuevas páginas o incluso nuevas apps de Django.

Template tag url
----------------

Con este template tag podemos establecer vínculos a otras páginas enlazando los names del archivo de rutas.

¿recuerdas las líneas que escribimos dentro de urls.py? ``path('', views.home, name = 'home'),``, el path recibe tres valores, la ruta del navegador, la ubicación de la vista y por último el nombre de la ruta,
este tercer valor es el que utilizamos con el template tag **url**

* vamos a editar el archivo base.html para añadir un menú de navegación:

.. code:: html

    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Página de prueba</title>
    </head>
    <body>
        <h1>Bienvenido a mi página de prueba</h1>
        <h2>Aquí haremos pruebas varias</h2>

        <nav>
            <!-- el template tag url lo usamos dentro del atribut href de un hipervínculo: -->
            <a href="{% url 'home' %}">Índice</a> <!-- lleva entre comillas simples el nombre de la ruta que vamos a vincular -->
            <a href="">Sobre mí</a>
            <a href="">Contacto</a>
        </nav>

        {% block cuerpo %}{% endblock %}

        <footer>Piptocode, hecho con cariño y para amantes de la programación</footer>
    </body>
    </html>

.. attention::
    Si añadimos un name que no existe en el archivo de rutas Django lanzará una pantalla de error en lugar de la plantilla.

Template tag static
-------------------

Con este template tag vamos a cargar archivos estáticos de nuestra web, entre ellos están las imágenes, videos, hojas de estilo y javascript.

* Siguiendo una práctica convencional creamos una carpeta llamada **static** dentro del directorio de la app y dentro de static una carpeta con el nombre de la app: ``nombre_de_tu_app/static/nombre_de_tu_app``.
* Dentro de la última carpeta podemos ir añadiendo carpetas básica como css, js e img para ir añadiendo los archivos correspondientes.
* Ahora podemos utilizar archivos estáticos dentro de dichas rutas:

.. code:: html

    <!-- cargamos el template tag static -->
    {% load static %}

    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Página de prueba</title>
        <!-- ahora si queremos cargar un archivo estatico como una hoja de estilo lo hacemos así: -->
        <link rel="stylesheet" href="{% static 'nombre_de_tu_app/css/estilos.css' %}">
    </head>
    <body>
        <h1>Bienvenido a mi página de prueba</h1>
        <h2>Aquí haremos pruebas varias</h2>

        <nav>
            <a href="{% url 'home' %}">Índice</a> 
            <a href="">Sobre mí</a>
            <a href="">Contacto</a>
        </nav>

        {% block cuerpo %}{% endblock %}

        <footer>Piptocode, hecho con cariño y para amantes de la programación</footer>
    </body>
    </html>

Template tag de datos 
---------------------

Los template tags de datos muestran información que enviamos desde la vista al template.

* Si nos vamos a views.py para añadir un dato:

.. code:: python

    from django.shortcuts import render 

    def home(request):
        # creamos una variable:
        nombre = "Guillermo Granados Gómez"        
        return render(request, 'nombre_de_tu_app/home.html', {'nombre':nombre}) # devolvemos la información en un diccionario

* Ahora que tenemos un dato, podemos mostrarlo en cualquier template de nuestra app:

.. code:: html

    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Página de prueba</title>
    </head>
    <body>     <!-- Ahora podemos mostrar el dato usando su clave -->
        <h1>Bienvenido a la web de {{ nombre }}</h1>
        <h2>Aquí haremos pruebas varias</h2>

        <nav>
            <a href="{% url 'home' %}">Índice</a> 
            <a href="">Sobre mí</a>
            <a href="">Contacto</a>
        </nav>

        {% block cuerpo %}{% endblock %}

        <footer>Piptocode, hecho con cariño y para amantes de la programación</footer>
    </body>
    </html>

Template tag for
----------------

En los templates de Django para hacer un bucle for lo hacemos del siguiente modo:

* Para empezar necesitamos un diccionario al que acceder desde views.py:

.. code:: python 

    from django.shortcuts import render 

    def home(request):
        # creamos un diccionario:
        personas = [
            {'nombre': 'Pepe', 'edad': 26},
            {'nombre': 'Antonio', 'edad': 38},
            {'nombre': 'María', 'edad': 37}
        ]        
        return render(request, 'pruebauno/home.html', {'personas':personas}) # devolvemos la información en un diccionario

* Y ahora podemos recorrer el diccionario en nuestro template con el template tag for:

.. code:: html

    <h3>Listado de Clientes</h3>
    <ul>
        {% for persona in personas %} <!-- Abrimos el bucle for en el template -->
            <li>Nombre: {{ persona.nombre }}, Edad: {{ persona.edad }}</li> <!-- Creamos el elemento que va a iterar en la lista imprimiendo los valores -->
        {% endfor %} <!-- Y lleva una llave de cierre -->
    </ul>

Template tag if
---------------

Con el template tag if podemos establecer condiciones dentro de los templates, retomando el ejemplo de for vamos a pintar de verde uno de los registros:

.. code:: 

    <h3>Listado de Clientes</h3>
    <ul>
        {% for persona in personas %} 
            <!-- Si en nombre se encuentra Antonio lo pintaremos de verde: -->
            <li {% if 'Antonio' in persona.nombre  %} style="color: green" {% endif %}>
                Nombre: {{ persona.nombre }}, Edad: {{ persona.edad }}
            </li> 
        {% endfor %} 
    </ul>

Modelos
#######

Los modelos en Django sirven para crear estructuras de bases de datos con las que podremos interactuar gracias a sus QuerySets.

En cada app que creamos tenemos un archivo models.py, vamos a editar uno para ver que campos tiene:

.. code:: python

    # Los modelos se crean usando una clase que hereda de la superclase Model:
    class Prueba(models.Model):
        titulo = models.CharField(max_length=200, verbose_name="Título") # CharField es un campo de tipo texto, el primer parámetro que le pasamos define el tamaño máximo y es obligatorio, el segundo es opcional y sirve para todos los campos (verbose_name define como se mostrará la label del panel de administración)
        descripcion = models.TextField(verbose_name="Descripción") # Con TextField tenemos una caja de texto sin límite de rango.
        link = models.URLField(null=True, blank=True, verbose_name="Enlace") # URLField nos permite agregar una url válida. 
        fecha_creacion = models.DateTimeField(auto_now_add = True) # crea un campo de fecha y hora, podemos pasarle la fecha de una publicación de forma automática con auto_now_add.
        fecha_edicion = models.DateField(auto_now = True) # aquí tenemos otra variante, en primer lugar DateField guarda solo la fecha y opcionalmente podemos decir que lo haga cuando editamos la entrada con auto_now.

        
        # opcionalmente podemos usar la clase Meta para editar valores que nos servirán para mostrar los datos en el panel de administración:
        class Meta: 
            verbose_name = "prueba" # Nombre de la tabla en el panel.
            verbose_name_plural = "pruebas" # nombre en plural.
            ordering = ["-fecha_creacion"] # Orden prioritario, en este caso por fecha descenciente.

        # Con esta función podemos retornar en el panel de administración un valor de referencia
        def __str__(self):
            return self.titulo

..attention
    Tienes que tener registrada tu app en el apartado INSTALLED_APPS o sino dará error a la hora de migrar la base de datos.

.. hint::
    Los parámetros comunes para prácticamente todos los campos son verbose_name (nombre que muestra), blank (True o False para permitir el campo vacío), null (True o False para permitir campo nulo)

Cargar imágenes en modelos con Pillow
*************************************

Pillow es una librería de Python que se utiliza para el tratamiento de imágenes. En Django la podemos utilizar para gestionar la carga de estas.

* Lo primero que tenemos que hacer es instalar Pillow en nuestro entorno: ``pip install Pillow``
* Ahora vamos a editar nuestra clase de models.py:

.. code:: python

    class Prueba(models.Model):
        titulo = models.CharField(max_length=200, verbose_name="Título") 
        descripcion = models.TextField(verbose_name="Descripción")
        fecha_creacion = models.DateTimeField(auto_now_add = True)
        fecha_edicion = models.DateField(auto_now = True)
        # con ImageField podemos subir una imagen a un directorio que elijamos:
        imagen = models.ImageField(upload_to="imagenes/")

        class Meta: 
            verbose_name = "prueba"
            verbose_name_plural = "pruebas" 
            ordering = ["-fecha_creacion"]

        def __str__(self):
            return self.titulo

* Para poder subir las imágenes tenemos que añadir en settings.py la siguiente línea:

.. code:: python

    MEDIA_URL = '/media/'
    MEDIA_ROOT = os.path.join(BASE_DIR, 'media')

* Finalmente nos vamos al archivo de rutas principal (el que se encuentra dentro de la carpeta con el nombre de tu proyecto) y añadimos la siguiente configuración para poder visualizar las imágenes desde el panel:

.. code:: python 

    from django.contrib import admin
    from django.urls import path
    from nombre_de_tu_app import views 
    # Importamos la librería settings:
    from django.conf import settings

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', views.home, name = 'home'), 
    ]

    # Cargamos la ruta siempre que este en modo debug:
    if settings.DEBUG:
        from django.conf.urls.static import static
        urlpatterns += static(settings.MEDIA_URL, document_root = settings.MEDIA_ROOT)

De este modo y mientras no estemos en producción podremos visualizar las imágenes desde el panel de administrador para probar que funciona correctamente.


Generar modelo y migrar la base de datos
****************************************

Cuando creamos un modelo nuevo lo primero que tenemos que hacer es maquetar la estructura que vamos a migrar cada vez que generemos la base de datos:

* Para crear el modelo de las tablas de una app ejecutamos ``python manage.py makemigrations nombre_de_tu_app``.
* Si todo va bien, migramos la base de datos con ``python manage.py migrate nombre_de_tu_app``

..attention
    Antes de hacer una migración debemos generar todo el Scaffold para el sistema de login por primera vez ejecutando ``python manage.py migrate``

Panel de administración
#######################

El panel de Administración de Django es un modelo CRUD ya definido por defecto con todo el Scaffold del sistema login preparado por defecto.

Puesta en marcha
****************

Para poner en marcha el panel tenemos que hacer un par de cosas en consola:

* Primero tenemos que crear todo el Scaffold ejecutando ``python manage.py migrate``
* Después ejecutamos ``python manage.py createsuperuser`` para generar un nuevo superusuario.

Ahora ya podemos acceder al panel de administración desde la ruta ``localhost:8000/admin``

Mostrar datos de nuestros modelos
*********************************

El panel de Administración solo dispone por defecto de las tablas de usuarios. Pero si hemos creado un modelo debemos implementarlo,
para ello en la carpeta de nuestra app veremos un archivo admin.py el cual editamos:

.. code:: python 

    from django.contrib import admin

    # Importamos el modelo:
    from .models import Prueba

    # Registramos en el panel el modelo:
    admin.site.register(Prueba)

De este modo podremos leer, editar, borrar y añadir registros a esta tabla de nuestra app.

Personalizar titulos de las Apps 
********************************

En el panel de administración vemos que las tablas se irán dividiendo en apartados según su app, si tenemos varias apps veremos que cada
tabla esta dentro de apartados. Podemos cambiar el título de estos apartados accediendo a nuestra app y editando el archivo app.py:

.. code:: python 

    from django.apps import AppConfig


    class nombre_de_tu_appConfig(AppConfig):
        name = 'nombre_de_tu_app'

        # Podemos asignarle un nombre que veremos en el panel:
        verbose_name = 'App de Prueba'

* Para que esto funcione tenemos que exportar dicha configuración a settings.py:

.. code:: python 

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'nombre_de_tu_app.apps.nombre_de_tu_appConfig' # cambiamos el nombre de la app por su clase configuradora.
    ]

Personalizar tablas
*******************

Cuando accedemos a una tabla podemos ver una lista con todos los títulos o el valor que hayamos devuelto en el modelo. Pero podemos modificar su comportamiento
editando el archivo admin.py:

.. code:: python

    from django.contrib import admin
    from .models import Prueba

    # Creamos una clase que se encargará de editar las configuraciones de nuestro panel:
    class PruebaAdmin(admin.ModelAdmin):
        # con esta tupla definimos los campos que serán de solo lectura cuando abramos un registro.
        readonly_fields = ('fecha_creacion', 'fecha_edicion')

    admin.site.register(Prueba, PruebaAdmin)