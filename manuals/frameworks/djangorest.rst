=====================
Django Rest Framework
=====================
 
.. image:: /logos/logo-django-rest.png
    :scale: 75%
    :alt: Logo HTML5
    :align: center

.. |date| date::
.. |time| date:: %H:%M

Última edición el día |date| a las |time|.
 
Esta es la documentación que he recopilado para trabajar con Django, un framework basado en Python que sirve para desarrollar aplicaciones web.

.. contents:: Índice 
 
Primeros Pasos
##############
 
Crear un proyecto Django 
************************

* Lo primero que vamos a hacer es crear un entorno virtual.
* Luego instalamos Django ``pip install django``
* Creamos un projecto en Django ``django-admin startproject prueba_api``
* Ejecutamos el servidor para ver que se ha creado correctamente ``python manage.py runserver``

Instalar y configurar Django Rest Framework
*******************************************

Empezamos instalando las librerías necesarias:

* Instalamos Django Rest Framework ``pip install djangorestframework``
* Instalamos Django-filter ``pip install django-filter``
* Y por último, instalamos Markdown: ``pip install markdown``

Pasamos a configurar el proyecto:

* Lo primero será añadir **rest_framework** a settings.py:

.. code:: python 

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'rest_framework'
    ]

* Ahora como mínimo necesitamos tener una app creada, para ello ejecutamos ``python manage.py startapp API``
* Añadimos la app a settings.py:

.. code:: python 

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'rest_framework',
        'API'
    ]

* Realizamos la migración de la base de datos ``python manage.py migrate``
* Y creamos un superusuario ``python manage.py createsuperuser``

Serializadores
##############

Los serializadores se encargan de trabajar con los modelos de datos para adaptarlos a la API.

* Para comenzar tenemos que crear un modelo en nuestra API (API/models.py):

.. code:: python 

    from django.db import models

    class Empleados(models.Model):
        nombre = models.CharField(max_length=100, verbose_name="Nombre")
        apellidos = models.CharField(max_length=100, verbose_name="Apellidos")
        observaciones = models.TextField(verbose_name="Observaciones")

        def _str__(self):
            return self.nombre

* Ejecutamos ``python manage.py makemigrations API`` para preparar las migraciones y migramos la tabla ``python manage.py migrate API``
* Vamos a crear un archivo para los serializadores en la ruta (API/serializers.py):

.. code:: python

    # Importamos la librería de serializers:
    from rest_framework import serializers
    # Importamos el modelo de datos a usar:
    from .models import Empleados

    # Creamos el serializador:
    class EmpleadosSerializer(serializers.ModelSerializer):
    class Meta:
        # Elegimos el modelo:
        model = Empleados
        # Podemos elegir los campos a mostrar:
        # fields = ['nombre', 'apellidos', 'observaciones']
        # O mostrar todos los campos:
        fields = '__all__'

Con esto ya hemos preparado el primer serializador.

ViewSets
########

Los viewsets se implementan en las vistas de Django y sirven para mostrar los valores de la API o bien en su frontend o bien como un JSON, 
para crear un ViewSet nos vamos a (API/views.py):

.. code:: python 

    from django.shortcuts import render
    # Importamos la librería de viewsets:
    from rest_framework import viewsets
    # El modelo Empleados:
    from .models import Empleados
    # Y el serializador de Empleados:
    from .serializers import EmpleadosSerializer

    # Creamos un Viewset para mostrar los datos:
    class EmpleadosViewSet(viewsets.ModelViewSet):
        # En el lanzamos un QuerySet al modelo Empleados:
        queryset = Empleados.objects.all()
        # y le decimos que lo serialize con EmpleadosSerializer:
        serializer_class = EmpleadosSerializer

Con esto ya tenemos listo el ViewSet.

Rutas de la API
###############

Para configurar las rutas de la API utilizamos un archivo adicional de rutas o en nuestro caso vamos a usar el archivo principal (prueba_api/urls.py):

.. code:: python 

    from django.contrib import admin
    from django.urls import path, include # importamos include
    # Importamos la librería routers de rest_frameworks
    from rest_framework import routers
    # Importamos las vistas de la API
    from API import views

    # Creamos un enrutador para la API:
    router = routers.DefaultRouter()

    # En el router vamos añadiendo los endpoints a los viewsets:
    router.register('empleados', views.EmpleadosViewSet)

    urlpatterns = [
        path('api/v1/', include(router.urls)), # Aquí añadimos la ruta de la api que irá recibiendo los distintos endpoints arriba.
        path('admin/', admin.site.urls),
    ]

Ahora podemos ejecutar la API en ``http://localhost:8080/api/v1/`` y ver como podemos añadir registros.

.. attention::
    Con el nivel actual de permisos cualquiera puede introducir valores en la API. Para cambiar eso tenemos que ir al apartado de **permisos**


Permisos 
########

Tenemos varios tipos de permisos para gestionar nusetra API. Para establecer permisos creamos una lista al final de (prueba_api/settings.py):

* Por defecto nuestra API estará disponible para lectura y escritura de cualquier extraño.
* Establecer permisos a solo lectura:

.. code:: python 

    REST_FRAMEWORK = {
        'DEFAULT_PERMISSION_CLASSES': [                     
            'rest_framework.permissions.DjangoModelPermissionsOrAnonReadOnly',
        ],
    }

* Añadir acceso por login para poder editar y ver datos.

.. code:: python 

    REST_FRAMEWORK = {
        'DEFAULT_PERMISSION_CLASSES': [                     
            'rest_framework.permissions.IsAuthenticated',
        ],
    }

* Login requerido para editar y visualización sin login:

.. code :: python

    REST_FRAMEWORK = {
        'DEFAULT_PERMISSION_CLASSES': [                     
            'rest_framework.permissions.IsAuthenticatedOrReadOnly',
        ],
    }