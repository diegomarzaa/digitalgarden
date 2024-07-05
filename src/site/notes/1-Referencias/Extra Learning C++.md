---
{"dg-publish":true,"permalink":"/1-Referencias/Extra Learning C++/","title":"Extra Learning C++","noteIcon":""}
---

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

# Extra

## Introduction

C++ es un lenguaje de programación de alto nivel que se utiliza para desarrollar aplicaciones de software. Es una extensión del lenguaje de programación C y agrega características como la programación orientada a objetos y la manipulación de memoria. C++ es ampliamente utilizado en la industria del software debido a su eficiencia y capacidad para crear programas de alto rendimiento.

Four major updates to the C++ language (C++11, C++14, C++17, and C++20)
- C++11 is typically considered the modern minimum
- Finalized language standards are named after the years in which they are finalized (e.g. C++17 was finalized in 2017).

"Trust the programmer":
C++ is designed to allow the programmer a high degree of freedom to do what they want. However, this also means the language often won’t stop you from doing things that don’t make sense, because it will assume you’re doing so for some reason it doesn’t understand.

**Puntos Positivos C++**

- excels in situations where high performance and precise control over memory and other resources is needed

**Good Practise**

When you sit down and start coding right away, you’re typically thinking “I want to do something”, so you implement the solution that gets you there the fastest. This can lead to *programs that are fragile*, hard to change or extend later, or have lots of bugs (technical defects).
*it’s worth your time to spend a little extra time up front* (before you start coding) thinking about the best way to tackle a problem, what assumptions you are making, and how you might plan for the future, in order to save yourself a lot of time and trouble down the road.


**STATEMENTS**
- they are the smallest independent unit of computation in the C++ language
- they act much like sentences do in natural language
- Most end in a semicolon (;)
- ![Pasted image 20230718204415.png](/img/user/_Archivos/Pasted%20image%2020230718204415.png)

## IDEs y Instalación

### Instalación

[C++ programming with Visual Studio Code](https://code.visualstudio.com/docs/languages/cpp#_example-install-mingwx64)
[MSYS2](https://www.msys2.org/)

### Otros

==setup correctly (linux too): https://www.learncpp.com/cpp-tutorial/installing-an-integrated-development-environment-ide/)==

Programs that are easily portable to LInux: [Code::Blocks](https://www.codeblocks.org/downloads/binaries/)

### Running Program

VSCode
- *g++ build and debug active file*  (En linux al instalar VSCode ya me venía por defecto)

TERMINAL LINUX
`g++ -o NombreEjecutableCustom NombreFichero.cpp`
`./NombreEjecutableCustom`

### Configuring Compiler (build configurations)

https://www.learncpp.com/cpp-tutorial/configuring-your-compiler-build-configurations/

## FUNCIONES

### CARACTERISTICAS

- Every C++ program must have a special function named **main**
- Functions that you write yourself are called ;;; user-defined functions
<!--ID: 1691421002878-->
- Can you define functions inside other functions? ;;; No
<!--ID: 1691421002887-->
- Como inicializar variable con el resultado de llamar a una funcion ;;;  ``int num { funcion() };``
<!--ID: 1691421002895-->

**returnType** in functions
- *"void"* returnType in functions means ;;; that no value will be returned
<!--ID: 1691420984818-->

- Returning a value from a void function will ;;; cause a compile error
<!--ID: 1691420984826-->

**main**
- Your `main` function should return the ==value== {{0}} if the program ran normally.
- Make sure your functions with non-void return types ==return a value== in all cases. The only exception is ==main()==, that will implicitly return 0.

**Parámetros y Argumentos En Funciones**

Cómo se crea una función que recibe argumentos ;;;
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

## Variables + Types of Data

### Instantiation

- A variable is a named *object*
- Variables are used to access memory.
- Variables have an *identifier* (name), a *type*, and a *value*
{ #73bxc6}

- the variable will be *instantiated* when the program is run (called runtime)
    - Instantiation means the object will be created and assigned a memory address

```cpp
// VARIABLE INITIALIZATION
int x; // define a variable named x, of type int
int a, b;  // define multiple variables 
int a; double b; // correct (but not recommended)
```

```cpp
// WRONG:
int a, int b;
int a, double b;
```

- *List initialization* produces an error when initializing a variable with a wrong type (useful)

```cpp
// VARIABLE ASSIGMENT AND INITIALIZATION

int width; // define an integer variable named width
width = 5; // copy assignment of value 5 into variable width

int b = 5;     // initializer after equals sign (copy initialization)

int c( 6 );    // initializer in parenthesis (direct initialization)

// List initialization methods (C++11) (preferred)
int d { 7 };   // initializer in braces (direct list initialization)
int e = { 8 }; // initializer in braces after equals sign (copy list initialization)
int f {};      // initializer is empty braces (value initialization)
```

- *Initialization* gives a variable an initial value at the point when it is created.
- *Assignment* gives a variable a value at some point after the variable is created

- *Default initialization* is when a variable initialization has no initializer (e.g. `int x;`). In most cases, the variable is left with an indeterminate value.
- *Value initialization* is when a variable initialization has an empty brace (e.g. `int x{};`). In most cases this will perform zero-initialization.
- *You should prefer value initialization* to default initialization

```cpp
// MULTIPLE INITIALIZATION
int a = 5, b = 6;          // copy initialization
int c( 7 ), d( 8 );        // direct initialization
int e { 9 }, f { 10 };     // direct brace initialization (preferred)
int g = { 9 }, h = { 10 }; // copy brace initialization
int i {}, j {};            // value initialization

// WRONG
int a, b = 5; // wrong (a is not initialized!)
int a, b( 5 );
```

*Value Initialization and Zero Initialization { 0 } Vs {}*

Use an explicit initialization value if you’re actually using that value.

```cpp
int x { 0 };    // explicit initialization to value 0
std::cout << x; // we're using that zero value
```

Use value initialization if the value is temporary and will be replaced.

```cpp
int x {};      // value initialization
std::cin >> x; // we're immediately replacing that value
```

### Types of Data

- A data type (more commonly just called a type) tells the compiler what type of value (e.g. a number, a letter, text, etc…) the variable will store.
- C++ also allows you to *create your own* user-defined types

- ![2023-09-16_12-09-37_datatypes.png](/img/user/_Archivos/2023-09-16_12-09-37_datatypes.png)
- char: Surround with single quotes
- *==String==*:
	- Text, double quotes
	- Use import ``<string>`` library
	- Can use + to concatenate. Or *append()* function
	- Can access or modify certain characters using string[n] (python)  or *string[n] = 'm'*
	- auto: automatically detect the type of variable
- null pointer
- void: no storage, absence of value (None in python)
- ==const==: read-only

Creating variables:

```cpp
int x = 5;
int y(3);
int z{2};
float pi = 3.1416;
float cash = 2;
char a = 'a';
bool is_true = true;
auto check = false;

```

### 🔜 Paso Por Referencia

```cpp
int numero = 30;
int &refNumero = numero;  // refNumero es una referencia a numero

refNumero = 40;  // Modificar refNumero también modifica numero
```

## ✅ Operadores, Logicos, Operaciones...

- Igual que python
- Orden: Parenthesis first, then Exponents, then Multiplication & Division, then Addition & Subtraction
- ==++ y --: Increment, decrement==
- ==+=: Add a value to a variable==

```cpp	
cout << 5 + 2 << endl; // 7
```

**Logical Operators**

![2023-09-16_12-18-16_logical.png](/img/user/_Archivos/2023-09-16_12-18-16_logical.png)

``&&``, ``||``

![2023-09-16_12-19-07_and_or_not.png](/img/user/_Archivos/2023-09-16_12-19-07_and_or_not.png)

```cpp
cout << (5 == 5) << endl; // 1 
string y;
getline(cin, y);
return 0;
```

## 🔜 CONTROL FLOW: IF, WHILE, FOR, BREAK

[4.10 -- Introduction to if statements](https://www.learncpp.com/cpp-tutorial/introduction-to-if-statements/) y [Control flow introduction](https://www.learncpp.com/cpp-tutorial/control-flow-introduction/)

### Break, Return, Continue

- break: jump out of loop
- Continue: Going to the next iteration

### If, Else If, Else

- Ejemplo

```cpp
if (x > y)
	std::cout << "Una instrucción puede ponerse sin {}";
else if (x == y)
{
	// etc
}
else
{ // note addition of block here
	std::cout << "You are not tall enough to ride.\n";
	std::cout << "Too bad!\n";
}

if (x > 10)
    ; // this is a null statement
```

### Switch

- Bloques if-else muy optimizados
- Condición debe ser un {; numero unico}
<!--ID: 1697966755439-->

- El default se ejecuta si ninguno coincide
- Es importante usar break o return
```cpp
switch (x) // x is evaluated
	{
		case 1:
			std::cout << "One";
			return;
		case 2:
			std::cout << "Two";
			return;
		case 3:
			std::cout << "Three";
			break;
		default:
			std::cout << "Unknown";
			break;
	}
```
<!--ID: 1694803705796-->

==MIRAR MÁS==: [8.6 — Switch fallthrough and scoping – Learn C++](https://www.learncpp.com/cpp-tutorial/switch-fallthrough-and-scoping/)

### Goto

- Used for jumping to a labeled statement in the same function.
- Avoid using it as much as possible (use for, while, do-while)
```c++
#include <iostream>

int main() {
    int x = 0;

    start: // Label
    x++;

    if (x < 5) {
        goto start; // Jump back to the label
    }

    std::cout << "x is " << x << std::endl;

    return 0;
}

```

### For

- The end-expression is evaluated the last in the loop
``` c++
for (init-statement; condition; end-expression)
   {
   statements;
   }
```
- For loops with multiple counter
```c++
#include <iostream>

int main()
{
    for (int x{ 0 }, y{ 9 };    x < 10;    ++x, --y)
        std::cout << x << ' ' << y << '\n';
    return 0;
}
```
- Loop through elements in a list:
```c++
int myNumbers[5] = {10, 20, 30, 40, 50};  
for (int i : myNumbers) {  
  cout << i << "\n";  
}
```

### While

- You can exit infinite loops with return, break, exit, goto
``` c++
#include <iostream>

int main() 
{
    int x = 0;
    // Mientras x menor que 5, sumar 1 a x:
    while (x < 5) {
        x++;
    }
    std::cout << "x is " << x << std::endl;
    return 0;
}
```

### Do-while

- *Executes the code block once before checking conditions*
- Effective for reducing complexity
- Use it as less as possible.
- For showing a menu for example and then asking repeatedly for a number

```c++
#include <iostream>

int main()
{
    // selection must be declared outside of the do-while-loop
    int selection{};

    do
    {
        std::cout << "Please make a selection: \n";
        std::cout << "1) Addition\n";
        std::cout << "2) Subtraction\n";
        std::cin >> selection;
    }
    while (selection != 1 && selection != 2);
}
```
