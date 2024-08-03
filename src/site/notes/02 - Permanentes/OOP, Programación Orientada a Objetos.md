---
{"dg-publish":true,"permalink":"/02 - Permanentes/OOP, Programación Orientada a Objetos/","title":"OOP, Programación Orientada a Objetos","noteIcon":""}
---


# Qué es esta vaina?

- Proporcionan una forma de empaquetar datos y funcionalidad juntos.
- Una clase define un nuevo tipo de objeto, permitiendo crear nuevas instancias de ese tipo.
- Todo valor es un objeto y tiene un tipo.

- **CLASES**:
	- [OOP](https://www.w3schools.com/cpp/cpp_oop.asp)
		- A class is a template for objects, and an object is an instance of a class
	- [Classes and Objects](https://www.w3schools.com/cpp/cpp_classes.asp)
		- Atributes and methods
	- [Class Methods](https://www.w3schools.com/cpp/cpp_class_methods.asp)
		- Se pueden definir fuera de la clase accediendo con Clase::Funcion(). Pero se debe declarar dentro de la clase
	- [Constructors](https://www.w3schools.com/cpp/cpp_constructors.asp)
		- Funcion que usa el mismo nombre que la clase
		- Son publicos siempre
		- No tienen valor de retorno
	- [Access Specifiers](https://www.w3schools.com/cpp/cpp_access_specifiers.asp)
		- Los atributos privados no pueden ser accedidos desde el programa principal, aunque si con un metodo publico de dentro de la clase
		- Es una buena practica declarar los atributos como privados todo lo que se pueda
	- [Encapsulation](https://www.w3schools.com/cpp/cpp_encapsulation.asp)
		- Ejemplo atributo privado: "salario"
		- No se puede acceder a él con Persona.salario
		- Pero sí se puede usar una función pública: getSalario() para acceder al salario
		- Esto ayuda a cambiar partes del código sin afectar a otras
	- [**Classes (I)**](https://cplusplus.com/doc/tutorial/classes/)
	- [**Classes (II)**](https://cplusplus.com/doc/tutorial/templates/) (salvo *templates*)
	- [**Special members**](https://cplusplus.com/doc/tutorial/classes2/)
	- [**Friendship and inheritance**](https://cplusplus.com/doc/tutorial/inheritance/) (funciones amigas)

# Python

- 2 tipos de operaciones
	- Instanciación de la clase = crear objeto
      - objeto = clase()
	- Referenciar a atributos y métodos
      - objeto.atributo 
      - objeto.metodo()
        - Objeto es una instancia de la clase sobre la que se llama al método


- Como se construyen las clases
	- ![Pasted image 20230201192647.png](/img/user/_Archivos/Pasted%20image%2020230201192647.png)



## Metodos mágicos

`__init__(self, parametro1, parametro2)` constructor

``__str__`` se ejecutra al hacer print sobre el objeto

``__add__`` se ejecuta al sumar 2 objetos

``__repr__`` muestra el objeto indicando su tipo

``__len__`` se ejecuta al hacer len sobre el objeto

``__sub__`` se ejecuta al restar 2 objetos

``__mul__`` se ejecuta al multiplicar 2 objetos

``__truediv__`` se ejecuta al dividir 2 objetos (/)

``__floordiv__`` se ejecuta al dividir 2 objetos (//)

``__mod__`` se ejecuta al hacer el modulo de 2 objetos (%)

``__lt__`` se ejecuta al hacer un menor que 2 objetos (<)

``__le__`` se ejecuta al hacer un menor o igual que 2 objetos (<=)

``__eq__`` se ejecuta al hacer un igual que 2 objetos ``(==)``

``__ne__`` se ejecuta al hacer un distinto que 2 objetos (!=)

``__gt__`` se ejecuta al hacer un mayor que 2 objetos (>)

``__ge__`` se ejecuta al hacer un mayor o igual que 2 objetos (>=

``__pow__`` se ejecuta al hacer la potencia de 2 objetos ``(**)``

``__contains__`` para in




```python  
from abc import ABC, abstractmethod
from datetime import datetime

class ElementoSistemaFicheros(ABC):
    def __init__(self, nombre):
        self.nombre = nombre
        self.fecha_creacion = datetime.now()
        self.fecha_modificacion = datetime.now()

    @abstractmethod
    def get_tamanio(self):
        pass

    def renombrar(self, nuevo_nombre):
        self.nombre = nuevo_nombre
        self.fecha_modificacion = datetime.now()

class Archivo(ElementoSistemaFicheros):
    def __init__(self, nombre, contenido=""):
        super().__init__(nombre)
        self.contenido = contenido

    def get_tamanio(self):
        return len(self.contenido)

    def escribir(self, nuevo_contenido):
        self.contenido = nuevo_contenido
        self.fecha_modificacion = datetime.now()

    def leer(self):
        return self.contenido

class Directorio(ElementoSistemaFicheros):
    def __init__(self, nombre):
        super().__init__(nombre)
        self.contenido = []

    def get_tamanio(self):
        return sum(elemento.get_tamanio() for elemento in self.contenido)

    def agregar(self, elemento):
        self.contenido.append(elemento)
        self.fecha_modificacion = datetime.now()

    def eliminar(self, elemento):
        self.contenido.remove(elemento)
        self.fecha_modificacion = datetime.now()

    def listar_contenido(self):
        return [elemento.nombre for elemento in self.contenido]

class ArchivoTexto(Archivo):
    def contar_palabras(self):
        return len(self.contenido.split())

class ArchivoImagen(Archivo):
    def __init__(self, nombre, ancho, alto):
        super().__init__(nombre)
        self.ancho = ancho
        self.alto = alto

    def get_resolucion(self):
        return f"{self.ancho}x{self.alto}"

# Ejemplo de uso
raiz = Directorio("raiz")

documentos = Directorio("documentos")
raiz.agregar(documentos)

texto = ArchivoTexto("nota.txt")
texto.escribir("Esto es una nota de ejemplo.")
documentos.agregar(texto)

imagen = ArchivoImagen("foto.jpg", 1920, 1080)
documentos.agregar(imagen)

print(f"Contenido de {raiz.nombre}: {raiz.listar_contenido()}")
print(f"Contenido de {documentos.nombre}: {documentos.listar_contenido()}")
print(f"Tamaño de {raiz.nombre}: {raiz.get_tamanio()} bytes")
print(f"Palabras en {texto.nombre}: {texto.contar_palabras()}")
print(f"Resolución de {imagen.nombre}: {imagen.get_resolucion()}")
```


---

Concepto de clases abstractas y métodos abstractos en Python, explorando sus características, usos y beneficios.

1. Clases Abstractas en Python:

Las clases abstractas son un concepto fundamental en la programación orientada a objetos que permite definir una interfaz común para un grupo de subclases relacionadas.

Características principales:
- No pueden ser instanciadas directamente.
- Pueden contener métodos abstractos y métodos concretos (implementados).
- Sirven como "contratos" para las subclases.

En Python, para crear una clase abstracta, se utiliza la clase `ABC` del módulo `abc`:

```python
from abc import ABC, abstractmethod

class MiClaseAbstracta(ABC):
    # ...
```

1. Métodos Abstractos:

Los métodos abstractos son métodos declarados en una clase abstracta pero sin implementación. Las subclases deben proporcionar una implementación para estos métodos.

Características:
- Se declaran usando el decorador `@abstractmethod`.
- No tienen cuerpo (o tienen `pass`).
- Fuerzan a las subclases a implementar estos métodos.

Ejemplo:

```python
class Animal(ABC):
    @abstractmethod
    def hacer_sonido(self):
        pass
```

1. Métodos Concretos en Clases Abstractas:

Las clases abstractas pueden tener métodos concretos (implementados) junto con métodos abstractos:

```python
class Animal(ABC):
    @abstractmethod
    def hacer_sonido(self):
        pass
    
    def dormir(self):
        print("Zzz...")
```

1. Herencia y Polimorfismo con Clases Abstractas:

Las clases abstractas son poderosas para implementar herencia y polimorfismo:

```python
class Perro(Animal):
    def hacer_sonido(self):
        return "Guau!"

class Gato(Animal):
    def hacer_sonido(self):
        return "Miau!"

def hacer_ruido(animal):
    print(animal.hacer_sonido())

perro = Perro()
gato = Gato()

hacer_ruido(perro)  # Imprime: Guau!
hacer_ruido(gato)   # Imprime: Miau!
```

1. Beneficios de las Clases Abstractas:

- Proporcionan una estructura común para clases relacionadas.
- Fuerzan la implementación de ciertos métodos en las subclases.
- Permiten escribir código más genérico y reutilizable.
- Facilitan el mantenimiento y la extensión del código.

1. Clases Abstractas vs Interfaces:

En algunos lenguajes, hay una distinción clara entre interfaces y clases abstractas. En Python, las clases abstractas pueden funcionar como ambas:

- Como interfaces: Cuando todos los métodos son abstractos.
- Como clases abstractas tradicionales: Cuando hay una mezcla de métodos abstractos y concretos.

1. Métodos Abstractos de Propiedad:

Python también permite definir propiedades abstractas:

```python
class Base(ABC):
    @property
    @abstractmethod
    def valor(self):
        pass
```

1. Verificación en Tiempo de Ejecución:

Python verifica la implementación de métodos abstractos en tiempo de ejecución, no en tiempo de compilación:

```python
class MiClase(Animal):
    pass  # No implementa hacer_sonido()

# Esto lanzará un TypeError al intentar instanciar MiClase
mi_objeto = MiClase()  # TypeError: Can't instantiate abstract class MiClase with abstract method hacer_sonido
```

Las clases abstractas y los métodos abstractos en Python proporcionan una forma poderosa de definir interfaces y estructuras comunes en la programación orientada a objetos. Permiten crear jerarquías de clases bien definidas y forzar la implementación de ciertos comportamientos en las subclases, lo que lleva a un código más robusto y mantenible.

¿Hay algún aspecto específico de las clases abstractas o métodos abstractos sobre el que te gustaría profundizar más?

# C++

Mirar programas ejemplo en VSCode

- **Conceptos random de clases**

	- `objeto.funcion(parametro)`
		- realmente tiene 2 parametros, el objeto y el parametro c.
	- `int Denominador() const;`
		- El const se refiere al parametro implícito, el propio objeto

- **Operation Overload

	- [c++ - What are the basic rules and idioms for operator overloading? - Stack Overflow](https://stackoverflow.com/questions/4421706/what-are-the-basic-rules-and-idioms-for-operator-overloading)

	- a += b;  a.Mas(b)
	- Nuevas posibles interpretaciones
		- operator+= (a, b)
		- a.operator+= (b)

	- flujo << a;
		- operator<<(flujo, a)
		- AUNQUE AHORA no tenemos lo siguiente, ya que no podemos acceder al objeto del flujo: flujo.operator<<(a)

- **PUNTEROS, memoria dinámica** ([Pointers](https://cplusplus.com/doc/tutorial/pointers/)), incrementos, new

	- BASICO

		- Es una variable que almacena una *dirección de memoria* de otra variable
		- Para ver la direccion de memoria de esta otra variable, usamos *&*
		- Se debe indicar el *tipo de dato* del dato al que apunta el puntero para poder "derreferenciarlo" cuando queremos acceder al valor que está en la dirección de memoria de este.
		- No confundir el *asterisco* que indica que es un puntero, con el asterisco para derreferenciar

		```cpp
		// CREAR Y ALMACENAR DIRECCIÓN DE MEMORIA
		`int x = 10; 
		int* ptr = &x;     // 0x6dfed4  
		
		// ACCEDER A EL VALOR DONDE ESTÁ EL PUNTERO (DERREFERENCE)
		int y = *ptr   // 10
		
		// CAMBIAR VALOR DEL PUNTERO
		*ptr = 12
		
		// SI EL PUNTERO ES UN OBJETO
		// Accedemos a un atributo del objeto con
		(*ptr).atributo
		ptr->atributo
		
		```

		- \*this es un caso concreto de puntero, que apunta a la dirección de memoria del objeto que lo invoca.

	- **SOLICITUD Y BORRADO DE MEMORIA DINÁMICA**
		- Se reserva cuando hace falta. No va asociado a ningún frame. Se tiene que liberar manualmente en el momento que corresponda.
		- Eficiente para estructuras de datos *tamaños variables*

		- Se solicita con `new`
		- Hay que indicar el tipo de dato
		- Devuelve un *puntero* al principio de la memoria que se asigna
		- Luego se inicializa el objeto.

		- Se libera con `delete`
		- Esto llama al *destructor* de la clase, que se escribirá con `~` delante del nombre de la clase.

		```cpp
		int* dynamicInt = new int;
		*dynamicInt = 42;
		
		delete dynamicInt;
		
		NodoStr *nuevo_nodo = new NodoStr(a, nullptr);
		```

	- *Fugas de memoria*:
		- Cuando se asigna memoria dinámica pero no se libera (usando delete)

	- INCREMENTO Y DECREMENTO
		 - `++ptr` o `ptr = ptr + 1` no tiene por que aumentar su valor en 1, depende de lo que ocupe el valor situado en el puntero. Simplemente va al siguiente elemento del mismo tipo

	- PUNTERO NULO
		- Los punteros pueden tomar el valor de cualquier dirección de memoria. El problema podría venir de intentar acceder al valor en esa dirección.
			- El `nullptr` o el `0` se encargan de hacer que el puntero no apunte a ningún sitio.

- **STRUCT**

	- Son como clases, pero sus miembros son públicos por defecto, a diferencia de las clases

- **SOBRECARGA**

	- multiple functions of different types are defined with the same name
	- mismo nombre (o símbolo) para llamar a funciones que se diferencian por su lista de parámetros (u operandos).

- **HERENCIA**

	- Tenemos clases y subclases
	- Las subclases tienen atributos en común, y pueden tener otros atributos más específicos

	- Una clase puede heredar de otra usando ":"
		- ``class Car: public Vehicle``
	- También puede heredar de varias, separandolas por ","
		- ``class Car: public Vehicle, public Object``

- **POLIMORFISMO**

	- *EJEMPLO CON PUNTEROS*:
		- Un puntero de el tipo padre (Shape), puede contener objetos de diferentes hijos (Circle/Square)
		- Al llamar a draw de este puntero, según lo que contenga llamará a la función draw de un objeto o del otro.
		```cpp
		Shape* shape1 = new Circle(); 
		Shape* shape2 = new Square(); 
		shape1->draw(); 
		shape2->draw();
		```

	- Condiciones necesarias.
		- Hacer virtual el método base.
	- Slicing: Copiar objeto derivado en el hueco del objeto base, se eliminaran los atributos y métodos de la clase hija, y se quedarán las del padre
		```cpp
		Dog rex;                     // Clase hija
		Animal pet = rex;            // Se sobreescribe, ahora es objeto de la clase padre
		```
