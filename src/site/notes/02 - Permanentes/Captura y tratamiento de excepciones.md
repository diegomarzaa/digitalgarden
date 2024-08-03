---
{"dg-publish":true,"permalink":"/02 - Permanentes/Captura y tratamiento de excepciones/","title":"Captura y tratamiento de excepciones","noteIcon":""}
---

Relacionados:
[[02 - Permanentes/Unittest - Program Testing - Caja Negra y Blanca\|Unittest - Program Testing - Caja Negra y Blanca]]

# Tipos de excepciones:

- Exception: Excepción genérica
- TypeError: Error de tipo, por ejemplo, al sumar un int y un str
- ValueError: Error de valor, por ejemplo, al pasar un valor no válido a una función
- IndexError: Error de índice, por ejemplo, al acceder a un elemento de una lista que no existe
- KeyError: Error de clave, por ejemplo, al acceder a un elemento de un diccionario que no existe
- NameError: Error de nombre, por ejemplo, al acceder a una variable que no existe
- ZeroDivisionError: Error de división por cero
- FileNotFoundError: Error de fichero no encontrado
- AttributeError: Error de atributo, por ejemplo, al acceder a un atributo de un objeto que no existe
- IOError: Error de entrada/salida
- RuntimeError: Error de ejecución.

# Python

```python
try:
    # Código que puede generar una excepción
    result = 10 / 0
except ZeroDivisionError:
    # Manejo de la excepción
    print("No se puede dividir por cero.")
except (ValueError, ZeroDivisionError) as e:
	print(f"Error: {e}")
else:
    # Si no ocurre ninguna excepción
    print("La división fue exitosa.")
finally:
    # Siempre se ejecuta
    print("Finalización del bloque try-except.")
```

- El contexto de excepciones (`__context__` y `__cause__`) permite rastrear excepciones encadenadas.

- Puedes volver a lanzar una excepción capturada utilizando `raise`.

- Excepciones propias
	```python
		class CustomError(Exception):
		    pass
		
		try:     
			raise CustomError("Un error personalizado.")
		except CustomError as e:     
			print(f"Caught custom exception: {e}")`
	```

# C++

- Igual pero en lugar de except, poner catch
- Usando noexcept se puede especificar que una funcion no lance excepciones.

	```c++
	try {
	    // Código que podría lanzar una excepción
	} catch (const std::runtime_error& e) {
	    // Manejar excepción de std::runtime_error
	} catch (const std::exception& e) {
	    // Manejar excepción genérica de std::exception
	}
	
	```

- LANZAR
	- `throw std::invalid_argument("elements is empty");`

- UNITTEST
	- `CPPUNIT_ASSERT_THROW(funcion(), std::invalid_argument)`

```cpp
#include <iostream>
#include <exception>

class CustomException : public std::exception {
public:
    const char* what() const noexcept override {
        return "Excepción personalizada.";
    }
};

int main() {
    try {
        throw CustomException();
    } catch (const CustomException &e) {
        std::cerr << "Capturada excepción personalizada: " << e.what() << std::endl;
    }
    return 0;
}

```
