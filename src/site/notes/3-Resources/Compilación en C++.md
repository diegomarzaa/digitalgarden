---
{"dg-publish":true,"permalink":"/3-Resources/Compilación en C++/","title":"Compilación en C++","noteIcon":""}
---


C++ es un lenguaje compilado, ver más sobre esto aquí: [[3-Resources/Compilador y intérprete\|Compilador y intérprete]]

# Aspectos básicos e instalación

- Es necesario compilar el codigo fuente en codigo maquina
- g++ es el compilador, lo convierte en un fichero ejecutable.
- Diferencias: python mas lento pero facil de escribir. C++ permite hacer operaciones de bajo nivel, es más eficiente (espacio y tiempo), código preciso para ciertas acciones.
	- Python te ahorraba tener que indicar el tipo de variable.
- En qué convierte el compilador un codigo fuente?
	- En archivos de objeto llamados tipicamente *nombre.o* o nombre.obj.
	- En binario, leíble por la compu

- **INSTALACIÓN**
	- [C++ programming with Visual Studio Code](https://code.visualstudio.com/docs/languages/cpp#_example-install-mingwx64)
	- [MSYS2](https://www.msys2.org/)
	- setup correctly (linux too): https://www.learncpp.com/cpp-tutorial/installing-an-integrated-development-environment-ide/)
	- Programs that are easily portable to LInux: https://www.codeblocks.org/downloads/binaries/

- **CONFIGURAR COMPILADOR**
	- https://www.learncpp.com/cpp-tutorial/configuring-your-compiler-build-configurations/

- **FORMAS DE COMPILAR**;
	- 1)  Directamente en exe
		- ``g++ principal.cpp auxiliar.cpp -o programa.exe``
	- 2)  Primero objetos, luego linkeado en exe
		- ``g++ -c auxiliar.cpp``
		- ``g++ -c principal.cpp``
		- `g++ principal.o auxiliar.o -o programa.exe` (enlace)
	- La ventaja del 2 es que obtenemos los.o y ante cambios no habrá que recompilarlo todo

# Compiling errors and warnings

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
