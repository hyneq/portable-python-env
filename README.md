# Portable Python environment
A venv-like structure that can be used as a portable environment for Python.

It differs from common virtual environments by not hardcoding any absolute paths so it works after being run from a different directory.
The same version of Python is required for binary compatibility of some modules.

## Requirements
- Linux
- supported Python 3 version with `ensurepip` available


## Installation
1.  Clone this repository to a directory you would like to use as the Python environment, e.g. `pythonenv`:

        git clone https://github.com/hyneq/portable-python-env.git python-env

    Alternatively, add this repository as a submodule to an existing repo:

        git submodule add https://github.com/hyneq/portable-python-env python-env

2.  Initialize the environment:

        python-env/bin.static/init-env


## Usage
1.  Activate the environment:

        source python-env/bin.static/activate

2.  Use the `python` or `python3` command for calling the interpreter and the `pip` or `pip3` command for installing/uninstalling packages.


## Selecting the Python interpreter
The Python interpreter can be selected in the following ways (in order of precedence):
1.  The `PYTHON_INTERPRETER` env variable, which can contain absolute path or command name which is looked up in `PATH` excluding `bin.static`.
2.  The `python_interpreter` file in the root of this Python environment, which can contain absolute path or command name which is looked up in `PATH` excluding `bin.static`.
3.  The `PYTHON_VERSION` env variable, which can contain a version number (e.g. `3.12`) which results in lookup of the command name `python<version>` in `PATH` excluding `bin.static`.
4.  The `python_version` file in the root of this Python environment, which can contain a version number (e.g. `3.12`) which results in lookup of the command name `python<version>` in `PATH` excluding `bin.static`.


## Notes
-   Use the same Python version when using the environment on different machines, otherwise the installed modules would not be found.
    You can select the Python interpreter as described in [Selecting the Python interpreter](#selecting-the-python-interpreter).

-   There are two bin directories:
    - `bin/` - for scripts installed by pip
    - `bin.static/` - for custom scripts that are part of this repository

-   It is necessary that the environment is activated when calling scripts from `bin/` or `bin.static/`, otherwise the Python environment would be ignored.

-   It is necessary to use pip by calling the command `pip` or `pip3`. Calling `python -m pip` (or `python3 -m pip`) would result in scripts not being portable.
