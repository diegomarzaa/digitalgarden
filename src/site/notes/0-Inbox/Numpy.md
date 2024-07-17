---
{"dg-publish":true,"permalink":"/0-Inbox/Numpy/","title":"Numpy","noteIcon":""}
---


- **PENDIENTE**: MEJORAR Y APRENDER MEJOR

![[Numpy introduction.pdf]]


- **Numpy: La base de ciencia de datos y bibliotecas ML en Python**
		- Juega un papel crucial en el ecosistema de Python para ciencia de datos, proporcionando la infraestructura fundamental para manipular datos y realizar cálculos numéricos complejos de forma eficiente.
		- Soporte para librerías como Pandas, Scikit-learn, TensorFlow, Torch y SciPy.
- **Conceptos Principales de Numpy**
		- **Clases, constantes y funciones** para manipular arrays numéricos contiguos.
				- `import numpy as np`
		- **Array:** objeto que contiene el array contiguo y operaciones básicas.
				- `v = np.array([1.0, 2.0, 3.0])`
		- **Operadores matemáticos básicos sobrecargados.**
				- `v2 = v + np.ones((1, 3))`
		- **Constructores de array:** `np.ones(shape)`, `np.zeros(shape)`, `np.full(shape, val)`, `np.eye(N)`.
- **Slicing y Broadcasting**
		- **Slicing en Numpy**: Permite extraer secciones de un array para obtener un nuevo array.
		- **Estructura básica**: `a[start:end:step]`
			- **start:** Indica el índice del primer elemento del subconjunto que queremos seleccionar. Si se omite, se asume que es el inicio del array (índice 0).
			- **end:** Representa el índice del elemento donde termina el subconjunto. Este elemento **no** se incluye en el subconjunto resultante. Si se omite, se asume que es el final del array.
			- **step:** Especifica el paso, o intervalo, entre los elementos seleccionados del subconjunto. Por ejemplo, un `step` de 2 seleccionará cada segundo elemento del rango definido por `start` y `end`. Si se omite, se asume que el paso es 1, seleccionando así todos los elementos en el rango.
		- **Uso de slicing**:
				- Para seleccionar un rango en un array unidimensional: `a[1:5]`.
				- Extraer elementos con un salto específico: `a[0:6:2]`.
				- Seleccionar elementos hasta un índice específico: `a[:5]`.
				- Seleccionar elementos desde un índice hasta el final: `a[2:]`.
				- Invertir un array: `a[::-1]`.
		- **Slicing en arrays multidimensionales**:
				- Se puede aplicar slicing en cada dimensión: `a[0:2, 1:4]`.
						- En este caso, se seleccionan filas de 0 a 1 y columnas de 1 a 3.
				- Seleccionar una columna completa: `a[:, 1]`.
				- Seleccionar una fila completa: `a[1,:]`.
		- **Slicing con índices negativos**:
				- Python permite índices negativos, lo que se interpreta como una selección desde el final. Ejemplo: `a[-3:-1]`.
		- **Uso de arrays de índices para slicear**:
				- `a[:, np.array([0, 2])]`: selecciona todas las filas y las columnas en los índices 0 y 2.
				- `a[np.newaxis,:]`: agrega una nueva dimensión.
		- **Asignación con slicing**:
				- Se pueden modificar secciones de un array usando slicing en la asignación: `a[0:2] = np.array([3, 2])`.

	- **Broadcasting en Numpy**: Facilita operaciones entre arrays de diferentes tamaños o shapes, ajustando automáticamente sus dimensiones para que coincidan.
		- **Reglas básicas**:
				- Las dimensiones de los arrays se comparan elemento a elemento, empezando por la dimensión más a la derecha (última).
				- Dos dimensiones son compatibles para el broadcasting si:
						- Son iguales,
						- Una de ellas es 1.
		- **Aplicación**:
				- Si los arrays no tienen el mismo número de dimensiones, el shape del array de menor dimensión se "rellena" con 1 en su lado izquierdo.
				- Si el shape de los dos arrays no coincide en alguna dimensión, el array con shape igual a 1 en esa dimensión se estira para coincidir con el otro shape.
				- El estiramiento implica replicar el contenido del array a lo largo de la dimensión en la que tiene tamaño 1.
		- **Ejemplos**:
				- **Suma de un vector y un escalar**: `v = np.array([1, 2, 3]); s = 4; result = v + s;`
						- Aquí, `s` se "broadcastea" a `[4, 4, 4]` y se suma a `v`.
				- **Suma entre una matriz 2D y un vector 1D**:
						- `a = np.array([[1, 2], [3, 4]]); v = np.array([10, 20]); result = a + v;`
						- `v` se "broadcastea" a un array 2D `[[10, 20], [10, 20]]` para que coincida con `a`.
		- **Ventajas**:
				- Elimina la necesidad de duplicar datos, lo que resulta en operaciones más eficientes en términos de memoria.
				- Simplifica código al evitar bucles explícitos para operaciones elementales.

- **Reshaping y Ordenamiento**
		- **Reshape:** Cambia la forma manteniendo el total de elementos. `a.reshape((3,2))`
		- **Flatten:** Aplana un array. `a.flatten()`
		- **Sort:** Organiza elementos. `np.sort(a, axis=0)`
- **Indexación Booleana**
		- Filtrar datos con condiciones booleanas. `a[filter_pos]`
- **Comparando Arrays**
		- Usa `a == b` para comparación elemento a elemento o `np.equal_array(a, b)` para comparar forma y contenido.
- **Funciones Principales de Numpy**
		- Constantes: `np.nan`, `np.Infinity`, `np.pi`, `np.e`.
		- Agregaciones: `np.sum(a, axis=0)`.
		- Estadísticas: `np.min`, `np.max`, `np.mean`, `np.median`, `np.argmin`, `np.argmax`, `np.prod`, `np.std`, `np.var`, `np.corrcoef`.
		- Operaciones: Producto punto `np.dot`, transpuesta `A.T`, chequeo de NaN `np.isnan`.
- **Numpy y Álgebra Lineal**
		- **numpy.linalg:** funciones para realizar operaciones básicas de álgebra lineal como determinantes, inversas de matrices, productos de matrices, valores propios, normalización y solución de ecuaciones.
