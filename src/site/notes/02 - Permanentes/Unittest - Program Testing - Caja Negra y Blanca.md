---
{"dg-publish":true,"permalink":"/02 - Permanentes/Unittest - Program Testing - Caja Negra y Blanca/","title":"Unittest - Program Testing - Caja Negra y Blanca","noteIcon":""}
---


Relacionados:
[[02 - Permanentes/Captura y tratamiento de excepciones\|Captura y tratamiento de excepciones]]

# Lo esencial

- Si el programa de pruebas está mal, es que la tabla de casos y escenarios deben ser corregidas.

# Python

- 3 formas para hacer las pruebas unittest:
	- Como script:
		- "python3 -m unittest fichero.py"
			- La opción -m permite ejecutar un **módulo como un script**
			- Es mejor ejecutar el módulo de pruebas como un script, en lugar de importarlo como un módulo, ya que así no se importa si no lo usamos

	- Para ejecutar directamente desde el módulo
		- "python3 fichero.py"
			- import unittest
			- if **name** == '**main**':
					unittest.main()

	- Buscando pruebas en el directorio actual
	- "python3 -m unittest discover"
		- Busca todos los ficheros que empiecen por test_ o que terminen por _test.py
		- Busca todas las clases que empiecen por Test
		- Busca todos los métodos que empiecen por test

- El fichero de pruebas debe empezar por test_ o terminar por _test.py
- Hay que importar el módulo unittest


``` python
import unittest  


# FUNCION A PROBAR
def suma(a,b):  
    return a + b  
  

# Comprobación  
# This gives us a lot of methods to test our code in this class  
class TestSuma(unittest.TestCase):  
  
    # En setUp se inicializan las variables que se van a utilizar en las pruebas, ayuda a no repetir código en cada prueba  
    # Es necesario usar self para que las variables sean accesibles desde cualquier método    
    def setUp(self):  
        self.suma_elem = ((1, 2, 3), (2, 3, 5), (3, 4, 8), ("a", "b", "ab"))  
        print("Set Up ejecutando")  


    # Aquí se ponen las pruebas, cada test es una funcion  
    # IMPORTANTE: Cada prueba debe empezar con test_    
    def test_suma(self):  
        for (elem1, elem2, val) in self.suma_elem:  
            self.assertEqual(suma(elem1, elem2), val)  
        print("Funciona")  


    # Este se invocará después de cada prueba    
    def tearDown(self):  
        self.suma_elem = None  
        print("Tear Down ejecutando")  
  
if __name__ == "__main__":  
    unittest.main(argv=['first-arg-is-ignored'], exit=False)
```

``` python
# *IMPORTANTE: Cada prueba debe empezar con test*  
  

# Tipos de assert:  
  
assertEqual(a, b) a == b  
assertNotEqual(a, b) a != b  
assertTrue(x) bool(x) is True  
assertFalse(x) bool(x) is False  
assertIs(a, b) a is b  
assertIsNot(a, b) a is not b  
assertIsNone(x) x is None  
assertIsNotNone(x) x is not None  
assertIn(a, b) a in b  
assertNotIn(a, b) a not in b  
assertRaises(ValueError, function, argument1, argument2)  
  
assertAlmostEqual(a, b) round(a-b, 7) == 0  
assertNotAlmostEqual(a, b) round(a-b, 7) != 0  
assertGreater(a, b) a > b  
assertGreaterEqual(a, b) a >= b  
assertLess(a, b) a < b  
assertLessEqual(a, b) a <= b  
  
```

# C++

- CPPUNIT
	- Clase y programa en un fichero
	- Agrupar pruebas en clase TestFixture con TestSuite
	- No es necesario usar un método de prueba distinto para cada caso de prueba si hay muchos.
	- Lanzador con salida por consola
	- `g++ AAA_test.o AAA.o -lcppunit -o AAA_test`

- OBJETIVOS
	- Pruebas de Unidad: Funciones o clases
	- Un programador debe evitar probar su propio programa
	- Prever condiciones inválidas
	- Evita improvisar los casos de prueba
	- El estado mental correcto es asumir que habrá errores.

	- Técnica FIRST:
		- Fast (rápido): Ejecución frecuente de los tests
		- Independent (independiente): El orden de los tests no debe de afectar al resultado
		- Repeatable (repetible): Independiente del servidor, configuración...
		- Self-validating (auto evaluable): Booleano como resultado, no debemos comprobar el resultado de los tests de forma manual.
		- Timely (oportuno): Hacer las pruebas antes de desarrollar el programa

## Caja negra

- Comprobar el comportamiento sin conocer su implementación interna (Resultados externos)
- Sirven para definir un conjunto de ESCENARIOS

```cpp
 1    int f(int a, int b) {
 2        if (a > 10) {            // D1
 3            a += 10;
 4        }
 
 5        if (a > 2 and b > 2) {   // D2 (D2.1 y D2.2)
 6            return a * b;
 7        } else {
 8            return a + b;
 9        }
10    }
```

- **TABLA DE ESCENARIOS**

	- Situaciones generales donde queremos probar el programa.
	- Un escenario es inválido si no se cumplen las precondiciones.
	- Los escenarios pueden estar en funcion de 1 entrada, relaciones de varias entrada, o de salida.
	- No todo escenario va a acabar convirtiéndose en una prueba específica.

	- Posibles escenarios:
		- Equilatero, Isosceles, Escaleno, No es un triangulo
		- La decisión del if de la línea 10 del método llega a tomar el valor false

	- *Planteamiento de escenarios*
		- escenarios basados en las entradas
			- En números, negativos, 0, positivos
		- escenarios basados en las relaciones entre las diferentes entradas
			- a > b+c
		- escenarios basados en las posibles salidas
		- escenarios basados en la relación entre entradas y salidas

	- *Escenarios inválidos vs válidos*
		- Cada escenario inválido ha de ser cubierto con un caso de prueba específico que no cubra ningún otro escenario inválido
		- En escenarios válidos, cubrir cuantos más mejor

	- Prefijos
		- V o I según valido o invalido

	- TABLA ESCENARIOS EJEMPLO
		- ![2023-10-13_16-12-00_escenarios_tabla.png](/img/user/_Archivos/2023-10-13_16-12-00_escenarios_tabla.png)

- **TABLA DE CASOS**
	- ![2023-10-13_16-02-46_casosprueba.png](/img/user/_Archivos/2023-10-13_16-02-46_casosprueba.png)
	- Casos concretos (*completamente especificados*) usados para comprobar el programa.
		- a = 7,    b = 8,    salida true
	- Con pocos casos de prueba cubrimos muchos escenarios.
	- Se puede dividir la entrada en subcolumnas

## Caja blanca

- DEFINICIÓN Y CONCEPTOS
	- A diferencia de la caja negra, aquí nos dejamos guiar por el código que queremos probar. Prueban la estructura interna y la lógica de un código, sabiendo como funciona por dentro.
	- No tenemos en cuenta codigos validos o invalidos, simplemente queremos probar todo el codigo.
	- Deberemos hacer *diferentes casos de prueba para que se cubran todas las posibles coberturas*

- POSIBLES COBERTURAS:      `c1 or (c2 and c3)`
	- Cobertura de sentencias
		- Todas cubiertas al menos una vez
		- Ejemplo, un if sin else, o se cubre la sentencia o no se cubre
	- Escenarios de cobertura de *decisiones*
		- (un test que cubra ejemplos para todos los "if" por ejemplo *al menos una vez con true y false*)
		- Ignoramos la complejidad y los operadores lógicos, solo nos importa true o false.
		- D1T, D2F
	- Cobertura de *condiciones*
		- Son los elementos más pequeños, unidos con "or", "and"...
		- D1.1F, D1.2T, D1.3T, D1.3F...
		- C1T, C1F, C2T, C2F, C3T, C3F
		- 2^n escenarios para n condiciones
	- Cobertura de *condición múltiple*
		- Tablas de verdad para cada decisión.
		- D1TXX, D1FTT, D1FTF, D1FFX
		- C++ es en *circuito corto*, por lo que a veces es inutil seguir comprobando si ya se cumple.



- *CAJA BLANCA EJEMPLO*:
	```cpp
	int CountNumbers(const std::string& s) {
		int n = 0;
		bool out_before = true;
		for (int i = 0; i < s.length(); ++i) {
			if (s.at(i) >= '0' and s[i] <= '9') { // now in a number
				if (out_before) {
					++n;
					out_before = false;
				}
			} else {
				out_before = true;
			}
		}
		return n;
	}
	```


	- **TABLA DE DECISIONES**
		![2023-10-27_20-20-11_.png|409](/img/user/_Archivos/2023-10-27_20-20-11_.png)
		- Error: `1 < s.length()` es` i < s.length()`
		- *Decisión*: todo lo de dentro de un if
		- *Escenarios*: (T/F) para cada decisión
		- Al hablar de un escenario concreto (Como D1F) queremos decir las situaciones en las que al ejecutar el programa se cumplirá ese escenario concreto al menos una vez. D1F -> siempre, indica que en la ejecución del programa, independentemente de cadena introducida, siempre se llegará a cumplir. En este programa se debe a que el bucle for va decrementando la i (la foto está mal es una i en lugar de 1)

	- **TABLA DE CASOS**
		![2023-10-27_20-19-01_.png|380](/img/user/_Archivos/2023-10-27_20-19-01_.png)
		- Con un solo caso cubrimos los 6 escenarios. Con esto queremos decir que al ejecutar el programa con el input "x44y9", se pasará por todos los tipos escenarios posibles para las diferentes sentencias if, while... Comprobando así la seguridad del código al no dejar nada por revisar.


	- **TABLA DE ESCENARIOS ---- COBERTURA DE CONDICIÓN MULTIPLE**
		![2023-10-27_20-18-16_.png|557](/img/user/_Archivos/2023-10-27_20-18-16_.png)
		- Todo lo de la tabla de decisiones anterior, pero ahora viendo cada *condición* concreta por separado.
		- *Decisiones iguales en diferentes puntos* han de ser tratadas (x>10)

	- **TABLA DE CASOS  -----  COBERTURA DE CONDICIÓN MULTIPLE**
		![2023-10-27_20-18-43_.png](/img/user/_Archivos/2023-10-27_20-18-43_.png)
		- Igual que la normal pero ahora según los nuevos escenarios, más posibilidades
		- Datos:
			- / esta por debajo del 0
			- : esta por encima del 9
