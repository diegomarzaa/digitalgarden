---
{"dg-publish":true,"permalink":"/0-Inbox/Compilación en C++/","title":"Compilación en C++","noteIcon":""}
---

Relacionados: [[3-Resources/Compilador y intérprete\|Compilador y intérprete]]

- Aspectos básicos:
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
