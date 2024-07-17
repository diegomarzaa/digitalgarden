---
{"dg-publish":true,"permalink":"/0-Inbox/Punteros y memoria dinámica/","title":"Punteros y memoria dinámica","noteIcon":""}
---


- **PENDIENTE: MEJORAR**

---

- ARRAYS DE C Y PUNTEROS / MEMORIA DINÁMICA
	- `int foo [20];`    // Talla fija de tipo int
	- `int* foo = new int[5];`
		- Returns a pointer to the first element.
		- The first element can be accessed with `foo[0]` or  `*foo`
		- The second, with `foo[1]` or `*(foo+1)`

- `delete[] pointer;`
	- releases the memory allocated for arrays of elements using new and a size

```cpp  file:"Ejemplo Aritmétrica Punteros" hl:9
char *mychar;    // Memoria 1000
short *myshort;  // Memoria 2000
long *mylong;    // Memoria 3000

++mychar;    // +1
++myshort;   // +2
++mylong;    // +4

// Esto se debe a que sumar uno a un puntero se hace segun el tamaño del tipo de dato que contiene cada puntero. No tendría sentido sumar siempre 1 a la dirección de memoria.

// También se puede usar --
// También se pueden usar otros números a sumar o restar



*p++   // same as *(p++): increment pointer, and dereference unincremented address
*++p   // same as *(++p): increment pointer, and dereference incremented address
++*p   // same as ++(*p): dereference pointer, and increment the value it points to
(*p)++ // dereference pointer, and post-increment the value it points to 
```

- **copy and swap**
	- en c++, al hacer a=b, esperamos que `a` y `b` sigan vidas independientes
	- intercambia el contenido de dos objetos sin necesidad de copiar sus datos
	```cpp warn:2
	ListaSimple& ListaSimple::operator=(const ListaSimple& otra) {
		if (&otra != this) {
			//(this != &otra): Si hacen referencia exactamente al mismo objeto, en la misma posición de memoria, simplemente devolverlo

			// - Esto evita autoasignación, como vector1 = vector1, cosa que daría error al borrar los datos y luego intentar acceder a ellos.

			// - Lo que no evita es hacer vector1 = vector2, vector1 = vector2, vector1 = vector2...
			ListaSimple copia(otra);
			std::swap(ini_, copia.ini_);
			std::swap(fin_, copia.fin_);
			std::swap(talla_, copia.talla_);
			// ahora el objeto actual (`*this`) contiene los datos de la copia,
			// y la copia contiene los datos originales del objeto actual
		}
	// Al salir del if, se destruye automatico el objeto copia
	// con los contenidos del antiguo this
	return *this;
	}
	```
