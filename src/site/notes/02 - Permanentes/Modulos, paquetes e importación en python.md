---
{"dg-publish":true,"permalink":"/02 - Permanentes/Modulos, paquetes e importación en python/","title":"Modulos, paquetes e importación en python","noteIcon":""}
---


# Modulo vs paquete vs biblioteca

- Un módulo es un archivo.py que contiene distintas funciones
- Un paquete es un directorio formado por una agrupación de módulos según su funcionalidad. Contiene un archivo `__init__.py`
- Una biblioteca es una colección de paquetes

# Importación correcta

- Distintos módulos, lineas separadas
- Mismo módulo, lineas juntas
	- `from my_module import MyClass, my_function`
- `from my_module import *`     (se importan todos, no recomendado)
	- Si esto causa problemas de importación, puede usar:
		- `import my_module`
		- Y luego acceder a los elementos de la siguiente manera:
			- `my_module.MyClass`
			- `my_module.my_function`
- Para que no dé error por nombres similares
	- from my_module import MyClass as C, my_function as f

	```python  
	import math  
	from math import ceil, floor  
	  
	print(-2 ** 4)  
	print(math.sqrt(100))  
	print(1357%100)  
	  
	print(ceil(2.4))  
	print(floor(2.4))  
	  
	numero=102  
	print(numero%10)
	```

# Búsqueda de módulos y paquetes

Cuando se importa un módulo, el intérprete realiza una búsqueda en varios lugares para encontrar la localización de un módulo.
Primero busca el módulo especificado entre sus módulos integrados, si no lo encuentra, busca en la lista de directorios de `sys.path`. Esta lista contiene las siguientes rutas por defecto:

1. La ruta del directorio de trabajo actual.
2. Las rutas incluidas en la variable de entorno `PYTHONPATH`.
3. La ruta de instalación de Python ``pythonhome`` y las rutas de los módulos estándar.

Si el módulo no se encuentra en ninguna de estas rutas, Python generará un error `ImportError`. También es posible agregar o eliminar rutas de la lista `sys.path` en tiempo de ejecución si es necesario.

- ``Pythonpath``
	- Es una variable de entorno formada por una lista de directorios los cuales el intérprete de Python buscará para encontrar módulos y paquetes que se importen en python
	- Esto puede ser útil para añadir módulos propios al intérprete de Python

- ``Pythonhome``
	- Es una variable de entorno que especifica la ruta de instalación de Python en el sistema
	- En caso de tener varias versiones de Python instaladas, se puede especificar la ruta de instalación de la versión que queramos utilizar

- ``sys.path``
	- Es una variable que contiene las distintas rutas a los módulos de Python
	- sys: es un módulo integrado de Python que contiene parámetros específicos del sistema, es decir, contiene variables y métodos que interactúan con el intérprete y también se rigen por él.

# Gestión de paquetes PyPI (Python Package Index)

- Es un repositorio de paquetes y modulos de terceros de Python
- Los desarrolladores pueden subir sus paquetes y módulos para que otros los puedan descargar e instalar usando ``pip``
- pip es el gestor de paquetes estándar de python

- Para instalar un paquete:
"python3 -m pip install nombre_paquete"
"pip install nombre_paquete"

- Para actualizar un paquete:
"python3 -m pip install --upgrade nombre_paquete"

- Para ver los paquetes instalados:
"pip3 list"

Los paquetes se instalan en el directorio:
- $PYTHONPATH/lib/python3.X/site-packages/"

# DIR()

Es la función que se usa para conocer las variables, funciones y clases definidas en un módulo
Retorna una lista ordenada de cadenas.
Sin argumentos, dir() lista los nombres que tienes actualmente definidos

# HELP()

Sirve para obtener ayuda sobre un objeto, función, módulo, etc. Si se le pasa un objeto, devuelve la documentación asociada a ese objeto. Si se le pasa un módulo, devuelve la documentación del módulo. Si se le pasa una cadena, devuelve la documentación asociada a esa cadena.

help(MyClass)

``` python
Help on class MyClass in module __main__:
class MyClass(builtins.object)
 |  A simple example class
 |  
 |  Methods defined here:
 |  
 |  f(self)
 |      funcion f
 |  
 |  g(self)
 |      funcion f
 |  
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |  
 |  __dict__
 |      dictionary for instance variables (if defined)
 |  
 |  __weakref__
 |      list of weak references to the object (if defined)
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |  
```
