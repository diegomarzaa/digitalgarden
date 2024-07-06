---
{"dg-publish":true,"permalink":"/1-Referencias/Conceptos Adicionales C++/","title":"Conceptos Adicionales C++","noteIcon":""}
---


> [!abstract]+ CONTENIDO EXTRA:
>
> - [Cplusplus.com](https://cplusplus.com/)
> - *[Cppreference.com](https://en.cppreference.com/)*
>
> - [C++ Tutorial](https://www.w3schools.com/cpp/) en W3Schools
> - [The C++ Workshop](https://ebookcentral.proquest.com/lib/univjau1/detail.action?docID=6039456)
>
> - [OnlineGDB](https://www.onlinegdb.com/)
> - C++ en II17 (2010/2011): [introducción](https://aulavirtual.uji.es/pluginfile.php/6556898/mod_label/intro/Tema1-II17.pdf), [clases](https://aulavirtual.uji.es/pluginfile.php/6556898/mod_label/intro/Tema2-II17.pdf) y [herencia](https://aulavirtual.uji.es/pluginfile.php/6556898/mod_label/intro/Tema3-II17.pdf)
> - Git y GitHub en IR2113 (2022/2023): partes [primera](https://aulavirtual.uji.es/pluginfile.php/6556898/mod_label/intro/Git1-IR2113.pdf) y [segunda](https://aulavirtual.uji.es/pluginfile.php/6556898/mod_label/intro/Git2-IR2113.pdf)
> - [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
> - [Stack Overflow](https://stackoverflow.com/questions)
> - [The Kattis Problem Archive](https://open.kattis.com/)
>
> - CppUnit:
> 	- [CppUnit Cookbook](http://cppunit.sourceforge.net/doc/1.8.0/cppunit_cookbook.html)
> 	- [CppUnit Tutorial](http://www.evocomp.de/tutorials/tutorium_cppunit/howto_tutorial_cppunit_en.html)
> - [Test Smell Types](https://testsmells.org/pages/testsmells.html)
>
>
> ==[Learn C++ – Skill up with our free tutorials](https://www.learncpp.com/)==
> [Draft C++ Standard: Contents](https://eel.is/c++draft/)
> [Learn Contemporary C++ | Concise&Visual Examples | hacking C++](https://hackingcpp.com/)

# Debug code

[GDB online Debugger | Compiler - Code, Compile, Run, Debug online C, C++](https://www.onlinegdb.com/)

# Possible Errors, Warnings...

**POSIBLE ERRORS IN COMPILING**
https://www.learncpp.com/cpp-tutorial/compiling-your-first-program/
https://www.learncpp.com/cpp-tutorial/a-few-common-cpp-problems/

**Compiler Extensions**
https://www.learncpp.com/cpp-tutorial/configuring-your-compiler-compiler-extensions/
- many compilers implement their own changes to the language, often to enhance compatibility with other versions of the language.
- *Writing a program that makes use of a compiler extension allows you to write programs that are incompatible with the C++ standard*
- compiler extensions are often enabled by default.
- Disable compiler extensions to ensure your programs (and coding practices) remain compliant with C++ standards and will work on any system


**Compiler Warning and Error Levels**
https://www.learncpp.com/cpp-tutorial/configuring-your-compiler-warning-and-error-levels/
- Best practice: *Turn your warning levels up to the maximum*, especially while you are learning. It will help you identify possible issues
- Best practice: *Enable “Treat warnings as errors”*. This will force you to resolve all issues causing warnings.

# sizeof() + Size of Variables

The `sizeof()` operator returns the size of a variable or data type in bytes. For example:

```cpp
int x = 5;
std::cout << sizeof(x) << std::endl; // 4 bytes
```

Types of variables and their sizes:

short: 2 bytes
int: 4 bytes
long: 4 bytes
long long: 8 bytes
double: 8 bytes

# Signed Vs Unsigned

signed: can be positive or negative
unsigned: can only be positive

By default, integer types are signed.

![Pasted image 20230630002733.png](/img/user/_Archivos/Pasted%20image%2020230630002733.png)

# Integer Ranges and Limits

In C++, the range and limits of integer types depend on the size and signedness of the specific integer type. The standard library provides the ``<limits>`` header, which contains information about the limits of various types. Here are some commonly used integer types and their ranges:

```cpp
cout << INT_MIN << endl; // -2147483648
cout << INT_MAX << endl; // 2147483648
cout << LONG_MIN << endl; // -2147483648
cout << LONG_MAX << endl; // 2147483648
cout << SHRT_MIN << endl; // -32768
cout << SHRT_MAX << endl; // 32767
```

char:

char can be either signed or unsigned, depending on the compiler implementation.
If char is signed, its range typically goes from -128 to 127 (8 bits).
If char is unsigned, its range typically goes from 0 to 255 (8 bits).

short:

short is typically a signed integer type.
Its range is usually from -32,768 to 32,767 (16 bits).

int:

int is typically a signed integer type.
Its range is usually from -2,147,483,648 to 2,147,483,647 (32 bits).

long:

long is typically a signed integer type.
Its range is usually the same as int, from -2,147,483,648 to 2,147,483,647 (32 bits).
However, the exact size of long may vary depending on the platform. On some systems, long may have a larger size than int (e.g., 64 bits).

long long:

long long is typically a signed integer type.
Its range is usually from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 (64 bits).

unsigned types:

unsigned types are always non-negative and can represent a larger positive range than their signed counterparts.
For example, unsigned int has a range from 0 to 4,294,967,295 (32 bits).

# cin.ignore()

The cin.ignore() function can be used to ignore (skip) characters in the input buffer until a specified size or delimiter is reached.

# Extra Functions

- lenght() or size()
- getline()
	- read a line of text with multiple whitespaces, tabs...
	- cin only stores one word
- ``<cmath>``: sqrt, round, log...
	- max(x,y), min

## FUNCIONES

### CARACTERISTICAS

- Every C++ program must have a special function named **main**
- Functions that you write yourself are called;;; user-defined functions
<!--ID: 1691421002878-->
- Can you define functions inside other functions?;;; No
<!--ID: 1691421002887-->
- Como inicializar variable con el resultado de llamar a una funcion;;;  ``int num { funcion() };``
<!--ID: 1691421002895-->

**returnType** in functions
- *"void"* returnType in functions means;;; that no value will be returned
<!--ID: 1691420984818-->

- Returning a value from a void function will;;; cause a compile error
<!--ID: 1691420984826-->

**main**
- Your `main` function should return the ==value== {{0}} if the program ran normally.
- Make sure your functions with non-void return types ==return a value== in all cases. The only exception is ==main()==, that will implicitly return 0.

**Parámetros y Argumentos En Funciones**

Cómo se crea una función que recibe argumentos;;;
- ![Pasted image 20230728141829.png](/img/user/_Archivos/Pasted%20image%2020230728141829.png)
<!--ID: 1691420914608-->

Qué hacer cuando ya no se usa un parámetro dentro de una función;;;
- ![Pasted image 20230728142344.png](/img/user/_Archivos/Pasted%20image%2020230728142344.png)
<!--ID: 1691420914616-->

![2023-09-16_12-36-01_default_parameter.png](/img/user/_Archivos/2023-09-16_12-36-01_default_parameter.png)

**Paso por referencia**

![2023-09-16_12-37-44_.png](/img/user/_Archivos/2023-09-16_12-37-44_.png)

**Function overloading**

![2023-09-16_12-38-48_function_overload.png](/img/user/_Archivos/2023-09-16_12-38-48_function_overload.png)

### EJEMPLOS

```cpp
#include <iostream>   // for std::cout

int main()
{
   std::cout << "Hello" << " world!";   // Print to console
   return 0;
}
```

```cpp
#include <iostream>

// less-bad version
int main()
{
	std::cout << "Enter an integer: ";

	int num{ };
	std::cin >> num;
	
	std::cout << "Double that number is: " << num * 2 << '\n'; // then print the value
	return 0;
}
```

```cpp  
#include <iostream> // for std::cout

// Definition of user-defined function doPrint()
void doPrint() // doPrint() is the called function in this example
{
    std::cout << "In doPrint()\n";
}

// Definition of function main()
int main()
{
    std::cout << "Starting main()\n";
    doPrint(); // Interrupt main() by making a function call to doPrint().  main() is the caller.
    std::cout << "Ending main()\n"; // this statement is executed after doPrint() ends

    return 0;
}
```

```cpp
#include <iostream>

// Función para calcular el factorial
int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

int main() {
    int num;

    std::cout << "Ingrese un número: ";
    std::cin >> num;

    // Validar si el número es negativo
    if (num < 0) {
        std::cout << "El número debe ser no negativo." << std::endl;
        return 0; // Salir del programa
    }

    int result = factorial(num);

    std::cout << "El factorial de " << num << " es: " << result << std::endl;

   return 0;
}
```
