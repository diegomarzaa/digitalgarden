---
{"dg-publish":true,"permalink":"/02 - Permanentes/Virtual Environments (venv) Python/","title":"Virtual Environments (venv) Python","noteIcon":""}
---

Ver también:
- [[02 - Permanentes/Python en la consola\|Python en la consola]]


Conceptos:

- Son útiles para evitar conflictos, pudiendo instalar ciertos paquetes para un proyecto concreto, sin que afecte a las instalaciones de los paquetes del sistema.
- Lo que se crea es una carpeta donde quieras donde se instala una versión light de [[02 - Permanentes/Python\|Python]] que solo tendrá los módulos que necesites para ese proyecto, haciendo un source de ese path de python lo habilitarás, y todos los pip install que hagas irán a esa carpeta, en "local" digamos, sin que afecte al root o a todo el sistema.
- Caso útil: Por ejemplo si para un proyecto necesitas una versión más antigua de una libreria que ya tienes en el sistema, creas ese 'venv' y instalas la versión que quieres ahí, seguirás teniendo la más reciente en el sistema.
- [Learn Python 1: First install and Virtual Environments - Windows 10 - YouTube](https://youtu.be/x1cbYa2SSlE)

- Creación venv:   `python -m venv.venv`
	- .venv es el nombre, suele ser este por defecto

- Activación venv:   `source.venv/bin/activate`

- Path del interprete:  `.venv/bin/python3`
	- Por si el visual studio lo necesita para no mostrar errores de que faltan librerias


- Guardado de los modulos instalados:  `pip freeze > requirements.txt`
- Instalado de los modulos guardados:  `pip install -r requirements.txt`
	- Estos dos últimos comandos son por si quieres borrar la carpeta para que no ocupe espacio. O simplemente si quieres que otra persona instale automaticamente todos los modulos que tú instalaste en el venv para que funcionara el proyecto, con las versiones determinadas y todo.

PROBLEMS

- Ir con cuidado con los sources automaticos, el problema que tenía es que se ejecutaban los sources de ros2, y al hacer pip list se llenaba de todo tipo de modulos

# Usando pyenv

Inicialización correcta (en .bashrc)

```
export PATH="$HOME/.pyenv/bin:$PATH" 
eval "$(pyenv init -)" 
eval "$(pyenv virtualenv-init -)"
```

- `pyenv virtualenv --version`
- `pyenv virtualenvs`
- `pyenv virtualenv 3.11.0 interpreter_env`
- `pyenv activate interpreter_env`


Otros:

[How To Setup Jupyter Notebook in VS Code (w/ Virtual Env & Kernels) | DS](https://devinschumacher.com/how-to-setup-jupyter-notebook-virtual-environment-vs-code-kernels/#strong-prerequisites-strong)

Jupyter › Interactive Window › Text Editor: Execute Selection
	When pressing shift+enter, send selected code in a Python file to the Jupyter interactive window as opposed to the Python terminal.
